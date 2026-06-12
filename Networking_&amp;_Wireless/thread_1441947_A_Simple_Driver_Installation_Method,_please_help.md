---
title: "A Simple Driver Installation Method, please help"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by seano33 on 2010-03-29
I'm looking all over these forums and other places and yet nothing has come along simply stating, "This is how you install a driver from scratch..."

Please help. I have downloaded this. [http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/)
I believe it has the driver I need. But they don't explain how to install it simply. Nothing makes this obvious to a newbie. 

Its for a Linksys PCI Wireless card. Karmic Koala 9.10. Intel P4 tower. Please help.

---

### Post by n0dix on 2010-03-29
Do you first look in the drivers recommendations: System > Administration > Hardware Drivers?

---

### Post by seano33 on 2010-03-29
Yes, nothing

---

### Post by Iowan on 2010-03-29
Found [this]("http://www.extremetech.com/article2/0,2845,2111770,00.asp") article for installing Linksys wireless driver - but it's dated April '07. A couple of others were more currint - but model-specific.

---

### Post by chili555 on 2010-03-29
There might be a simple method, depending on which Linksys it is. Please open a terminal and do:```
lspci -nn
```Post the result and we'll get you running!

---

### Post by seano33 on 2010-03-30
I have done as you say, and here is the result. Thank You. Very interesting. The Linksys shows up at the bottom.

00:00.0 Host bridge [0600]: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) [8086:2530] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge [8086:2532] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 04)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 04)
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 04)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 04)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] [10de:002d] (rev 15)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03)
02:09.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
02:09.1 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
02:09.2 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
02:09.3 USB Controller [0c03]: ALi Corporation USB 2.0 Controller [10b9:5239] (rev 01)
02:09.4 FireWire (IEEE 1394) [0c00]: ALi Corporation M5253 P1394 OHCI 1.1 Controller [10b9:5253]
02:0a.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]
02:0b.0 Serial controller [0700]: 3Com Corp, Modem Division 56K FaxModem Model 5610 [12b9:1008] (rev 01)
02:0c.0 Ethernet controller [0200]: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 [1317:0985] (rev 11)
02:0d.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)

---

### Post by seano33 on 2010-03-30
Also, the Model is WMP11. That is not on this page. [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCI)

So anyway... I'm learning that there is no tried true and simple way for all this to work... I suppose not until manufacturers begin developing hardware with Linux drivers right on their support pages.

---

### Post by chili555 on 2010-03-30
> there is no tried true and simple way for all this to work.Actually, there probably is.

The drivers for it have been built in to the kernel for many years; sometimes two conflicting drivers load. May I please see:```
lsmod | grep -e host -e orinoco
```Thanks.

---

### Post by seano33 on 2010-03-30
lsmod | grep -e host -e orinoco

result

hostap_pci             48652  0 
hostap                103360  1 hostap_pci
lib80211                6432  2 hostap_pci,hostap
orinoco_pci             4700  0 
orinoco                63600  1 orinoco_pci

---

### Post by chili555 on 2010-03-30
Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add two new lines:```
blacklist hostap
blacklist hostap_pci
```Proofread carefully, save and close gedit. Reboot with any ethernet cable detached. Click the Network Manager icon and see your network and connect. Post back and tell us how your wireless is working.

---

### Post by seano33 on 2010-03-30
I'm not sure what to think. I don't know if its recognizing anything. It so far still shows no wireless signal (as I write this I'm connected via Mac airport card on my laptop) but my Ubuntu still shows no signal. There is a house wireless signal that I'm not getting on the Ubuntu computer and when I click on the icon at the top right of the screen, it shows all ports as disconnected. When I checked System>Network Connections, I could see the name of my network under wireless, but it had no info inside it and I think that I had created it myself in a blind attempt to seek the signal, some time before posting at this forum.

I'm not sure how I was supposed to run that code. But I did what I thought you meant. Here is the info.

The following was done in two steps as I understood the instructions.

1st ENTERED CODE:
sudo gedit /etc/modprobe.d/blacklist.conf

RESULT:
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

2nd ENTERED CODE:
blacklist hostap
blacklist hostap_pci

RESULT:

sean@InterArts:~$ blacklist hostap
blacklist: command not found
sean@InterArts:~$ blacklist hostap_pci
blacklist: command not found
sean@InterArts:~$ 

THEN I RESTARTED THE COMPUTER AND RAN THE 1ST STRING OF CODE AGAIN. FOLLOWING THAT I ADDED YOUR BLACKLIST COMMANDS IN TO THE RESULTING CODE PASTED ABOVE AND PRESSED SAVE, RESTARTED THE COMPUTER AND GOT NOTHING DIFFERENT. HAVE I DONE THIS RIGHT??

---

### Post by chili555 on 2010-03-30
> HAVE I DONE THIS RIGHT??No, sir. You were to add the two lines to the file you opened up so it looks like this:> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist hostap
blacklist hostap_pci
Proofread your entries carefully. Click 'Save' at the top of gedit. Close gedit. Now reboot and give us your report.

---

### Post by seano33 on 2010-03-31
Gosh, nothings working, I'm sorry. Actually, even though I messed up my first attempt, I did enter in your code just like you have it there. In fact I wrote that point in caps in the last post, though I could understand if that didn't read clearly. So tonight, just now, when I ran the sequence and the gedit document opened up, it showed the document exactly as you have it there above, since I had done that and saved it correctly yesterday. Thus, this technique isn't working.

I bought this PCI card from a place that told me it had been tested in Ubuntu to work. Perhaps they didn't really. Its a volunteer run place without tech support for customers, so nobody is riding anyone's a$$ if things aren't properly tested.

Thanks for all your help. Let me know if you think of anything. I might just plug this in via ethernet at this point to see if the automatic updating will work. 

By the way, you just want me to click on the icon at the corner of the screen right? If the driver is working then bars should be showing up right?

---

### Post by chili555 on 2010-04-01
Yes, I do want you to click on the icon. The bars will be showing *after you are connected.* For security reasons, Ubuntu will not just automatically connect to any old rogue, virus-ridden access point. You must click the icon and select your known, trusted network. You will be asked for any WEP or WPA details and connect.

Prism 2.5 cards are very well supported. I have a PCMCIA version and have had it working on two different laptops in the last few weeks; with, of course, the *hostap *gang blacklisted. Mine is old enough that it does not support WPA and only does 11 Mb/s.

Post back; I am anxious to help you get going.

---

### Post by seano33 on 2010-04-01
Right, so thats just it, I always go to that icon and look for bars and my household wireless signal (the one my Apple ibook is connected to now which comes in very strong) and it doesn't show. It has never showed. When I click and it lists 3 possible access points from two separate ethernet ports and the wireless port, each of them say "disconnected". I'm not sure what else to say about it.

Just out of theoretical curiosity, that gedit document is read by Ubuntu in some kind of sequence which tells the computer how to operate the hardware? Is that kind of a rough vague idea of the theory of how this works?

So finally, I'm anxious for you to help me also, I really do appreciate all your help.  Well you know what, I'll have a friend with the same problem (but his is a laptop wifi card) do the same sequence to see what happens and let you know what changes for him. In the mean time, my computer is boxed up as I'm moving to a new address on Saturday, but I have to be out of here today. So two days of crashing around and hopefully I'll have Ubuntu up and running again on Sunday.

---

### Post by chili555 on 2010-04-01
> it lists 3 possible access points from two separate ethernet ports and the wireless port, each of them say "disconnected"So you do not see any networks from which to select? Please see attached. In this example, there are three networks available, GBR1, to which I connected, Dynex and WEST5214. Do you see nothing or nobody? Please run a command in a terminal:```
iwconfig
```Do you see a wireless interface, similar to this?> lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:24:56:2A:77:89   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0If not, we have not yet created a wireless interface to use to connect.> Just out of theoretical curiosity, that gedit document is read by Ubuntu in some kind of sequence which tells the computer how to operate the hardware?Gedit is a text editor; we used to to change a file in the system, called 'blacklist.' We said, hey, system, you are trying to load too many conflicting drivers for this poor card to handle. We know the orinoco boys will do a good job, so please put the hostap gang in jail so they can't start a fight. This is from your earlier post:> smod | grep -e host -e orinoco

result

[COLOR="Red"]hostap_pci[/COLOR] 48652 0
[COLOR="Red"]hostap[/COLOR] 103360 1 [COLOR="Red"]hostap_pci[/COLOR]
lib80211 6432 2 [COLOR="Red"]hostap_pci,hostap[/COLOR]
orinoco_pci 4700 0
orinoco 63600 1 orinoco_pci > Well you know what, I'll have a friend with the same problem (but his is a laptop wifi card) do the same sequence to see what happens and let you know what changes for him.Unless your friend also has a Prism 2.5 card, it will do nothing.

Post back on Sunday; I will be around.

---

### Post by gordintoronto on 2010-04-01
Just to go back to your original question, which was "how do you install a driver," the answer in your case is, "you don't, it has been part of Linux for several years." In fact, Linux already contains many, many drivers.

BTW, I find a slightly different approach works for me in getting wireless working: right-click on the network manager icon, select "edit connections." When the window opens, click the wireless tab, then "add." Then you enter SSID, encryption type and password in the appropriate spots.

---

