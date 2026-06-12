---
title: "Need help with wireless and wired networking."
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by spartan0746 on 2009-04-03
I'm using an aspire one netbook running Xp at the moment sigh

But as this also comes in a working Ubuntu model im not sure as to why the networking is not working. I clicked enable networking and was still unable to connect to a ethernet connection. And the option to enable wireless is not there.

I'm sure as a Linux new boy its just me messing up, but any help would be appreciated.

"I have it on good authority that several Ubuntu users have successfully connected to the internet, myself included. (grin) I would advise looking at your Windows connection and see if you have a fixed IP address or are using an address assigned by your DSL router, etc.. I agree that the Ubuntu Fora would be the place to go, but let them know HOW you expect to connect to the internet, i.e., what hardware is being used to provide the connection (DHCP). ... I used an Ubuntu Live CD to Ubuntuize an XP computer here and it connected with no problem. I'm using a 2Wire DSL modem which supplies IP addresses to my computers." ive been told that on reddit and if im honest im not exactly sure what they mean... Yes im a new guy so please be nice :D

And im on an acer aspire one netbook. 

# Intel Atom N270 1.6 GHz Processor
# 512 KB L2 Cache, 533 MHz Front Bus speed
# 1024 MB DDR2 (PC2-4200) RAM
# 120GB (5400 RPM) SATA Hard Drive

    *  3 USB 2.0 ports for connecting a wide range of peripherals--from digital cameras to MP3 players
    * Secure Digital (SD) card reader, also compatible with MultiMedia cards (MMCs)
    * Multi-in-one card reader supports SD, MMC, Memory Stick/Memory Stick PRO, and XD Picture Cards
    * 1 VGA monitor port
    * 1 headphone jack and 1 microphone jack
    * RJ-45 port for 10/100 Fast Ethernet connection
Intel Graphics Media Accelerator 950, which uses shared video memory with the main memory 

I'm sure you all know this though.

---

### Post by kestrel1 on 2009-04-03
Can you post the output of```
ifconfig
```
You need to open a terminal to run this command.

---

### Post by spartan0746 on 2009-04-03
sam@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:b8:8c:f7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:497725881 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

sam@ubuntu:~$

Sorry this took so long. i had to fire up the second computer so i could run the laptop at the same time.

---

### Post by kestrel1 on 2009-04-03
OK, your ethernet controller looks like it is installed, but no wireless. Can you now try this command & post the result```
lspci
```

---

### Post by spartan0746 on 2009-04-03
sam@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
sam@ubuntu:~$

---

### Post by kestrel1 on 2009-04-03
Looking at that output it does look like the wireless has been installed.
If you left click on the NM-Applet what do you see? If you right click on it are you able to enable networking?

---

### Post by spartan0746 on 2009-04-03
Ive enabled networking. If i right click.

But if i left click i see auto eth0 and Wired Network but they are faded out and i cant click them.

---

### Post by kestrel1 on 2009-04-03
What version of Ubuntu are you using? I assume 8.10. If so I need to reboot so that I can guide you better. On 8.04 at present.

---

### Post by spartan0746 on 2009-04-03
I assume so, I used wubi. So whatever version that downloads.

Thanks for the help btw!

---

### Post by kestrel1 on 2009-04-03
I may not get to reboot for a while as I am installing knoppix on a virtual machine at present, but I will as soon as I am able. I am in the UK & it is nearly 9pm. I was up at 6am & will probably get to bed by 11pm tonight. So if I do not reply in the next couple of hours I will get back to it tomoorow. Sorry if there is a delay.

---

### Post by spartan0746 on 2009-04-03
Yeh i'm in the uk aswell. I'm going out soon anyway i think. So i probably wont be able to get back to this till the morning either.

---

### Post by kestrel1 on 2009-04-04
Got on to my 8.10 syatem now.
If you right click on the NM-applet you should see 'Edit Connections'
This should open this screen:
[ATTACH]108636[/ATTACH]
If you select the Auto eth0 & click 'Edit' you should get this sort of screen:
[ATTACH]108637[/ATTACH]
If you go to the IPv4 Settings tab is this set to Automatic (DHCP):
[ATTACH]108638[/ATTACH]

---

### Post by YMS_1975 on 2009-04-04
I've got the same problem. I've got an MSI GX-720 laptop, and as spartan0746 mentioned, when I right click on the icon, I get the exact same results. 

I just can't connect wirelessly online.

---

### Post by spartan0746 on 2009-04-04
Yeh its set to that. 

And is this for wired or wireless? And how do you search for wireless networks on Ubuntu? Just to see if theres even a way around to conenct to any of them.

---

### Post by kestrel1 on 2009-04-04
With 8.10 if you left click on the NM-applet you should get wireless networks that are available listed.
That was for the Wired network connection. You can do the same for the wireless to see how it is configured if you go to the Wireless tab.
I thought it would be best to get one thing working first though. Are you sure that the ethernet cable that you are connecting your computer to your router is OK.

---

### Post by spartan0746 on 2009-04-04
Wooo wired is finally working! 

Just down to wireless now. I know wireless is working on my other computer as is connected now and to my Iphone.

---

### Post by kestrel1 on 2009-04-04
What got the wired connection going?

---

### Post by spartan0746 on 2009-04-04
I'm not sure. And i was using the same cable and connection i tried last night.

---

### Post by kestrel1 on 2009-04-04
Oh well, at least it is working. Now to the Wireless.
What result do you get if you type```
iwconfig
``` in a terminal.

---

### Post by spartan0746 on 2009-04-05
sam@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

sam@ubuntu:~$

Ive been at work all day. Sorry i took so long to reply.

---

### Post by kestrel1 on 2009-04-05
Doesn't appear to be picking up the wireless for some reason. Have a look at this thread & see if it helps:
[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

---

