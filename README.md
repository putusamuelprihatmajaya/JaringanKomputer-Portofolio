### Nama Repository: `JaringanKomputer-Portofolio`

## 📄 FILE 1: README.md (JaringanKomputer-Portofolio)

# JaringanKomputer-Portofolio

## 👤 Informasi Dosen
- **Nama:** Putu Samuel Prihatmajaya, M.Kom
- **Program Studi:** Teknik Informatika
- **Instansi:** STIKOM Yos Sudarso Purwokerto
- **Mata Kuliah:** Jaringan Komputer

## 📚 Tentang Repository Ini
Repository ini adalah **portofolio** untuk mata kuliah **Jaringan Komputer**.

Mahasiswa dapat melihat repository ini sebagai **referensi** dalam membuat portofolio GitHub mereka sendiri.

## 🎯 Apa yang Bisa Dipelajari dari Repository Ini?

| No | Aspek | Penjelasan |
|----|-------|------------|
| 1 | **Struktur Folder** | Cara mengorganisir file berdasarkan topik praktikum |
| 2 | **Penamaan File** | Cara memberi nama file yang jelas dan profesional |
| 3 | **README.md** | Cara membuat halaman depan portofolio yang informatif |
| 4 | **Dokumentasi** | Cara mendokumentasikan konfigurasi dan skrip |
| 5 | **Version Control** | Cara menggunakan Git dan GitHub untuk portofolio |

## 📂 Struktur Folder yang Direkomendasikan


JaringanKomputer-Portofolio/
├── README.md                      # Halaman depan (wajib!)
│
├── 01-Pengenalan-Jaringan/        # Subnetting, OSI Layer, TCP/IP
│   ├── README.md
│   └── subnetting_calculator.py
│
├── 02-VLAN/                       # Konfigurasi VLAN & Trunking
│   ├── README.md
│   └── vlan_config.txt
│
├── 03-Static-Routing/             # Static Routing
│   └── static_route_config.txt
│
├── 04-Dynamic-Routing/            # RIP, OSPF, EIGRP
│   └── ospf_config.txt
│
├── 05-DHCP-DNS/                   # DHCP & DNS Server
│   ├── dhcpd.conf
│   └── named.conf
│
├── 06-Analisis-Paket/             # Wireshark, Scapy
│   ├── analyze_pcap.py
│   └── capture.pcapng
│
├── 07-Network-Security/           # ACL, Firewall, SSH
│   └── acl_config.txt
│
├── 08-Mininet-SDN/                # SDN, Mininet
│   └── simple_topology.py
│
├── 09-Monitoring/                 # Ping, iperf3, monitoring
│   └── ping_monitor.py
│
└── UTS_UAS/                       # Jawaban ujian
    └── README.md

## 📋 Instruksi untuk Mahasiswa

### Langkah-langkah Membuat Portofolio:

1. **Buat akun GitHub** (jika belum punya) di [github.com](https://github.com)

2. **Buat repository baru** dengan nama:

   JaringanKomputer-Portofolio

3. **Pilih pengaturan:**
   - ✅ Public (agar bisa dilihat industri)
   - ✅ Add a README file

4. **Isi description:**
   
   Portofolio mata kuliah Jaringan Komputer - semester 4
   

5. **Buat struktur folder** seperti contoh di atas

6. **Upload file-file** yang sudah Anda buat selama praktikum:
   - File konfigurasi (.txt, .conf)
   - Skrip Python/Bash
   - File Packet Tracer (.pkt)
   - Hasil capture Wireshark (.pcapng)
   - Laporan/latihan (.pdf, .docx)

7. **Edit README.md** ganti dengan biodata Anda sendiri

8. **Kumpulkan link repository** ke Google Classroom

## 🛠 Tools yang Digunakan dalam Mata Kuliah Ini

| Kategori | Tools |
|----------|-------|
| **Simulasi** | Cisco Packet Tracer, Mininet |
| **Analisis** | Wireshark, Scapy |
| **Scripting** | Python, Bash |
| **Monitoring** | ping, iperf3, netstat |
| **Konfigurasi** | Cisco IOS, Linux netplan |

## 📫 Kontak Dosen
- **GitHub:** [github.com/putusamuelprihatmajaya](https://github.com/putusamuelprihatmajaya)
- **Email:** [email dosen]
- **Google Classroom:** [kode kelas]

## 📄 FILE 2: README di dalam folder (01-Pengenalan-Jaringan/README.md)

File ini sebagai contoh dokumentasi di dalam sub-folder.


# 01 - Pengenalan Jaringan

## Topik yang Dipelajari
- Model OSI Layer (7 layer)
- Model TCP/IP
- Subnetting IP Address
- Perhitungan CIDR

## File dalam Folder Ini
| File | Deskripsi |
|------|-----------|
| `subnetting_calculator.py` | Kalkulator subnetting berbasis Python |
| `tugas_subnetting.pdf` | Hasil tugas perhitungan subnetting |

## Cara Menjalankan Kalkulator Subnetting

python3 subnetting_calculator.py


## Hasil Belajar
Setelah mempelajari topik ini, mahasiswa diharapkan mampu:
1. Menjelaskan fungsi masing-masing layer OSI
2. Menghitung subnet mask, network ID, dan broadcast address
3. Merancang skema IP addressing untuk jaringan sederhana




## 📄 FILE 3: Contoh Kode (subnetting_calculator.py)

Simpan di folder `01-Pengenalan-Jaringan/`

#!/usr/bin/env python3
"""
SUBNETTING CALCULATOR
Contoh program Python untuk menghitung informasi subnetting

Dibuat untuk: Mata Kuliah Jaringan Komputer
Dosen: Putu Samuel Prihatmajaya, M.Kom
"""

def subnetting_calculator(ip_address, subnet_mask):
    """
    Menghitung informasi subnetting dari IP address dan subnet mask
    """
    
    def ip_to_binary(ip):
        return ''.join([format(int(octet), '08b') for octet in ip.split('.')])
    
    def binary_to_ip(binary):
        octets = [str(int(binary[i:i+8], 2)) for i in range(0, 32, 8)]
        return '.'.join(octets)
    
    # Parsing subnet mask (support CIDR seperti /24)
    if subnet_mask.startswith('/'):
        cidr = int(subnet_mask[1:])
        mask_binary = '1' * cidr + '0' * (32 - cidr)
        mask_ip = binary_to_ip(mask_binary)
    else:
        mask_ip = subnet_mask
        mask_binary = ip_to_binary(mask_ip)
        cidr = mask_binary.count('1')
    
    # Konversi IP ke biner
    ip_binary = ip_to_binary(ip_address)
    
    # Hitung Network ID (AND operation)
    network_binary = ''.join(['1' if (ip_binary[i] == '1' and mask_binary[i] == '1') else '0' for i in range(32)])
    
    # Hitung Broadcast Address
    broadcast_binary = network_binary[:cidr] + '1' * (32 - cidr)
    
    # Hitung First dan Last Host
    first_host_binary = network_binary[:cidr] + '0' * (32 - cidr - 1) + '1'
    last_host_binary = network_binary[:cidr] + '1' * (32 - cidr - 1) + '0'
    
    # Konversi ke IP
    network_ip = binary_to_ip(network_binary)
    broadcast_ip = binary_to_ip(broadcast_binary)
    first_host = binary_to_ip(first_host_binary)
    last_host = binary_to_ip(last_host_binary)
    
    # Jumlah host
    total_hosts = 2 ** (32 - cidr)
    usable_hosts = total_hosts - 2
    
    # Tampilkan hasil
    print("=" * 50)
    print("HASIL PERHITUNGAN SUBNETTING")
    print("=" * 50)
    print(f"IP Address        : {ip_address}")
    print(f"Subnet Mask       : {mask_ip} (CIDR: /{cidr})")
    print(f"Network ID        : {network_ip}")
    print(f"Broadcast Address : {broadcast_ip}")
    print(f"First Host        : {first_host}")
    print(f"Last Host         : {last_host}")
    print(f"Total Hosts       : {total_hosts}")
    print(f"Usable Hosts      : {usable_hosts}")
    print("=" * 50)


if __name__ == "__main__":
    print("SUBNETTING CALCULATOR")
    print("-" * 30)
    
    ip = input("Masukkan IP Address (contoh: 192.168.1.0): ")
    mask = input("Masukkan Subnet Mask (contoh: 255.255.255.0 atau /24): ")
    
    subnetting_calculator(ip, mask)

---

## 📄 FILE 4: Contoh File Konfigurasi (vlan_config.txt)

Simpan di folder `02-VLAN/`


========================================
KONFIGURASI VLAN PADA SWITCH CISCO
========================================
Mata Kuliah: Jaringan Komputer
Topik: VLAN dan Trunking

========================================
TOPLOGI
========================================
Switch 1 (S1) terhubung ke:
- PC1 (VLAN 10) - Port Fa0/1
- PC2 (VLAN 20) - Port Fa0/2
- Router (Trunk) - Port Fa0/24 (untuk inter-VLAN routing)

========================================
KONFIGURASI VLAN
========================================

! Membuat VLAN
S1(config)# vlan 10
S1(config-vlan)# name SALES
S1(config-vlan)# exit

S1(config)# vlan 20
S1(config-vlan)# name ENGINEERING
S1(config-vlan)# exit

! Assign port ke VLAN
S1(config)# interface fastEthernet 0/1
S1(config-if)# switchport mode access
S1(config-if)# switchport access vlan 10
S1(config-if)# exit

S1(config)# interface fastEthernet 0/2
S1(config-if)# switchport mode access
S1(config-if)# switchport access vlan 20
S1(config-if)# exit

========================================
KONFIGURASI TRUNK (ke Router)
========================================

S1(config)# interface fastEthernet 0/24
S1(config-if)# switchport mode trunk
S1(config-if)# switchport trunk allowed vlan 10,20
S1(config-if)# exit

========================================
VERIFIKASI
========================================

! Cek konfigurasi VLAN
S1# show vlan brief

! Cek konfigurasi trunk
S1# show interfaces trunk

========================================
HASIL VERIFIKASI
========================================

VLAN 10 (SALES) - Port: Fa0/1, Fa0/3
VLAN 20 (ENGINEERING) - Port: Fa0/2, Fa0/4
Trunk aktif di port Fa0/24 dengan allowed VLAN 10,20


---

## 📄 FILE 5: Contoh Skrip Monitoring (ping_monitor.py)

Simpan di folder `09-Monitoring/`


#!/usr/bin/env python3
"""
PING MONITOR
Contoh skrip monitoring koneksi jaringan dengan Python

Dibuat untuk: Mata Kuliah Jaringan Komputer
Dosen: Putu Samuel Prihatmajaya, M.Kom
"""

import subprocess
import time
from datetime import datetime
import sys

def ping_host(host, count=4):
    """
    Melakukan ping ke host dan mengembalikan hasilnya
    """
    try:
        # Untuk Windows: ping -n, untuk Linux/Mac: ping -c
        import platform
        if platform.system().lower() == "windows":
            cmd = ["ping", "-n", str(count), host]
        else:
            cmd = ["ping", "-c", str(count), host]
        
        result = subprocess.run(cmd, capture_output=True, text=True, timeout=10)
        return result.returncode == 0, result.stdout
    except subprocess.TimeoutExpired:
        return False, "Timeout"
    except Exception as e:
        return False, str(e)

def extract_ping_time(output):
    """
    Mengekstrak waktu ping dari output
    """
    import re
    # Cari pola seperti "time=12.3 ms" atau "time=12ms"
    match = re.search(r'time[=<](\d+\.?\d*)\s*ms', output)
    if match:
        return float(match.group(1))
    return None

def monitor_ping(host, interval=5, duration=60):
    """
    Monitoring ping secara berkelanjutan
    """
    print("=" * 60)
    print(f"PING MONITOR - Target: {host}")
    print(f"Interval: {interval} detik | Durasi: {duration} detik")
    print(f"Mulai: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}")
    print("=" * 60)
    
    start_time = time.time()
    success_count = 0
    total_count = 0
    ping_times = []
    
    while time.time() - start_time < duration:
        timestamp = datetime.now().strftime('%H:%M:%S')
        success, output = ping_host(host, count=1)
        total_count += 1
        
        if success:
            ping_time = extract_ping_time(output)
            success_count += 1
            if ping_time:
                ping_times.append(ping_time)
                status = f"✅ OK - {ping_time} ms"
            else:
                status = "✅ OK"
        else:
            status = "❌ FAILED - No response"
        
        print(f"[{timestamp}] {status}")
        time.sleep(interval)
    
    # Ringkasan
    print("\n" + "=" * 60)
    print("RINGKASAN")
    print("=" * 60)
    print(f"Total ping      : {total_count}")
    print(f"Berhasil        : {success_count}")
    print(f"Gagal           : {total_count - success_count}")
    print(f"Success rate    : {(success_count/total_count)*100:.1f}%")
    
    if ping_times:
        print(f"Min ping time   : {min(ping_times):.2f} ms")
        print(f"Max ping time   : {max(ping_times):.2f} ms")
        print(f"Avg ping time   : {sum(ping_times)/len(ping_times):.2f} ms")
    
    print("=" * 60)


if __name__ == "__main__":
    # Target default: Google DNS
    target = "8.8.8.8"
    
    if len(sys.argv) > 1:
        target = sys.argv[1]
    
    monitor_ping(target, interval=5, duration=30)


---

## 📋 Struktur Lengkap Repository Dosen

Setelah semua file dibuat, struktur repository Anda akan terlihat seperti ini:

JaringanKomputer-Contoh-Portofolio/
│
├── README.md                                 # Halaman utama (sudah dibuat)
│
├── 01-Pengenalan-Jaringan/
│   ├── README.md                             # Contoh dokumentasi folder
│   └── subnetting_calculator.py              # Contoh kode Python
│
├── 02-VLAN/
│   └── vlan_config.txt                       # Contoh file konfigurasi
│
├── 03-Static-Routing/
│   └── (kosong, bisa diisi nanti)
│
├── 04-Dynamic-Routing/
│   └── (kosong, bisa diisi nanti)
│
├── 05-DHCP-DNS/
│   └── (kosong, bisa diisi nanti)
│
├── 06-Analisis-Paket/
│   └── (kosong, bisa diisi nanti)
│
├── 07-Network-Security/
│   └── (kosong, bisa diisi nanti)
│
├── 08-Mininet-SDN/
│   └── (kosong, bisa diisi nanti)
│
├── 09-Monitoring/
│   └── ping_monitor.py                       # Contoh skrip monitoring
│
└── UTS_UAS/
    └── README.md                             # Contoh dokumentasi ujian

---

## 📌 Instruksi yang Dibagikan ke Mahasiswa

Setelah repository contoh Anda selesai, copy-paste teks ini ke Google Classroom:

---

**📢 PENGUMUMAN: CONTOH PORTOFOLIO JARINGAN KOMPUTER**

Kepada mahasiswa mata kuliah Jaringan Komputer,

Bapak telah membuat **repository contoh** untuk portofolio GitHub. Silakan lihat sebagai referensi.

**Link repository contoh:**
https://github.com/putusamuelprihatmajaya/JaringanKomputer-Contoh-Portofolio

**Apa yang bisa kalian lihat di sana:**
1. Struktur folder yang rapi (per topik praktikum)
2. File README.md sebagai halaman depan
3. Contoh kode Python (subnetting calculator, ping monitor)
4. Contoh file konfigurasi (VLAN, routing)
5. Cara mendokumentasikan setiap folder

**Tugas kalian:**
1. Buat repository dengan nama `JaringanKomputer-Portofolio`
2. Buat struktur folder seperti contoh
3. Upload semua file praktikum yang sudah kalian buat
4. Isi README.md dengan biodata kalian
5. Kumpulkan link repository ke Google Classroom

**Deadline:** [tanggal]
