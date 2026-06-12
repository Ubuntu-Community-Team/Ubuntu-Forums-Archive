---
title: "Problem with Playing music in Ubuntu 10.10"
date: 2010-10-23
forum: Multimedia Software
---

### Post by $uraj on 2010-10-23
Am having problem with playing music with Ubuntu 10.10. Ubuntu 10.04 had no problem. I downloaded VLC player too but still the problem exists, that to more than the movie player.. tried Rhythmbox music player too.. same problem.. if anyone knows solution to the prob pls help.

Problem is: Music wont play properly, instead breaks at some point. skips some 2-3seconds then continues. again it repeats.. for example, playing music from a badly scratched CD or DVD !!!!! but the music file am trying to play is in hard disk.. Its playing well in Windows 7..

---

### Post by cascade9 on 2010-10-23
I'd guess that you dont have ubuntu-restricted-extras installed. 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

If that isnt the problem, then more information would help.

---

### Post by $uraj on 2010-10-23
Thanks a lot.. after installing the restricted packages, i rebooted.. Now everything is working superb :)

---

### Post by cascade9 on 2010-10-24
Good, it worked. 

Since this is fixed, its a good idea to mark the theread 'solved'- look above the 1st post, find 'thread tools', click it and then select 'solved' ;)

---

### Post by $uraj on 2010-10-24
hey.. but again its not working :( . It will play clearly untill i use my laptop(i mean, typing text or using touchpad) if i stop using touchpad, the next second the music gets stuck.. and if i disturb the touchpad, music will play clearly.. :(

---

### Post by Robert Lutken on 2010-10-24
[FONT="Palatino Linotype"][FONT="Georgia"]I'm having the same problem, my sound system is configured correctly because i can hear the welcome sounds and when i close windows i get a sound, when i try playing music through a media player i get nothing or broken up sounds also i have Ubuntu restricted extras installed.[/FONT][/FONT]

---

### Post by Robert Lutken on 2010-10-24
Ive managed to solve my problems by fiddling around with the sound preferences System>Preferences>Sound then click on the hardware tab and play around with the "settings for selected device", change the profile and you might find this fixes your problem.

---

### Post by $uraj on 2010-10-24
Ok.. I changed to "Analog Stereo  Output" instead "Analog Stereo Duplex". Right now its playing properly.. Will try a reboot now.. and will update the results soon :)

---

### Post by $uraj on 2010-10-24
no... again the same problem.. first song plays well.. second gets stuck frequently :(

---

### Post by cornish12 on 2010-10-24
I am having the same prob. Tried the above suggestions but didn't fix things.

---

### Post by kunalchakra on 2010-10-25
Yeh I am also having the same problem:(

---

### Post by lidex on 2010-10-25
There have been issues with this plugin:
```
gstreamer0.10-pulseaudio
```
Try uninstalling it.

---

### Post by $uraj on 2010-10-26
uninstalled 

gstreamer0.10-pulseaudio 
from synaptic package manager.. but still the problem persists :(

---

### Post by clickwir on 2010-10-26
I and several others seem to be having lots of audio problems with Maverick. 

Even after doing a fresh install, my sound doesn't work right. Sometimes I get choppy sound, most of the time I get nothing. I thought it was to do with my ATI HDMI card, but as far as I can tell, I've disabled and blacklisted it every which way. But still audio problems. :mad:

---

### Post by $uraj on 2010-10-27
So, this issue with audio seems to be found with many ubuntu users. Developers and debuggers please find a solution to solve this problem with playing audio. 

Also, playing video on Ubuntu 10.10 has the same type of problem. :(

---

### Post by $uraj on 2010-10-27
Again encountered another issue.. Even the videos from youtube face the same problem.. i mean even the video streaming is also affected.. 

This issue should be solved soon to stop users migrating or using windows OS to watch their favorite video, or to listen to their favorite music.

---

### Post by $uraj on 2010-10-27
Again encountered another issue.. Even the videos from youtube face the same problem.. i mean even the video streaming is also affected.. 

This issue should be solved soon to stop users migrating or using windows OS to watch their favorite video, or to listen to their favorite music.

---

### Post by lidex on 2010-10-27
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by $uraj on 2010-10-28
did it.. i guess there is no problem with hardware. Ubuntu 10.04 was working awesome..!!! But don know what happened to Ubuntu 10.10. Even i cant stream videos on facebook and youtube.. May be, the OS is failing to retrieve music file properly on time. Sometimes the system monitor too pauses. when i disturb the mouse, the graph starts moving, if i stop disturbing the mouse, again the same problem(pauses)[Note: This system monitor pausing problem wont occur frequently as the problem with music and video].

May be some process is getting idle.. so.. when i disturb the mouse, the music and video plays correctly. if i stop using the mouse, problem reoccurs. :(

---

### Post by lidex on 2010-10-28
> **$uraj said:**
> did it.. i guess there is no problem with hardware. Ubuntu 10.04 was working awesome..!!! But don know what happened to Ubuntu 10.10. Even i cant stream videos on facebook and youtube.. May be, the OS is failing to retrieve music file properly on time. Sometimes the system monitor too pauses. when i disturb the mouse, the graph starts moving, if i stop disturbing the mouse, again the same problem(pauses)[Note: This system monitor pausing problem wont occur frequently as the problem with music and video].

May be some process is getting idle.. so.. when i disturb the mouse, the music and video plays correctly. if i stop using the mouse, problem reoccurs. :(

Did you file a bug report and, if so, would you provide a link please?

---

### Post by $uraj on 2010-10-29
ya.. sure.. 
below i have pasted the link where i reported the bug..
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/667609](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/667609)

---

### Post by lidex on 2010-10-30
> **$uraj said:**
> ya.. sure.. 
below i have pasted the link where i reported the bug..
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/667609](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/667609)

I appreciate you taking the time and effort to do this. Ubuntu will be better for it. I am trying to get as much feedback as possible to the devs  so we can get this fixed and not have to rely on workarounds.

---

### Post by clickwir on 2010-10-31
Check what kind of sound card you are using. I have been trying everything for the past week to get my sound working. Did some googling around tonight and found many others are having trouble with X-Fi cards. I have an X-Fi. 

I took it out and replaced it with an old (but reliable) Diamond Monster Sound (ES1968) and I had sound on startup. Nothing needed to be done. It just works. 

Don't know what you have, but if you have an X-Fi, try something else. I think there are severe issues with the X-Fi series right now. Mine worked fine in 10.04. No problems at all. Flawless. Got to 10.10 and now I see issues. It started out ok, then it got choppy... then nothing. But sound is working ok now.

---

### Post by niedxwiedx on 2010-11-01
I have the same problem as You. It's a fresh install of Ubuntu 10.10. I can hear music and watch videos from different sources (Youtube, Totem, Rhythmbox), but very frequently it loops till i move mouse or type something. When it loops whole screen freezes. I have Intel HDA.

---

### Post by niedxwiedx on 2010-11-01
update:

After installing NVidia graphic drivers endless loops are over. Now there is only sound stuttering

---

### Post by cgha on 2010-11-14
I think it is not the fault of audio, it's the fault of power management of idle state. 
It infeluence not only the audio,vedio,but also like the download ,update and so on. When your pc's mouse,keyboard,touchpad are in idle state,then this problem happens! For example,the download pause, the music plays ugly!
So where to set the time the pc goes into idle state??
I've tested ubuntu9.10 10.10,they both happens.
Someone here saied the 10.04 is ok, i'll try to test it.

Chris:confused:

---

### Post by cgha on 2010-11-14
10.04 works for me.
Next time i will think twice before i switch to *.10 version of ubuntu. Thanks!

Chris

---

### Post by cgha on 2010-11-14
Still has some problem, first ,the download still need i to keep it alive peredically by move mouse or hit keyboard, second ,during play music ,it will resume after misfunction but not like in 10.10(repeat),i think it's time to give up for my laptop. May be i should try centos for alternation.

Chris

---

### Post by mattro2.0 on 2011-02-21
So, it looks like this problem was dropped in November without a resolution. 

I'm having the same problem with one of my machines. That is, Ubuntu 10.10, all media players randomly skip for a couple of seconds every once in a while. 

Did anyone find a solution?

---

### Post by mattro2.0 on 2011-02-21
Never mind the last question. I checked to see if ubuntu-restricted-extras was installed, but it was not (thought I did that with the install.)

Restricted extras fixed the problem.

---

