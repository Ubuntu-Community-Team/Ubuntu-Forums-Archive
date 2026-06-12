---
title: "Audio on Thinkpad T410 speakers stop working after a minute on 12.04-64"
date: 2014-03-16
forum: Multimedia Software
---

### Post by magnus07 on 2014-03-16
I have a Thinkpad T410 with Ubuntu 12.04-64 fully patched.

My problem is that the audio from speakers works for seconds, possibly some minutes and then stops making any sound.
That happens with any application (Rythm, Totem, ...)
If I put the earphones in the audio jack I can hear all perfectly.
I I do "sudo alsa reload" I can hear again the sound from speakers.

Please let me know what other info could be of help to understand the problem.

Thanks.

---

### Post by tgalati4 on 2014-03-16
I have a laptop with 12.10 that does the same thing, but I find plugging and unplugging the headphone jack brings sound back to the speakers.  I have not spent the time to track down the problem yet.

After a little searching:

[http://askubuntu.com/questions/280566/my-headphones-mute-alsamixer-when-i-plug-them-in-hp-dv6-12-04](http://askubuntu.com/questions/280566/my-headphones-mute-alsamixer-when-i-plug-them-in-hp-dv6-12-04)

[http://askubuntu.com/questions/140454/how-can-i-get-sound-on-headphones-without-switching-back-to-speakers-manually](http://askubuntu.com/questions/140454/how-can-i-get-sound-on-headphones-without-switching-back-to-speakers-manually)

I have not played with these settings yet.  Let us know what works for you.

---

### Post by magnus07 on 2014-03-17
I've reviewed both links and mostly speak about muted speakers when inserting an headphones.
My issue is not related to headphones. 
The speakers go mute (ie: the volume indicator is at max but nothing comes out of the speakers) without doing anything.
After that I can hear sounds using an headphone or reloading alsa.

---

### Post by tgalati4 on 2014-03-17
Turn all the volumes low.  Sometimes a high volume level will cause the audio circuit to go mute for protection.  See if the audio continues to work at low volumes.  Unfortunately, Thinkpad sound levels are low to begin with, so there is a temptation to set them to maximum.

---

### Post by magnus07 on 2014-03-17
Your suggestion was interesting.
I tried sperkers not at max vol. The sound didn't stop for minutes then I gave up.
Turned to max and stopped after seconds.
Tried to reset but didn't work. No application can emit sound using speakers.
On the headphones I get the sound as usual.

Will investigate more. It could be a defective HW...

---

### Post by tgalati4 on 2014-03-17
The headphones are powered directly from the sound chip.  The speakers go through an amplifier chip which may have clip-limiting.  There is a small tab in the headphone jack that detects when a jack in plugged in and makes the switch between headphone jack and speakers.  This is called "headphone sense".  It's possible that your amplifier is worn out, or just a safety fuse that will reset when some time has passed for it to cool down.  Although the newer thinkpads have better sound than the old ones, they are still crappy by any standard.

---

### Post by magnus07 on 2014-03-18
Today it stopped working with volume at 3/4 after seconds.
Possibly is not a volume setting problem.

What else?

---

### Post by magnus07 on 2014-03-21
I did some additional tests.
It stops emitting sound from speakers generally after 1-2 minutes.
If I use "sudo alsa force-reload" it will generally emit sounds again, generally stopping a thread
Happens with any application using the speaker.
I already tried to reinstall all alsa but nothing changed.
Need some ideas...

---

### Post by David_Medders on 2014-08-05
I have two T410 laptops suffering the same intermittent speaker failure.

Speakers on both work after booting Ubuntu 12.04 or 14.04, but fail within a few minutes.  This was not always the case.  All was well for a few months when 12.04 was loaded on these laptops soon after its initial release.  Subsequent patching introduced this fault.

Speakers work perfectly with CentOS 7 -- problem solved if only I wanted to run CentOS 7.

I have found numerous erroneous explanations  for this problem over the past many months.  None are consistent with the symptoms experienced by us T410 users.  This is not a fault in the headphone jack.  It is not audio clipping in speaker amplifier.  It is a software problem -- it appears with Ubuntu 12.04 and 14.04, then disappears when CentOS 7 is loaded.

What is required to investigate this as the Ubuntu software fault that it is?

Thanks,
David

---

### Post by kirk3 on 2014-10-29
> **David_Medders said:**
> I have two T410 laptops suffering the same intermittent speaker failure.

Speakers on both work after booting Ubuntu 12.04 or 14.04, but fail within a few minutes.  This was not always the case.  All was well for a few months when 12.04 was loaded on these laptops soon after its initial release.  Subsequent patching introduced this fault.

Speakers work perfectly with CentOS 7 -- problem solved if only I wanted to run CentOS 7.

I have found numerous erroneous explanations  for this problem over the past many months.  None are consistent with the symptoms experienced by us T410 users.  This is not a fault in the headphone jack.  It is not audio clipping in speaker amplifier.  It is a software problem -- it appears with Ubuntu 12.04 and 14.04, then disappears when CentOS 7 is loaded.

What is required to investigate this as the Ubuntu software fault that it is?

Thanks,
David

I am still observing this same problem. I have tried many things, but nothing seems to work.

Any new about this topic?

---

### Post by magnus07 on 2014-10-30
I still have a T410 with the same issue and would be very interested in a solution.

---

### Post by smoczynski.marcin on 2014-10-30
I have same issue with my t410s - internal speakers stop at random. I believe it is related to the poor heatsink design and high temperature inside - the sound is being cut of more often when temperature is over 70 degrees. It could be overheat protection in lenovo firmware.

I came across "hda_analyzer" application which informs when something has been changed in sound card configuration. When sound mutes sound card goes from D0 to D3 power state (turn off).
To turn it on again one have to execute:

 ```
sudo hda-verb /dev/snd/hwC0D0 0x1f SET_POWER_STATE 0
```

log from hda analyzer:
```

Diff for codec 0/0 (0x14f15069):
--- 
+++ 
@@ -179,17 +179,17 @@
 Node 0x1f [Pin Complex] wcaps 0x400501: Stereo
   Control: name="Speaker Phantom Jack", index=0, device=0
   Pincap 0x00000010: OUT
   Pin Default 0x901701f0: [Fixed] Speaker at Int N/A
     Conn = Analog, Color = Unknown
     DefAssociation = 0xf, Sequence = 0x0
     Misc = NO_PRESENCE
   Pin-ctls: 0x40: OUT
-  Power: setting=D0, actual=D0
+  Power: setting=D3, actual=D3
   Connection: 2
      0x10 0x11*
 Node 0x20 [Pin Complex] wcaps 0x400781: Stereo Digital
   Pincap 0x00000010: OUT
   Pin Default 0x40f001f0: [N/A] Other at Ext N/A
     Conn = Unknown, Color = Unknown
     DefAssociation = 0xf, Sequence = 0x0
     Misc = NO_PRESENCE


```

Suspending and waking up system again or reloading snd_hda_intel driver will do the same because the driver switches internal sound card to D0 power mode on probe.
Of course it does not solve the problem which I believe is more likely to be design flaw in t410s than software issue:
[http://superuser.com/questions/567255/thinkpad-speaker-turns-mute-linux-codec-issue](http://superuser.com/questions/567255/thinkpad-speaker-turns-mute-linux-codec-issue)

---

### Post by kirk3 on 2014-10-30
I am observing this also.
It looks like a hardware problem...

---

### Post by jurgen32 on 2014-10-31
Just a wild guess.... you never know.
Do you have TLP (from Linrunner) installed? The config file (/etc/default/tlp) contains an option for sound: 

```
Audio
SOUND_POWER_SAVE_ON_AC=0
SOUND_POWER_SAVE_ON_BAT=1

Timeout (in seconds) for the audio power saving mode (supports Intel HDA, AC97). A value of 0 disables power save.

Hint: this setting can cause slight clicks in sound output.
SOUND_POWER_SAVE_CONTROLLER=Y

    Y – powers off the controller together with the sound chip
    N – controller active permanently
```

---

### Post by magnus07 on 2014-11-01
I've checked and I don't have TLP installed.

Are you suggesting to install it?

---

### Post by kirk3 on 2014-11-01
I have TLP installed and my audio options look exactly like that and the issue is till there.

---

### Post by jurgen32 on 2014-11-02
No I was not suggesting to install TLP. I have it installed on my w540 and it works great.
I knew about the audio setting and wondered whether that could be your problem. When I use a headphone I can distinctly hear the sound being switched of after a second of silence (it turns back on whenever there is something to hear).

That is why I said 'just a wild guess'. To bad! I would have been great to see this problem solved :(

---

### Post by kirk3 on 2014-11-03
Yes, of course, I understood you, but I just wanted to let know more about my personal situations.
Anyway, thank you.

---

### Post by kirk3 on 2014-11-03
Has anyone tried to make a clean installation of ubuntu 14.04 instead of upgrading from 12.04?
Could it be a bug in 12.04 that remains after the upgraded but it could be solved starting from 14.04?

---

### Post by kirk3 on 2014-11-05
A new sign that I have observed: After the problem with the speakrs and a few minutes in silence (all the sound sources stopped), I am able to use the speakers again.
However the issue remains and the sound dissapears after a few minutes again.

---

