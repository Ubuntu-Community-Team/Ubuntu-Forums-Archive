---
title: "Newbie troubles with wifi"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by Rob.I on 2009-06-26
Hi all, I'll try to be as informative as possible. I have a Dell Inspiron 6000 that I bought about 3 years ago. I recently (today) reformatted windows and wiped it off my computer. I installed the latest Ubuntu and I love it so far. The only thing I can't get is the wireless. In the bios, my Wifi is turned on, so I'm assuming there are drivers I have to install in order to activate the wifi card or something? In the Network system tray icon under Wireless, there is nothing there. I tried reading the documentation, but it was way over my head. Can an Ubuntu noob like me get some down to earth help? Thanks, Rob!

---

### Post by kerry_s on 2009-06-26
i just noticed theres 2 types of wireless used.
open the terminal & type> lspci
tell us what kind of wireless it is.

---

### Post by Rob.I on 2009-06-26
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by kerry_s on 2009-06-26
> Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

i was so hopping it was not that 1, those are a pain in the butt.
i'm going to leave you to someone who has installed that recently.
hang in there, i know people have got that card working around here.

bumping you up.

---

### Post by Rob.I on 2009-06-26
Allright, thanks!

---

### Post by Rob.I on 2009-06-26
I tried dropping down to 8.10 since when I searched people seemed to have more luck...I typed in iwconfig and here is what I got:


lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by Rob.I on 2009-06-26
Still have had no luck whatsoever...I've read countless threads and tried countless things.

---

### Post by kerry_s on 2009-06-27
man, i can't believe no one has helped you yet.

the last time i did that card, if i remember right, i had to go with ndiswrapper and use the windows inf.

**sudo apt-get install ndisgtk**

thats the gui for ndiswrapper. i think i got the "inf" file off the recovery disk. also i think you have to blacklist the kernel bcm driver.

sorry, i know it's not a lot of info,  it's been at least 8 months since i dealt with that card on a friends pc & it took us forever to get it working.

---

### Post by Rob.I on 2009-06-27
I do have a "bcmwl5.inf" on my thumb drive...and the "bcmwl5.sys" file...but I don't know what to do with them...I don't know the command in Terminal.

---

### Post by kerry_s on 2009-06-27
> **Rob.I said:**
> I do have a "bcmwl5.inf" on my thumb drive...and the "bcmwl5.sys" file...but I don't know what to do with them...I don't know the command in Terminal.

install that gui, then just point it at the bcmwl5.inf. you'll need to be connected to the internet then run this command in the terminal:

```
sudo apt-get install ndisgtk
```

that will give you a pretty gui, you don't have to run anything else in the terminal.
it should appear in the menu under applications> system
i think, it will be obvious and say something like install windows drivers in the little info pop up.

---

### Post by Ayuthia on 2009-06-27
Before you go to that step, can you try and install b43-fwcutter first:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

Or you can go into Synaptic and install b43-fwcutter also.

---

### Post by Rob.I on 2009-06-27
PRoblem is I don't have internet because I can't get my wired to work either.

---

### Post by Ayuthia on 2009-06-27
Can you try the following to see if it will get your wired card working:
```
sudo modprobe -r b43 b44 ssb
sudo modprobe b44
```After a few seconds, your wired card should be detected my NetworkManager.  If it does not, please try the following:
```
sudo ifconfig eth0 up 
sudo dhclient eth0
```

If that does not work, here is a guide on how to download the files you need to make it work:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by Rob.I on 2009-06-27
Ok I did everything, download the firmware and did the terminal thingies...restarted the comp, switched my Wifi thing to ON and I'm starting now. 

..
After the start, my wifi light on my comp still isn't on and the icon doesn't show any networks available.

---

### Post by Ayuthia on 2009-06-27
This is going to sound a little odd, but you should be able to continue from this issue.  The problem is that you must have said yes when it asked you if you wanted it to download the firmware.  If you say yes, it will try and fail.  However, b43-fwcutter is there so you should be able to do the rest of the steps.  Once those steps are complete and you have wireless, we can come back and fix this by reinstalling b43-fwcutter (since we have a working connection, it will reinstall the firmware again and be fixed).

You should be able to confirm that b43-fwcutter is there by doing the following in the Terminal:
```
which b43-fwcutter
```
It should return the location of the file.  If it does not, then we will figure out what to do next.

---

### Post by Rob.I on 2009-06-27
Yes, it says /usr/bin/b43-fwcutter.

Woohoo, we're getting somewhere!
Now, where should I start off again?

---

### Post by Ayuthia on 2009-06-27
You should go to the Downloading Firmware section and download the two files.

---

### Post by Rob.I on 2009-06-27
Ok, I have downloaded them, have done the necessary edits in the Terminal as well. Next, should I restart, or do I need to activate the driver firsT?

---

### Post by Ayuthia on 2009-06-27
> **Rob.I said:**
> Ok, I have downloaded them, have done the necessary edits in the Terminal as well. Next, should I restart, or do I need to activate the driver firsT?

You can either restart or do the following:
```
sudo modprobe -r b43 b44 ssb
sudo modprobe b43
sudo modprobe b44
sudo iwlist scan
```If it shows wireless sites, you should be ready to go!

---

### Post by Rob.I on 2009-06-27
I did it, and nada. Out of curiosity, I went into the Hardware Drivers section, and the B43 wireless driver is in there but not enabled. I tried to enable it and it said "Downloading and installing 50%" then stopped...no errors or anything...

---

### Post by kerry_s on 2009-06-27
Thankyou  Ayuthia! for helping him.

---

### Post by Rob.I on 2009-06-27
> **kerry_s said:**
> thankyou  Ayuthia! for helping him.
IT's not fixed yet, but we're getting somewhere for sure...
But yes, thanks very much for your time!

---

### Post by Ayuthia on 2009-06-27
It sounds like we are missing something.  Did you run these commands:
```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy

```

If so, can you check and see if there are files in /lib/firmare/b43?  If there are files there, please check:
```
dmesg|grep b43
```

---

### Post by Ayuthia on 2009-06-27
> **kerry_s said:**
> Thankyou  Ayuthia! for helping him.

Don't thank me until it is working!!!  :D

---

### Post by Rob.I on 2009-06-27
I've done the commands again and checked the /lib/firmware/b43 folder, and there is NO /b43 folder in /firmware or b43 file inside /firmware.

---

### Post by kerry_s on 2009-06-27
> **Ayuthia said:**
> Don't thank me until it is working!!!  :D

do you that wireless too?

---

### Post by Ayuthia on 2009-06-27
> **Rob.I said:**
> I've done the commands again and checked the /lib/firmware/b43 folder, and there is NO /b43 folder in /firmware or b43 file inside /firmware.
What does the system say when you do this command:
```
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
```This is the command that extracts the necessary information and places them into the /lib/firmware folder.  It seems that this is where we are having the problem.

---

### Post by Ayuthia on 2009-06-27
> **kerry_s said:**
> do you that wireless too?

I usually help support the Broadcom cards.  I have a 4306 rev 03, 4311, and 4328 card here.  I have worked on a 4318 rev 02 card before, but I have never really had any problems with them but I don't install them in the way that is typically done in Ubuntu.

So far, there seems to be problems with the 4318 and 4303 cards and I am trying to pinpoint the issue.  They are mainly with getting the card to turn on.

---

### Post by Rob.I on 2009-06-27
When I input it and press Enter, it asks me for my password, in which I press enter again. Then it just gives me the next line so input more things.

---

### Post by Ayuthia on 2009-06-27
> **Rob.I said:**
> When I input it and press Enter, it asks me for my password, in which I press enter again. Then it just gives me the next line so input more things.
And there is nothing in /lib/firmware/b43?  Usually when it gives you the next line, it means that it did not run into any problems with creating the /lib/firmware/b43 directory and extracting the files there.

---

### Post by Ayuthia on 2009-06-27
By any chance, did you try:
```
sudo modprobe -r b43 b44 ssb
sudo modprobe b44
sudo ifconfig eth0 up 
sudo dhclient eth0
```
This is a test to see if you are able to get the wired card to run without needing to activate the b43 module.

---

### Post by Rob.I on 2009-06-27
No, there is nothing in /lib/firmware/b43 ..like I said...there IS no /b43 :(

---

### Post by Ayuthia on 2009-06-27
I guess it is not playing nice with us.  I have attached a file that contains the b43 folder.  I am assuming that you are using a kernel version 2.6.25 or higher (Intrepid or Jaunty).  If that is the case, you can then do the following:
```
tar xvjf b43.tar.bz2
sudo cp -a b43 /lib/firmware
sudo modprobe -r b43 b44 ssb
sudo modprobe b43
sudo modprobe b44
sudo iwlist scan
```

Let me know if you run into problems.

---

### Post by Rob.I on 2009-06-27
Wow, that finally did it! I'm posting now from teh Ubuntu machine! Ayuthia, thank you very very much for your time!

---

### Post by Ayuthia on 2009-06-27
> **Rob.I said:**
> Wow, that finally did it! I'm posting now from teh Ubuntu machine! Ayuthia, thank you very very much for your time!

Glad to see it working!  Thanks for hanging in there!

---

### Post by Rob.I on 2009-06-27
> **Ayuthia said:**
> Glad to see it working!  Thanks for hanging in there!
Yeah I'm glad I hunng around as well...its working good for what I need. What a hassle to get it setup though! :P
Anyways, thanks a bunch for your time and effort!

---

### Post by kerry_s on 2009-06-27
i knew you guys would do it, congrats to both of you you. :P

---

