---
title: "Cannot Connect"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by raywood on 2009-05-10
I have a dual-boot system, running 9.04 and WinXP.  WinXP connects to the Internet, no problem.  Jaunty was connecting this morning, but now, after reboot, it won't connect.  Today's activities before reboot:  installing packages via Synaptic and add-ons for Firefox (new Ubuntu installation).  I connect two machines to DSL via wired connection to router.  I'm typing this on the other machine, so router etc. seems OK.

---

### Post by Iowan on 2009-05-10
Does it get IP address? (I'm having similar problem on laptop that worked until this morning.)

---

### Post by superprash2003 on 2009-05-11
post outptu of ifconfig from the terminal

---

### Post by raywood on 2009-05-11
Here it is:

ray@ANTEC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:e2:07:2c:8c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:1b:21:2e:12:11  
          inet6 addr: fe80::21b:21ff:fe2e:1211/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1154 (1.1 KB)  TX bytes:468 (468.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:592 (592.0 B)  TX bytes:592 (592.0 B)

---

### Post by superprash2003 on 2009-05-11
in your terminal type the following 2 commands and then try
1)sudo dhclient eth0
2)sudo dhclient eth1

---

### Post by raywood on 2009-05-11
Brilliant!  At least it seems to have worked on eth1.  It "killed old client process, removed PID file," did its DHCPOFFER and DHCPREQUEST, etc.  So I'm getting webpages in Firefox now.  Thank you!  :)

On eth0, I got "No DHCPOFFERS received.  No working leases in persistent database - sleeping."  Attempts to start Google Earth still fail with an Error code: 29.  "Google Earth detected an error while trying to authenticate.  Please check the following:  - your network connection (can you get to ww.google.com?) [Yes, I can.] - your firewall settings (are you blocking /home/ray/google-earth/googleearth-bin?" (I don't think so.)

---

### Post by raywood on 2009-05-11
Update:  logged in again.  Now the network icon on the top panel says, "No network connection."

---

### Post by panosgr on 2009-05-12
I have similar problems...
My card was working well till yesterday, after installing the last recommended updates.
The strange thing is that my ethernet card seems to be connected (gets an ip) but I don't have access neither to the web nor my router ip! The same thing happens if I use my linksys usb wifi adapter. It connects to my router (asks about the WPA2 password) but firefox cannot connect. I have tried other programs like Ekiga, Pidgin, Add/remove programs. Updates manager but there is no connection with the web.
If I type dhclient eth0 I get the following text:
wmaster0:unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: permission denied
SIOCSIFADDR: permission denied
SIOCSIFFLAGS: permission denied
wmaster0:unknown hardware address type 801
open a socket for LPF: Operation not permitted
I am a new user to ubuntu and I don't know what to do...
Please help.
My system is a Compaq Presario 1510EA laptop with 512MB Ram and only Ubuntu 9.04 installed (no dual boot).
--------------------------------------------------------------------------------
I looked at [http://ubuntuforums.org/forumdisplay...er=desc&page=2](http://ubuntuforums.org/forumdisplay...er=desc&page=2)
and followed the advise to remove network manager and install wicd manager. After this my laptop keeps to connect (ethernet and wireless) to my router but no internet.
I checked /etc/resolv.conf and it shows the correct nameservers that also use my second pc connected to the same router and running winxp. This pc has internet access so the router is OK.
I used livecd 8.1 on my laptop and internet is OK. The problem is only with jaunty.
Do I have to go back to 8?

---

### Post by superprash2003 on 2009-05-12
im thinking this is a bug.. i've seen such threads earlier as well..you could try setting up static ip so you dont need to depend on the router to give you an ip.. [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by pedramslhr on 2009-05-12
This is the problem sometimes happens for me too. And the only way is to restart computer-even many times.
I have reinstalled ubuntu 8.04 again due to problem I had with win XP. But I remember I had this problem with the previous installation at the firs days. But it was working well after one or more weeks. Maybe it was gone because of updates I installed.
I mentioned it here too:  [COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=1039347]("http://ubuntuforums.org/showthread.php?t=1039347")[/COLOR]

---

### Post by raywood on 2009-05-12
Prashanth -- I tried your tutorial, but I wasn't sure what numbers to use for the static IP address etc.  What I used didn't work.  Advice?

---

### Post by superprash2003 on 2009-05-13
what is your router's ip

---

### Post by raywood on 2009-05-13
Sorry, I'm not sure how to find the router's ip address.

---

### Post by Iowan on 2009-05-13
> **raywood said:**
> Sorry, I'm not sure how to find the router's ip address.*Probably* 192.168.0.1 or 192.168.1.1 - but an easy way might be to boot into XP, find the "run" option, enter "cmd" without quotes, then type **ipconfig**. That will give XP's IP address, the router is *probably* similar but X.X.X.1. If XP is working, you might check router configuration page, but you'll need to know the address to get there.

---

### Post by raywood on 2009-05-13
Right.  Here it is:

IP Address:  192.168.2.105
Default Gateway:  192.168.2.1

Thanks!

---

### Post by superprash2003 on 2009-05-14
so i guess you answered your own question in post no 11

---

### Post by raywood on 2009-05-14
> **Iowan said:**
> *Probably* 192.168.0.1 or 192.168.1.1 - but an easy way might be to boot into XP, find the "run" option, enter "cmd" without quotes, then type **ipconfig**. That will give XP's IP address, the router is *probably* similar but X.X.X.1. If XP is working, you might check router configuration page, but you'll need to know the address to get there.

Plugging this into the tutorial at [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html?showComment=1242344880000#c543011506034342187](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html?showComment=1242344880000#c543011506034342187) gives the solution.  Thanks all!

---

