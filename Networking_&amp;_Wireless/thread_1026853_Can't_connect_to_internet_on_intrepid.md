---
title: "Can't connect to internet on intrepid"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by Sashin on 2008-12-31
I use a PPPOE connection and when I try to connect to create a connection it says:

Interface eth0 has an MTU of 64 ---should be 1500

and once it's finished scanning the ethernet devices it says

"Sorry I scanned 2 interfaces but the Access concentrator of your provider did not respond..."

Does anyone know what this means or how to fix this?

---

### Post by pytheas22 on 2008-12-31
You can change the MTU of eth0 by typing:
```

sudo ifconfig eth0 mtu 1500
```

Then try connecting again.  Does this fix it, or at least change the error message?

---

### Post by Sashin on 2008-12-31
it gets rid of that message, but it still says that the access concentrator isn't responding.

---

### Post by pytheas22 on 2008-12-31
Have you checked all the hardware, making sure cables are connected, etc.?  Does the same configuration work on a Windows computer?

Also, what is the output of these commands:
```

sudo dhclient eth0
lspci -nn
```

---

### Post by Sashin on 2008-12-31
I don't have a windows computer. It works on both my computers with Hardy. But when I try to boot from the intrepid live CD it doesn't work. I've tried installing Intrepid on another hardrive, and trying there and it doesn't work.

I'm about to go somewhere now, I won't be able to check those commands until I get back.

---

### Post by superprash2003 on 2009-01-01
also post output of ifconfig.. you may not be getting an ip

---

### Post by Sashin on 2009-01-01
```
ubuntu@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No buffer space available
Listening on LPF/eth0/00:14:85:38:79:30
Sending on   LPF/eth0/00:14:85:38:79:30
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
send_packet: Message too long
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ubuntu@ubuntu:~$ lspci -nm
00:00.0 "0580" "10de" "005e" -ra3 "1458" "5000"
00:01.0 "0601" "10de" "0050" -ra3 "1458" "0c11"
00:01.1 "0c05" "10de" "0052" -ra2 "1458" "0c11"
00:02.0 "0c03" "10de" "005a" -ra2 -p10 "1458" "5004"
00:02.1 "0c03" "10de" "005b" -ra3 -p20 "1458" "5004"
00:04.0 "0401" "10de" "0059" -ra2 "1458" "ae01"
00:06.0 "0101" "10de" "0053" -rf2 -p8a "f458" "5002"
00:07.0 "0101" "10de" "0054" -rf3 -p85 "1458" "b003"
00:08.0 "0101" "10de" "0055" -rf3 -p85 "1458" "b003"
00:09.0 "0604" "10de" "005c" -ra2 -p01 "" ""
00:0a.0 "0680" "10de" "0057" -ra3 "1458" "e000"
00:0b.0 "0604" "10de" "005d" -ra3 "" ""
00:0c.0 "0604" "10de" "005d" -ra3 "" ""
00:0d.0 "0604" "10de" "005d" -ra3 "" ""
00:0e.0 "0604" "10de" "005d" -ra3 "" ""
00:18.0 "0600" "1022" "1100" "" ""
00:18.1 "0600" "1022" "1101" "" ""
00:18.2 "0600" "1022" "1102" "" ""
00:18.3 "0600" "1022" "1103" "" ""
05:00.0 "0300" "10de" "0141" -ra2 "" ""

```

---

### Post by Sashin on 2009-01-01
```
ubuntu@ubuntu:~$ lspci -nn
00:00.0 Memory controller [0580]: nVidia Corporation CK804 Memory Controller [10de:005e] (rev a3)
00:01.0 ISA bridge [0601]: nVidia Corporation CK804 ISA Bridge [10de:0050] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation CK804 SMBus [10de:0052] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005a] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005b] (rev a3)
00:04.0 Multimedia audio controller [0401]: nVidia Corporation CK804 AC'97 Audio Controller [10de:0059] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation CK804 IDE [10de:0053] (rev f2)
00:07.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0054] (rev f3)
00:08.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0055] (rev f3)
00:09.0 PCI bridge [0604]: nVidia Corporation CK804 PCI Bridge [10de:005c] (rev a2)
00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev a3)
00:0b.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0c.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0d.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0e.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
05:00.0 VGA compatible controller [0300]: nVidia Corporation NV43 [GeForce 6600] [10de:0141] (rev a2)
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:85:38:79:30  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1300 (1.3 KB)  TX bytes:1869 (1.8 KB)
          Interrupt:21 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140496 (140.4 KB)  TX bytes:140496 (140.4 KB)


```

---

### Post by Copernicus1234 on 2009-01-01
Never mind.

---

### Post by Sashin on 2009-01-01
Huh?

---

### Post by pytheas22 on 2009-01-01
hmmm, I'm sorry to ask for more output, but I'm still not sure where to go here.  Could you please post:
```

sudo ifconfig eth0 mtu 1500
sudo dhclient eth0
```

as well as the total output that you get when you try to initiate your pppoe connection?

---

### Post by Sashin on 2009-01-02
ubuntu@ubuntu:~$ sudo ifconfig eth0 mtu 1500
ubuntu@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:14:85:38:79:30
Sending on   LPF/eth0/00:14:85:38:79:30
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.2 from 192.168.1.1
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 33542 seconds.


I don't get any code when I try to create a connection with "sudo pppoeconf".

---

### Post by superprash2003 on 2009-01-02
your ifconfig shows eth0 without an ip.. that is probably the reason.. have you tried static ip/

---

### Post by pytheas22 on 2009-01-02
> Listening on LPF/eth0/00:14:85:38:79:30
Sending on LPF/eth0/00:14:85:38:79:30
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.2 from 192.168.1.1
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 33542 seconds.

According to the output above, it looks like you did manage to get an IP address on eth0, which is a good sign.  Were you able to browse the Internet after that?  If not, please post the output (in this order) of these commands:
```

sudo ifconfig eth0 mtu 1500
sudo dhclient eth0
wget google.com
ping -c 5 google.com
ping 74.125.45.100
cat /etc/resolv.conf
```

I think we're closer to a solution now.

---

### Post by Sashin on 2009-01-02
I was able to get internet working after that. I didn't check before.

Is that a permanent fix?

---

### Post by pytheas22 on 2009-01-02
Good!  To make the fix permanent, we can just create a boot script.  To do that, first type:

```
sudo gedit /etc/init.d/internet-fix.sh
```

A blank file will pop open.  Put this into it:
```

#!/bin/bash

#this script changes the mtu of eth0 and runs dhclient to get an IP address; http://ubuntuforums.org/showthread.php?t=1026853&page=2 for more information

ifconfig eth0 mtu 1500
dhclient eth0
```

Then save and close the file, and run these commands:
```

cd /etc/init.d
sudo chmod +x internet-fix.sh
sudo update-rc.d internet-fix.sh defaults
```

Now reboot.  After rebooting, you should automatically be connected to the Internet.  Does this work?

---

### Post by Sashin on 2009-01-02
No it doesn't work. I did what you said, restarted and internet wasn't there. I had some error about gedit not being able to do something, but when I checked the internet file was there. I'll try again.

---

### Post by pytheas22 on 2009-01-02
Sorry that didn't work; it's probably just some issue with the script.  Could you please post the output of these commands after a fresh reboot:
```

ls -l /etc/init.d/internet-fix.sh
ifconfig eth0
sudo dhclient eth0
dmesg | grep -e eth
```

I'm thinking that the problem could also be caused by Network Manager (the applet in your upper Gnome panel that looks like two computer monitors) interfering with the changes made by the boot script; in that case, you could just uninstall NM by typing:
```

sudo apt-get remove network-manager
```

But if you need Network Manager manager for anything, like connecting to wireless, you should probably not uninstall it.

---

### Post by Sashin on 2009-01-02
```
jude@home:~$ ls -l /etc/init.d/internet-fix.sh
-rwxr-xr-x 1 root root 206 2009-01-03 08:04 /etc/init.d/internet-fix.sh
jude@home:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:14:85:38:79:30  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2191 (2.1 KB)  TX bytes:5387 (5.3 KB)
          Interrupt:21 Base address:0x8000 

jude@home:~$ sudo dhclient eth0
[sudo] password for jude: 
There is already a pid file /var/run/dhclient.pid with pid 6220
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No buffer space available
Listening on LPF/eth0/00:14:85:38:79:30
Sending on   LPF/eth0/00:14:85:38:79:30
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
send_packet: Message too long
DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
send_packet: Message too long
No DHCPOFFERS received.
Trying recorded lease 192.168.1.2
SIOCSIFADDR: No buffer space available
SIOCSIFNETMASK: Cannot assign requested address
SIOCSIFBRDADDR: Cannot assign requested address
connect: Network is unreachable
SIOCSIFADDR: No buffer space available

```

---

### Post by wmdiem on 2009-01-02
> **superprash2003 said:**
> your ifconfig shows eth0 without an ip.. that is probably the reason.. have you tried static ip/

I was under the impression that pppoe should be setup before an ip address is asigned.

---

### Post by pytheas22 on 2009-01-02
hmmm, it looks like the script that we wrote isn't being run for some reason.  Could you please run these commands again and post the output:
```

cd /etc/init.d
sudo chmod +x internet-fix.sh
sudo update-rc.d internet-fix.sh
cat /etc/init.d/internet-fix.sh
```

Then reboot.  Do you still have no connection?

---

### Post by Sashin on 2009-01-02
> shaili@home:/etc/init.d$ sudo chmod +x internet-fix.sh
shaili@home:/etc/init.d$ sudo update-rc.d internet-fix.sh
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
shaili@home:/etc/init.d$ cat /etc/init.d/internet-fix.sh
#!/bin/bash this script changes the mtu of eth0 and runs dhclient to get 
#an IP address; [http://ubuntuforums.org/showthread.php?t=1026853&page=2](http://ubuntuforums.org/showthread.php?t=1026853&page=2) 
#for more information
ifconfig eth0 mtu 1500
dhclient eth0


Still no connection on reboot

---

### Post by pytheas22 on 2009-01-03
ahhh sorry it still won't work.

Please run this command:

```
touch /root/worked
```

Then reboot, and please tell me the output after rebooting of:
```

ls -l /root/worked
```

---

### Post by Sashin on 2009-01-03
```
shaili@home:~$ ls -l /root/worked
-rw-r--r-- 1 root root 0 2009-01-03 19:15 /root/worked
shaili@home:~$ 
```

---

### Post by kevdog on 2009-01-03
Pytheas

with the update-rc.d command would you like to place the script at start position 99 so it is run last in the boot sequence rather than at 20 (which I think is the default position)?

So first remove the script:

sudo update-rc.d -f internet-fix.sh remove

Then re-add it with:

sudo update-rc.d internet-fix.sh defaults 99

---

### Post by pytheas22 on 2009-01-03
> with the update-rc.d command would you like to place the script at start position 99 so it is run last in the boot sequence rather than at 20 (which I think is the default position)?


Thanks for pointing this out.  I actually don't know much about how the init scripts really work, but running this script as late as possible might help.

So Sashin, please try running these commands:

So first remove the script:

```
sudo update-rc.d -f internet-fix.sh remove
sudo update-rc.d internet-fix.sh defaults 99 
```

Then reboot.  Does your connection work this time?  If not, is it still sufficient to type just:
```

sudo ifconfig eth0 mtu 1500
sudo dhclient eth0
```

to get connected?

---

### Post by Sashin on 2009-01-03
It's not working.

I can type in that second code to get connected, but I'd really much prefer to have it connected at boot time. I'm not the only one using the computer.

---

### Post by Sashin on 2009-01-03
It works now, Problem solved. I just had to edit the /etc/network/interfaces file.

Thanks alot.

---

### Post by dragos_iliescu_2005 on 2009-01-03
try delete all in /etc/network/interfaces except of the line |"iface lo inet loopback"
then, run again pppoeconf
it should work

---

### Post by pytheas22 on 2009-01-03
I'm glad to see it's fixed.  I'm still a bit perplexed as to why the script wouldn't work, but at least it's solved.

---

