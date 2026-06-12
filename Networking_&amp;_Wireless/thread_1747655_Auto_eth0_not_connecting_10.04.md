---
title: "Auto eth0 not connecting 10.04"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by zepolmot on 2011-05-02
So, I can't figure out why my ethernet isn't recognizing its connection. ifconfig returns the hardware address, route -n returns an empty table.  Anybody have any advice?

---

### Post by Antarctica32 on 2011-05-02
Believe it or no I had this same problem when I first got into Ubuntu in the beginning. If I remember correctly I fixed it by renaming Auto eth0 to something else so that when it worked instead of saying "Auto eth0 connection established" it said "(name I changed it to) connection established". I completely forget how or why I changed it but I vaguely remember that working. Hope I could help probably didn't, sorry.

---

### Post by zepolmot on 2011-05-02
Hey thanks for the reply Antarctica, unfortunately you're right.  Renaming the connection didn't work

lspci -k gives:

2:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev3)
Kernel driver in use: r8169
Kernel modules: r8169

---

### Post by zepolmot on 2011-05-03
Is there any advice besides reformatting and crossing my fingers that installing again will fix this?  Thanks again

---

### Post by Antarctica32 on 2011-05-03
I don't know that much about this but try going to the network notifier on the top panel,right click, click edit connections, and under the wired tab click add. That may lead you somewhere. try adding the name of the network you are trying to get on. When this happened to me I was using a Ethernet port on my mobo and not a PCI card. Now I have an ethernet PCI card. When you add a second ethernet port it is named "auto eth1". Your first port is called "Auto eth0". When I hooked up my PCI card ethernet port it worked out of the box with no problems (adding the same model card to my windows desktop took about an hour). IF you are adding an ethernet port for whatever reason does your mobo have an ethernet port? if so does it work? I have a few ideas

---

### Post by Antarctica32 on 2011-05-03
Try this

/etc/rc.d/rc.inet1 eth0_restart

if that doesn't work try changing eth0 to eth1

---

### Post by stevedude on 2011-05-03
Same thing happened with me after I did a fresh install of Natty. After the installation, when I used the LIVE CD, the (wired) ethernet connection worked,when I booted into the system, it would not connect (and by not connecting I could not DL updates and drivers needed for the wireless).

Unfortunately, I had to reinstall the system and it worked perfectly afterwards.

There has got to be an issue with the installation of the system because I actually did an upgrade from Maverick which broke my system with no ethernet access. Then I did a fresh install (install option to erase everything), and the ethernet did not work, but would work with booting from the Live CD, then I did another reinstall (install option to erase everything) and the last time was the charm.

I would give booting from the Live CD a try, if it works, then there may have been a system installation issue like me. I don't know if a reinstall is feasible in your mind, but that's what worked for me.

---

### Post by zepolmot on 2011-05-03
Thanks for the advice you two.  I'm using the port built into my mobo and would rather not install a second port via a PCI card.  I'm not at the machine now but I'll test out /etc/rc.d/rc.inet1 eth0_restart and report back.

Again, not sure if this will give anybody any clues but heres the output from  sudo /sbin/dhclient eth0
         
        Internet Systems Consortium DHCP Client V3.1.3
        Copyright 2[004-2009]("callto:004-2009") Internet Systems Consortium.
        All rights reserved.
        For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
        
        Listening on LPF/eth0/e0:cb:4e:d7:5b:78
        Sending on   LPF/eth0/e0:cb:4e:d7:5b:78
        Sending on   Socket/fallback
        DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
        DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
        DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
        DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
        DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
        DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
        No DHCPOFFERS received.
        No working leases in persistent database - sleeping.

---

### Post by zepolmot on 2011-05-03
/etc/rc.d/rc.inet1 eth0_restart
"No such file or directory"

---

### Post by zepolmot on 2011-05-03
I have the CD that came with my mobo and it has the LAN driver, specifically for linux, can somebody point me towards a how-to for removing the linux driver and installing this one properly?

---

### Post by zepolmot on 2011-05-04
nm-tool reports that eth0 is not the default connection, Is there a way I can change this?

---

### Post by Antarctica32 on 2011-05-04
what does it say the default is? Auto eth1?

---

### Post by zepolmot on 2011-05-04
No default is listed, only eth0 comes up

---

### Post by zepolmot on 2011-05-04
one thing i've noticed is that 

auto eth0
iface eth0 inet dhcp

is not in my /etc/network/interfaces file, and when I add it and reboot the connection issue is not fixed and my network manager icon no longer appears in my notification area.  commenting the lines out and rebooting returns the icon.

---

### Post by zepolmot on 2011-05-04
Attempting to connect on the live cd also fails

---

### Post by zepolmot on 2011-05-05
Any sage advice out there on the forums?

---

### Post by Antarctica32 on 2011-05-05
So even when booting from a CD it still won't work..... That is rather strange. I assume that that also means a fresh install won't work.... This is really weird, I have never encountered a situation were ubuntu will just not work with the hardware. Try booting from a Maverick or Natty CD. If it works we know that Lucid just won't work with the hardware. Sometimes partitions and HDD formatting can cause problems like that, but if it doesn't work when booting from a cd thats something tottally different. For right now thats all I know, first try bo0ting from a different OS or just a different version of Ubuntu

---

### Post by zepolmot on 2011-05-16
After nothing worked, I opened up the case of the computer and re-set the RTC memory using the pins on the motherboard, then I went into BIOS and disabled the LAN driver ROM then re-enabled it.  Now it works.

---

