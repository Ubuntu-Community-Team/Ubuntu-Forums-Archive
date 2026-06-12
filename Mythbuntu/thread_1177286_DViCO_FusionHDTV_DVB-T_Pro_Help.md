---
title: "DViCO FusionHDTV DVB-T Pro Help"
date: 2009-06-03
forum: Mythbuntu
---

### Post by DrWarm on 2009-06-03
Just realised I accidentally bought an unsupported (out-of-the-box) TV tuner card for my new HTPC (I meant to get the Dual Digital 4) and have been having some amount of grief, especially as I can't return it! 

After finding this website:
[http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/]("http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/")

I tried installing his custom driver with in Mythbuntu 9.04 (64bit) which would not let me complete the installation, possibly as I already tried installing with the guide on here (which installed fine): [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers")

I was still not able to tune however, but then I found this  [HERE]("http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers") :

> If you are using a Dvico FusionHDTV DVB-T Pro with Ubuntu 9.04 and you can not get a video lock with MythTV (no video) you may see this message when running dmesg:

xc2028 0-0061: Error: firmware xc3028-v27.fw not found

If this is the case you are missing the firmware needed for this card. Please refer to the following link: How to Obtain the Firmware 

Which I found was missing, and I followed the link, and i got the firmware ok. 

Now I can watch tv via the terminal using something like (taken from [HERE]("http://ubuntuforums.org/showthread.php?t=616103")):
```
scan /usr/share/dvb/dvb-t/au-Adelaide > channels.conf

sudo cp channels.conf /etc && cp channels.conf ~/.tzap

tzap -c /etc/channels.conf -r "Ten ONE"

leave open and from a new terminal window as a normal user type

mplayer /dev/dvb/adapter0/dvr0
```

But now I'm not sure how to get this new stuff back into MythTV!!?!?

When I try adding a device (either the analogue or digital) it has a few options which show DViCO FusionHDTV DVB-T Pro, which i then select. But as input it only allows Composite or S-Video, when I want Antenna. 

Then later in MythTV when I'm trying to find sources it says it can't open the card!!!


Any tips? I've almost followed every link I could find for the DVB-T Pro and Linux, and still haven't go to the bottom of it.


Thanks for your help,
Dr Warm

PS I think I'm going to have some more fun with the remote!

---

### Post by DrWarm on 2009-06-05
I realise its only been a couple of days, but should I be posting this on the MythTV forums instead? 

Or is more information required?

Sorry about the double post.

---

### Post by DrWarm on 2009-06-18
Made some headway, now have managed to get video tuned, when selecting this tuner in MythTV:

> Zarlink ZL10353 DVB-T

It was able to tune all the channels fine. Sweet as!!!!

I had a little go with the remote, tried:
```
dmesg | grep IR
```

But nothing showed, so then I was just looking through all of dmesg in hope and saw this:
> [    8.885353] xc2028 1-0061: Error on line 1124: -6
Is that anything to worry about?

Couldn't see anything else that looked to me like a remote, so might just have to stick with the wireless keyboard/mouse. Oh well.

---

