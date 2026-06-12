---
title: "ndisdrapper says that no hardware present"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by wolfmaniac on 2006-06-27
well i tried to configure my brodcom 4306 on dell inspiron 6000.
first i used bcmxx cutter.
then i used ndiswrapper.
the card is detected at eth1 and i can also ping the router.
i installed bcmwl5.sys 
but the ndisgtk displays the message that no hardware is present.
can someone help me.
here is my lspci
> wolfmaniac@zone:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
0000:03:01.2 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
0000:03:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by stupidkid on 2006-06-27
You're not suppose to load the .sys file but rather the .inf file. Then it should work fine.

---

### Post by rsfeller on 2007-07-25
I doubt that is the answer as it will not all you to even load a *.sys file to get to the "Hardware Present: no" message.

I don't have the solution as I have been struggling to for almost a week trying to get wifi to work on my laptop with a dozen differnt cards and onboard wifi. Aways the same...driver loads but Hardw Present: No...yet the network sees my Acess Point...but no signal.

so much fun...

---

### Post by kevdog on 2007-07-25
Try this:

Obviously the hardware is present.
```

gksu gedit /etc/modprobe.d/blacklist
```

Add the following line:
```
blacklist bcm43xx
```

Make sure there is no line in the file saying blacklist ndiswrapper.


Then provide the following:
lshw -C network
ndiswrapper -v
ndiswrapper -l

---

### Post by aldo_m on 2007-11-04
ok im doing the same thing and using the ndisgtk interface. when i install the new driver it keeps saying.
bcmwl5
hardware prsent:No
im tring to find a way to enable the hardware and change it to bcmwl5
under hardware info. say bcm4306 i need to install my windows drivers.

pleaseeeeeeeeee help me. "noob" here so be helpfull.
thanks!
oh yeah i also blacklisted the mod. but what happend is the interface under the card name is gone. it use to be there when i first installed it. being thats what i did with the blacklist. but now can we get the card to install new driver.

---

### Post by kevdog on 2007-11-04
Post the following

modinfo ndiswrapper
ndiswrapper -l

Then make sure the /etc/modules/ndiswrapper directory is completely empty.

---

### Post by aldo_m on 2007-11-04
yesssssssssssssssssssss i got it last night i download the l5a drivers and read somthing try that and it work it turn hardware from not prsent to prsent instently. i wish i remeber where i got it from it was on the fourm i know somone posted the direction if youo have ndisgtk install and working then all you need is the right driver.
i will go back threw everything i did and post it here for retards like myself.

---

### Post by kevdog on 2007-11-04
> yesssssssssssssssssssss i got it last night i download the l5a drivers and read somthing try that and it work it turn hardware from not prsent to prsent instently. i wish i remeber where i got it from it was on the fourm i know somone posted the direction if youo have ndisgtk install and working then all you need is the right driver.
i will go back threw everything i did and post it here for retards like myself.

Did you forget to take your pills for your bipolar mania today??

---

### Post by aldo_m on 2007-11-08
damn your right man i should of gone and :lolflag::lolflag:picked up a bunddle and did all at once.:lolflag:

---

