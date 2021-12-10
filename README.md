# Jarkom Modul 4 E03 2021

Daftar Kelompok:

1. Reyhan Naufal Rahman - 05111940000171
2. Vicky Thirdian - 05111940000211
3. Fiodhy Ardito Narawangsa - 05111940000218

## Subnetting & Routing

### Foosha
```
auto eth0
iface eth0 inet static
 address 192.168.122.2
 netmask 255.255.255.252
 gateway 192.168.122.1
     
auto eth1
iface eth1 inet static
 address 192.201.7.145
 netmask 255.255.255.252

auto eth2
iface eth2 inet static
 address 192.201.7.149
 netmask 255.255.255.252
```
### Water7
```
auto eth0
iface eth0 inet static
 address 192.201.7.146
 netmask 255.255.255.252
 gateway 192.201.7.145

auto eth1
iface eth1 inet static
 address 192.201.7.1
 netmask 255.255.255.128

auto eth2
iface eth2 inet static
 address 192.201.0.1
 netmask 255.255.252.0

auto eth3
iface eth3 inet static
 address 192.201.7.129
 netmask 255.255.255.248
```
### Guanhou
```
auto eth0
iface eth0 inet static
 address 192.201.7.150
 netmask 255.255.255.252
 gateway 192.201.7.149

auto eth1
iface eth1 inet static
 address 192.201.4.1
 netmask 255.255.254.0

iface eth2 inet static
auto eth2
 address 192.201.7.137
 netmask 255.255.255.248

auto eth3
iface eth3 inet static
 address 192.201.6.1
 netmask 255.255.255.0
```
### Jipangu
```
auto eth0
iface eth0 inet static
 address 192.201.7.131
 netmask 255.255.255.248
 gateway 192.201.7.129
```
### Doriki
```
auto eth0
iface eth0 inet static
 address 192.201.7.130
 netmask 255.255.255.248
 gateway 192.201.7.129
```
### Maingate
```
auto eth0
iface eth0 inet static
 address 192.201.7.139
 netmask 255.255.255.248
 gateway 192.201.7.137
```
### Jorge
```
auto eth0
iface eth0 inet static
 address 192.201.7.139
 netmask 255.255.255.248
 gateway 192.201.7.137
```
### Routing
```
route add -net 192.201.6.0 netmask 255.255.255.0 gw 192.201.7.150
route add -net 192.201.7.128 netmask 255.255.255.248 gw 192.201.7.146
route add -net 192.201.7.0 netmask 255.255.255.128 gw 192.201.7.146
route add -net 192.201.0.0 netmask 255.255.252.0 gw 192.201.7.146
route add -net 192.201.4.0 netmask 255.255.254.0 gw 192.201.7.150
route add -net 192.201.7.136 netmask 255.255.255.248 gw 192.201.7.150
```
## Soal & Penyelesaian

1. Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Foosha menggunakan iptables, tetapi Luffy tidak ingin menggunakan MASQUERADE.
    ```
    iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 192.168.122.2 -s 192.201.0.0/16
    ```
2. Kalian diminta untuk mendrop semua akses HTTP dari luar Topologi kalian pada server yang merupakan DHCP Server dan DNS Server demi menjaga keamanan.

3. Karena kelompok kalian maksimal terdiri dari 3 orang. Luffy meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 3 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.

4. Akses dari subnet Blueno dan Cipher hanya diperbolehkan pada pukul 07.00 - 15.00 pada hari Senin sampai Kamis.

5. Akses dari subnet Elena dan Fukuro hanya diperbolehkan pada pukul 15.01 hingga pukul 06.59 setiap harinya.

6. Karena kita memiliki 2 Web Server, Luffy ingin Guanhao disetting sehingga setiap request dari client yang mengakses DNS Server akan didistribusikan secara bergantian pada Jorge dan Maingate