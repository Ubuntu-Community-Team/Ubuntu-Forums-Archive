---
title: "Able to connect to XP Share fully via wireless but not with ethernet connection."
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by JUNiA on 2009-07-27
Hello all.. 

I have left a previous message about this similiar issue but have not had any input.  My desktop home machine is a XP SP2 box and my laptop is running Ubuntu 9.04, kernal 2.6.28-13-generic. I have scoured almost every single instruction on ubuntuforums on how to set up samba with xp shares and I am going crazy with all the stuff I have tried.  I have edited the smb.conf a zillion times, one option after the next to get this to work via ethernet by restarting the samba server by the commandline after every edit of smb.conf. I can ping my XP box and recieve replies.  In ubuntu via ethernet, thru nautilus, i can navigate to an XP share for e.g. I enter into the top of the nautilus address bar smb://192.168.1.100/HQ.D.Vault and it will mount, but I cannot enter it, nor any of my other shares, it just times out.  For the last umteen hours I have been banging my head of the wall trying configuration after configuration of smb.conf/restarting samba after every edit w/o no success in being able to see files on a xp share folder via nautilus nor thru 'Connect to' dialogue.  I can see the mounted volume (hq.d.vault at 192.168.1.100) in nautilus but just can't access it further.     On the XP side I am connected via a dedicated ethernet connection, and when I connect to a ubuntu share, I can enter empy folders that are shared but not shared folders that have files in them.  Then lo and behold.. I had to go somewhere in my house with my laptop and switched to a wireless connection to my home network and attempted to see if I could connect to my XP shares, and I was able all of a sudden to view all my XP shares via nautilus, go into the shared folders via nautilus, see whats there, copy whats there to my ubuntu laptop, stream to my ubuntu laptop a couple of test videos from my xp share, view pictures on my xp shares all thru nautilus etc. This has got me very frustrated and would really appreciate assitance in getting this resolved. :| :mad: ](*,) :frown:

Can someone PLEASE HELP ME understand why I can connect to my XP shares via wireless and perform browsing, file transfers etc with no problems but why when my laptop is hooked up via ethernet to my router (instead of by wireless to my router) I am unable to even see whats in a XP share and only able to mount the volume but not access it to view files, copy files etc?  Can someone tell me how to get this to work via ethernet since I use my Ubuntu Laptop on a wired connection mainly? Your help will be GREATLY APPRECIATED :) and THANK YOU in advance..

---

### Post by swerdna on 2009-07-28
Wow, tough one.

Here's a left-field thought: I wonder about the IP subnets. What return do you get when you run this command in a terminal:```
sudo ifconfig
```Do it three times. Once with just the wireless running. Then with just the wired running. Then with both the wireless and the wired running.

You only need to paste/post the lines like this that show the devices and addresses:
[html]eth0      Link encap:Ethernet  HWaddr 00:13:D4:FE:36:59  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0[/html]

Also post the return from these two commands:
[LIST=1]
[*]testparm -s
[*]cat /etc/samba/smb.conf | grep workgroup
[/LIST]
From these I'm interested in any filtering you have on IPs or devices in smb.conf, or other quirky blocks in the configuration file.

Oh and do you have a firewall running? (e.g. sudo ufw status).

---

### Post by JUNiA on 2009-07-28
> **swerdna said:**
> Wow, tough one.

Here's a left-field thought: I wonder about the IP subnets. What return do you get when you run this command in a terminal:```
sudo ifconfig
```Do it three times. Once with just the wireless running. Then with just the wired running. Then with both the wireless and the wired running.

You only need to paste/post the lines like this that show the devices and addresses:
[html]eth0      Link encap:Ethernet  HWaddr 00:13:D4:FE:36:59  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0[/html]Also post the return from these two commands:i
[LIST=1]
[*]testparm -s
[*]cat /etc/samba/smb.conf | grep workgroup
[/LIST]
From these I'm interested in any filtering you have on IPs or devices in smb.conf, or other quirky blocks in the configuration file.

Oh and do you have a firewall running? (e.g. sudo ufw status).

[B]
I use firestarter as my firewall.  In wireless mode firestarter auto shuts itself off, but in ethernet mode I can choose if I want it on or off and I have it set to accept connections from my XP Box (192.168.1.100).


Output of 'sudo ifconfig' with just wireless running[/B];

eth0      Link encap:Ethernet  HWaddr 00:e0:b8:fa:c2:32  

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0

wlan0   Link encap:Ethernet  HWaddr 00:1f:3c:76:d6:a1  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
        
wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-76-D6-A1-00-00-00-00-00-00-00-00-00-00  
 
**Output of 'sudo ifconfig' with just wired running;**

eth0      Link encap:Ethernet  HWaddr 00:e0:b8:fa:c2:32  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0


**Output of 'sudo ifconfig' with wired and wireless connection running at same time;**

eth0      Link encap:Ethernet  HWaddr 00:e0:b8:fa:c2:32  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:76:d6:a1  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:2

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-76-D6-A1-00-00-00-00-00-00-00-00-00-00  

[B]Output of testparm -s (from smb.conf);

[/B]Load smb config files from /etc/samba/smb.conf
WARNING: Ignoring invalid value 'Nobody' for parameter 'map to guest'
Processing section "[print$]"
Processing section "[printers]"
Processing section "[DVD Drive]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = THE_RESISTANCE
    netbios name = MOBILEHQ
    server string = Trinity Server
    interfaces = lo, eth0, wlan0
    bind interfaces only = Yes
    null passwords = Yes
    obey pam restrictions = Yes
    passdb backend = tdbsam
    username map = /etc/samba/smbusers
    syslog only = Yes
    announce version = 5.0
    name resolve order = lmhosts wins bcast host
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = CUPS
    dns proxy = No
    usershare owner only = No
    invalid users = root
    read only = No
    guest ok = Yes

[print$]
    path = /var/lib/samba/printers
    write list = root
    read only = Yes
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = Yes
    browseable = No

[DVD Drive]
    path = /media/cdrom
    read only = Yes
[B]
Output of 'cat /etc/samba/smb.conf | grep workgroup'; 
[/B]workgroup = The_Resistance

(Btw what does grep do?)

**Output of 'sudo ufw status';**
Status: inactive

---

### Post by swerdna on 2009-07-28
There's no anomaly in the IP addressing.
The only mildly puzzling thing/s that I can see relating to network interfaces are these two:
> interfaces = lo, eth0, wlan0
bind interfaces only = Yes
So I suggest you try it with those out. I read the man pages of smb.conf for those two and simply couldn't understand on the first read. Test it and see. Restart Samba after the edit.

This and some other things there were interesting:> If bind interfaces only is set and the network address 127.0.0.1 is not added to the interfaces parameter list smbpasswd and swat may not work as expected due to the reasons covered below.

---

### Post by superprash2003 on 2009-07-28
strangely when only wired is running ,eth0 didnt seem to get an ip address.. that is weird!! . next time type **sudo dhclient eth0 **in your terminal and then try

---

### Post by JUNiA on 2009-07-28
> **superprash2003 said:**
> strangely when only wired is running ,eth0 didnt seem to get an ip address.. that is weird!! . next time type **sudo dhclient eth0 **in your terminal and then try

[B]This is what I got when I ran that command;
[/B]
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:e0:b8:fa:c2:32
Sending on   LPF/eth0/00:e0:b8:fa:c2:32
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.

---

### Post by JUNiA on 2009-07-28
> **swerdna said:**
> There's no anomaly in the IP addressing.
The only mildly puzzling thing/s that I can see relating to network interfaces are these two:

So I suggest you try it with those out. I read the man pages of smb.conf for those two and simply couldn't understand on the first read. Test it and see. Restart Samba after the edit.

This and some other things there were interesting:


I did what you said, and now my ethernet connection can't connect to the net or network shares at all.  But yet I can ping my XP Box from the ubuntu laptop on a wired connection .... this is weird.  Only wireless works.  egad.  Before this, ethernet was working for internet and so was wireless.  Now I am able to post this reply via a wireless connection.  Also.. a new thing.. now when the ethernet cable is connected and the wireless turned off, I can't even access my router now at 192.168.1.1 thru a browser.. frustrating it is.

---

### Post by swerdna on 2009-07-28
Let's check the hardware. Turn the router off -- pause -- on. I have to do that about once a week or my wired link stops for samba. Turn the modem similarly (thorough).

Run this command and post here the results:```
lspci -nnk
```Just extract the lines relating to network cards-- for example here's what I get:
[HTML]00:08.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
	Kernel driver in use: ath5k_pci
	Kernel modules: ath5k
00:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp[/HTML]
Paste them using the html tags/braces to make them readable.

Finally, what are the brand names of your wired and wireless net cards (if you know off hand -- don't undo the case to look).

---

### Post by JUNiA on 2009-07-28
> **swerdna said:**
> Let's check the hardware. Turn the router off -- pause -- on. I have to do that about once a week or my wired link stops for samba. Turn the modem similarly (thorough).

Run this command and post here the results:```
lspci -nnk
```Just extract the lines relating to network cards-- for example here's what I get:
[html]00:08.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
    Kernel driver in use: ath5k_pci
    Kernel modules: ath5k
00:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp[/html]Paste them using the html tags/braces to make them readable.

Finally, what are the brand names of your wired and wireless net cards (if you know off hand -- don't undo the case to look).


[B]Output of lspci -nnk (i just put the whole thing. ... getting too frustrated)

[/B]00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
    Kernel modules: intelfb
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 04)
    Kernel driver in use: uhci_hcd
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 04)
    Kernel driver in use: uhci_hcd
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 04)
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 04)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 04)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 04)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 04)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 04)
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 04)
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 04)
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 04)
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f4)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 04)
    Kernel modules: iTCO_wdt
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 04)
    Kernel driver in use: ata_piix
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 04)
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 04)
    Kernel modules: i2c-i801
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Kernel driver in use: r8169
    Kernel modules: r8169
 

As for brand of my wired and wireless cards, I do not understand you fully.  On my laptop, it has a ethernet connection and it has built in wifi.  Any commands you can suggest to get that info? TIA

---

### Post by swerdna on 2009-07-28
Googling that card indicates it might be problematic in Linux:
[http://www.google.com/search?hl=en&safe=off&num=100&q=RTL8101E%2FRTL8102E+linux&btnG=Search&meta=](http://www.google.com/search?hl=en&safe=off&num=100&q=RTL8101E%2FRTL8102E+linux&btnG=Search&meta=)

Your wired card is using driver r8169 instead of r8101.

Here are the realtek drivers for Linx (r8101):
[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

---

### Post by JUNiA on 2009-07-28
> **swerdna said:**
> Googling that card indicates it might be problematic in Linux:
[http://www.google.com/search?hl=en&safe=off&num=100&q=RTL8101E%2FRTL8102E+linux&btnG=Search&meta=]("http://www.google.com/search?hl=en&safe=off&num=100&q=RTL8101E%2FRTL8102E+linux&btnG=Search&meta=")

Your wired card is using driver r8169 instead of r8101.

Here are the realtek drivers for Linx (r8101):
[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)



Ok. I appreciate the ongoing assistance. How you does one innstall drivers in Ubuntu/Linux system for this?

---

### Post by swerdna on 2009-07-28
here's the download on this link:
[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)
find this text:
> LINUX driver for kernel 2.6.X and 2.4.X (Support x86 and x64)and beside it click the button labelled "GO" for site 1 (or site 2 or site3). If that doesn't download, enable javascript (or is it java?) in your browser.

How to install is in the enclosed file as a document called "readme". Right-clcik the download and select "extract here". Then have a go at "readme" and ask more questions.

---

### Post by JUNiA on 2009-07-28
> **swerdna said:**
> here's the download on this link:
[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)
find this text:
and beside it click the button labelled "GO" for site 1 (or site 2 or site3). If that doesn't download, enable javascript (or is it java?) in your browser.

How to install is in the enclosed file as a document called "readme". Right-clcik the download and select "extract here". Then have a go at "readme" and ask more questions.


Ok, I downloaded the driver. and...

**But instruction How to install driver looks like this :** 
<Quick install with proper kernel settings>
    Check whether the built-in driver, r8169.ko (or r8169.o for kernel 2.4.x), is installed. 
        # lsmod | grep r8169

    If it is installed, please remove it.
        # rmmod r8169
note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remmove it again or reboot your computer.

    Unpack the tarball :
        # tar vjxf r8101-1.aaa.bb.tar.bz2

    Change to the directory:
        # cd r8101-1.aaa.bb

    If you are running the target kernel, then you should be able to do :

        # make clean modules    (as root or with sudo)
        # make install
        # depmod -a
        # modprobe r8101

    You can check whether the driver is loaded by using following commands.

        # lsmod | grep r8101
        # ifconfig -a

    If there is a device name, ethX, shown on the monitor, the linux 
    driver is loaded. Then, you can use the following command to activate 
    the ethX.

This is what I did as I have shown below.  I have only removed the old river and r8169 does not exist :

**user@P:~$ rmmod r8169 **
ERROR: Module r8169 does not exist in /proc/modules 
**user@P:~$ sudo tar vjxf /home/user/Pulpit/r8101-1.012.00.tar.bz2 **
[sudo] password for user: 
r8101-1.012.00/ 
r8101-1.012.00/src/ 
r8101-1.012.00/src/rtl_ethtool.h 
r8101-1.012.00/src/rtl_eeprom.h 
r8101-1.012.00/src/r8101_n.c 
r8101-1.012.00/src/Makefile 
r8101-1.012.00/src/rtl_eeprom.c 
r8101-1.012.00/src/Makefile_linux24x 
r8101-1.012.00/src/r8101.h 
r8101-1.012.00/Makefile 
r8101-1.012.00/readme 
**user@P:~$ cd r8101-1.012.00** 
**user@P:~/r8101-1.012.00$ sudo make clean modules **
make -C src/ clean 
make[1]: Entering directory `/home/user/r8101-1.012.00/src' 
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers Module.markers *.order 
make[1]: Leaving directory `/home/user/r8101-1.012.00/src' 
make -C src/ modules 
make[1]: Entering directory `/home/user/r8101-1.012.00/src' 
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/src modules 
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic' 
scripts/Makefile.build:41: /src/Makefile: No such file or directory 
make[3]: *** No rule to make target `/src/Makefile'.  Stop. 
make[2]: *** [_module_/src] Error 2 
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic' 
make[1]: *** [modules] Error 2 
make[1]: Leaving directory `/home/user/r8101-1.012.00/src' 
make: *** [modules] Error 2 
**user@P:~/r8101-1.012.00$ sudo make install **
make -C src/ install 
make[1]: Entering directory `/home/user/r8101-1.012.00/src' 
install -m 744 -c r8101.ko /lib/modules/2.6.28-11-generic/kernel/drivers/net/ 
install: cannot stat `r8101.ko': No such file or directory 
make[1]: *** [install] Error 1 
make[1]: Leaving directory `/home/user/r8101-1.012.00/src' 
make: *** [install] Error 2
  
This is what I received, I proceeded to the next command

**depmod -a **

and then it paused for a couple minutes and returned to the prompt.

I then entered **modprobe r8101** and what I got after this was;

root@MobileResistance:/home/warriorsoldier/Desktop/r8101-1.012.00# modprobe r8101
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Module r8101 not found.

**Than I ran thru the commands again and it worked on the second time**;

root@MobileResistance:/home/warriorsoldier/Desktop/r8101-1.012.00# rmmod r8169
ERROR: Module r8169 does not exist in /proc/modules
root@MobileResistance:/home/warriorsoldier/Desktop/r8101-1.012.00# make clean modules
make -C src/ clean
make[1]: Entering directory `/home/warriorsoldier/Desktop/r8101-1.012.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers Module.markers *.order
make[1]: Leaving directory `/home/warriorsoldier/Desktop/r8101-1.012.00/src'
make -C src/ modules
make[1]: Entering directory `/home/warriorsoldier/Desktop/r8101-1.012.00/src'
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/warriorsoldier/Desktop/r8101-1.012.00/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/warriorsoldier/Desktop/r8101-1.012.00/src/r8101_n.o
/home/warriorsoldier/Desktop/r8101-1.012.00/src/r8101_n.c:432: warning: &#8216;rtl8101_ephy_read&#8217; defined but not used
  CC [M]  /home/warriorsoldier/Desktop/r8101-1.012.00/src/rtl_eeprom.o
  LD [M]  /home/warriorsoldier/Desktop/r8101-1.012.00/src/r8101.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/warriorsoldier/Desktop/r8101-1.012.00/src/r8101.mod.o
  LD [M]  /home/warriorsoldier/Desktop/r8101-1.012.00/src/r8101.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
strip --strip-debug r8101.ko
make[1]: Leaving directory `/home/warriorsoldier/Desktop/r8101-1.012.00/src'

root@MobileResistance:/home/warriorsoldier/Desktop/r8101-1.012.00# make install
make -C src/ install
make[1]: Entering directory `/home/warriorsoldier/Desktop/r8101-1.012.00/src'
install -m 744 -c r8101.ko /lib/modules/2.6.28-13-generic/kernel/drivers/net/
make[1]: Leaving directory `/home/warriorsoldier/Desktop/r8101-1.012.00/src'

root@MobileResistance:/home/warriorsoldier/Desktop/r8101-1.012.00# depmod -a

root@MobileResistance:/home/warriorsoldier/Desktop/r8101-1.012.00# modprobe r8101
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.

root@MobileResistance:/home/warriorsoldier/Desktop/r8101-1.012.00# lsmod | grep r8101
r8101                  44176  0 
root@MobileResistance:/home/warriorsoldier/Desktop/r8101-1.012.00# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:fa:c2:32  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14344 (14.3 KB)  TX bytes:14344 (14.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:76:d6:a1  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe76:d6a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10790 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5109279 (5.1 MB)  TX bytes:1552638 (1.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-76-D6-A1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

  
I can not seem to be able to remove the r8169 driver.. how do i get rid of this? For now i have both drivers listed when I do a 'lsmod | grep DRIVERNAME ?  Man this is making me feel like i've been awake for 8 days.  Just delerium.  As soon as I connect via wireless... EVERYTHING works.. files sharing.. and surfing the net.. but as soon as the ethernet cable goes in .. no go.. it doesn't make sense.. before I was getting internet and viewing a bit of the shares on teh xp box.. now nothing.  Well.. then I figured out the problem... I had a thought, I decided to uninstall Network Manager for I thought perhaps it may be my network connection manager software possibly having some buggy issue.   I removed network manager and installed wicd .. and configured it .. and what do you know I am able to via ethernet and wireless now to surf the net under both connection types (Wired and Wireless) and view my XP shares, copy, browse, view etc..!!!! SO IT WORKS NOW!!!

 Are you trying to tell me that all along it may have just been a corrupted version of the network manager giving me probs?  Well now after seeing that work.. i uninstalled Wicd and rebooted to try and reinstall Network manager again ..and now i'm unable to even establish and internet connection since Network Manager is not available nor is Wicd and I can not use the Synaptic Package simply because it needs to connect to the internet and I can't now.  So I tried with this puter to download all the necessary packages for network manager, put it on a usb stick, stuck it in my ubuntu laptop, but I dont know how to install the packages from the USB drive in order to set up network-manager software though I do not have an internet connection period now.  oh brother.. what did i do now .. any pointers?

---

### Post by Loosewheel on 2009-07-28
Hi JUNiA,

Open a terminal and type:
1) 'sudo ifdown eth0'                     without the "'", then
2) 'sudo nano /etc/network/interfaces'    and ADD this to the bottom of the file:
'auto eth0 inet dhcp'                     Then reboot.

(to write the file you must hit 'ctl-o' 'enter' and 'ctl-x' to exit.)

---

### Post by JUNiA on 2009-07-29
> **Loosewheel said:**
> Hi JUNiA,

Open a terminal and type:
1) 'sudo ifdown eth0'                     without the "'", then
2) 'sudo nano /etc/network/interfaces'    and ADD this to the bottom of the file:
'auto eth0 inet dhcp'                     Then reboot.

(to write the file you must hit 'ctl-o' 'enter' and 'ctl-x' to exit.)


Did not work.

---

### Post by Loosewheel on 2009-07-29
JUNiA,
Sorry, I made an error in previous post.
sudo nano /etc/network/interfaces and add:
'auto eth0'
'iface eth0 inet dhcp'
on two seperate lines, instead of what I told you....sorry again.
If it still doesn't come up check the folowing:

What is the output of 'ifconfig -a' now.
And the output of 'cat /etc/udev/rules.d/70-persistent-net.rules'

If eth0 is listed in ifconfig, you have a driver. And we want to see if "NAME="eth0"", is in '70-persistent-net.rules' file.

---

### Post by JUNiA on 2009-07-29
> **Loosewheel said:**
> JUNiA,
Sorry, I made an error in previous post.
sudo nano /etc/network/interfaces and add:
'auto eth0'
'iface eth0 inet dhcp'
on two seperate lines, instead of what I told you....sorry again.
If it still doesn't come up check the folowing:

What is the output of 'ifconfig -a' now.
And the output of 'cat /etc/udev/rules.d/70-persistent-net.rules'

If eth0 is listed in ifconfig, you have a driver. And we want to see if "NAME="eth0"", is in '70-persistent-net.rules' file.


It's ok, your human.  Only God's perfect. heh. Ok so I re-edited the interfaces file as you have explained above (on 2 seperate lines).  I rebooted and ran the command 'ifconfig -a' and this was the out put;

eth0           Link encap: Ethernet   HWaddr 00:e0:b8:fa:c2:32
                 UP BROADCAST MULTICAST MTU: 1500 Metric:1
                 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                 collisions:0 txqueeuelen: 1000
                 RX bytes:0 (0.0 B)   TX bytes: 0 (0.0 B)
                 Interrupt: 251  Base address: 0x6000

lo         Link encap: Local Loopback
                            LOOKBACK MTU: 16436  Metric:1
                            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueeuelen: 0
           RX bytes:0 (0.0 B)   TX bytes: 0 (0.0 B)
                  
wlan0        Link encap: Ethernet   HWaddr 00:1f:3c:76:d6:a1
          BROADCAST MULTICAST MTU: 1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueeuelen: 1000
          RX bytes:0 (0.0 B)   TX bytes: 0 (0.0 B)
                
wmaster0  Link encap: UNSPEC   HWadr 00-1f-3c-76-                      
                               d6-a1-00-00-00-00-00-00-00-00-00-00
               BROADCAST MULTICAST MTU: 1500   Metric:1
               RX packets:0 errors:0 dropped:0 overruns:0 frame:0
               TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
               collisions:0 txqueeuelen: 1000
               RX bytes:0 (0.0 B)   TX bytes: 0 (0.0 B)
                               Interrupt: 251  Base address: 0x6000
 
[B]Output of 'cat /etc/udev/rules.d/70-persistent-net.rules'

# This file maintains persistent names for network interfaces
# See udev(7) for syntax
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8136 (r8169)
# SUBSYSTEM=="net",  ACTION=="add",  DRIVERS=="?*",  ATTR{address}=="00:e0:b8:fa:c2:32",  ATTR{type}=="1",     
   KERNAL=="eth*",  NAME="eth0"

[/B][B]# PCI device 0x8086:0x4222 (iwl3945)
# SUBSYSTEM=="net",  ACTION=="add",  DRIVERS=="?*",  ATTR{address}=="00:1f:3c:76:d6:a1",  ATTR{type}=="1",  
   KERNAL=="wlan",  NAME="wlan0"

[/B]Side Note: BTW I was wondering.. when I output this last command, after it I did a 'sudo dhclient eth0' because I was told that it renews an ip address; 

[B]wmaster:0 unknown hardware address type 801
[/B][B]wmaster:0 unknown hardware address type 801
Listening on LPF/eth0/00:e0:b8:fa:c2:32
Sending on   LPF/eth0/00:e0:b8:fa:c2:32
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
[/B]**DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67**
[B]DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 prot 67 interval 8
[/B][B]DHCPDISCOVER on eth0 to 255.255.255.255 prot 67 interval 16
[/B][B]DHCPDISCOVER on eth0 to 255.255.255.255 prot 67 interval 13
[/B][B]DHCPDISCOVER on eth0 to 255.255.255.255 prot 67 interval 12
[/B][B]DHCPDISCOVER on eth0 to 255.255.255.255 prot 67 interval 12
No DHCP offers recieved.
Trying recorded lease 192.168.1.101
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 recieved, 100% packet loss, time 0ms

No working leases in perstent database - sleeping.
* Reloading /etc/samba/smb.conf smbd only
No process in pidfile '/var/run/samba/smd/pid' found running; none killed
     ...done.

[/B]
Now I know you can gather information from this, but my quesiton is this.. why is the command trying to do a DHCPDISCOVER on eth0 to 255.255.255.255 and not 255.255.255.0 ???? Is there anyway to reconfigure that so it doesn't try to renew to this and instead 255.255.255.0? What is it that tells DHCPDISCOVER to attempt to use 255.255.255.255 and not 255.255.255.0?

Thanks.

---

### Post by Loosewheel on 2009-07-29
Uncomment this line in 'net.rules' file:
# SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:e0:b8:fa:c2:32", 


get rid of the ' # ', and reboot.....

---

### Post by JUNiA on 2009-07-29
> **Loosewheel said:**
> Uncomment this line in 'net.rules' file:
# SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:e0:b8:fa:c2:32", 


get rid of the ' # ', and reboot.....


That was a typo in the last post, there are not '#' symbols in front of that key..

It really reads as this;

#PCI device 0x10ec:0x8136 (r8169)

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:e0:b8:fa:c2:32"

---

### Post by Loosewheel on 2009-07-30
"DHCPDISCOVER on eth0 to 255.255.255.255"  This is not a problem.

"Trying recorded lease 192.168.1.101
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 recieved, 100% packet loss, time 0ms"   This is.

If you have another ethernet cable, try swaping it out. Or, you could boot from the Live CD, and see if it brings up a connection.

---

### Post by JUNiA on 2009-07-30
> **Loosewheel said:**
> "DHCPDISCOVER on eth0 to 255.255.255.255"  This is not a problem.

"Trying recorded lease 192.168.1.101
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 recieved, 100% packet loss, time 0ms"   This is.

If you have another ethernet cable, try swaping it out. Or, you could boot from the Live CD, and see if it brings up a connection.


Tried both.  No success. My Live CD is a USB Stick (16gig).  How about this, could you teach me how to install Network Manager w/o an internet connection?

---

### Post by Loosewheel on 2009-07-30
JUNia,
I guess this is beyond me.
Have you thought about reinstalling Ubuntu 9.04....starting over?

Check out Ubuntu Help: click, System > Help and Support.
That will get you the Ubuntu Help Center.
Click, Adding, Removing, and Updating Applications > Installing Software Packages without Internet Connection.

That's going to tell you how to install packages from a CD....If you have a system to download and burn a Live CD, that might work.

---

### Post by JUNiA on 2009-07-31
> **Loosewheel said:**
> JUNia,
I guess this is beyond me.
Have you thought about reinstalling Ubuntu 9.04....starting over?

Check out Ubuntu Help: click, System > Help and Support.
That will get you the Ubuntu Help Center.
Click, Adding, Removing, and Updating Applications > Installing Software Packages without Internet Connection.

That's going to tell you how to install packages from a CD....If you have a system to download and burn a Live CD, that might work.


I could reinstall but i have already done that like 3 times and now I have the system setu p exactly how I like it.. sigh. 

I checked out that help and ha get this... my CD/DVD will not mount... good god.. 9.04 is like Africa..got some Big Bugs.. 

I have Live CD in the drive and it still can't mount it, I have adjusted my /etc/fstab file accordingly .. but still no go.

ahhhhhhhhhhhhhhhhhhhh ... i will just reinstall.  Does 9.04 still have a bug with reading teh CD/DVD Drive?

---

