---
title: "no sound after Jaunty 9.04 upgrade on Dell 1420N"
date: 2009-05-02
forum: Multimedia Software
---

### Post by robertbub on 2009-05-02
Sound was working perfectly before my upgrade from intrepid to jaunty.

I tried adding> options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
to /etc/modprobe.d/alsa-base.conf and the "/etc/init.d/alsa-utils restart".  And tried rebooting.  No go.

I've tried both OSS and ALSA and neither work.

The "PC Beep" (enabled in GNOME ALSA Mixer) works fine.

Here's what I have:> # lsmod|grep snd
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_timer              29704  1 snd_pcm
snd                    62628  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
# lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Device 01f3
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

---

### Post by robertbub on 2009-05-03
OK, I managed to get OSS working, but ALSA still will not work.

To get to a better state, I commented out all the "options snd-hda-intel" quirks in /etc/modprobe.d/alsa-base.conf .

But, ALSA does not work:> $ sudo alsactl init
Unknown hardware: "HDA-Intel" "SigmaTel STAC9228" "HDA:83847616,102801f3,00100201 HDA:14f12c06,14f1000f,00100000" "" ""
Hardware is initialized using a guess methodI'll keep working on it.

---

### Post by robertbub on 2009-05-08
OK, I discovered one thing.  It looks like my firewall (via Firestarter) was preventing pulseaudio from operating.  So, I decided to get rid of pulseaudio via the guide at [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/) .

Next, I found that I could "aplay" a WAV file ('tho it didn't sound right -- it sounds like static) from the root account, but not from the user account.  I found out that my user account had a ~/.asoundrc which was directing everything to pulseaudio.  So, I nixed that.

At this point, I can "aplay" (albeit with only a static hiss) as a normal user, but the "Test" button in Sounds Preferences says> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
My plan next is to use *strace* on the Sounds Preferences app to figure out what's failing.

---

### Post by robertbub on 2009-05-08
I fixed it.  I didn't have to do the strace as suggested above.

Instead, I needed to remove all the quirks from /etc/modprobe.d/alsa-base.conf (i.e., make it the equivalent of **options snd-hda-intel model=dell-bios**) and do "alsa force-reload".

I still have no start-up sound, but I can hear the logon sound and I can again hear flash videos.

Phew.  What a pain.

---

### Post by mlinksva on 2009-05-24
I'm not sure I grok all of the above, but on my Dell 1420n running 9.04 'alsa force-reload' makes sound work, but has to be run again after each suspend or reboot to make sound work.

---

### Post by robertbub on 2009-05-30
> **mlinksva said:**
> I'm not sure I grok all of the above, but on my Dell 1420n running 9.04 'alsa force-reload' makes sound work, but has to be run again after each suspend or reboot to make sound work.**alsa force-reload** was insufficient.  I tried that several times.  It was definitely due to pulse audio and my firewall.

---

### Post by byjg on 2009-06-01
Hi, I had the same problem, but I resolved. If you open Sound Control (on Gnome Desktop -> Right Click over sound icon), you have to check IEC958. This is done for both on my Dell Docking Station and only for notebook. 

I hope this help you.

---

### Post by Cavemann on 2009-06-01
Hi

I have Dell inspiron 8600 and just upgraded to Jaunty from heron and am trying to kill all beeps and sounds but still get loud closeing down beep which wakes the dog and he starts barking which is not good at midnight.

In Heron there was a System Beeps tab in the Sounds menu but this is missing in Jaunty (unless there is something I have not installed - forgetful?)I have turned off (unticked ) play all sounds. 

Any help would be appreciated
Thanks

---

### Post by uhurusurfa on 2009-07-17
The suggestion by byjg for my Dell Inspiron 8500 solved the problem.

Steps were:
1.Right click on sound/speaker icon in menu bar and choose"Open Volume Control"
2. Select "Preferences" button
3. Scroll down to "IEC958" option and select
4. Click "Close"
5. Select the "Switches" tab in the sound control window
6. Check the"IEC958" checkbox

---

### Post by sgk1945 on 2009-09-20
I spent hours following the instructions here and still could not get sound except by selecting "OSS" as the playback device. But I had no startup sound, no system sounds, and no sound in WINE. (When I selected "Automatic" I got no sound at all.)

I went to bed frustrated and got up this morning, opened the startup application folder "SYSTEM>PREFERENCES>STARTUP APPLICATIONS" and unchecked the box for "Pulse Audio Session Management"  Everything works great now.

---

