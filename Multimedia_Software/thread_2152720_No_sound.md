---
title: "No sound"
date: 2013-06-08
forum: Multimedia Software
---

### Post by KiwiPete on 2013-06-08
I am running Ubuntu 12.04 on an old Dell Mini netbook.
All was well until a few months ago after running software updates when the sound no longer worked.
Neither speakers nor headphone jack produces any sound - no system sounds, nothing.
The soundcard is not recognised in Sound Settings.
I have googled and searched lots of forums - and tried all sorts of recommended fixes without success.
I'd appreciate some help.

Here are some outputs:

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

uname -a
Linux old-Inspiron-910 3.2.0-45-generic-pae #70-Ubuntu SMP Wed May 29 20:31:05 UTC 2013 i686 i686 i386 GNU/Linux

alsactl --version
alsactl version 1.0.25

And here is link to my AlsaInfo [http://www.alsa-project.org/db/?f=0a802b2b7d0478fd0726ffc6cca61b9501e64be8](http://www.alsa-project.org/db/?f=0a802b2b7d0478fd0726ffc6cca61b9501e64be8)

Grateful for any advice.

KiwiPete

---

### Post by Baldrick_NZ on 2013-06-10
When you go into sound settings, under output, what device is listed?

---

### Post by KiwiPete on 2013-06-10
Hi Baldrick
No device is listed under output, the panel is completely blank.
KiwiPete

---

### Post by virtdave@mcn.org on 2013-06-10
same problem here...here are my outputs:

david@david-desktop:~$ alsactl -version
alsactl version 1.0.25
david@david-desktop:~$ lspci|grep Audio
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
david@david-desktop:~$ uname -a
Linux david-desktop 3.5.0-32-generic #53~precise1-Ubuntu SMP Wed May 29 20:33:37 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Yellow Pasque on 2013-06-10
Would try latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by virtdave@mcn.org on 2013-06-10
> **Temüjin said:**
> Would try latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

That may have done it....at least I can now use Skype (via a USB mike/headset), which I couldn't before....and I can stream internet radio thru my speakers.  
One peculiar thing tho is that no sound input/output options are shown in the Sound screen.....the Output (Play Sound Through) and the Input (Record Sound From) areas are blank.  So I guess if I wanted to listen to music on the headphones, I'd be out of luck.  I can live with that.  And luckily the default volume for both input and output on the headset are fine, since it's not clear how I would change them.

---

### Post by Yellow Pasque on 2013-06-10
virtdave: it sounds like pulseaudio is not running
Try:
```
rm -r ~/.pulse*; pulseaudio
```

---

### Post by KiwiPete on 2013-06-11
Thanks Temujin
Installing the latest driver has not fixed the sound problem, however the sound settings does now list "Speakers - built in audio"
But still no sound at all.
Any other suggestions?
Peter

---

### Post by KiwiPete on 2013-06-11
Hi again Temujin
I just checked the headphones and I have sound working there.
So it is just the speakers now that are not wprking.
Any ideas?
Peter

---

### Post by KiwiPete on 2013-06-11
Hi again
This very strange. After plugging in the headphones the device panel in sound settings output device is blank again. But sound works well through the headphones.
When I try 
rm -r ~/.pulse*; pulseaudio
I get this message:
D-Bus name org.PulseAudio1 already taken.
Any help / advice?
Peter

---

### Post by virtdave@mcn.org on 2013-06-11
> **Temüjin said:**
> virtdave: it sounds like pulseaudio is not running
Try:
```
rm -r ~/.pulse*; pulseaudio
```

Am asymptotically approaching full audio function.  I used the above code, and now the expected stuff does appear in the Sound window--but testing the sound in any of the Output options does not produce anything.  When my USB headphones/mike is plugged in, I can use it with Skype, no problem.  And I can stream internet radio via the external speakers or the headphones, choosing the desired output via the Sound window.  So the only thing not 100% is the non-operative Test Sound button.  I can live with this, tho if there's an easy answer, I'll apply it out of compulsiveness.
Btw, I think I got in this jam by following Skype's recommendations on how to set up Skype in Ubuntu.  Maybe.  In any case, thanks for the help.

post edited at 1333h France time 11 June 2013:
Perhaps this is a bug.  See [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1003058](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1003058)

---

### Post by Yellow Pasque on 2013-06-11
@Kiwi: it sounds like this bug: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1029213](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1029213)

---

### Post by KiwiPete on 2013-06-12
Thanks Temujin
I am not familiar with the process for getting bugs resolved.
Do I just have to wait, and hope that someone creates a fix?
Or is there something more I can try?
Regards
Peter

---

