---
title: "Sound.. then no sound after a while in 11.04"
date: 2011-04-29
forum: Multimedia Software
---

### Post by PhonicLynx on 2011-04-29
Just installed 11.04 and for the first time Alsa actually detected my IEC985 digital device without any trouble.. every other version has not worked at all until i've installed pulseaudio.

Sound works on boot of the system.. then after some time the sound just stops. Not in just one application.. but in every application.

Weird thing is.. I have more than one device hooked up too.. and I can go into Sound Preferences, select one of the other devices and the sound will work through it.

Not too sure how to troubleshoot as to what is going on with the sound?

---

### Post by PhonicLynx on 2011-04-30
Its weird... I can't produce it because ever time its different. I've looked at /var/logs/dmesg and monitored it and its not said anything substantial.. because I can't find what it causing it to freeze.

Can anyone give me some guidance as to where i could be looking other than that?

---

### Post by PhonicLynx on 2011-04-30
My Alsa info is here:  [http://www.alsa-project.org/db/?f=ae841166414947e4e35f10ae31d22bcbe549f0bb](http://www.alsa-project.org/db/?f=ae841166414947e4e35f10ae31d22bcbe549f0bb)

---

### Post by lidex on 2011-05-01
Try setting a model in alsa-base.conf
Your options:
```
AD1988/AD1988B/AD1989A/AD1989B
==============================
  6stack	6-jack
  6stack-dig	ditto with SPDIF
  3stack	3-jack
  3stack-dig	ditto with SPDIF
  laptop	3-jack with hp-jack automute
  laptop-dig	ditto with SPDIF
  auto		auto-config reading BIOS (default)

```
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model= 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by PhonicLynx on 2011-05-01
Okay.. I've added "options snd-hda-intel model=3stack-dig" .. I hope that is what you mean. Only time will tell if that works.

---

### Post by PhonicLynx on 2011-05-01
Nope... 

DOing that didn't have any effect... sound has still disappeared.

It was there on reboot.. but 5 mins later.. it just stopped.

Interestingly enough.. if I go into pulseaudio and have a look at the outgoing sound.. it says that its pushing out sound.. but nothings coming out the speakers.

---

### Post by lidex on 2011-05-01
Alsa sees 5 devices, probably a conflict between them.

What is this output:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by PhonicLynx on 2011-05-02
```
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  nat        1541 F.... pulseaudio
/dev/snd/controlC1:  nat        1541 F.... pulseaudio
/dev/snd/controlC2:  nat        1541 F.... pulseaudio
/dev/snd/controlC5:  nat        1541 F.... pulseaudio

```

---

### Post by PhonicLynx on 2011-05-03
How is this for weird... If I leave Pulse Audio Volume Control on the sound does not disappear.. not sure why this is.. but if I close it.. give it a good 5 mins or so and it will disappear.

---

### Post by lidex on 2011-05-04
Interesting, saw that once before but didn't follow the thread. 
Do me a favor - the next time audio drops out run that last command again. 
It should tell us what is taking control of the sound card.
The output you posted is perfect.

---

### Post by PhonicLynx on 2011-05-04
Before:
```
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  nat        1876 F.... pulseaudio
/dev/snd/controlC1:  nat        1876 F.... pulseaudio
/dev/snd/controlC4:  nat        1876 F.... pulseaudio
/dev/snd/controlC5:  nat        1876 F.... pulseaudio
/dev/snd/seq:        timidity   1476 F.... timidity

```
I will post again when ts not working.

---

### Post by PhonicLynx on 2011-05-04
and after:
```
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  nat        1876 F.... pulseaudio
/dev/snd/controlC1:  nat        1876 F.... pulseaudio
/dev/snd/controlC4:  nat        1876 F.... pulseaudio
/dev/snd/controlC5:  nat        1876 F.... pulseaudio
/dev/snd/pcmC0D1p:   nat        1876 F...m pulseaudio
/dev/snd/seq:        timidity   1476 F.... timidity

```

---

### Post by PhonicLynx on 2011-05-04
I then checked again a few mins after and the same result came back.
```
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  nat        1876 F.... pulseaudio
/dev/snd/controlC1:  nat        1876 F.... pulseaudio
/dev/snd/controlC4:  nat        1876 F.... pulseaudio
/dev/snd/controlC5:  nat        1876 F.... pulseaudio
/dev/snd/seq:        timidity   1476 F.... timidity

```

---

### Post by PhonicLynx on 2011-05-04
Thought I'd try it again a bit later.. this time the sound vol has been kept on for quite a few hours. Not sure what this means:
```
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  nat        1761 F.... pulseaudio
/dev/snd/controlC1:  nat        1761 F.... pulseaudio
/dev/snd/controlC2:  nat        1761 F.... pulseaudio
/dev/snd/controlC5:  nat        1761 F.... pulseaudio
/dev/snd/pcmC0D0c:   nat        1761 F...m pulseaudio
/dev/snd/pcmC0D1p:   nat        1761 F...m pulseaudio
/dev/snd/pcmC1D0c:   nat        1761 F...m pulseaudio
/dev/snd/pcmC1D0p:   nat        1761 F...m pulseaudio
/dev/snd/pcmC2D0c:   nat        1761 F...m pulseaudio
/dev/snd/pcmC2D0p:   nat        1761 F...m pulseaudio
/dev/snd/pcmC5D0c:   nat        1761 F...m pulseaudio
/dev/snd/seq:        timidity   1481 F.... timidity

```

---

### Post by PhonicLynx on 2011-05-08
Have you got any ideas on this one? Its still doing it.. not seen any updates come through as yet either. It did work fine in 10.10 after I installed PulseAudio for some reason. But I've done that in this one but its not made any effect.

---

### Post by lidex on 2011-05-08
Try disabling timidity - it looks like it may be interfering.
Or reconfigure it:
> timidity

Timidity is a MIDI file player. You can reconfigure it to use the esound protocol (which pulseaudio implements) by editing the file /etc/default/timidity (you'll have to be root to do that). Find the row saying 'TIM_ALSASEQPARAMS="-Os"' and change it to:

TIM_ALSASEQPARAMS="-Oe"

Then restart timidity:

sudo /etc/init.d/timidity force-reload



---

### Post by PhonicLynx on 2011-05-09
I made that change and not long after the sound went out. So its not solved the problem still.

---

### Post by PhonicLynx on 2011-05-09
That seems to be worse... It goes out quicker and sometimes on reboot the sound doesn't start at all.

---

### Post by lidex on 2011-05-09
Try resetting your pulse configuration (again).
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*
When the sound goes out, run that command again:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by spoon_ on 2011-07-15
Same problem here! Ever since version 11.04, my sound never lasts long after a reboot.

---

### Post by PhonicLynx on 2011-07-15
I pretty well gave up.. I could't figure it out.. I ended up using a USB sound card which was cleaner then the sound out of the mobo.. but only had the problem with the SPDIF not any other sound devices.

---

### Post by spoon_ on 2011-07-15
Oh I'm using USB speakers! So I don't think it's purely a non-USB issue. I guess different hardware is affected differently though.

Sucks for me. I'd go back to an earlier Ubuntu release but I can't get my RAID array recognized in anything prior to 11.04 now. Gah.

---

### Post by PhonicLynx on 2011-07-15
i found as a work around that if I installed pulseaudio and then opened up the sound mixer that the sound stayed avaliable the whole session.. if I forgot it.. I had to reboot and make sure it was open the next time around.

---

### Post by spoon_ on 2011-07-15
Oh that's interesting, thanks for that. I'll give that a try. Sounds plausible because the sound never seems to die when something is actually playing. 

But pulseaudio is installed by default. Why do you mention installing it explicitly?

---

### Post by AKADAP on 2011-07-15
I'll chime in as a third person suffering this issue.
I did not have this issue when using the analog outputs of my motherboard, but switched to SPDIF because of limitations on my Denon receiver when using the analog input (no volume control, and earphones don't work when using the analog inputs).
Since switching to SPDIF I have been having the sound stop working.
Interestingly when it fails, if I log out, the sound still plays for the login screen, but if I log in again, the sound is still dead. I must reboot the computer to get sound working again.

---

### Post by AKADAP on 2011-07-17
Another point of reference:

sound working: 

```
$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC1:  dpeale     2090 F.... pulseaudio
/dev/snd/controlC2:  dpeale     2090 F.... pulseaudio
```

sound not working:

```
$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  dpeale     2054 F.... pulseaudio
/dev/snd/controlC1:  dpeale     2054 F.... pulseaudio
/dev/snd/controlC2:  dpeale     2054 F.... pulseaudio
/dev/snd/pcmC0D1p:   dpeale     2054 F...m pulseaudio
```

---

### Post by lidex on 2011-07-17
If you are using apps that access alsa directly, it could be locking the soundcard which means pulse cannot use it.
[http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by spoon_ on 2011-07-17
I don't have the problem of ALSA apps not showing up under sound-using applications...

---

### Post by AKADAP on 2011-07-18
> **lidex said:**
> If you are using apps that access alsa directly, it could be locking the soundcard which means pulse cannot use it.
[http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

If that is the case, why would it affect only the digital (SPDIF) output and not the analog output? I did not have this problem when I was using the analog outputs.

---

### Post by spoon_ on 2011-07-20
To the people experiencing this problem: do you have an HDMI output on your video card or motherboard? I'm not asking whether you're using it -- just whether you have one.

If you do, follow-up question: do you see these kinds of messages in dmesg:

```
hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
```

---

### Post by PhonicLynx on 2011-07-20
> **spoon_ said:**
> To the people experiencing this problem: do you have an HDMI output on your video card or motherboard? I'm not asking whether you're using it -- just whether you have one.

If you do, follow-up question: do you see these kinds of messages in dmesg:

```
hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
```

In fact I have two on my ATI cards (as I have crossfire) I believe.. not sure why it thinks it's a HDMI interface because its only a d-port and two DVI's.. yet its picking it up in Linux and windows as HDMI out.

---

### Post by spoon_ on 2011-07-20
> **PhonicLynx said:**
> In fact I have two on my ATI cards (as I have crossfire) I believe.. not sure why it thinks it's a HDMI interface because its only a d-port and two DVI's.. yet its picking it up in Linux and windows as HDMI out.

OK, the reason I ask is that I have a suspicion that the problem we're experiencing may be related to that. 

I have two Nvidia cards with HDMI ports (neither of which I'm using) in my machine. I disabled HDMI by adding these lines to /etc/modprobe.d/blacklist.conf:

```
blacklist snd_hda_codec_nvhdmi
blacklist snd_hda_codec_hdmi

```

The first line is unnecessary if you have an ATI card. I don't know whether the second line is sufficient or another ATI-specific line is required.

Anyway, now my system no longer shows HDMI audio outputs and I no longer see those error messages in dmesg. But it's too soon to say whether this has fixed my sound issue. So far sound works. We'll see in time...

---

### Post by spoon_ on 2011-07-21
Never mind, sound's gone! Good old Ubuntu.

---

### Post by PhonicLynx on 2011-07-21
> **spoon_ said:**
> Never mind, sound's gone! Good old Ubuntu.

Famous last words :P

---

### Post by spoon_ on 2011-07-21
> **PhonicLynx said:**
> Famous last words :P

Indeed! Just curious, are you running Sandy Bridge by any chance? Is this an SB-specific issue?

---

### Post by AKADAP on 2011-07-22
> **spoon_ said:**
> To the people experiencing this problem: do you have an HDMI output on your video card or motherboard? I'm not asking whether you're using it -- just whether you have one.

Yes I have one and am not using it. I'm not sure I can use it since I need dual link DVI for my monitor.
> 
If you do, follow-up question: do you see these kinds of messages in dmesg:

```
hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
```

Yes I do have this message in dmesg.

---

### Post by spoon_ on 2011-07-22
False alarm, AKADAP. Still a very mute Ubuntu.

---

### Post by AKADAP on 2011-07-22
> **spoon_ said:**
> False alarm, AKADAP. Still a very mute Ubuntu.

Are you sure?

Has anyone reported this problem without also having an HDMI audio output that they were not using?

---

### Post by spoon_ on 2011-07-22
> **AKADAP said:**
> Are you sure?

Has anyone reported this problem without also having an HDMI audio output that they were not using?

I don't know. But I do know that even after disabling the HDMI outputs (such that the OS no longer sees them), the sound problem persists.

---

### Post by spoon_ on 2011-08-01
Problem solved by switching to Fedora :/

---

### Post by huntt on 2011-08-01
Please try to install some other software and try to play then it will give you a double sound.

---

### Post by PhonicLynx on 2011-08-01
> **huntt said:**
> Please try to install some other software and try to play then it will give you a double sound.

hu? no it doesn't :S

---

### Post by afonic on 2012-02-01
Any updates on this ?

I have the same problem on Arch so it's no distro specific. I think it started happening with the 3.x kernel, I will check an older one in order to make sure.

---

