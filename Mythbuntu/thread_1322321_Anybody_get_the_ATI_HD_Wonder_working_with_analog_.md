---
title: "Anybody get the ATI HD Wonder working with analog TV?"
date: 2009-11-10
forum: Mythbuntu
---

### Post by AKADAP on 2009-11-10
Has anyone gotten the ATI HD Wonder working with analog TV?
I have it working fine with QAM, but my cable system also has a bunch of analog channels, so I thought I'd set up the analog stuff.

I tried to follow the setup on the MythTV wiki, but that is out of date, and the analog seems to be setting up the composit input rather than the TV stuff. I tried it anyway, but all I get is fixed garbage screens for every channel. I got the channels enabled by using the automatic channel download from Schedules direct, but the channel scan does nothing (does not even try).

Also, is there any way to specify which input the ATI HDWonder uses? it has two, but I've seen no way to specify which one to use so far.

---

### Post by AKADAP on 2009-11-11
Interesting development. After a cold power cycle (I shut my computer off for the night) I now get video, but not audio for the analog channels. Changing channels has a 90% probability of giving me a 1/3 sized picture shoved in the upper left corner of the screen with the twitching remains of the previous channel at the bottom of the screen, and fixed garbage on the right. Exiting live TV and re-entering gets a full sized picture back.

So, how is the audio supposed to be hooked up? do I need some connection between the HD Wonder and the audio inputs on the mother board?

---

### Post by blackoper on 2009-11-11
I have the card but I only use it for qam. I see the analog part of the card show up when i choose my pvr-150 card. I'll give it a try and see if it works as a test for you

---

### Post by AKADAP on 2009-11-12
Power cycled the computer again, and now I am back to a fixed pattern of garbage on all analog channels.
QAM on ATSC are never affected by these problems.

---

### Post by blackoper on 2009-11-12
check in mythtv backend to make sure the /dev numbers are not changing on your capture cards.

---

### Post by AKADAP on 2009-11-13
> **blackoper said:**
> check in mythtv backend to make sure the /dev numbers are not changing on your capture cards.

Where would I look and why would they be changing?

---

### Post by blackoper on 2009-11-13
> **AKADAP said:**
> Where would I look and why would they be changing?

you can just look by opening your existing tuner in mythbacken-setup. See if it's the correct /dev/xxxx device

---

### Post by AKADAP on 2009-11-15
> **blackoper said:**
> you can just look by opening your existing tuner in mythbacken-setup. See if it's the correct /dev/xxxx device

Video device: /dev/video0
VBI device /dev/vbi0
Audio device /dev/dsp

There are no other options in the list box for video device.
I just changed the audio device to "ALSA:default" since "/dev/dsp" certainly isn't working.

So far, the working video has never repeated, even though I have not changed any video settings.

I know that I do not need any type of analog audio cable as there is no place to connect one on the the ATI HD Wonder.

---

### Post by AKADAP on 2009-11-17
I have noticed a discrepancy. The front end thinks my analog tuner is tuner number 10, but there is no tuner number 10. The backend thinks the analog tuner is tuner number 6. Could this cause analog TV to not work? How would I go about fixing this?

---

### Post by blackoper on 2009-11-17
try deleting all your tuners in the mythtv setup program and readding it

---

### Post by AKADAP on 2009-11-18
> **blackoper said:**
> try deleting all your tuners in the mythtv setup program and readding it

That would be very painful. It usually takes several days to straighten out the mess every time Comcast shuffles channels, starting from scratch would take even longer. I have 5 tuners in my system with several hundered channels (467 actually with most duplicated at least twice, some duplicated as many as 4 times). I do NOT want to start from scratch.

---

### Post by blackoper on 2009-11-18
just the tuners, not your channel lineups. It should take under 5 min to add the tuners back in and assign input sources to them.

---

### Post by novellahub on 2009-11-18
blackoper is correct.  You can delete your tuners without affecting the channel line-ups.  Delete all of them and re-add.  Then re-add the input connections.

---

### Post by AKADAP on 2009-11-19
Good news & bad news.
I tried deleting all tuners & recreating them.

The good news is that this eliminated the discrepancy of tuner numbers. Mythweb and the front end both agree that the analog tuner is tuner number 2.

The bad news is that I still get no picture or sound.

---

### Post by blackoper on 2009-11-19
ok I'm off work for the next two days, I'll try to get the analog part of my ati hd wonder working and see what happens. Perhaps like the hd qam tuner it requires a driver or something to be functional. I do know i have seen it listed when selecting my pvr-150.

---

### Post by AKADAP on 2009-11-20
The analog part is set up as a separate tuner card. This makes me wonder how MythTV knows that only the analog or the digital portion of the card can be used, never both at the same time. Maybe it doesn't know, and that is why it does not work. Tuner 1 is the digital portion of the card and is the one that watch live TV always starts on.

I have seen analog video once from the card, but since I did not change anything before or after it worked, I have no idea why it worked that one time.

---

### Post by AKADAP on 2010-01-09
Bump.
I have made no progress on this.

---

### Post by AKADAP on 2010-05-01
I made a bit of progress on this...

Per a suggestion on the mythtv-user mailing list:
I ran mythbackendsetup to stop the mythTV backend from running.
As super user, I ran the following script:
```
#!/bin/sh
#
# unload hdtv wonder modules
#
/sbin/modprobe -r cx8800
/sbin/modprobe -r cx88_dvb
/sbin/modprobe -r nxt200x
/usr/bin/pkill pulseaudio; /sbin/modprobe -r cx88_alsa
/sbin/modprobe -r tuner
/sbin/modprobe -r tuner_simple
/sbin/modprobe -r tuner_types
/sbin/modprobe -r tda9887
/sbin/modprobe -r tda8290
#
# reload hdtv wonder modules
#
/sbin/modprobe cx88_dvb
/sbin/modprobe cx8800 video_nr=1 vbi_nr=1
/sbin/modprobe cx88_alsa index=1

```
Then I ran:
```

mplayer tv://32 -tv device=/dev/video1:driver=v4l2:chanlist=us-cable:alsa:adevice=hw.1,0:amode=1:audiorate=48000:forceaudio:volume=100:immediatemode=0:norm=NTSC
```

up pops a window showing video with sound!
Unfortunately, when I exited mythbackendsetup, and tried to view live TV, the analog tuner was missing.
Worse, I have since updated to Ubuntu 10.04, and now mythfrontend segmentation faults when I try to run liveTV

---

### Post by AKADAP on 2010-05-02
I figured out that the liveTV crash was caused by openGL being broken in 10.04. I changed the renderer to use something other than openGL, and was able to get liveTV to work.

I also figured out that the script was changing the device from /dev/video0 to /dev/video1.
This is why mythTV could not find it, it was looking for video0
Changing it to video1 allowed the channel scan to work for the first time.
LiveTV is still broken, but now it shows a second of video every time I start it, or change channels, but then the picture freezes, then switches to black or flickering garbage.

I haven't been able to find documentation on the modules the script messes with yet, so I don't know what switches are available, or what the ones used in the script do.

---

