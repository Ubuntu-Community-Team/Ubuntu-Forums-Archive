---
title: "KWorld ATSC 115 and SD Content"
date: 2008-03-09
forum: Mythbuntu
---

### Post by JPurdy on 2008-03-09
I have a KWorld ATSC 115 that I have setup for Digital cable and I'm getting unencrypted QAM-256 stuff pretty nicely.  I thought I would add in the Analog cable content because there are a few channels that I don't get via the Digital Cable.

So in the mythtv-setup, I added a new tuner (V4L) on /dev/video0 and scanned for channels.  It picked up the usual suspects, so I thought I was doing great.
[B]
But when I tune to the channel to watch it, I get 1 or 2 seconds of the content and then the screen goes black.[/B]

From the frontend.log:
```

2008-03-09 00:50:34.433 Using protocol version 31
2008-03-09 00:50:34.633 Could not bind to UDP notify port: 6948
2008-03-09 00:50:34.774 Opening ALSA audio device 'default'.
2008-03-09 00:50:34.875 VideoOutputXv: XvMCTex: Init failed
2008-03-09 00:50:34.875 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0x198
2008-03-09 00:50:35.026 Realtime priority would require SUID as root.
2008-03-09 00:50:35.129 Video timing method: USleep with busy wait
2008-03-09 00:50:35.849 NVP: prebuffering pause
2008-03-09 00:50:36.372 RingBuf(/video/3023_20080309005034.nuv): Waited 1.0 seconds for data to become available...
2008-03-09 00:50:36.373 Checking to see if there's a new livetv program to switch to..
2008-03-09 00:50:38.101 RingBuf(/video/3023_20080309005034.nuv): Waited 1.0 seconds for data to become available...
2008-03-09 00:50:38.101 Checking to see if there's a new livetv program to switch to..
2008-03-09 00:50:38.125 NVP: prebuffering pause
2008-03-09 00:50:39.641 NVP: prebuffering pause
2008-03-09 00:50:39.697 RingBuf(/video/3023_20080309005034.nuv): Waited 1.0 seconds for data to become available...
2008-03-09 00:50:39.697 Checking to see if there's a new livetv program to switch to..
2008-03-09 00:50:41.133 RingBuf(/video/3023_20080309005034.nuv): Waited 1.0 seconds for data to become available...
2008-03-09 00:50:41.133 Checking to see if there's a new livetv program to switch to..
2008-03-09 00:50:41.141 NVP: prebuffering pause
```

From the backend.log:
```

2008-03-09 00:50:34.433 MainServer::HandleAnnounce Playback
2008-03-09 00:50:34.438 adding: purdymyth as a client (events: 0)
2008-03-09 00:50:34.440 TVRec(7): Changing from None to WatchingLiveTV
2008-03-09 00:50:34.449 TVRec(7): HW Tuner: 7->7
2008-03-09 00:50:34.570 Unknown video codec
2008-03-09 00:50:34.574 Please go into the TV Settings, Recording Profiles and
2008-03-09 00:50:34.575 setup the four 'Software Encoders' profiles.
2008-03-09 00:50:34.576 Assuming RTjpeg for now.
2008-03-09 00:50:34.576 NVR: Error, unknown audio codec
VIDIOCGCHAN: Invalid argument
```

I went into the TV Settings and changed the recording profiles and that didn't do it.  I also added the:

```
options dvb_core dvb_shutdown_timeout=0
```

to the /etc/modprobe.d/options file.

Thanks!

---

### Post by thecoolcat on 2008-03-10
This is a know issue with this card if in the myth database it is defined as two cards (one for DVB and the other as v4l).
See this post:
[http://ubuntuforums.org/showpost.php...5&postcount=42](http://ubuntuforums.org/showpost.php...5&postcount=42)
Basically what you want to do is tell myth that is is a single card with DVB as a parent card and v4l as a child card. To do this, you will have to manually edit the myth database using some frontend editor. I used phpmyadmin.
See this thread that discusses this extensively (pages 2, 3):
[http://ubuntuforums.org/showthread.php?t=643415](http://ubuntuforums.org/showthread.php?t=643415).

---

### Post by JPurdy on 2008-03-11
Perfect!  That helped a lot.  I had come across a similar thread before, but it was less helpful.  It helps to have someone point this out - gives me reassurance to be patient and try again.

So at this point, I was able to get the card to work and I'm able to tune it in, but I cannot hear anything.  In that same thread, there are some similar complaints.  I tried the *arecord* command trick in a separate console and then I'm able to hear the audio, but it doesn't stop when I exit the recording until I stop the command (Control-C).

I see in that thread, you fixed it by editing your audio settings in the General Setup.  I tried duplicating that, but it didn't work when I put it back on ALSA.

So I'm *almost* there -- I can taste it! ;)  Any help on the audio part?

---

### Post by thecoolcat on 2008-03-11
Great. Now are you getting any audio at all? 

For me, I had to use arecord only if I was using tvtime to watch analog channels. With mythtv, I was getting high pitched sound. 

I'm assuming you want it to work with mythtv. If there's any configuration in mythtv for audio sampling rate, can you make sure it is set to 32KHz?

In dmesg, can you make sure alsa module is loaded?
If you do "dmesg|grep -i saa" you'll see something like this:
```
saa7134 ALSA driver for DMA sound loaded
saa7133[0]/alsa: saa7133[0] at 0xf5006000 irq 19 registered as card 1
```

---

### Post by JPurdy on 2008-03-12
I had to "break apart" the V4L adapter again to reset the audio rate to 32000 and then put it back together.  Now I'm getting audio, but it's ... strange.  It's like the Chipmunks - the voices of the actors are higher than normal.

The ALSA module is being loaded.

The only place I see to set the audio rate is in the capture card settings in the mythtv-setup program.  Am I missing somewhere else?  The General audio settings, perhaps?

Thanks!

---

### Post by thecoolcat on 2008-03-12
Hmm. After I got this squeaky sound I just kept fiddling with the audio settings and it magically worked. I'm sorry I couldn't give you any expert (rational?) solution here. You need to bump this to an expert.
> At the main screen, go to Setup / Utilities -> Setup -> General -> the Audio page. Here, the sound device is the OUTPUT device and should be configured as the ALSA device. For me, this field is ALSA:default. I changed to /dev/dsp1 and there was no audio.. I changed it back to ALSA: default and it started working. Don't know how!

---

### Post by JPurdy on 2008-03-14
Now I've got a worse situation.  I upgraded to .21 and now the capturecard table no longer has a parentid field.  The docs say there's a new "Analog Options" button somewhere, but I don't see it.  My DVB capture card reports a different card (that I had in there at one point, but it's no longer there - an Air2PC), but it is able to tune the QAM/Digital cable channels.

---

### Post by thecoolcat on 2008-03-14
I was of the opinion that .21 would have fixed these issues. When you view the capture card (the one you have set to using the DVB driver) in mythtv-setup, do you see an "analog options" button?

---

### Post by JPurdy on 2008-03-14
Nope.  Just the Disq-- (I forget the acronym atm) settings, which seem to go to something that would control an antennae and then the Recording Options, which seem to involve DVB timeouts, etc.  No "Analog Options" button.  I'll try to post a screenshot when I get home.

Interestingly, it reports the card as an Air2PC, but that card is no longer in the machine.

---

### Post by thecoolcat on 2008-03-14
Quick one: Do you at least have DVB working? (Are you able to tune ATSC channels and watch digital content?)

---

### Post by JPurdy on 2008-03-14
Yup.  After the upgrade, I wasn't able to originally, but I simplified the box by removing the Air2PC card and moved the KWorld tuner to the first PCI slot.  Note that before that, the mythtv-setup was still confusing the tuner chipsets, calling the Air2PC card a Broadcom and the KWorld an Air2PC.  That led me to wasted work b/c I was configuring the wrong card and not understanding why it wasn't working. ;)

But yeah, now, I'm able to tune/watch ATSC.  But without the parentid field or the Analog Options button, I'm unsure how to re-add the NTSC "tuner".  My guess is that mythtv sees it as the Air2PC card and knows it doesn't have an analog tuner part, so it doesn't offer the Analog Options button.

---

### Post by novellahub on 2008-06-06
> **JPurdy said:**
> Yup.  After the upgrade, I wasn't able to originally, but I simplified the box by removing the Air2PC card and moved the KWorld tuner to the first PCI slot.  Note that before that, the mythtv-setup was still confusing the tuner chipsets, calling the Air2PC card a Broadcom and the KWorld an Air2PC.  That led me to wasted work b/c I was configuring the wrong card and not understanding why it wasn't working. ;)

But yeah, now, I'm able to tune/watch ATSC.  But without the parentid field or the Analog Options button, I'm unsure how to re-add the NTSC "tuner".  My guess is that mythtv sees it as the Air2PC card and knows it doesn't have an analog tuner part, so it doesn't offer the Analog Options button.

It appears that Mythtv .21 uses a feature called "Input Group" with mythtv-setup in "Input connections".

---

### Post by kwisher on 2008-07-26
> **novellahub said:**
> It appears that Mythtv .21 uses a feature called "Input Group" with mythtv-setup in "Input connections".

I have two Kworld-115's and would like to know if there is any documentation or instructions explaining this new "input group" feature?

TIA,

kwisher

---

