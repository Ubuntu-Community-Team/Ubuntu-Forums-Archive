---
title: "Hauppage 1600 &amp; Quickcam Pro 5000..."
date: 2008-05-06
forum: Multimedia Software
---

### Post by calimansi on 2008-05-06
New Ubuntu 8.04 user here.

I've read a lot already about getting the 2 to work together.  I have the hauppauge 1600 to work via the cx18 module.  I've been trying to get the quickcam pro 5000 (pre 2006) to work.  After modprobing the uvcvideo module, I get a "Unknown symbol in module" error.  I can't seem to find anymore info on this cryptic message.  I think there's a comflict with the tv card and the webcam wanting to access /dev/video0.

Any of you linux pros have a solution?

Thank you.

---

### Post by calimansi on 2008-05-06
bump... any hints?

---

### Post by xc3RnbFO8P on 2008-05-06
This card is not supported by linux, but you can try this:
[http://marc.info/?l=linux-video&m=119834005505084&w=2]("http://marc.info/?l=linux-video&m=119834005505084&w=2")

---

### Post by calimansi on 2008-05-06
Sorry.  I did get the tv card to work via the cx18 module.  Now all that remains is the uvcvideo driver.

---

### Post by usererror on 2008-05-19
I have not yet gotten my Hauppage 1600 card to work in 7.10 ubuntu, could you post any details to how you got the card to work?  or any sites you referenced?

I tried downloading the beta drivers, but they are no longer on the Hauppage site. (bad links)

---

### Post by willoconley on 2008-05-24
[QUOTE="usererror"]I have not yet gotten my Hauppage 1600 card to work in 7.10 ubuntu, could you post any details to how you got the card to work? or any sites you referenced?[/QUOTE]

```
$ sudo apt-get install mercurial
```

```
$ hg clone http://linuxtv.org/hg/v4l-dvb
```

```
$ cd v4l-dvb
```

```
$ sudo make
```

```
$ sudo make install
```

The above was from [here]("http://www.linuxtv.org/repo/")

```
$ sudo modprobe cx18
```

```
$ sudo reboot
```

```
$ sudo apt-get install mplayer
```

To view tv, assuming the card is device video0:
```
$ mplayer -cache 16384 /dev/video0
```

After I close mplayer, the next time I try to use it it says the device can't be accessed, so:
```
$ ps | grep dbus-launch
6581 pts/1    00:00:00 dbus-launch
```

so i do:
```
$ kill 6581
```
and now mplayer can access the device again

to change channels the only way I know is:
```
$ mplayer tv:// -tv \freq=289.625
```
where freq=theFreqOfChannelToView which I am getting [here]("http://www.jneuhaus.com/fccindex/cablech.html") for cable.

If anyone has a better way or can help setting up an mplayer list please do tell.

---

### Post by usererror on 2008-05-26
Thanks for the post!

All goes well except for at the very end at the modprobe command I get an error:

```
FATAL: Error inserting cx18 (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/cx18/cx18.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

I check /var/log/dmesg but find no line referring to the cx18 module.

Any ideas?  I'm not an expert in this area, unfortunately.

**UPDATE**

There was apparently a new kernel to be downloaded via apt, so I installed that and re-tried the compile and mod probe, this time no error at the modprobe step.

I then setup a recording with in my mythtv schedules (that is what the card's function is).  It records video great, but I'm not getting audio on it for some reason.  Not sure why that is.  I'll fudge around with it tomorrow, but if you have any ideas let me know.

Originally I was following steps here: [http://www.ivtvdriver.org/index.php/Cx18](http://www.ivtvdriver.org/index.php/Cx18)

but the make menuconfig step would not complete correctly, apparently due to linux-headers I was missing, and I tried installing them, but perhaps they were the wrong ones.

I may try upgrading the unit to 8.04, perhaps that will help.

---

### Post by willoconley on 2008-05-27
Hey, well I set up myth this morning and the volume is ok for me. Originally I didn't have any either but I didn't have the signal standard set correctly. Otherwise the only thing I did out of the ordinary was:
```
$ alsamixer -V all
```

and put all the settings on 100. Then I turned up all the volume settings in the mythtv configurations.

BTW I have no idea if it makes a difference, but I am on the 8.04.

---

### Post by usererror on 2008-05-27
> **willoconley said:**
> Hey, well I set up myth this morning and the volume is ok for me. Originally I didn't have any either but I didn't have the signal standard set correctly. Otherwise the only thing I did out of the ordinary was:
```
$ alsamixer -V all
```

and put all the settings on 100. Then I turned up all the volume settings in the mythtv configurations.

BTW I have no idea if it makes a difference, but I am on the 8.04.

You know, I bet that is my issue! I just remembered that on my OLD tuner I was replacing with the 1600 I had to mute one of the volume mixers because the audio was lagging behind the video.  I'll give that a try and post the results.

---

### Post by usererror on 2008-05-27
Well, the lines that I had muted before were longer muted, which was odd, but I still don't get sound on the 1600, with nothing muted.

I don't know if maybe there's a limitation on my onboard soundcard perhaps?

I will try upgrading to 8.04 tomorrow, but I could not tonight due to some recordings that were scheduled.

---

### Post by willoconley on 2008-05-30
take a look at this thread [here]("http://www.gossamer-threads.com/lists/ivtv/devel/38314"). close to the bottom the post by jahagan at comcast

> MythTV sets the sampling frequency to 32kHz and the bit rate to something higher than the default. One or both of these will stop the audio.

Through the MythTV front end you need to adjust your liveTV and recording profiles. I set them all to 48kHz and a bitrate that translates to 10 (I think it was around 224kb/s). 

I don't remember doing that manually but that is what mine are set at.

---

