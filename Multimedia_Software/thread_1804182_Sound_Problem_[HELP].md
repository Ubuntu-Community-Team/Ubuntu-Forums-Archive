---
title: "Sound Problem [HELP]"
date: 2011-07-14
forum: Multimedia Software
---

### Post by fileSnack on 2011-07-14
Hello all, i am new to this forum :) 

Few days ago i installed ubuntu 11.04 on my PC everything is fine but no sound at all, I am going to youtube and playing a video, a video started playing but no sound, i have just installed ubuntu restriced extras bun not working.. so can you help me, i really need sound.. 

Please i can't browse on internet without sound..:(

---

### Post by jerrrys on 2011-07-14
can you play music with your media player?  have you been to System>preferences>sound to see if you are muted?  and what kind of PC is this?  and welcome to the forum :)

---

### Post by mikewhatever on 2011-07-14
The first step is to make sure that the volume is not all the way down or that the Mute box is not checked. If that's not the problem, you'll need to post a moderate amount of technical info identifying you sound card. Open a terminal window and post the output of the **aplay -l** command.

---

### Post by fileSnack on 2011-07-14
@jerrys 

> can you play music with your media player? have you been to System>preferences>sound to see if you are muted? and what kind of PC is this? and welcome to the forum 

Yes i can play a music or video, i always go to the System>Preferences>Sound but isn't muted... What to do because i am new to Ubuntu..

@mikewhatever

> The first step is to make sure that the volume is not all the way down or that the Mute box is not checked. If that's not the problem, you'll need to post a moderate amount of technical info identifying you sound card. Open a terminal window and post the output of the aplay -l command.

Yes i checked many times but sound isn't muted. Ok i just write on terminalaplay -l and shows to me that: 
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``` 

Can you tell me what to do? 

@markfinned 

> Make sure that a sound device is installed on your computer; if one isn't, just install one. In most cases, Windows will automatically detect the new hardware and install the necessary software drivers.

Thanks for the reply! Well i don't know if sound device is installed. In my PC i was running Windows and i remove complete Windows and installed Ubuntu 11.04 everything works perfectly except sound... 

Help me people:confused:

---

### Post by lidex on 2011-07-14
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by fileSnack on 2011-07-15
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Thanks for the reply lidex 

Actually i use that command and here is my Alsa information : 
```
http://www.alsa-project.org/db/?f=0a5c7a0923c08e338d8b85dc1b7fd1374a307c8e
```

Can you help me now ? 

Thanks

---

### Post by fileSnack on 2011-07-15
Anyone can help me? i want a sound :(

---

### Post by rickytikki on 2011-07-15
try looking at the hardware in sound prefrences and make sure the right hardware is on and disable any other thats not working

---

### Post by fileSnack on 2011-07-15
> **rickytikki said:**
> try looking at the hardware in sound prefrences and make sure the right hardware is on and disable any other thats not working


Now i am to the hardware tab on Sound Preferences and they are three: 

Analog Stereo Input
Analog Stereo Output
Analog Stereo Duplex 

What to choose? 
I try everyone but again no sound.

---

### Post by lidex on 2011-07-15
Open alsa-base.conf:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Remove this line:
```
options snd-hda-intel model=generic
```
Change this line:
```
options snd-hda-intel model=auto
```
To this:
```
options snd-hda-intel model=w810
```
Save. Close. Reboot.

---

### Post by fileSnack on 2011-07-16
> **lidex said:**
> Open alsa-base.conf:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Remove this line:
```
options snd-hda-intel model=generic
```
Change this line:
```
options snd-hda-intel model=auto
```
To this:
```
options snd-hda-intel model=w810
```
Save. Close. Reboot.

Thanks for your reply but doesn't work. 

I open alsa-base.conf and do exactly what you say but stil no sound...:(

Please help me:(

---

### Post by fileSnack on 2011-07-16
Anyone can help me? I really need for you help..

Please i want sound..

---

### Post by fileSnack on 2011-07-17
Please help me i really need for sound..
Sorry for double post.;)

---

### Post by lidex on 2011-07-17
> **fileSnack said:**
> Please help me i really need for sound..
Sorry for double post.;)

Are you rebooting after those changes and checking levels in alsamixer as well as settings in 'Sound Preferences'?
Try changing w810 to z71v

---

### Post by fileSnack on 2011-07-25
> **lidex said:**
> Are you rebooting after those changes and checking levels in alsamixer as well as settings in 'Sound Preferences'?
Try changing w810 to z71v


Still sound not working, i changed w810 to z71v but now work. 

what to do?

---

### Post by lkjoel on 2011-07-27
> **fileSnack said:**
> Still sound not working, i changed w810 to z71v but now work. 

what to do?
Try Sound Troubleshooting in my signature.

---

### Post by JayPeeJay on 2011-07-27
Wait.... no sound at all, or just on the internet?  Almost all sound sources of the internet these days require Flash, which does not work very well in Firefox.  Yes, there are work a rounds if you feel like searching through backports for old Flash versions, or trying out Flash replacers that don't work quite right.  The easiest solution is to:

Switch your web browser.

I use Sea monkey (also Mozilla strangely enough), and that solved ALL of my flash issues.

---

