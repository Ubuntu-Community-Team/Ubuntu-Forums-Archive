---
title: "Recording What-u-Hear"
date: 2009-03-21
forum: Multimedia Software
---

### Post by Volt9000 on 2009-03-21
I would like the ability to record whatever is coming out of my speakers, like the "What-U-Hear" feature in Windows on Soundblaster cards (I have an SB Audigy 2.)

I found several threads on the forums already about this but nothing that seems to work. The closest I found was [http://ubuntuforums.org/showthread.php?t=566024](http://ubuntuforums.org/showthread.php?t=566024) but the OP doesn't specify what settings in their sound control panel they used.

If I double-click the sound icon and choose the Recording tab for my device "Audigy 2 [SB0240] (Alsa mixer)" whenever I uncheck the MUTE from any device, when I return to the panel the device is muted again! :(

Furthermore, I'm not certain which recording device to select in Audacity. I've attached a screenshot showing what I have.

Someone please help, this is driving me crazy!

---

### Post by Edho on 2009-03-21
Same.

Tryed 1000 combinations in Audacity.

Can't recording what i heare.

It's so stupid in fact.

---

### Post by boof1988 on 2009-03-21
I expect that others will have better recommendations...

If no one else has any better ideas you could try [*Jack*](http://jackaudio.org/).  The package name is [*jackd*](http://packages.ubuntu.com/hardy/jackd).  There is also a GUI for *jack* called [*qjackctl*](http://packages.ubuntu.com/hardy/qjackctl).

NOTE: The links (above) are for Hardy, but they should be available for other editions as well.

I haven't used it (and I'm not totally sure *yet* if it will do what you need).  But I have read a little about it and would like to try it myself sometime.  Don't know how involved the interface is (if it is relatively hard or easy).

Hope this helps a little.

---

### Post by jjgomera on 2009-03-21
check in gnome-volume-control, tab Record if you have check and up top the level

---

### Post by Volt9000 on 2009-03-21
> **boof1988 said:**
> I expect that others will have better recommendations...

If no one else has any better ideas you could try [*Jack*](http://jackaudio.org/).  The package name is [*jackd*](http://packages.ubuntu.com/hardy/jackd).  There is also a GUI for *jack* called [*qjackctl*](http://packages.ubuntu.com/hardy/qjackctl).

NOTE: The links (above) are for Hardy, but they should be available for other editions as well.

I haven't used it (and I'm not totally sure *yet* if it will do what you need).  But I have read a little about it and would like to try it myself sometime.  Don't know how involved the interface is (if it is relatively hard or easy).

Hope this helps a little.

Yeah I took a look at JACK, but I couldn't really figure it out... every time I tried to start it up it would start complaining it can't connect to the server.

> **jjgomera said:**
> check in gnome-volume-control, tab Record if you have check and up top the level
Yeah, that much I know. The problem is I have 11 devices listed so I don't know which one to pick. I tried a few but every time I go to the Recording tab and unmute a particular channel, it just automatically gets muted again.

---

### Post by boof1988 on 2009-03-22
> **Volt9000 said:**
> Yeah I took a look at JACK, but I couldn't really figure it out... every time I tried to start it up it would start complaining it can't connect to the server.

Sorry that didn't work for you.  Hopefully someone else will chime-in and give some ideas (that work).

---

### Post by Volt9000 on 2009-03-22
After sifting through lots of threads and trying a lot of different, things I FINALLY got it to work!
Please note not all of these steps may be necessary, but these are just the steps that I did to get this to work.
I've got a SoundBlaster Audigy 2 and I'm using the ALSA sound system, running on Intrepid Ibex 8.10. I presume this should work with any audio card that supports concurrent playback and recording, just make sure to substitute your card in Step 2 below.

Here's what I did:

1) Go to System > Preferences > Sound.
2) Next to "Sound capture:" select the following device:
Audigy 2 [SB0240] (rev.4, serial:0x10071102) ADC Capture/Standard PCM playback (ALSA) and click Close.
3) Double-click the sound icon in the system tray.
4) Select "Audigy 2 [SB0240] (Alsa mixer)" as the device and click Preferences.
5) Scroll down until you see "Recoding" in the second column and place a checkmark next to the following items:
  Master Capture
  PCM
6) Click Close and there should now be a Recording tab in the Volume Control window. Click it.
7) Crank up the Master Capture and PCM to maximum volume, and make sure the little microphones don't have an X on them. If they do, click them.
8 ) You can now close Volume Control.

**IMPORTANT NOTE:**
If you go back into Volume Control and click the Recording tab, you may notice that all devices still have the little X over the microphones. **THIS IS FINE** and I think it's a bug in the application.

Now you can start recording right away using Sound Recorder!

If you prefer to use Audacity, there are a few more steps:
9) In Audacity, click Edit > Preferences.
10) Under "Recording", select the device "ALSA: Audigy 2 [SB0240]: ADC Capture/Standard PCM Playback (hw:0,0)"

Now just hit the big record button in Audacity and it should automatically record whatever is coming through your speakers.

I hope this information helps distressed noobs like myself down the road. :D

---

### Post by boof1988 on 2009-03-22
> **Volt9000 said:**
> After sifting through lots of threads and trying a lot of different, things I FINALLY got it to work!
Please note not all of these steps may be necessary, but these are just the steps that I did to get this to work.
I've got a SoundBlaster Audigy 2 and I'm using the ALSA sound system, running on Intrepid Ibex 8.10. I presume this should work with any audio card that supports concurrent playback and recording, just make sure to substitute your card in Step 2 below.

Here's what I did:

1) Go to System > Preferences > Sound.
2) Next to "Sound capture:" select the following device:
Audigy 2 [SB0240] (rev.4, serial:0x10071102) ADC Capture/Standard PCM playback (ALSA) and click Close.
3) Double-click the sound icon in the system tray.
4) Select "Audigy 2 [SB0240] (Alsa mixer)" as the device and click Preferences.
5) Scroll down until you see "Recoding" in the second column and place a checkmark next to the following items:
  Master Capture
  PCM
6) Click Close and there should now be a Recording tab in the Volume Control window. Click it.
7) Crank up the Master Capture and PCM to maximum volume, and make sure the little microphones don't have an X on them. If they do, click them.
8 ) You can now close Volume Control.

**IMPORTANT NOTE:**
If you go back into Volume Control and click the Recording tab, you may notice that all devices still have the little X over the microphones. **THIS IS FINE** and I think it's a bug in the application.

Now you can start recording right away using Sound Recorder!

If you prefer to use Audacity, there are a few more steps:
9) In Audacity, click Edit > Preferences.
10) Under "Recording", select the device "ALSA: Audigy 2 [SB0240]: ADC Capture/Standard PCM Playback (hw:0,0)"

Now just hit the big record button in Audacity and it should automatically record whatever is coming through your speakers.

I hope this information helps distressed noobs like myself down the road. :D

Thanks for posting your solution.  Hopefully it will help someone in the future... I might even try it.

---

### Post by Volt9000 on 2009-04-26
Crud. It didn't seem to keep. :(

I just tried recording again (first time since I last made this post) and it no longer works.
Don't know what I did differently last time. :(

---

### Post by Volt9000 on 2009-04-26
Well good news. I found an extremely helpful thread on these forums that works perfectly!

[http://ubuntuforums.org/showthread.php?t=1005196](http://ubuntuforums.org/showthread.php?t=1005196)

It's a bit of a process but works like a charm.
Make sure to thank the OP if it works for you!

---

