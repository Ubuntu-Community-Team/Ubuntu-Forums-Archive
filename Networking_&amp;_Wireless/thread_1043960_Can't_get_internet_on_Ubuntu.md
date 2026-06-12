---
title: "Can't get internet on Ubuntu"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by lilchiko on 2009-01-19
Hello everyone, I am new to ubuntu. As a matter of fact I just install ubuntu two days ago. Well it does have a lot of cool features but I can't get my internet up and running. I have a dell inspiron 1501. I am on a linksys 54g router. My connection to the router is wireless but when I try to do the network setup I don't see my network anywhere. 

Please remember that I am new to ubuntu so please bear with me if I missed something.

---

### Post by ieee488 on 2009-01-19
read [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) first

---

### Post by mikewhatever on 2009-01-19
You need to provide more info to help us help you. Post the output of the following commands from Applications->Accessories->Terminal.

ifconfig
iwconfig
sudo lshw -C network

---

### Post by Terl on 2009-01-19
> **lilchiko said:**
> Hello everyone, I am new to ubuntu. As a matter of fact I just install ubuntu two days ago. Well it does have a lot of cool features but I can't get my internet up and running. I have a dell inspiron 1501. I am on a linksys 54g router. My connection to the router is wireless but when I try to do the network setup I don't see my network anywhere. 

Please remember that I am new to ubuntu so please bear with me if I missed something.

I have a dell 1501 as well (and use the same router).  Did you get the driver already via the restricted drivers?  Is the light on for the wireless?  Once I installed the driver I just right clicked on the network manager icon and made sure wirelss was enabled.  I have my router set on WPA2 with a passkey.

I am assuming you have your wireless turned on at the router.  I know I was working on mine once and realized I had turned it off.

Also, which version of Ubuntu are you using?

---

### Post by superprash2003 on 2009-01-19
what do you see under sytem->admin->hardware drivers?

---

### Post by lilchiko on 2009-02-05
well i see two drivers on that says wl and another that says ATI/AMD proprietary FGLRX graphics driver. The wl driver is activated but the ATI one isn't I try activating it and it does nothing.

---

### Post by lilchiko on 2009-02-05
edward@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:c8:d4:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

edward@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

edward@ubuntu:~$ 



This is what I got when i entered those commands, when i entered the sudo lshw -C network command it asked me for my password but when I entered it I got an incorrect password message.

---

