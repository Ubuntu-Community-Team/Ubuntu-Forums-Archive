---
title: "Help with M-Audio Delta Audiophile 2496 setup"
date: 2010-07-28
forum: Multimedia Software
---

### Post by topbayder on 2010-07-28
Ok, so I have read a lot of other threads on here, other forums and other websites about this sound card and what you have to/can do to get it working.

To be completely honest I don't really understand what I have to do from reading what I have done so far and cant find a simple explanation anywhere. I am now quite confused and overwhelmed as I don't really know what 'pulse' or some of the other programs are that have been mentioned. 

I pretty much have got a fresh install of the newest Ubuntu (lucid lynx 10.04 LTS). So hopefully that will make things easier.

What I am really looking for (trying not to be too cheeky :)) is for someone who would be kind enough to explain a step by step of what to do please.

Thanks.

---

### Post by cchhrriiss121212 on 2010-07-28
**Technical info** (skip this if you are not interested):
The basic sound chain in Ubuntu looks like this: sound card>ALSA>pulse>software

ALSA is the muscle of the audio processing, and pulse is a sound server that works on top of ALSA. Previously many systems would just use straight ALSA, but pulse was introduced to add a few features and give a simple GUI. Unfortunately pulse has a longstanding bug that means it does not recognise your series (models using the ice1712 chipset) of sound card.

**Fix**:
First check the card is recognised, so put this into a terminal:
```
aplay -l
```You should see your card listed. Its a good idea to disable any onboard sound you have through your BIOS screen, if you haven't already.

Then open this file for editing:
 ```
gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
 ```
options snd-ice1712 model=audiophile 
```Save. Close. Reboot. Check your levels in alsamixer.
 ```
alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

Credit to lidex for posting this fix in [this thread]("http://ubuntuforums.org/showthread.php?t=1484371").

---

### Post by jblock312 on 2010-07-28
Like you, I've been trying to get my delta 2496 card working with a recent install of Ubuntu 10.04.
It used to work fine in 9.04.
One of the threads you probably read is:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/)

go to #30 in the thread, then in your terminal window type:
gksudo gedit  /usr/share/alsa/cards/ICE1712.conf
(make sure to leave a space between "gedit" and "/usr")

when the text window comes up, scroll down to "ICE1712.pcm.front.0"
add 2 lines at the bottom, as listed in #30:

slave.format S32_LE
slave.channels 10

save, close and reboot.
Now go to system>preferences>sound, look up the delta and you should now have analog options.

Worked for me. Good luck.

---

### Post by stuart1 on 2010-09-14
[]("http://ubuntuforums.org/member.php?u=948514")Thanks Jblock312 and Cchhrriiss121212 for the suggestions. I'm still having trouble with my audiophile 2496- recognised in Alsamixer, but ..... no sound. In systems/preferences/multimedia system selector, ICE1712 isn't even an option whatever plug in is specified. This is the last thing I need to stop me needing Windows!

Any other ideas?

Thanks.

---

### Post by Ruhani04 on 2010-09-26
This is in reference to 10.10 beta (maverick meerkat) and audiophile 24/96:
I already filed a bug report but I am pretty sure nothing will come out of it as this is a known problem for many years with pulseaudio and nothing has changed.
In 10.04 there has been posted in a previous bug report a workaround. However this seems to no longer work in 10.10.
In my opinion there are two solutions:
Disable or remove pulseaudio and only use ALSA. This has worked for me and all applications are supported with great sound.
Or disable or remove pulseaudio and install OSS4. Worked for me but not all applications fully support OSS4. This is definitely a more complicated approach.
I have no experience with Jack and therefore can't say if this would be a third solution.:wink:

---

