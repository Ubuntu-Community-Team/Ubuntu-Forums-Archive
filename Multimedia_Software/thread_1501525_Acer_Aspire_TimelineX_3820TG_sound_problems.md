---
title: "Acer Aspire TimelineX 3820TG sound problems"
date: 2010-06-04
forum: Multimedia Software
---

### Post by audiocrush on 2010-06-04
Hello Forum
When I plug in some external speakers in the headphone jack, the sound disappears. If I unplug them I can hear the sound again...

Does anyone know how to workaround this problem?

I got two sound options:
1. The HDMI digital sound output of my ATI Mobility Radeon HD 5650
2. Analog sound output

I am using the analog sound in duplex mode (one stereo input one stereo output)

A quick solution would be great :D The sound of the internal speakers is really horrible xD

---

### Post by audiocrush on 2010-06-04
*push*

---

### Post by lidex on 2010-06-05
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by audiocrush on 2010-06-06
```
audiocrush@debistorm:~$ uname -a
Linux debistorm 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
audiocrush@debistorm:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC269 Analog [ALC269 Analog]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC269 Digital [ALC269 Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: Generic [HD-Audio Generic], Gerät 3: ATI HDMI [ATI HDMI]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
audiocrush@debistorm:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
audiocrush@debistorm:~$ head -n1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

```

how can I find out the make or model of my laptop?
I only know that it is an acer aspire timelineX 3820TG ._.

---

### Post by lidex on 2010-06-06
I would try an alsa upgrade via the link in my sig. Then try the following.

Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

No help there replace acer with 'acer-aspire' or 'auto'

---

### Post by audiocrush on 2010-06-08
wuhuauuuu

I followed your alsa upgrade tutorial and it worked very well for me :]
I want to help you and give you the information you need for a supported hardware list^^

---

### Post by napetesy on 2010-06-08
> **lidex said:**
> I would try an alsa upgrade via the link in my sig. Then try the following.


Hello lidex and other users of Acer Aspire 3820TG
I have the same configuration as "audiocrush". I can confirm that just upgrading alsa via your ling ([http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")) solved problem with no sound from headphone jack. No further modifications as you suggested ```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
``` is necessary.
Thank you for your work and sharing your knowledge!

For all other users: if you don't have any sound (even from internal speakers) don't forget to change device for sound output in sound preferences (Gnome: left click on speaker icon -> Sound Preferences -> tab "Outpup" -> choose "Internal Audio Analog Stereo".

---

### Post by moreira on 2010-06-12
I have Acer Aspire 3820TG and was also strugling with the audio. I saw this thread and even though I am using debian lenny 2.6.32 I thought I should give your script a shot :)

At first it did not work, the driver simply wouldn't compile. I found out that headers were missing as reported in this bug here [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=540307](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=540307)

As a final desperate measure I did the following:

```

cd /usr/src
mv linux-headers-2.6.32-bpo.5-amd64 linux-headers-2.6.32-bpo.5-amd64.orig
mkdir linux-headers-2.6.32-bpo.5-amd64
cp linux-headers-2.6.32-bpo.5-amd64.orig/* linux-headers-2.6.32-bpo.5-amd64/
cp linux-headers-2.6.32-bpo.5-common/* linux-headers-2.6.32-bpo.5-amd64/

```

Then I run your script again. It worked like a charm. It seems that somehow the compilation process looks for the headers in the wrong folder. 

Thx for your script now I have headphones :]  And special thx to my husband who did most of the work-around process ;)

---

### Post by petunder on 2010-08-28
Thanks a lot! It works after upgrading! Headphones in 3820 are working now!
But there is problem with built-in microphone  - it doesn't work at all. Can anybody help me?

Tnx!

---

### Post by lidex on 2010-08-28
> **petunder said:**
> Thanks a lot! It works after upgrading! Headphones in 3820 are working now!
But there is problem with built-in microphone  - it doesn't work at all. Can anybody help me?

Tnx!

First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by petunder on 2010-08-29
> **lidex said:**
> 
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.


Thank you thank you thank you!!!! O-la-la!!! It works now!!! Great!!!
Fail was concluded in sliders: I ve tried to drag LEFT slider to zero and its not work. But if RIGHT slider downed to zero mic WORKS!!! O-la-la!!!

Acer Aspire 3820 ubuntu microphone issue solved!!!!

Thank you!!!

---

### Post by rogman on 2010-09-21
Thanks for the help, I managed to get my audio to output but now since I did this I have sound coming out of one speaker on the laptop, its like it thinks its a mono output. 

I don't find a great help on a google search so i'll ask here. 

My left speaker is working, my right is not. On output to my amp the audio does go to the left and right speaker.

I'm using the 5820TG.

Cheers
Rogman

---

### Post by redmorning on 2010-10-31
> **lidex said:**
> First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
*[COLOR="Red"]Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.[/COLOR]*

From alsa documentation:

thank you very much lidex, great solution, now i can use skype again (:

---

### Post by wjamoore on 2011-06-23
On my ACER 3820TZ I have tried all of the above and I cannot get the mic to work.  This is a pain in the jacksy because I need to use skype for work.

Mic works fine in windows 7 which I am now delighted not to have deleted.

This mic issue is ongoing for years now.  Why is there no fix?

cheers
WJAM

---

### Post by lidex on 2011-06-25
> **wjamoore said:**
> On my ACER 3820TZ I have tried all of the above and I cannot get the mic to work.  This is a pain in the jacksy because I need to use skype for work.

Mic works fine in windows 7 which I am now delighted not to have deleted.

This mic issue is ongoing for years now.  Why is there no fix?

cheers
WJAM

There is a fix, don't know why it doesn't work for you. Maybe you missed something. 
Does the mic work for anything other than skype? Is the option to allow skype to control audio disabled?
Is the google version an option?

---

### Post by wjamoore on 2011-06-25
I don't have microphone working in any application.  Neither does the jack socket mic.

The mic works perfectly in Windows 7

Any advise appreciated, but not the turn the left or right channel down.  Tried them all

Maybe something new?

cheers

WJAM

---

### Post by lidex on 2011-06-26
Gotta start from scratch. Please run the alsa-info script, choose the upload option, and post the link to the output.

---

### Post by wjamoore on 2011-06-26
Do you want this?


wjaelectron@wjaelectron-laptop:~$ uname -a
Linux wjaelectron-laptop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux

wjaelectron@wjaelectron-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC269 Digital [ALC269 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

wjaelectron@wjaelectron-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

wjaelectron@wjaelectron-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX
wjaelectron@wjaelectron-laptop:~$ 

Maybe something useful in there.

Thanks

WJAM

---

### Post by lidex on 2011-06-26
More would be better. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by wjamoore on 2011-06-27
Thanks...  Here you go
[http://www.alsa-project.org/db/?f=fd549a75d1974d9a488c680552ec46305023c46c](http://www.alsa-project.org/db/?f=fd549a75d1974d9a488c680552ec46305023c46c)

Wow there's a ton of stuff in there.

cheers

WJAM

---

### Post by lidex on 2011-06-27
> **wjamoore said:**
> Thanks...  Here you go
[http://www.alsa-project.org/db/?f=fd549a75d1974d9a488c680552ec46305023c46c](http://www.alsa-project.org/db/?f=fd549a75d1974d9a488c680552ec46305023c46c)

Wow there's a ton of stuff in there.

cheers

WJAM

Your model selection in alsa-base.conf is incorrect. Instead of acer try basic or auto.

---

### Post by wjamoore on 2011-06-28
Dude!

Now I have no sound.

Devices in pulse audio shows only dummy output device.

At least I had sound last night...  Tried basic and auto with no success and I can't see why I don't have sound

wjam

---

### Post by wjamoore on 2011-06-28
And another thing.   In preferences I have  default sound card.

If I pick that it says opening default sound card for a few seconds then vanishes

this might be significant i think

wjam

---

### Post by wjamoore on 2011-06-28
OK then....  the latest kernel seems to have screwed up the sound card.

I booted from previous and sound is back but mic is as before

WJAM

---

### Post by wjamoore on 2011-06-28
the default sound card in preferences is the same though.  Says starting default sound card for 15 seconds then vanishes

WJAM

---

### Post by wjamoore on 2011-06-28
well...  I don't believe it.  Now it's working.


I suspect 1 of these fixes is really a fix, but my update promptly screwed it back up.

Question is...  How did I fix it?  Or how do I find out to be more exact.

cheers

WJAM

---

### Post by rimez on 2011-07-05
I'm also having problems with the microphone on my 3820tg. I could use some help here. After going through the thread though, it's not obvious to me what exctly I should do in my case (even the last poster said he's not sure how he fixed it). 

[**Here's the output from the script**]("http://www.alsa-project.org/db/?f=00d3609baa0b2318d529d9287faa66e46676933c") that was mentioned (lots of data).

EDIT: Just to be clear, sound is working (i.e. speakers and headphones). It's just the input that doesn't work.

---

### Post by lidex on 2011-07-06
> **rimez said:**
> I'm also having problems with the microphone on my 3820tg. I could use some help here. After going through the thread though, it's not obvious to me what exctly I should do in my case (even the last poster said he's not sure how he fixed it). 

[**Here's the output from the script**]("http://www.alsa-project.org/db/?f=00d3609baa0b2318d529d9287faa66e46676933c") that was mentioned (lots of data).

EDIT: Just to be clear, sound is working (i.e. speakers and headphones). It's just the input that doesn't work.

Your default capture input is muted:
```
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 17 [55%] [9.00dB] [off]
  Front Right: Capture 17 [55%] [9.00dB] [off]
```
Use a mixer to unmute.
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by rimez on 2011-07-07
Thanks for the reply. 

I tried that but I don't see anything muted

[IMG]http://img7.imagebanana.com/img/vcbywmng/Selection_051.png[/IMG]

Any ideas?

---

### Post by lidex on 2011-07-07
That dashed line signifies the element is not selected for capture. You can probably fix it with gnome-alsamixer, but try this command first:
```
amixer sset Capture,0 cap
```

---

### Post by rimez on 2011-07-08
Hi Lidex,

Unfortunately it's still not working. Entering the command gave me this output:

```
amixer sset Capture,0 cap
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 28 [90%] [25.50dB] [on]
  Front Right: Capture 28 [90%] [25.50dB] [on]
```
it DID remove the dashes but it's still not working. 

Screen of Mixer:
[IMG]http://img7.imagebanana.com/img/utcz94dd/Selection_056.png[/IMG]



Here's what I see in the Gnome mixer app. 
[IMG]http://img7.imagebanana.com/img/b262sa8r/SoundPreferences_054.png[/IMG]

And finally, the gnome alsa mixer
[IMG]http://img7.imagebanana.com/img/d2q2t07j/GNOMEALSAMixer_057.png[/IMG]

---

### Post by lidex on 2011-07-08
What profile do you have selected on the hardware tab?

---

### Post by rimez on 2011-07-08
> **lidex said:**
> What profile do you have selected on the hardware tab?

[IMG]http://img7.imagebanana.com/img/dl7j1aa3/SoundPreferences_059.png[/IMG]

---

### Post by lidex on 2011-07-08
You'll need to select another profile, one with an input or duplex.

---

### Post by rimez on 2011-07-09
> **lidex said:**
> You'll need to select another profile, one with an input or duplex.

Yeah I know, I'm completely stupid, but how exactly do I do that :(

EDIT: Never mind... I'm not that stupid I guess. Found it. Now testing.

EDIT2: Seems to work. Thanks for that!!!!!

---

### Post by kri_vijay on 2011-09-24
----SPEAKER & MIC FIXED WITH KERNEL 2.6.38-11 x64-----------------

The issue appears to have been fixed with the new kernel update. & mic appear to be working ok

I have a Acer 4830t & was having "no sound" issue. So I followed alsa-hda-dkms-acer3830tg_0.1_all.deb from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/783582?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/783582?comments=all). I got the speaker to work but had some issue with crackling/cracking sound while using internal mic.

I recently upgraded from kernel 2.6.38-8 to 2.6.38-11. I decided to check if the alsa modules had any patches applied -- so I uninstalled alsa-hda-dkms-acer3830tg_0.1_all.deb & ran depmod & rebooted. Viola -- speaker, headphone jack work.

Further the internal mic seems to work without crackling/cracking sound

(FYI my
/etc/modprobe.d/alsa-base.conf has
#options snd-hda-intel model=acer
options snd-hda-intel model=targa-2ch-dig --> not sure if its needed)
--K

---

### Post by freeloader105 on 2013-01-11
> **lidex said:**
> I would try an alsa upgrade via the link in my sig. Then try the following.

Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

No help there replace acer with 'acer-aspire' or 'auto'

This needs a bump! I have spent many hours trying to fix my sound issue and this is the only thing that fixed it. Thanks!

---

