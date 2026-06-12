---
title: "Samsung N150 Gobi 2000?"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by LordVaine on 2011-11-20
Hello, 

I am a first time Ubuntu User, decided to wipe my windows 7 starter from my Verizon Samsung N150 netbook and load up ubuntu on it. I know how to access the terminal if needed. My friend of mine has the same netbook with Ubuntu on it, however he is able to access the 3g connection from Verizon wireless on his NB, I am not able to do such, the preinstalled gobi 2000 card is not being detected. How do I set this up?

::EDIT::

I loaded up this hardware detector, and the qualcom device is detected.

48: USB 00.1: 0700 Serial controller
  [Created at usb.122]
  Unique ID: xnLL.ccp68s6JpK0
  Parent ID: k4bc.9T1GDCLyFd9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.1
  SysFS BusID: 1-4:1.1
  Hardware Class: unknown
  Model: "Qualcomm Gobi 2000"
  Hotplug: USB
  Vendor: usb 0x05c6 "Qualcomm, Inc."
  Device: usb 0x9244 "Qualcomm Gobi 2000"
  Revision: "0.02"
  Driver: "qcserial"
  Driver Modules: "qcserial", "qcserial"
  Device File: /dev/ttyUSB0
  Device Files: /dev/ttyUSB0, /dev/serial/by-path/pci-0000:00:1d.7-usb-0:4:1.1-port0, /dev/serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if01-port0
  Device Number: char 188:0
  Speed: 480 Mbps
  Module Alias: "usb:v05C6p9244d0002dc00dsc00dp00icFFiscFFipFF"
  Driver Info #0:
    Driver Status: qcserial is active
    Driver Activation Cmd: "modprobe qcserial"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #43 (Hub)


How do I configure it as active, with PPP and dial out to connect to the 3g connection?

---

### Post by Perfect Storm on 2011-11-21
Thread moved.

---

### Post by pdc on 2011-11-21
if you google, you get some references

[http://westhoffswelt.de/blog/0045_howto_setup_sony_vaio_x_wwan_gobi_2000_under_ubuntu_linux.html](http://westhoffswelt.de/blog/0045_howto_setup_sony_vaio_x_wwan_gobi_2000_under_ubuntu_linux.html)

and 

[http://ubuntuforums.org/showthread.php?t=1593581](http://ubuntuforums.org/showthread.php?t=1593581)

but perhaps the last may be the simplest

[https://nowhere.dk/articles/ubuntu-natty-making-a-gobi-2000-wireless-modem-work](https://nowhere.dk/articles/ubuntu-natty-making-a-gobi-2000-wireless-modem-work)

if you try that.........and let us know how you get along

---

### Post by LordVaine on 2011-11-21
Is there a way to do it without having a copy of windows?

---

### Post by pdc on 2011-11-21
I think this is your best bet

[http://www.voria.org/forum/viewtopic.php?f=3&t=643](http://www.voria.org/forum/viewtopic.php?f=3&t=643)

(I did this by following this  [http://bit.ly/rRmkbO](http://bit.ly/rRmkbO)  )                  .......can't find the icon for smiley face...........

good luck;

---

### Post by LordVaine on 2011-11-21
Sweet. It works but now a new issue is there. Verizon wireless is NOT on the supported list, so I have to enter an APN or make a custom name? I have the APN which is

AT+CGDCONT=1,"IP","inetgsm.vzw3g.com"

However its not letting me put Plus signs, commas, etc in the mobile broadband setup thing. What do I do next?

I tried to connect to it and it said 'modem connection disconnected)'


Also one more detail in the dropdown menu, it says Mobile Broadband and underneath it it says 'Not registered' AND mbis enabled. So how do I get this working? lol

---

### Post by pdc on 2011-11-21
this is a screenshot using network manager: selecting EDIT CONNECTIONS; (right or left click depending on which system one is running.........)

....mobile broadband.............add........US.>>>>>>>>Verizon Wireless

many folks have GSM systems; so a simcard and then the system knows who is contacting it.......

.....with a #777 system, one should have a username and a password........for an ID............

you enter those, and it should work.......

see screenshot below.........


> AT+CGDCONT=1........seems to me is a Hayes command ..

eg from a wvdial script...........so not needed here............

Surely you need to check again with Verizon for a username and password; and enter as I suggest above.......

...........well done to get it all installed.......that is a major breakthrough!! 

......and you got the firmware from the link too?

---

### Post by LordVaine on 2011-11-22
My provider is not on the list..and that APN i gave, the code, I called Verizon for it because Ubuntu said I should. I have a screenshot of the setup window, those are the only options I have,. The firmware was from the link you provided. THis is a huge breakthrough for someone who never toyed with Linux before. More programming is needed now to get this thing to work :D

WHen I click on the Wireless icon on the top bar to bring down the dropdown menu I was saying that under the Mobile Broadband (Greyed out) Is says registration denied.

-PS I have my username and password, got it from verizon, but still not connecting, being my provider is not selected...so we need to work on that now hehe

---

### Post by pdc on 2011-11-22
OK;

I would suggest clicking in the window below the installed options you show...........nothing for Verizon there??

I would set up the Verizon as I showed in my screenshot:

name is verizon, number is #777 and you enter your username and password; click to accept;

then if you click on the network manager icon, it should offer you the verizon you set up.........and you should be able to click on that 

> I was saying that under the Mobile Broadband (Greyed out) Is says registration denied.

......not sure about this;

---

### Post by LordVaine on 2011-11-22
Tried it as you said, not letting me connect. No verizon on the list

---

