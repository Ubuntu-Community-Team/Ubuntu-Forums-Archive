---
title: "internet working on xp but not on ubuntu.... :("
date: 2011-08-30
forum: Networking &amp; Wireless
---

### Post by fezar.fz on 2011-08-30
[COLOR=#000][FONT=times new roman]hey  there. m a linux user and recently switched on wired services.  in beginning internet was working fine on ubuntu but from last couple of  days vpn is connecting but i cant browse any site..really stuck on this  problem..although i connected net through xp from my laptop and it run  normal..please any solutions?? 





PS: wen not connected through vpn server runs fine and i can also download files from lan server.

[/FONT][/COLOR]

---

### Post by northd_tech on 2011-08-30
First, let's try to figure out what kind of network hardware you are running.

Can you post the output when you run the following terminal commands under Ubuntu (cut & paste is easiest using a USB flash drive):

```
sudo lshw -C network
lsmod
lspci | egrep 'thernet|ireless|etwork'
ifconfig
iwconfig
lsusb
cat /etc/lsb-release
nm-tool
uname -a
```

---

### Post by fezar.fz on 2011-08-30
thanks for the rply.. :) lyk run the commands one by one?

---

### Post by fezar.fz on 2011-08-30
hey is there a possibility that net can be blocked on types of operating systems? lyk xp is allowed to browse internet where as ubuntu is not..??

---

### Post by northd_tech on 2011-08-30
No, Ubuntu has supported wireless networking since at least version 8.04 (although some wireless cards/interfaces are more difficult to set up than others).  Depending upon your hardware, some are really easy, most take a little bit of work, and select few wireless interfaces are nearly impossible.

To find out what kind of hardware you have, yes just enter each command (cut/paste from my post will prevent errors) into a Ubuntu terminal.  (Go to Accessories > Terminal to open the terminal window in Ubuntu).

Then if you can save the output from each terminal command into a text file (use **gedit** or **Kate** to cut/paste the output from the terminal window and save as "results.txt" or something relevant).   The text editors **gedit** and **Kate** can be started from the Accessories menu (or you could just type **gedit &** in the terminal window before you enter the terminal commands that I gave you earlier).

Once you have saved the text file, you can copy/paste it in a post here (or you could just attach the text file to your post by using the little paperclip button between the smiley face and the "undo" button in the post editor window).

---

### Post by fezar.fz on 2011-08-30
here is ur results.txt file...

---

### Post by northd_tech on 2011-08-31
OK- it's a 32-bit Ubuntu Maverick Meerkat 10.10 installation:

> Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"with this kind of cabled ethernet connection:
> 01:01.0 Ethernet controller: **ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)**
nett@ubuntu:~$[COLOR=Purple]** ifconfig**[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:04:5a:66:da:b6  
         ** inet addr:10.111.14.46  Bcast:10.111.15.255**  Mask:255.255.248.0
          **inet6 addr:** fe80::204:5aff:fe66:dab6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
         ** RX bytes:876223 (876.2 KB)  TX bytes:74832 (74.8 KB)**
          Interrupt:22 Base address:0xb800There is also this:
> nett@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
[B]  Driver:            tulip
  State:             connected[/B]
  Default:           yes
  HW Address:        00:04:5A:66:DA:B6

  Capabilities:
    Carrier Detect:  yes

[B]  Wired Properties
    Carrier:         on[/B]

  IPv4 Settings:
    Address:         10.111.14.46
    Prefix:          21 (255.255.248.0)
    Gateway:         10.111.8.1

    DNS:             10.101.10.5
    DNS:             10.101.10.10 Apparently, you have at least a partial cable connection to your ISP- there is traffic and a connection there.  

Now I'm wondering about how your Virtual Private Network (VPN) is connected- it sounds like you've got an authentication or encryption problem in the VPN to me (but I haven't used those in a long time).  At this point, I don't believe this is an ethernet **hardware** problem, but it is probably in the VPN setup.  I'm hoping that someone else has 'fresher' Ubuntu/Linux VPN experience than I have though.

---

### Post by fezar.fz on 2011-08-31
ahan thanks...i was wondering is there is a 3rd party vpn client available for ubuntu..?

---

### Post by pdc on 2011-08-31
[http://tinyurl.com/4xwc34s](http://tinyurl.com/4xwc34s)

---

### Post by fezar.fz on 2011-08-31
do u knw the exact name of any client??

---

### Post by fezar.fz on 2011-08-31
now its working :)

---

