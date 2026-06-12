---
title: "half of my network just stoped working"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by chrismitt2002 on 2010-07-17
not real shure were to start explaining but here it goes 
i just got a new tv (using it as a monitor)along side with my smaller 19inch i use for a 2nd screen on my everyday pc i use vga for my server and 2nd screen on my everyday pc and dvi to hdmi for the 32 inch screen i had ubuntu 9.10 running perfect on my server and 10.04 on my everyday pc both linux 9.10 and 10.04 worked both ways includeing vbox runnin xp on my everyday pc for a few windows only apps when i went to shutdown to add a replcement hd and i went to turn it back on it would no longer boot properly so i decided to just upgrade so i did a clean install and set my network up just like before and it was working just fine both ways even vbox had 0 problems same as before here is the fstab and samba and fstab from both my server pc and my everyday pc now here is the problem the server pc asked to do a part upgrade so i did then asked to be rebooted and i did thinking nothing of it and i also uninstalled a bunch of stuff games video players etc on the server as i had no use for as it is a server and now i cant connect via mapped drives from everyday pc to the server here is the command i use in term 

owner@intel-quad:~$ sudo smbmount //192.168.1.2/G-1.5tb /media/G -o username=owner ,password=123,uid-1000,mask000
[sudo] password for owner: 
Password: 
retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
owner@intel-quad:~$ 

but yet when i Go To network and browse that way i can connect to the server's share's but yet the server can connect to the everyday pc i have it set up just like before with the exception of a 1.5tb hd in place of a 500gb hd that is now offline and contains backup im relly @ a complete loss i think the part upgrade might have broken the network any help would be great

---

### Post by chrismitt2002 on 2010-07-18
bump

---

### Post by chrismitt2002 on 2010-07-22
bump

---

### Post by endotherm on 2010-07-22
ok, from the pc, ping the server using the IP address you showed, and let us know if it works for that IP address. that will establish whether the network itself is stable. after that we can start troubleshooting samba

---

### Post by chrismitt2002 on 2010-07-22
well i did a reinstall tonight on my server thinking that was the problem but it doesnt seem that way as i had hoped it was that pc and not this it  still can not connect to it from my everyday pc so i HAS to be this pc i did the ping [B]owner@intel-quad:~$ ping 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
64 bytes from 192.168.1.3: icmp_seq=1 ttl=64 time=0.116 ms
64 bytes from 192.168.1.3: icmp_seq=2 ttl=64 time=0.080 ms
64 bytes from 192.168.1.3: icmp_seq=3 ttl=64 time=0.077 ms
64 bytes from 192.168.1.3: icmp_seq=4 ttl=64 time=0.081 ms
^C
--- 192.168.1.3 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.077/0.088/0.116/0.018 ms
owner@intel-quad:~$ 
it did respond same with the server to this pc

---

### Post by endotherm on 2010-07-23
ok, i'm noticing in your smbmount in your fstab that the ip address of the server was expected to be 192.168.1.2, but your ping shows .1.3. have you reconciled that change?

tell you what, post back an ifconfig from both boxes, and your current fstab and the smb.conf off your server. how are you creating your shares? in the smb.conf, or through nautilus?

---

### Post by chrismitt2002 on 2010-07-23
192.168.1.2 is my everyday box and 192.168.1.3 is my server

here is the ping from my server to this pc 

owner@server-pc:~$ ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=0.108 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=64 time=0.089 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=64 time=0.092 ms
64 bytes from 192.168.1.2: icmp_seq=4 ttl=64 time=0.088 ms
64 bytes from 192.168.1.2: icmp_seq=5 ttl=64 time=0.081 ms
64 bytes from 192.168.1.2: icmp_seq=6 ttl=64 time=0.087 ms
64 bytes from 192.168.1.2: icmp_seq=7 ttl=64 time=0.083 ms
64 bytes from 192.168.1.2: icmp_seq=8 ttl=64 time=0.087 ms
^C
--- 192.168.1.2 ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 6994ms
rtt min/avg/max/mdev = 0.081/0.089/0.108/0.011 ms

here is the ping from my everyday pc to the server 
owner@intel-quad:~$ ping 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
64 bytes from 192.168.1.3: icmp_seq=1 ttl=64 time=0.094 ms
64 bytes from 192.168.1.3: icmp_seq=2 ttl=64 time=0.083 ms
64 bytes from 192.168.1.3: icmp_seq=3 ttl=64 time=0.081 ms
64 bytes from 192.168.1.3: icmp_seq=4 ttl=64 time=0.089 ms
^C
--- 192.168.1.3 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.081/0.086/0.094/0.012 ms
owner@intel-quad:~$

---

### Post by endotherm on 2010-07-23
if you restart samba, does the functionality return, or does it continue to be naughty?
```
sudo service smbd restart
```

if it still does not work, on both boxes, run this command and post back with the output:
```
sudo testparm -s
```

this will validate your smb.conf and display any errors in format.
if both verify correctly then we'll look at the settings themselves.

---

### Post by chrismitt2002 on 2010-07-23
[print$]
	path = /var/lib/samba/printers
	write list = root
	create mask = 0664
	directory mask = 0775
	guest ok = Yes

[printers]
	path = /tmp
	guest ok = Yes
	printable = Yes
	browseable = No
	browsable = No

[D-931gb]
	path = /media/D-931gb/
	force user = owner
	read only = No
	create mask = 0644

[E-931gb]
	path = /media/E-931gb/
	force user = owner
	read only = No
	create mask = 0644

[F-931gb]
	path = /media/F-931gb/
	force user = owner
	read only = No
	create mask = 0644

[G-931gb]
	path = /media/G-931gb/
	force user = owner
	read only = No
	create mask = 0644

[H-698gb]
	path = /media/H-698gb/
	force user = owner
	read only = No
	create mask = 0644

[I-931gb]
	path = /media/I-931gb/
	force user = owner
	read only = No
	create mask = 0644

[J-931gb]
	path = /media/J-931gb/
	force user = owner
	read only = No
	create mask = 0644

[K-931gb]
	path = /media/K-931gb/
	force user = owner
	read only = No
	create mask = 0644
owner@intel-quad:~$ 

also the only pc that isnt working correctly is from everyday pc to server + vbox to server not server to everyday pc 
but here is the relly odd thing that i dont get is that when i goto network and browse that way i can connect to server shares but when i use owner@intel-quad:~$ sudo smbmount //192.168.1.3/D-1.5tb /media/D -o username=owner ,password=10121981,uid-1000,mask000
[sudo] password for owner: 
Password: 
retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
owner@intel-quad:~$ 

i get that but on the server it works perfect

---

### Post by endotherm on 2010-07-23
your path looks wrong in the fstab. shouldn't it be:
```
sudo smbmount //192.168.1.3/D-931gb /media/D -o username=owner ,password=10121981,uid-1000,mask000
```?

you don't appear to have a share called D-1.5tb

---

### Post by chrismitt2002 on 2010-07-24
i do on the server and the code u gave me puked out the same error
owner@intel-quad:~$ sudo smbmount //192.168.1.3/D-931gb /media/D -o username=owner ,password=10121981,uid-1000,mask000
[sudo] password for owner: 
Password: 
retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
owner@intel-quad:~$

---

### Post by chrismitt2002 on 2010-07-26
bump

---

### Post by chrismitt2002 on 2010-07-29
bump

---

### Post by chrismitt2002 on 2010-08-05
bump

---

