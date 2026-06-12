---
title: "Help with dial up please!!!"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by ryan mckeown on 2009-06-08
Hey.
Ok so heres the problem I'm faced with:

A few weeks ago I received the Ubuntu 9.04 (Jaunty Jackelope) CD and I installed it alongside my Windows XP OS on my Dell Dimension 3000. I think I'm right in saying that Ubuntu 9.04 has the kernal 2.6.28-11 (whether thats important or not is beyond me). Anyway I installed it with sucess and was quite happy until I decided to try to get online. I looked up the installed manual (System > Help and Support) and it said that "NetworkManager manages wired, wireless, mobile broadband, vpn and dsl connections. It does not currently support dialup modem connections but there is help available in Chapter 6 &#8213; Modems". So I went to chapter 6.1 titled "Identifying your modem" and from the instructions there, I downloaded scanModem from [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz) (under Windows XP) and followed the rest of the instructions to open "ModemData.txt". ModemData.txt contains the following information:

```

 Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.28-11-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: http://www.linux.org/groups/index.html.
They will know your Country's modem code, which may be essential for dialup service.
Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009
 scanModem update of:  2009_05_12

 There are no blacklisted modem drivers in /etc/modprobe*  files 
 Potentially useful modem drivers now loaded are:
                

Attached USB devices are:
 ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
 ID 04f2:a13e Chicony Electronics Co., Ltd 
 ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
 ID 0ea0:2168 Ours Technology, Inc. Transcend JetFlash 2.0 / Astone USB Drive
 ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
 ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
 ID 413c:5008 Dell Computer Corp. 
 ID 08ca:0021 Aiptek International, Inc. APT-2 Tablet
If a cellphone is not detected, see http://ubuntuforums.org/archive/index.php/t-878554.html

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to discuss@linmodems.org

For candidate card in slot 01:01.0, firmware information and bootup diagnostics are:
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 01:01.0    8086:1080    1028:1000    Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI 

 Modem interrupt assignment and sharing: 
 --- Bootup diagnostics for card in PCI slot 01:01.0 ----
[    0.678108] pci 0000:01:01.0: reg 10 32bit mmio: [0xfeafe000-0xfeafefff]
[    0.678115] pci 0000:01:01.0: reg 14 io port: [0xde00-0xdeff]
[    0.678152] pci 0000:01:01.0: PME# supported from D0 D3hot D3cold
[    0.678156] pci 0000:01:01.0: PME# disabled
[    1.979232] serial 0000:01:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.979345] 0000:01:01.0: ttyS1 at I/O 0xde08 (irq = 22) is a 16450
[    1.979420] 0000:01:01.0: ttyS2 at I/O 0xde10 (irq = 22) is a 8250
[    1.979494] 0000:01:01.0: ttyS3 at I/O 0xde18 (irq = 22) is a 16450
[    1.979519] Couldn't register serial port 0000:01:01.0: -28

 The PCI slot 01:01.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to discuss@linmodems.org
 if help is needed.
 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 01:01.0:
    Modem chipset  detected on
NAME="Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI "
CLASS=0703
PCIDEV=8086:1080
SUBSYS=1028:1000
IRQ=22
IDENT=INTEL537EP

 For candidate modem in:  01:01.0
   0703 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI 
      Primary device ID:  8086:1080
 Support type needed or chipset:    INTEL537EP
 


 Since 2006, Intel appears to have ceased its modem code updates for Linux.
 The outdated official Intel support packages can be accessed through:
       http://developer.intel.com/design/modems/support/drivers.htm
 Beneficially, Philippe Vouters has been provided updates as the Linux kernel evolves.
 But intensive personal support is not feasible, see:  http://archives.linmodems.org/24939
 The code for the INTEL537 and INTEL536 chipset modems is at
       http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/

 For Ubuntu Linux users with Intel 536 and 537 chipsets, there are driver 
 installation packages available thru http://groups.google.com/group/ubuntu-modems

 Read DOCs/Intel.txt and Modem/DOCs/YourSystem.txt for follow through guidance.


Writing DOCs/Intel.txt

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.3.3
             and the compiler used in kernel assembly: 4.3.3

 The patch utility is needed and is needed for compiling ALSA drivers, and possibly others. 

 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.3
   linuc_headers base folder /lib/modules/2.6.28-11-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at http://packages.ubuntu.com
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through http://packages.ubuntu.com
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
    -rwsr-xr-- 1 root dip 277352 2009-02-20 17:25 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html

To enable dialout without Root permission do:
    $ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
    sudo chmod a+x /usr/sbin/pppd

Checking settings of:    /etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

```I also went to the link at the bottom of the page (also under XP): [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) and I found that installing a dial-up modem should be as simple as:
   1. Indentify the modem
   2. Download a driver for your modem or buy a more suited modem
   3. Configure the connection to your ISP

Seemed staight forward enough. I already had identified my modem using scanModem and its a: Intel Coroperation FA82 537EP 56k V.92 DATA/FAX MODEM found on the PCI. I also know its in (windows settings) COM3.
So then I proceeded and clicked on the link "Setup Intel537EP driver" ([https://help.ubuntu.com/community/DialupModemHowto/Intel537EP](https://help.ubuntu.com/community/DialupModemHowto/Intel537EP)) and found that the driver was "pre-packaged" for new users (me!) into a .deb file. So I downloaded it and ran it with aparant sucess in Ubuntu.
Therefore, I continued to the third stage, I downloaded gnome-ppp (I heard it was good from threads I read and I found a useful page: [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer.htm](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer.htm) which gave me instructions as to how to install and run gnome-ppp) along with the dependancies it needed and ran it. I added myself to the dip and dialout groups, configured gnome-ppp and tried to dial. However, when I click "dial" the message appears "sending password" and it stays like that until the thing times out. I then decided to use wvdialconf to see if it detected my modem and it said it didn't.
I've tried loads of things since then and got nowhere. I found out that my modem has a Ambient MD3200 chipset and that Intel's support for the driver has all but ran out. Intel is actually telling me to try to contact the manufacturer because aparently Intel never actually manufactured the product themselves, they just put their name on it. I also learnt that Intel was formerly Ambient which was formerly Cirrus Logic. Aparently too there was a driver released for linux for my modem back in about 2002 but I can't seem to find it anywhere.

My ISP is Tiscali and I know the phone number to dial, the username and I have a fair idea of what my password is to use. I also know that the DNS address is determined on connection and the ISP uses PPP transfer methods.

Can anyone shed light on my gloomy situation? I've been trying everything I can for days now and constantly switching between OS is fustrating. Can you tell me how to get my modem to work or am I just better off buying a new one (if so do you have any suggestions, I don't want anything too expensive as I will be getting broadband in the new house we are building (in about 6-8 months)).

Also can you please explain everthing in lots of detail because, even though I have some experience in programming under Windows, Linux is still very new to me and hardware wouldn't really be my strong point either.

Thanks
Ryan

---

### Post by ryan mckeown on 2009-06-08
Wow this forum moves fast.
I have also encountered lots of broken links along my way, just so you know that those may need updating (not just your sites though).


Please can someone reply to give me some advise...


Ryan

---

