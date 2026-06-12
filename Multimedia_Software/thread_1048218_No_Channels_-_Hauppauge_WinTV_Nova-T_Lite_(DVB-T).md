---
title: "No Channels - Hauppauge WinTV Nova-T Lite (DVB-T)"
date: 2009-01-23
forum: Multimedia Software
---

### Post by TransplantedCanuck on 2009-01-23
I had this tuner reccomended to me by another person living in germany:   [http://ubuntuforums.org/showthread.php?t=1036787](http://ubuntuforums.org/showthread.php?t=1036787)


So... I purchased said Tuner, and the installation was really just as easy as stated...

I've gotten the "check that its working" confirmation of:

```
[   35.028736] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   35.028774] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   35.438352] dvb-usb: schedule remote query interval to 150 msecs.
[   35.438355] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[   35.438611] usbcore: registered new interface driver dvb_usb_dib0700
```


So now the problem is, I don't find any channels. I've tried using  Me-TV, I've tried using Kaffeine (both the auto setting and de Berlin) and I tried using the command line program w_scan and none of them were able to detect any channels.

In Kaffeine the signal seems to bounce between 80% and 0% at times, and other times stays stay at 67-80%.

Is our cable connection crap (that would be a depressing end) or is there something misconfigured or not quite right?

I've tried several different firmware versions... 1.10, 1.20 and 3-pre1.


Does anyone have any further advice or debugging I could post to help here?

---

### Post by TransplantedCanuck on 2009-01-24
bump...

anyone?

---

### Post by WatchingThePain on 2009-01-24
I used that card and installing it was fine, most of the drivers worked fine but the problem was reception. I had to buy a device called an attenuator or something which is basically a device that connects to the antenna that reduces interference from certain bandwiths. I also used a signal booster and then it picked up all the freeview channels.

---

### Post by TransplantedCanuck on 2009-01-24
still, you wouldn't think that would be needed with a normal cable connection. I'm going ot try and set it up on a windows machine and see what happens then.

---

### Post by WatchingThePain on 2009-01-24
I also use that device with my cable tv. Windows xp had the same problem for me.

---

### Post by akash2008 on 2009-01-24
I don't find any channels. I've tried using Me-TV, I've tried using Kaffeine (both the auto setting and de Berlin) and I tried using the command line program w_scan and none of them were able to detect any channels.

In Kaffeine the signal seems to bounce between 80% and 0% at times, and other times stays stay at 67-80%.

Is our cable connection crap (that would be a depressing end) or is there something misconfigured or not quite right?

---

### Post by TransplantedCanuck on 2009-01-24
yep, same thing in XP. Figures. 

So much for the HTPC concept.

---

### Post by TransplantedCanuck on 2009-01-26
so the reason I'm having troubles is because the cable signal is too weak? I'm not quite sure how that can be the case... its not like I'm living in a small town.

Or is the problem that this adapter needs such a strong signal.


still, I'd think hamburg would have just as strong a signal as berlin.

---

### Post by little_penguin on 2009-02-07
As far as I know, the WinTV Nova-T Lite DVB-T stick is only for digital TV and not for cable TV, which at least in Germany, is still analog in a lot of cases. To get analog cable reception you will need another type of stick than this one. I have analog cable TV myself, which I receive on my PC via a 2nd tv tuner, the Hauppauge WinTV PVR-150 pci card. 

There may be some hybrid USB sticks around that can receive both analog and digital TV, but 

a) they are a quite a bit more expensive, and 
b) it's difficult to find a hybrid one that is supported under linux.

Regards,
Little_Penguin

---

