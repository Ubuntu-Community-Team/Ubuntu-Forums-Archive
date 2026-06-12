---
title: "WinTV-HVR-950Q ATSC Mythbuntu 9.10 - Mythtv 0.22"
date: 2009-11-21
forum: Mythbuntu
---

### Post by amlino on 2009-11-21
Anyone able to use the HVR-950Q ATSC with mythbuntu 9.10 and Mythtv 0.22?

The card is sucessfully installed and setup in Mythtv-setup. But when scanning for channels, it does not find anything. Any ideas?

The cars type is setup as : DVB DTV capture card (v3.x)
frontend ID: Auvitek AU8522 QAM/ Subtype: ATSC
DVB adpater: /dev/dvb/adapter0/frontend0


```

[190188.252138] tveeprom 5-0050: Hauppauge model 72001, rev B3F0, serial# 3443487
[190188.252144] tveeprom 5-0050: MAC address is 00-0D-FE-34-8B-1F
[190188.252148] tveeprom 5-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[190188.252153] tveeprom 5-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[190188.252157] tveeprom 5-0050: audio processor is AU8522 (idx 44)
[190188.252161] tveeprom 5-0050: decoder processor is AU8522 (idx 42)
[190188.252165] tveeprom 5-0050: has no radio, has IR receiver, has no IR transmitter
[190188.252168] hauppauge_eeprom: hauppauge eeprom: model=72001
[190188.281430] au8522 5-0047: creating new instance
[190188.281434] au8522_decoder creating new instance...
[190188.801076] tuner 5-0061: chip found @ 0xc2 (au0828)
[190188.919956] xc5000 5-0061: creating new instance
[190188.925868] xc5000: Successfully identified at address 0x61
[190188.925872] xc5000: Firmware has not been loaded previously
[190188.926258] au8522 5-0047: attaching existing instance
[190188.933734] xc5000 5-0061: attaching existing instance
[190188.938618] xc5000: Successfully identified at address 0x61
[190188.938621] xc5000: Firmware has not been loaded previously
[190188.938626] DVB: registering new adapter (au0828)
[190188.938631] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[190188.939224] Registered device AU0828 [Hauppauge HVR950Q]
[190188.939304] usbcore: registered new interface driver au0828
[190190.242874] usbcore: registered new interface driver snd-usb-audio
[190375.590968] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[190375.590976] usb 1-1: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[190375.713748] xc5000: firmware read 12401 bytes.
[190375.713753] xc5000: firmware uploading...
[190382.380017] xc5000: firmware upload complete...
[190416.468922] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[190416.468930] usb 1-1: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[190416.474052] xc5000: firmware read 12401 bytes.
[190416.474058] xc5000: firmware uploading...
[190423.140017] xc5000: firmware upload complete...
[190938.600127] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[190938.600136] usb 1-1: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[190938.605214] xc5000: firmware read 12401 bytes.
[190938.605219] xc5000: firmware uploading...
[190945.272018] xc5000: firmware upload complete...

```

Thanks.

---

### Post by amlino on 2009-11-21
Got it working.

---

### Post by iondiode on 2009-11-21
how? isn't working for me what kernel are you running?

i'm getting 

```

[ 2610.667515] tveeprom 0-0050: Hauppauge model 72001, rev B3F0, serial# 6929662
[ 2610.667529] tveeprom 0-0050: MAC address is 00-0D-FE-69-BC-FE
[ 2610.667540] tveeprom 0-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[ 2610.667551] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[ 2610.667560] tveeprom 0-0050: audio processor is AU8522 (idx 44)
[ 2610.667569] tveeprom 0-0050: decoder processor is AU8522 (idx 42)
[ 2610.667579] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[ 2610.667587] hauppauge_eeprom: hauppauge eeprom: model=72001
[ 2610.678754] au8522 0-0047: creating new instance
[ 2610.678764] au8522_decoder creating new instance...
[ 2610.709237] tuner 0-0061: chip found @ 0xc2 (au0828)
[ 2610.709577] xc5000 0-0061: creating new instance
[ 2610.731759] xc5000: Device not found at addr 0x61 (0xffff)
[ 2610.731775] xc5000 0-0061: destroying instance
[ 2610.732827] au8522 0-0047: attaching existing instance
[ 2610.760082] xc5000 0-0061: creating new instance
[ 2610.815517] xc5000: Device not found at addr 0x61 (0xffff)
[ 2610.815533] xc5000 0-0061: destroying instance
[ 2610.815863] DVB: registering new adapter (au0828)
```


i'm running in karmic
 2.6.31-14-generic #48-Ubuntu SMP

---

### Post by amlino on 2009-12-09
[QUOTE=xistenznet]Can you post on the thread you created WinTV-HVR-950Q ATSC Mythbuntu 9.10 - Mythtv 0.22 how you were able to get the 950q up and running?  I think I am having he same issue.

Thanks.[/QUOTE]

Sure. In a nutshell, I got it working fine by avoiding the firmware reloading. If you check dmesg, you will see it reloads the firmware a lot.
I also increase the timeouts for the 950q in the mythvuntu setup. I do not have the screen in front of me now, but go to the page where you add the capture card. You will 2 settings. I changed both to 6000 (6 secs).

Also, under /etc/modprobe.d

create a file named 
sudo vi xc5000.conf

and add this line

options xc5000 no_poweroff=1  #avoid reload

You can now reboot or unload the xc5000 driver:
sudo modprobe -r xc5000
load:
sudo modprobe xc5000


Now ensure the antenna is connected to the card and scan. It should work.
```

[   42.230319] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[   42.230328] usb 1-3: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[   42.380891] xc5000: firmware read 12401 bytes.
[   42.380897] xc5000: firmware uploading...
[   44.782362] CPU0 attaching NULL sched-domain.
[   44.782372] CPU1 attaching NULL sched-domain.
[   44.796192] CPU0 attaching sched-domain:
[   44.796199]  domain 0: span 0-1 level SIBLING
[   44.796203]   groups: 0 1
[   44.796209]   domain 1: span 0-1 level MC
[   44.796213]    groups: 0-1 (__cpu_power = 2048)
[   44.796221] CPU1 attaching sched-domain:
[   44.796224]  domain 0: span 0-1 level SIBLING
[   44.796227]   groups: 1 0
[   44.796232]   domain 1: span 0-1 level MC
[   44.796235]    groups: 0-1 (__cpu_power = 2048)
[   50.212542] xc5000: firmware upload complete...

```


Hope this helps.
Marcello


I am using kernel Linux mythtv 2.6.31-14-generic

---

### Post by uomiarz on 2009-12-30
thx, this card was driving me nuts, working 50% of the time with constant reboots
now it is perfect!

---

### Post by iondiode on 2010-01-13
Are you able to use the LiveTV option? 

I've successfully scanned for channels but when i try to use livetv it doesn't work

---

### Post by markackerman8@gmail.com on 2011-10-12
I have just reinstalled Ubuntu 11.04 and the hvr-950q with mythtv and tvtime.  I have put my notes that may be of some help on a new (my first attempt) website.  

[www.ubuntubut.com](www.ubuntubut.com)

Visit it YeaH !!!

Mark



"Brendan.

Sorry it took do long to get back to you (1 week).  Yes I just got the hvr-950q working again yesterday after trying the new Ubuntu 11.10 beta and going back to 11.04 after too much aggravation.  Your request prompted me to start a website (my first attempt ever !) [www.ubuntubut.com](www.ubuntubut.com)  Do me the favor of visiting it where I put my notes of how to install the hvr-950q using MythTV, and a lot more.  I have google tracking and I would love to see  more visitors.

I got it working YEAH!

Feel free to advise me of how to make it better or how it worked well for you.  I hope it helps.

[www.ubuntubut.com](www.ubuntubut.com)

Mark Ackerman
www.ubuntubut.com"

---

