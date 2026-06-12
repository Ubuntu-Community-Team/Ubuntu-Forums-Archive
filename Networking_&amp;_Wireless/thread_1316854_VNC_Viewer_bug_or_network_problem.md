---
title: "VNC Viewer bug or network problem?"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by Tony Ricena on 2009-11-06
Hi, I'm new to the forums but not new to Ubuntu.  I switched from Windows to Ubuntu around 2 months ago and never looked back.  I love the functionality and stability that Ubuntu has to offer.  Everything works fine except one thing...VNC viewer.

The problem with VNC is that it appears to lag when I connect to the VNC Remote host.  Here is the setup:

I have 1 Desktop PC running Ubuntu 9.10 and 1 laptop running Opensuse 11.1

When I remote into the Desktop via laptop, the desktop appears and mouse moves, but when I attempt to open up lets just say the main menu I do not get the display on the laptop but looking at the desktop it recognizes that I opened the menu.  It just does not display on the laptop (VNC client).  The funny thing is if I decide to reverse it (remote into the laptop via the desktop) everything works fine!  When I open the menu on the laptop, I see it on the desktop.  

I know this just isn't a problem with the wireless card on the laptop.  This has happened when I was remoting between two desktops as well.  Even when I used VNC in Windows and remote into my ubuntu desktop.  It seems to just happen on the desktops.  

When I use the Terminal Server Client and used RDP to remote to my old Windows 7 computer, I never had any problems.  The desktop Gui came up and I could use it as if I was right in front of the computer.  

My question is #1
-Has anybody else run into this problem and has a solution?
and #2
-Is there an alternative to VNC (exp. Installing RDP on both Linux machines and use that rather then VNC?)

Now I know what you are going to say... just use ssh and use the command line.  Though I am 15% comfortable with the command line, I want the ability to use the GUI because I just convinced my father to switch to Linux and I want to be able to instruct him if he has any questions and actually show him what I am doing.  Its just easier for him and me.  

As of right now, this is being done through the LAN.  If it doesn't work here I know it won't work if I remote via Internet.

Here is my network info from issuing the command ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:24:1d:74:00:08  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe74:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3952714 (3.9 MB)  TX bytes:9501898 (9.5 MB)
          Interrupt:28 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:864 (864.0 B)  TX bytes:864 (864.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

The actual network card is imbeded into the mother board.
Realtek Semiconductor RTL8111/8168B
Subsystem : Giga-byte Technology Device e000

if there is specific information you need, please tell me along with command.  Lets see if you guys can help me.  thanks in advance

---

### Post by Tony Ricena on 2009-11-06
Here is the information with the command grep 'Ethernet driver' /var/log/dmesg
[    1.984916] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded

---

### Post by Tony Ricena on 2009-11-06
Bump

---

### Post by Tony Ricena on 2009-11-06
Guess Nobody can tackle this :(

---

### Post by Tony Ricena on 2009-11-06
Nobody can help with this??

---

### Post by yellowtip on 2009-11-12
I have the exact same problem as described here. It seems to be some sort of Vino bug if you ask me.

Extremely annoying.

Does anybody have a fix for this?

---

### Post by ivyharry on 2009-11-12
I guess it will be good if you can file a bugzilla on it...

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

or 

[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

### Post by slochewie on 2009-11-13
Same here. When I use vncviewer from a Solaris 10 workstation.

Edit:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126)

Seems for now you can just go to System -> Preferences -> Appearance and then go to the Visual Effects tab and select the None option.

---

