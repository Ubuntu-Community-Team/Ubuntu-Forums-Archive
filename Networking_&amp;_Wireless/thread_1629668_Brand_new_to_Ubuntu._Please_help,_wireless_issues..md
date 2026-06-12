---
title: "Brand new to Ubuntu. Please help, wireless issues.."
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by CretanThreat on 2010-11-24
Hello all, I am a fresh convert to the linux scene and I know virtually nothing about this beautiful piece of engineering.

I recently reformatted and dual partitioned to both Windows 7 as well as ubuntu 10.10.

Loading works fine and Windows 7 is 100% operational. I cannot seem to get my wireless network adapter to be read by Ubuntus 'Windows Wireless Drivers' gui. 

Here are the steps that I have done THUS far, to make sure that we are all on the right path.

Before I go any further, my wireless network adapter is an old school WUSB11 Linksys Wireless Network Adapter (running version 2.6).

Ok so... 

I have....

1) Downloaded and installed "ndiswrapper" from ubuntu's main website. I downloaded the common, utils and ndisgtk files and installed them accordingly.
2) I extracted these three files to the desktop of Ubuntu and accessed the terminal page.
3) From terminal I typed "cd Desktop" to change the directory to the desktop.
4) Next, I typed in "Sudo dpkg -i ndiswrapper-common_1.54-2ubuntu1_all.deb
                            Sudo dpkg -i ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb
                            Sudo dpkg -i ndisgtk_0.8.5-1_i386.deb"
5) This installed Windows Wireless Drivers gui successfully and I can access it.
6) I have downloaded the driver files for the adapter from the cisco website and searched them for the required files needed.
7) After extracting the .INF file from the "Drivers" directory named "NETUSB.SYS" (I wasn't sure if the other associated files within the same folder needed to be present together with NETUSB so I moved everything to the desktop) I typed in "sudo ndiswrapper -i NETUSB.inf".
8)After accessing the Windows Wireless Drivers gui I have noticed that the 'netusb' driver is present yet under it, the system states "Hardware present: No". This leads me to believe that maybe I installed incorrectly or my "fireware?" is not present? I was reading through the installation guide posted on the ubuntu website that in addition to the .INF file we also need the BIN file(s)? and SYS file(s)?.. The folder with the drivers for my adapter contains a BIN file but it is not within the "Drivers" section of the folder. 
9) Please advise me as to what to do. Upon mousing over the network Icon naturally my hardware is still not present.
10) From what I gather after the system finds the hardware I am to write into the terminal
         " ndiswrapper -l
           sudo depmod -a
           sudo modprobe ndiswrapper

           sudo ifdown wlan0
           sudo ifup wlan0

           sudo ndiswrapper -m  "

11) When I try to type sudo ndiswrapper - m into the terminal now it depicts an error stating "All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."

Any help would be greatly appreciated. 

I really want to start using Ubuntu!

Thanks! 

Emmanuel

---

### Post by CretanThreat on 2010-11-24
Ok so small update here. 

I was skeptical of the fact that I had all the driver files including the .BIN, .INF, and .SYS files and I was unsure as to why the gui NDISWRAPPER said that the hardware wasnt present. 

Using the graphical interface I delete the presnt NETUSB driver that was listed there and extracted every single thing that I thought was useful to the desktop of ubuntu.

From there I went back into the GUI and I selected NETUSB.INF again and this time it depicts the drivers installed as NETUSB (hardware: present). So it thinks that my hardware is somewhere?... nonetheless I still see no change in the wireless connectivity at the top of the page and my adapter is still no where to be found. 

I ran again the ndiswrapper -m command to see what it would do and now it depicts the files need .conf stuff for the ndiswrapper files.

Any ideas? 

Thanks a bunch!

---

### Post by CretanThreat on 2010-11-24
I ran lsusb and got the following back from the terminal:
 
*-network               
       description: Ethernet interface
       product: N10/ICH 7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:c2:6e:d8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI    
       [COLOR=Red]firmware=N/A[/COLOR] latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:ebeff000-ebefffff ioport:c8c0(size=64)

[COLOR=Red]Is this saying that I don't thave firmware installed? When I open the NDISWRAPPER gui it says that the drivers are installed and the hardware is present.

Below is what happens when typing in ndiswrapper -l

Please help.
[/COLOR]
emmanuel@emmanuel-Dell-DM051:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netusb : driver installed
    device (1915:2233) present (alternate driver: at76c50x_usb)

---

