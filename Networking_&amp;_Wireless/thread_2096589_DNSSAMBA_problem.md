---
title: "DNS/SAMBA problem"
date: 2012-12-20
forum: Networking &amp; Wireless
---

### Post by pdc124 on 2012-12-20
I've got a script that backs up a windows client  named gaia on the network ( belongs to SWMBO). it has worked for several months but recently stopped. The only thing that has chnaged is that for some reason the DHCP-assigned IP address has changed . I need to tell the server ( ubuntu 12.04 server ) that gaia is at 192.168.2.2

within the script I want to mount the client 
 ie
 mount  -t cifs //gaia/mail  //mnt/gaia

when i put this in a script and run it i get an error
"mount error: could not resolve address for gaia: Unknown error"

How do i tell it that gaia is at 192.168.2.2 ( used to be 192.168.2.5)  ?

ive added this to resolv.conf :

root@server2:/mnt# cat /etc/resolv.conf  | grep 2
nameserver 192.168.2.1
gaia 192.168.2.2
root@server2:/mnt#


it is up on the network
root@server2:/mnt# ping 192.168.2.2 -c4
PING 192.168.2.2 (192.168.2.2) 56(84) bytes of data.
64 bytes from 192.168.2.2: icmp_req=1 ttl=128 time=1.39 ms
64 bytes from 192.168.2.2: icmp_req=2 ttl=128 time=1.29 ms
64 bytes from 192.168.2.2: icmp_req=3 ttl=128 time=1.30 ms
64 bytes from 192.168.2.2: icmp_req=4 ttl=128 time=1.27 ms

--- 192.168.2.2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 1.276/1.315/1.390/0.057 ms

but i cant ping it by name

root@server2:/mnt# ping gaia  -c4
ping: unknown host gaia
root@server2:/mnt#

 relevant bit of
root@server2:/mnt# nmap -O 192.168.2.0/24

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2012-12-06 21:09 GMT
Nmap scan report for TACHYON (192.168.2.1)
Host is up (0.00022s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE
80/tcp open  http
MAC Address: 94:44:52:3A:7A:AD (Belkin International)
Device type: WAP|broadband router
Running: Belkin embedded, Linksys embedded, Philips embedded, Siemens embedded, Telekom embedded, USRobotics embedded
OS details: Belkin F6D4630-4 v1 WAP, ADSL modem: Linksys AM300, Philips CGA5722 or SNA6500, Siemens Gigaset SX541, T-Sinus 111, or USRobotics USR9111
Network Distance: 1 hop

Nmap scan report for 192.168.2.2
Host is up (0.011s latency).
Not shown: 993 filtered ports
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
443/tcp  open  https
445/tcp  open  microsoft-ds
1947/tcp open  unknown
5357/tcp open  unknown
MAC Address: 00:23:4D:93:8F:C8 (Hon Hai Precision Ind. Co.)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running: Microsoft Windows Vista|2008|7
OS details: Microsoft Windows Vista SP0 or SP1, Server 2008 SP1, or Windows 7
Network Distance: 1 hop

---

### Post by dannyboy79 on 2012-12-20
that name/IP needs to be added to your hosts file I believe

---

### Post by SeijiSensei on 2012-12-20
Either you need to fix your DNS server so it knows the new address for gaia, or you can add a static entry to /etc/hosts with the new address.

If gaia is a server, it should have a static address. You can either do that in /etc/network/interfaces or by reserving an address on the router based on gaia's MAC address.

---

