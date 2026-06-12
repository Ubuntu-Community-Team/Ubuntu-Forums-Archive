---
title: "Strange Wifi Issue in acer revo Atheros 5007EG"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by dazza76 on 2009-10-13
Hello (First Post),
I have installed a Minimal ubuntu with xfce and my wifi has a very strange issue.
it works for surfing the net no problems there .
my issue is i cannot ping it or ssh or samba to it from other devices on the local network.
 
if i ping the other device on the network first sometimes it works.
 
I am a bit of a ubuntu noob but not a noob with linux.
 
if i use the network cable I have no issue.
 
P.s both devices are on wifi
and i did not install any custom drivers it worked out of the box
 
cheers
Daz

---

### Post by t0mppa on 2009-10-13
Ok, can the other devices ping each other on the local network and can your Ubuntu box ping them? And does this happen when you have both a wired and wireless connection or just when you have only a wireless connection?

Mind also posting output of **netstat -nr** from your Ubuntu box?

---

### Post by dazza76 on 2009-10-14
ok more to add
when i reboot if i do not do a 
ifdown wlan0
ifup wlan0
other devices are unable to talk to it.
however it can ping other devices quite happily
 
 
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 wlan0
it is the same before and after the ifdown and ifup
 
all other devices can talk to each other
i have attached some files for any othe information you might need.
 
 
cheers
 
D

---

### Post by dazza76 on 2009-10-14
dmesg file

---

### Post by t0mppa on 2009-10-14
[QUOTE=dmesg][   19.259070] Bridge firewalling registered[/QUOTE]

Everything else seems to be in order, and the problems you were having sound like things that would normally be fairly default on firewalls against unknown addresses (ie. Internet), but naturally they're quite annoying on local network.

So, have you installed firewall software or added iptable rules by hand?

---

### Post by dazza76 on 2009-10-14
Currenty i am running from a minimal install
i have not added any iptables rules as it is still in testing mode.
i might try a fresh install to make sure i havn't *[COLOR=black]accidentally[/COLOR]* broken anything.
its just a little slow installing from the net
 
D

---

### Post by istvank on 2009-11-02
I have exactly the same issue. I installed Ubuntu minimal using the wired interface. After I enable the wireless interface, it makes the connection, it gets the IP address through DHCP from the router, but form that moment both interfaces start acting weird. The ping response raises from less than 1ms to between 8-15000ms and there are timeouts randomly between 6-30 seconds.
Do you have a clue where is the problem?

---

### Post by istvank on 2009-11-02
It look like installing wicd solves the problem:
sudo apt-get install wicd

---

### Post by elliottrand on 2009-11-05
My Atheros 5007EG WIFI never worked with 9.04 on a 64-bit Compaq despite 
hundreds of hours of downloading and trying.  I was delighted that the 
9.10 Live CD started up my Atheros 5007 right out of the box and worked 
great.  Then I installed 9.10 and it is back to square one.  The only way 
I can use wifi with the 64-bit Compaq is with the live CD, a real bummer.
-----------------
I have since discovered that there is no MENU.LST file in /boot/grub so I 
can't change the boot order.  I've had it with this piece of excrement.
--------------------
I am installing SuSE 11.1 over Ubuntu 9.10, and henceforth will refer to 
this experience "UBUNTU 9/11" as in the WTC & Osama Bin Ladin. 
--------------------
What a flaming shame.  Don't try to make this pile of garbage work.
---------------------
-- Elliott Rand (ekrand@yahoo.com)

---

### Post by declan23 on 2010-12-15
hi. this may or may not be directly relevant but I had an issue establishing a wifi connection between my revo atom pc which has an atheros card. my access point is linksys wrtg54. I could see the access point and signal strength was good but always failed to connect. Having installed the madwifi drivers and rebooted still had the issue. (I am using ubuntu 10). What fixed it was to change the wep setting on my router from "shared" to Auto and it worked.

---

