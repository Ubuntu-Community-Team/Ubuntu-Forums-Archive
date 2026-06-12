---
title: "Ubuntu and Modded Xbox"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by unvme1212 on 2009-01-18
Okay I think I am with minutes of having everything working right after about a month of trying but I know I must still be missing something because I can FTP into the X-Box but I can't access my Samba share or the internet from the X-Box.

I am trying to share my wireless connection to a modded X-Box through a crossover cable and my ethernet port on my Ubuntu machine.  I then want to be able to connect to a Samba share on the machine sharing the connection.  I am also hoping the X-Box can reach the internet to download info for the TV shows in my XBMC library.

I am running Intrepid with all the latest updates.  The X-Box is running XBMC Atlantis.  Below is basically everything I have changed to try and get this to work.

/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0

iface eth0 inet static
address 192.168.12.1
netmask 255.255.255.0

```

rc.local
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iptables -t nat -A POSTROUTING -s 192.168.12.0/24  -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

exit 0

```

smb.conf
```
[global]
; General server settings
netbios name = Corellia
server string = Share For Corellia
workgroup = Tatooine
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

;interfaces = 127.0.0.1, 192.168.12.0/24
interfaces = lo, eth0, ath0 (put you ethX here ,eth0 or 1 etc.)
bind interfaces only = true

hosts allow = 127.0.0.1, 192.168.12.2 (the ip of your xbox goes here)
hosts deny = 0.0.0.0/0

passdb backend = tdbsam
security = user
encrypt passwords = true
username map = /etc/samba/smbusers
obey pam restrictions = yes
invalid users = root

name resolve order = hosts wins bcast

wins support = no

; printing = CUPS
; printcap name = CUPS

syslog = 1
syslog only = yes

# Do something sensible when Samba crashes: mail the admin a backtrace
panic action = /usr/share/samba/panic-action %d

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;valid users = %S
;create mode = 0600
;directory mode = 0700
;browseable = no
;read only = yes
;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = yes

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = no
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
;[print$]
;path = /var/lib/samba/printers
;browseable = no
;guest ok = no
;read only = yes
;write list = root
;create mask = 0644
;directory mask = 0755

;[printers]
;path = /tmp
;printable = no
;guest ok = no
;browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = no
;read only = yes
;guest ok = no

[Share]
path = /home/deak/Share
browseable = no
read only = yes
guest ok = no
create mask = 0600
directory mask = 0700
force user = deak
force group = deak

```

Network Settings on the X-Box
```
IP Address: 192.168.12.2
Netmask: 255.255.255.0
Default Gateway: 192.168.12.1
DNS Server: 208.67.222.222
```

Share Address on X-Box
```
smb://deak:password@192.168.12.1/Share
```

If anyone knows what I am doing wrong and can help me I will be eternally grateful.

---

### Post by BertP on 2009-01-20
I don't really understand this myself, but I did get it to work by experimenting about a year ago.  

 in my smb.conf in addition to stuff already there.
------------------
#experiment from xbox instructions
interfaces = lo, eth0 (put you ethX here ,eth0 or 1 etc.)
bind interfaces only = true
hosts allow = 127.0.0.1, 192.168.1.28, 192.168.1.31
hosts deny = 0.0.0.0/0 

--------
[busershare]
path = /home/buser
available = yes
browsable = yes
public = yes
writable = no
------------

Good Luck!

---

### Post by BertP on 2009-01-20
I just checked again and those changes listed in my previous message can be appended to the end of the default smb.conf and it will work. At least that is what I am seeing here

You have actually installed samba, right?  I ask because I *think* that the smb.comf  was on my computer before samba was even installed!

the process goes like this:

if you need to install samba:
sudo apt-get install samba

then stop samba before you edit config
sudo /etc/init.d/samba stop

it's a good idea to backup your smb.conf before you edit it
 sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup

edit and make necessary changes
sudo gedit /etc/samba/smb.conf

then after finishing edit start samba again
sudo /etc/init.d/samba start

Thats it!
remember that if you search on this message base you can find much more robust instructions. They are what I used when setting mine up

When using XBMC I do not select "XMBC Network share"
instead I select "WORKGROUP (SMB) Network"  and I can browse without entering a password

ALSO don't run to you XBox right after you start Samba and expect it to work immediately. On my machine it seems to take a while  between the time samba is started on my computer and when samba is ready for the xbox to browse files on your PC,  I don't know what the time period is  but I think it is probably greater than 1 minute and less than 20

Again good luck!

---

### Post by iponeverything on 2009-01-22
Post the output of:

ifconfig
route -n
sudo iptables -L -n
sudo iptables -L -n -t nat
cat /proc/sys/net/ipv4/conf/all/forwarding

from the linux box.

---

### Post by unvme1212 on 2009-02-04
Sorry it took me so long to respond it's been real busy at work.  Here is the info you requested.  Thanks so much for your help.

```
**~$ ifconfig**
ath0      Link encap:Ethernet  HWaddr 00:1c:f0:a4:b5:78  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:f0ff:fea4:b578/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8631 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15797268 (15.7 MB)  TX bytes:878244 (878.2 KB)

eth0      Link encap:Ethernet  HWaddr 00:50:2c:07:86:fc  
          inet addr:192.168.12.1  Bcast:192.168.12.255  Mask:255.255.255.0
          inet6 addr: fe80::250:2cff:fe07:86fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:147064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8826498 (8.8 MB)  TX bytes:383038672 (383.0 MB)
          Interrupt:22 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:305 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21934 (21.9 KB)  TX bytes:21934 (21.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1C-F0-A4-B5-78-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45886 errors:0 dropped:0 overruns:0 frame:1031
          TX packets:26950 errors:9 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:19034781 (19.0 MB)  TX bytes:2048033 (2.0 MB)
          Interrupt:20 


**~$ route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 ath0
192.168.12.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ath0


**~$ sudo iptables -L -n**
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

[B]
~$ sudo iptables -L -n -t nat[/B]
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  192.168.12.0/24      0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


**~$ cat /proc/sys/net/ipv4/conf/all/forwarding**
1

```

---

### Post by iponeverything on 2009-02-16
I don't see anything wrong with your config that would explain ipmasq not working. 

from the Xbox command line can it ping 208.67.222.222?

> Sorry it took me so long to respond it's been real busy at work. 

Quite alright, I have been blissfully out of touch with the western world for the last 3 weeks.

---

