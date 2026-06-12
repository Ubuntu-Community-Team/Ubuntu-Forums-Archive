---
title: "I can't get my graphics card to work OR SOMETHING??"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by adn258 on 2008-01-23
okay I have a Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
......I don't think it is working or something when I go to System > Preferences > appearance and then visual affects it's on NONE:  And where it says normal it says you need moderate performance requirements and  I have more than enough lol I bought a 1000 dollar computer laptop here about 4 months agot and I could play heated 3D games.  Now I can't even get this to work let alone BERYL WHICH I WANT!!  here are all my stats help me out ??????????????????????????????????????????????

austin@bomb:~$ lcpi
bash: lcpi: command not found
austin@bomb:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)



Peace  



BTW my computer is a Hp Pavillion dv6000 EVERYTHING ELSE IF WORKING I JUST DON'T GET ADVANCED GRAPHIC STUFF

---

### Post by dannyboy79 on 2008-01-23
what graphics driver are you using? please post back the results of this command:

cat /etc/X11/xorg.conf | grep Driver

it should either say "intel" or "i810"

also, do this to make sure you don't ahev the proprietary ati driver installed.

sudo apt-get --purge remove xorg-driver-fglrx

here's the thread I found with the same graphics card as yours.

[http://forum.compiz-fusion.org/showthread.php?p=46558](http://forum.compiz-fusion.org/showthread.php?p=46558)

---

### Post by adn258 on 2008-01-23
> **dannyboy79 said:**
> what graphics driver are you using? please post back the results of this command:

cat /etc/X11/xorg.conf | grep Driver

it should either say "intel" or "i810"

also, do this to make sure you don't ahev the proprietary ati driver installed.

sudo apt-get --purge remove xorg-driver-fglrx

here's the thread I found with the same graphics card as yours.

[http://forum.compiz-fusion.org/showthread.php?p=46558](http://forum.compiz-fusion.org/showthread.php?p=46558)

okay as you can see below I DON'T HAVE THE ATI thing installed and it says INTEL I think mhm.  Now what do I do the advanced desktop features still don't work.

Peace friends

austin@bomb:~$ cat /etc/X11/xorg.conf | grep Driver
        Driver          "kbd"
        Driver          "mouse"
        Driver          "synaptics"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "intel"
austin@bomb:~$ 
austin@bomb:~$ sudo apt-get --purge remove xorg-driver-fglrx
[sudo] password for austin:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xorg-driver-fglrx is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
austin@bomb:~$

---

### Post by dannyboy79 on 2008-01-23
you go to that link I provided and read that thread. he has the same graphics card and the main developers of compiz-fusion tell him how to get desktop effects working. if you go to that thread and do all that they suggest, then let them know that in that samew thread, if they still can't gelp, then come back here.

---

### Post by adn258 on 2008-01-24
> **dannyboy79 said:**
> you go to that link I provided and read that thread. he has the same graphics card and the main developers of compiz-fusion tell him how to get desktop effects working. if you go to that thread and do all that they suggest, then let them know that in that samew thread, if they still can't gelp, then come back here.

okay sorry friend but I tried all that stuff with no success :/ and I kept getting what you see below meaning I didn't have what I was supposed to remove.  What should I do now? 


Reading state information... Done
Package xorg-driver-fglrx is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
austin@bomb:~$

---

### Post by dannyboy79 on 2008-01-24
please post your xorg.conf file so I can see what you all have in there.

---

### Post by magnat2 on 2008-01-24
> **adn258 said:**
> okay I have a Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
......I don't think it is working or something when I go to System > Preferences > appearance and then visual affects it's on NONE:  And where it says normal it says you need moderate performance requirements and  I have more than enough lol I bought a 1000 dollar computer laptop here about 4 months agot and I could play heated 3D games.  Now I can't even get this to work let alone BERYL WHICH I WANT!!  here are all my stats help me out ??????????????????????????????????????????????

austin@bomb:~$ lcpi
bash: lcpi: command not found
austin@bomb:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)



Peace  



BTW my computer is a Hp Pavillion dv6000 EVERYTHING ELSE IF WORKING I JUST DON'T GET ADVANCED GRAPHIC STUFF
Your graphic card is blacklisted, due to problems of stability, in normal ubuntu 7.10 installation the intel driver is already provided and installed, if you want to see a work-around go: [http://acer5720linuxubuntu.blogspot.com/2008/01/acer-5720-ubuntu-710-eng.html](http://acer5720linuxubuntu.blogspot.com/2008/01/acer-5720-ubuntu-710-eng.html)

Its very easy, you should not have any trouble:)

---

### Post by adn258 on 2008-01-24
> **magnat2 said:**
> Your graphic card is blacklisted, due to problems of stability, in normal ubuntu 7.10 installation the intel driver is already provided and installed, if you want to see a work-around go: [http://acer5720linuxubuntu.blogspot.com/2008/01/acer-5720-ubuntu-710-eng.html](http://acer5720linuxubuntu.blogspot.com/2008/01/acer-5720-ubuntu-710-eng.html)

Its very easy, you should not have any trouble:)

BELIEVE IT OR NOT it still didn't work but I think were getting close I tried using the command the say fixes it and look what I got.  A syntax error what is wrong with it it's what they tell you to use.

Peace

austin@bomb:~$ sudo su
root@bomb:/home/austin# Mkdir-p ~ / .config / compiz / & & echo SKIP_CHECKS = yes>> ~ / .config / compiz / compiz-manager
bash: syntax error near unexpected token `&'
root@bomb:/home/austin#

---

### Post by dannyboy79 on 2008-01-24
it most likely should be 

```
mkdir -p  ~/.config/compiz/ && echo SKIP_CHECKS = yes >> ~/.config/compiz/compiz-manager

```

you had way too many spaces. it looks like that blog had spaces in it so it's not your fault. What this command is doing is first it's creating a directory within your users home directory and it's path is /home/username/.config/compiz/, then the 2 &'s mean, do this next command only after you have done the first one (meaning create that directory. Echo means, display a line of text to standard out (which is SKIP_CHECK = yes) and the 2 >'s mean to append what was displayed to standard out to the end of a  file called compiz-manager within that folder you just created at the beginning of the command.

good luck. fyi, without the proper xorg.conf it's not going to run right which is why I asked to see it.

---

### Post by adn258 on 2008-01-24
> **dannyboy79 said:**
> it most likely should be 

```
mkdir -p  ~/.config/compiz/ && echo SKIP_CHECKS = yes >> ~/.config/compiz/compiz-manager

```

you had way too many spaces. it looks like that blog had spaces in it so it's not your fault. What this command is doing is first it's creating a directory within your users home directory and it's path is /home/username/.config/compiz/, then the 2 &'s mean, do this next command only after you have done the first one (meaning create that directory. Echo means, display a line of text to standard out (which is SKIP_CHECK = yes) and the 2 >'s mean to append what was displayed to standard out to the end of a  file called compiz-manager within that folder you just created at the beginning of the command.

good luck. fyi, without the proper xorg.conf it's not going to run right which is why I asked to see it.
I got it working thanks so much dude :)

---

### Post by adn258 on 2008-01-24
Okay now that I got this working I would like to install beryl but so far have had no success can someone help my graphics are working but like beryl I followed their installation instructions and it said like important kbd file missing. What am I doing wrong? What is the easiest way to install it? From the link below I am using the latest version.

[http://www.beryl-project.org/releases.php](http://www.beryl-project.org/releases.php)

---

### Post by dannyboy79 on 2008-01-25
> **adn258 said:**
> Okay now that I got this working I would like to install beryl but so far have had no success can someone help my graphics are working but like beryl I followed their installation instructions and it said like important kbd file missing. What am I doing wrong? What is the easiest way to install it? From the link below I am using the latest version.

[http://www.beryl-project.org/releases.php](http://www.beryl-project.org/releases.php)
well I never messed with Beryl. I know compiz and beryl joined to make compiz-fuzion so why do you want to use Beryl? Sorry, can't help anymore.

When I did a search in aptitude for kdb, this is what it returned:
p   kdbg                            - graphical debugger interface
p   kdbus                           - D-BUS service browser for KDE
p   libdevel-ptkdb-perl             - Perl debugger using a Tk GUI

You could try installing those but still unsure if that's going to do it.

---

### Post by adn258 on 2008-01-25
> **adn258 said:**
> Okay now that I got this working I would like to install beryl but so far have had no success can someone help my graphics are working but like beryl I followed their installation instructions and it said like important kbd file missing. What am I doing wrong? What is the easiest way to install it? From the link below I am using the latest version.

[http://www.beryl-project.org/releases.php](http://www.beryl-project.org/releases.php)

awww it's cool dude I am pleased you have all been very helpful now if I could just back up my system lol which I don't know how to do.

---

### Post by dannyboy79 on 2008-01-25
have you checked out simple-backup (sbackup) or even this script that someone created?

[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

---

### Post by adn258 on 2008-01-25
> **dannyboy79 said:**
> have you checked out simple-backup (sbackup) or even this script that someone created?

[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

no but that's awesome dude thanks :)

---

