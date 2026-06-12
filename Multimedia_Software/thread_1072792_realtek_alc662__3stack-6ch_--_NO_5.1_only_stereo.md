---
title: "realtek alc662  3stack-6ch -- NO 5.1 only stereo"
date: 2009-02-17
forum: Multimedia Software
---

### Post by gdoteof on 2009-02-17
I have a Vostro 220 from Dell, E7300.  Realtek ALC662 integrated 5.1 audio.  I could not get the sound working but eventually found 
[ALSA Upgrade Script]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=alc662") which got my sound working.

Now, I am trying to hook up my 5.1 but am only getting 2 channels.  I have tried 

```
**gdot@gdot-ubuntu:/etc/modprobe.d$ uname -a**
Linux gdot-ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

```

```
**gdot@gdot-ubuntu:/etc/modprobe.d$ aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
**gdot@gdot-ubuntu:/etc/modprobe.d$ tail /etc/modprobe.d/alsa-base**
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=3stack-6ch
```

Note:  I have also tried 
options snd-hda-intel model=3stack-dig 
options snd-hda-intel model=3stack-6ch 
options snd-hda-intel model=3stack-6ch-dig 
options snd-hda-intel model=stack-dig 
options snd-hda-intel model=auto 

[IMG]http://i.dell.com/images/global/products/vostrodt/desktop_vostro_highlights/desktop-vostro-220mt-overview3.jpg[/IMG]

```

**gdot@gdot-ubuntu:/etc/modprobe.d$ lsmod | grep -i sn**d
snd_hda_codec_realtek   267396  1 
snd_hda_intel          38024  4 
snd_hda_codec          87680  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17160  1 snd_hda_codec
snd_pcm_oss            52256  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                98824  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy          11652  0 
snd_seq_oss            43648  0 
snd_seq_midi           15808  0 
snd_rawmidi            34080  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67744  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              33424  2 snd_pcm,snd_seq
snd_seq_device         16788  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    83400  20 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18576  2 snd_hda_intel,snd_pcm
```



Any help would be appreciated!

Oh yeah: Ubuntu 8.10 64 bit version

---

### Post by neu2buntu on 2009-02-17
have you rebooted each time you edit the "alsa-base"  file to make it take effect....
   also try adding "index=0" to the end of the file ie 
```
options snd-hda-intel model=3stack-6ch index=0
``` to give it first priority
  and also after trying the snd-hda-intel options and rebooting goto the speaker icon on top panel right click >open volume control> preferences > tick all options... in this volume control look at > playback and in any other tabs look for switch... something like spdif (forget exact name ) and tick it... there may be other switches just experiment...  i remember reading something about this before,..well i hope this is of some help

---

### Post by du@dde on 2009-02-17
I had a similar problem where I only got 2-channel sound out of my Audigy card. I solved it by editing /etc/pulse/daemon.conf.

; default-sample-channels = 2
uncomment the line and add more channels. I put a 4 there, but I guess you would need a 6 for 5.1

After a reboot the issue was solved.

GL

---

### Post by gdoteof on 2009-02-17
I was so excited to get two responses of things I haven't tried but neither worked. =(

I have rebooted after each edit of alsa-base.

---

### Post by neu2buntu on 2009-02-17
have you tried the iec958 switches to see if they work?  also have you looked at the settings in > syste3m > preferences > sound  and check that you have alsa mixer as default (sometimes the settings here override the other mixer in panel)

---

### Post by gdoteof on 2009-02-17
yes they don't seem to do anything.  it is the s/pdif output (i think) which comes out of my mother board but i am not using it

---

### Post by du@dde on 2009-02-17
In my case I have to adjust the volume on "PCM Center", "PCM Front", "PCM LFE" and "PCM Surround" to get anything out of the other speakers. I noticed that you did not have them available in your volume control. See if you can enable them and unmute them.

---

### Post by gdoteof on 2009-02-17
i had it there before, i had changed it just trying to fiddle with it

---

### Post by gdoteof on 2009-02-17
> **du@dde said:**
> In my case I have to adjust the volume on "PCM Center", "PCM Front", "PCM LFE" and "PCM Surround" to get anything out of the other speakers. I noticed that you did not have them available in your volume control. See if you can enable them and unmute them.

.

---

### Post by du@dde on 2009-02-17
Sorry, I am out of ideas.

But I found the link to the page that helped me to get my surround working.
[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

Perhaps it can help you. GL

---

### Post by neu2buntu on 2009-02-17
maybe "alsa-mixer" is the wrong device for using surround post a screenshot with the volume-control device pull down list open to see what options there are

---

### Post by gdoteof on 2009-02-17
unfortunately that tutorial did not work for me.

---

### Post by gdoteof on 2009-02-17
oops empty post plz delete

---

### Post by gdoteof on 2009-02-17
this?

---

### Post by gdoteof on 2009-02-18
Anyone else have a Vostro out there?

---

### Post by neu2buntu on 2009-02-18
hmmm your mixer options dont show any digital playback. im stumped here unfortunately, try this post it has extensive sound setup options and theres a section on surround too ,,,,
[http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack](http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack)
the section about "digital output" may also interest you .pay attention to rebooting each time you try any of the digital switches also....

---

### Post by gdoteof on 2009-02-18
I'm not sure I have digital out at all?  Isn't digital out a specific type of jack that isn't the same as the normal headphone style ones?  If it is, I don't have it.. I will check out that link

---

### Post by gdoteof on 2009-02-18
Your ALSA information is located at [http://www.alsa-project.org/db/?f=ee18b7d407f9a73214fc6986215fc61e03c9679d](http://www.alsa-project.org/db/?f=ee18b7d407f9a73214fc6986215fc61e03c9679d)

---

### Post by gdoteof on 2009-02-18
slightly updated

[http://www.alsa-project.org/db/?f=59d4f71caba89f00c30c84662e5ac24f2d72c65c](http://www.alsa-project.org/db/?f=59d4f71caba89f00c30c84662e5ac24f2d72c65c)

---

### Post by gdoteof on 2009-02-18
SOOOOOOOOOOOOOOOOOLLLLLLLLLVVVVVVVVVVVEEEEEDDDDDDDDDDDDDDDDD

In my /etc/modprobe.d/options there was a line that said 

options snd-hda-intel model=laptop

I replaced that with

options snd-hda-intel model=3stack-6ch-dig


I also recompiled and uninstalled alsa a million times but this is what fixed it.

---

### Post by rb-cohen on 2009-04-22
Wow, this actually worked! I can't believe how happy having 5.1 again has made me. Anyway, I did the following to get surround sound working with the Realtek alc662:

[LIST=1]
[*]Followed the (simple) instructions at [http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

[*]Added the line "options snd-hda-intel model=3stack-6ch-dig" to the end of /etc/modprobe.d/alsa-base

[*]Restarted computer (for step 2 to take affect)

[*]Opened sound preferences, selected ALSA mixer, ticked the newly listed "Center, LFE", etc.

[*]Still under sound preferences, on the options tab I set 'Channel mode' to 6ch.

[*]I used "$ speaker-test -Dplug:surround51 -c6 -l1 -twav" to test all worked, and it certainly did!
[/LIST]

The key is **step 2**, the other steps are all well documented elsewhere.

---

### Post by dasan on 2009-08-02
it was enabled default for me only i need to do was select 6 ch from mixer

you can select it from command prompt too

type [COLOR="Blue"]alsamixer[/COLOR] in command and you will find a channel section select 6ch

---

### Post by Eeqmcsq on 2009-08-22
Thank you thank you thank you thank you thank you!!!
Thanks both to gdoteof for the original solution and rb-cohen for the solution that fit me best. Here's my test scenario for in case others with my motherboard need it.

This was tested using an Ubuntu 9.04 Desktop Live CD, so you can test it before permanently making changes to a real installation.

Motherboard: Zotac GF8200-C-E (aka GeForce 8200 ITX)
Sound: ALC662 

1. From a terminal, type "gksudo gedit /etc/modprobe.d/alsa-base.conf". At the end of the file, insert the line "options snd-hda-intel model=3stack-6ch-dig". Save and quit out of gedit.
2. Force the alsa sound library to reload: "sudo /sbin/alsa force-reload". The Volume Control app will probably report that it has crashed. Just click Reload to reload it.
3. Open the Volume Control app, click Preferences. Check Surround, Center, LFE, and most importantly, Channel Mode.
4. Now go to the Options tab. For Channel Mode, select 6ch.
5. Type "aplay -L" to list all available devices. You can pick one of these devices when using the "speaker-test" command.
6. Run a 6 channel speaker test: "speaker-test -twav -c6 -Dsurround51:CARD=NVidia,Dev=0". The 6 channels will come out of the 3 audio jacks in the back of the motherboard.

Other notes:
- If you want pulseaudio to work in more than 2 channels, follow the link in step 1 of rb-cohen's instructions.

---

### Post by sir4taye on 2009-09-13
So...
I'm wanting to buy this board from newegg. Have you had any other motherboard centered issues? Any other workarounds? Did the SATA recognize and flow without a IDE hard drive? 

Thanks in advance for your time.

---

### Post by xjgnsdof on 2009-12-11
The instructions in post #23 worked on my Zotac Ionitx-A-U in Xubuntu 9.10.

---

### Post by mi.k on 2010-01-14
Unfortunately post #23 does not work on my ZOTAC IONITX-D-E - NVIDIA ION. I am trying to check Check Box "Channel Mode" (in gnome-alsamixer), but after restart check box is again unchecked :(

Many thanks in advance for your time. Mike

---

### Post by djmaxmalta on 2010-11-13
> **dasan said:**
> it was enabled default for me only i need to do was select 6 ch from mixer

you can select it from command prompt too

type [COLOR="Blue"]alsamixer[/COLOR] in command and you will find a channel section select 6ch

by using the quoted method and without retating my wubi, i used terminal with "sudo /sbin/alsa force-reload" gave it my pasward and let it do its work, when terminal was ready i restarted rythembox


and bam my 5.1 labtec Arena 685 all worked (better then in windows)

---

