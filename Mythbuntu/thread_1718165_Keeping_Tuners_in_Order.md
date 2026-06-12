---
title: "Keeping Tuners in Order"
date: 2011-03-30
forum: Mythbuntu
---

### Post by zuixro on 2011-03-30
I have two tuner cards in my Mythbox. One is a Hauppauge PVR-500, the other is a Hauppauge HVR-1600, so a total of 3 analog tuners, 1 digital tuner.

The problem I am having is that every time I reboot, it changes the order of the analog tuners in the /dev directory. Example: Last time, the 1600 was /dev/video0 and the 500 was /dev/video1 and video2. This time the 1600 is /dev/video1 and the 500 was /dev/video0 and video2.

How can I force the cards to always stay the same? 

This wouldn't be a big deal, except that the 1600 is much higher quality than the 500's (probably a cabling problem that I hope to clear up soon).

For now I've just been manually rearranging them in the backend setup after every reboot, which is a huge pain, and has been slowly creeping my tuner numbers up each time (right now my tuners are starting at 13, is there a way to reset that number?)

---

### Post by azmyth on 2011-03-30
You can write a udev rule to create a symbolic link to the tuner so no matter what the video(number) is it'll always point to say for example /dev/pvr150. I think someone wrote a script on here to do this automatically but I'm not sure which thread it was. I believe you have to do a delete all tuners to reset the numbers. Under M (Menu) button on your remote, you should see the option.

---

### Post by zuixro on 2011-03-31
Ah, Should have done some more searching before I posted.  I don't know if this is what you were talking about, but I think it worked:

[http://www.mythtv.org/wiki/Device_Filenames_and_udev](http://www.mythtv.org/wiki/Device_Filenames_and_udev)

Thanks so much! I've been putting off rebooting so I wouldn't have to rearrange everything.

---

### Post by klc5555 on 2011-03-31
Just for reference, you can also use modprobe configuration options to load the 1600 in a particular order with reference to the 500 tuners.

For example: options ivtv ivtv_first_minor=1

would force Hauppauge x50 tuners to populate video1 and following.

Or: options cx18 cx18_first_minor=2 would force the cx18 to load at video2

The modinfo command can give you the list of recognized params for a particular module.

Modprobe options was the method I used on an older machine where two 1600s were playing dueling tuners at every boot with the unused analog half of a pchdtv-hd5500 and the also unused framebuffer half of an Avermedia A180. I optioned the the cx18 to first_minor=2 and everything was set.

Also, its not your imagination or (necessarily) cabling: the recording quality of the older Hauppauge PVR-x50-type tuners is simply lower than that of the analog side of the 1600, no matter how you tweak them. For this reason I finally retired the last of my pvr-150s a year ago.

---

### Post by zuixro on 2011-04-01
I had most channels (that I watch anyway) coming in pretty clear on the 500's a while back, but with the new tuner, I changed my cabling (and kinda broke the connector a while back...)

But yeah, I'm hoping to retire that card and get another 1600, hopefully one with QAM this time.

---

### Post by klc5555 on 2011-04-01
> **zuixro said:**
> I had most channels (that I watch anyway) coming in pretty clear on the 500's a while back, but with the new tuner, I changed my cabling (and kinda broke the connector a while back...)

But yeah, I'm hoping to retire that card and get another 1600, hopefully one with QAM this time.

Check to see whether your current 1600 actually does do QAM. 

I got a 74551 (Model 1101) a year ago to do analog only, as a replacement for a PVR-150. I got the 1600 used for next to nothing because, as the wiki document points out, ( [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600)) the 74551 model doesn't support QAM "under Windows". Imagine my surprise about 5 months later when on a lark I compiled a reasonably recent set of v4l-dvb drivers, hooked up the digital input and discovered that the thing could handle the QAM digital lineup the same as my other 1600s do. The Windows issue with this model (and perhaps the other one?) seems to be a Windows driver issue, which problem the cx18 driver may not share.

So give it a try.

---

