---
title: "Sound-ly Frustrated"
date: 2010-07-10
forum: Multimedia Software
---

### Post by mlhudson on 2010-07-10
So, I've got a great Acer Aspire 7736. Seems to have a RealTek ALC888 card & Intel HDA. 

I've upgraded Alsa.
I've used the Drivers at the RealTek site.
I've checked alsamixer over and over and over.

Yet, currently I cannot get sound through the headphone jack. 

Originally, I had problems w/ headphone/speakers playing simlutaneously. Somewhere in my adventures I fixed that, but then only one app would use sound during a login (UGH). So, I kept poking...as all good linux users do...now I'm afraid I've totally wonked it.

I'll put all pertinent alsa-info up [here]("http://www.alsa-project.org/db/?f=58850a92a9ea0edbf28a8d014a875cdbd81b621d") for an ubuntu-hero who will help!!

I guess I'm bright enough to really mess it up, but dumb enough not to have a clue how to fix it.

It has NEVER been able to recognize a headphone plugged in the jack automatically. I hope someone knows...

---

### Post by skyjacker on 2010-07-10
I use the standard sound software that comes with Netbook Remix. There is an icon for "Indicator Applet 0.3.7"  in the top bar, and if I left click it there is a "sound preferences" listed. By left clicking this and choosing "hardware", it lists all of the available hardware attached to my laptop. I can choose the one I want to use (i.e headphones, external speakers, etc.) Hope this helps...

---

### Post by mlhudson on 2010-07-10
For me, switching to headphones produces no sound at all. Only the Speakers work. Thanks for that suggestion, but no joy there. :(

---

### Post by lidex on 2010-07-10
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer-aspire-7730g 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by mlhudson on 2010-07-10
Now no sound at all. See alsamixer screenshot.

 

> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer-aspire-7730g 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by lidex on 2010-07-10
Is that the soundcard you want to use? Press F6 in alsamixer to select. What is that USB device?

Try changing that line in alsa-base.conf to this:
```
options snd-hda-intel model=acer
```

---

### Post by mlhudson on 2010-07-10
I will give it a go. The USB device I believe is my webcam w/ integrated mic. Sharp eyes! I'll post back re: changing to simply acer.

---

### Post by mlhudson on 2010-07-10
> **lidex said:**
> 
Try changing that line in alsa-base.conf to this:
```
options snd-hda-intel model=acer
```

Still no joy. AlsaMixer is still not showing me anything to change on Headphones. Please say there are more tricks to try :D

---

### Post by lidex on 2010-07-10
From this thread:
[http://ubuntuforums.org/showthread.php?t=1366524]("http://ubuntuforums.org/showthread.php?t=1366524")
> **MrPotter said:**
> [LEFT]Hi lidex,

here can you find the output from alsa-info script:
[http://www.alsa-project.org/db/?f=2939ed08b62ec9e77435b078ee3aa224b21974e9](http://www.alsa-project.org/db/?f=2939ed08b62ec9e77435b078ee3aa224b21974e9)

Thank's for your support! ;)

**+++++Update++++**

Now it works! I deleted the options-line in the config file completly. Then I changend in the sound preferences in the output-tab the "connection link" to "Headphones". After I turned up the volume from channel "Front" with alsamixer, I can change between speakers and headphones without any problem. [/LEFT]
*I see your 'Front' is muted*
Another:
[http://ubuntuforums.org/showthread.php?t=1485335]("http://ubuntuforums.org/showthread.php?t=1485335")

---

### Post by mlhudson on 2010-07-10
Per the other user, I deleted the line completely from my conf file. I can confirm I have sound again in the speakers. But, still nothing at all from headphones. 

As I mentioned above, I may have wonked them in my previous attempts to get them functioning correctly. I've been at this issue a while now. 

So, speakers = working great, headphones = no joy.



> **lidex said:**
> From this thread:
[http://ubuntuforums.org/showthread.php?t=1366524]("http://ubuntuforums.org/showthread.php?t=1366524")

*I see your 'Front' is muted*
Another:
[http://ubuntuforums.org/showthread.php?t=1485335]("http://ubuntuforums.org/showthread.php?t=1485335")

---

### Post by Yellow Pasque on 2010-07-10
Nvm

---

### Post by mlhudson on 2010-07-16
Ok, so I have NOT solved the problem completely. However, I copied my Home folder out to an external drive and reinstalled 10.04. I got sound back--but in both headphones & speakers (first problem that sent me down this rabbit hole). No amount of fiddling with ALSA sound options or /etc/modprobe.d/alsa-base.conf changed this.

SO, I ran the upgrade script to ALSA 1.0.23, and this gives me back control through the sound panel to manually change from headphones to speakers.

I am not thrilled that there is no automatic headphone detection that works for me, but this is better than no sound.

I am STILL also suffering from PulseAudio issues where only one app gets the sound at a time, but I guess I'll save that for another post. 

Consider this post unsolved, but closed.

---

### Post by lidex on 2010-07-17
> **mlhudson said:**
> Ok, so I have NOT solved the problem completely. However, I copied my Home folder out to an external drive and reinstalled 10.04. I got sound back--but in both headphones & speakers (first problem that sent me down this rabbit hole). No amount of fiddling with ALSA sound options or /etc/modprobe.d/alsa-base.conf changed this.

SO, I ran the upgrade script to ALSA 1.0.23, and this gives me back control through the sound panel to manually change from headphones to speakers.

I am not thrilled that there is no automatic headphone detection that works for me, but this is better than no sound.

I am STILL also suffering from PulseAudio issues where only one app gets the sound at a time, but I guess I'll save that for another post. 

Consider this post unsolved, but closed.
See this:
[http://ubuntuforums.org/showthread.php?t=1455816]("http://ubuntuforums.org/showthread.php?t=1455816")

---

### Post by MikeyDL on 2010-08-11
I have the same model with similar problems.  Only I didn't get sound out of both speakers and headphones, just speakers.  I upgraded to ALSA 1.0.23 but still no joy.  I can go into preferences -- output and then select analog headphones but still no sound output.  Running 32 bit not 64 Ubu. 

So thinking I was clever I went out and brought a set of Logitech USB headphones.  However, plugging those in cause the system to crash/freeze.  I"m going to use the magic -r option with the Alsa script and see if I can use the USB Logitech headphones without crashing the system.

Ugg...

---

### Post by MikeyDL on 2010-08-12
Well I did the -R switch on the ALSA upgrade and no luck for me regarding the headphones.  I can choose headphones in the output preferences but it doesn't output sound to them.  

The USB logitech PRO headphones don't crash the system anymore but don't seem to be recognized either.  I guess I'll research to see if I can get them working.

---

### Post by lidex on 2010-08-14
> **mlhudson said:**
> Ok, so I have NOT solved the problem completely. However, I copied my Home folder out to an external drive and reinstalled 10.04. I got sound back--but in both headphones & speakers (first problem that sent me down this rabbit hole). No amount of fiddling with ALSA sound options or /etc/modprobe.d/alsa-base.conf changed this.

SO, I ran the upgrade script to ALSA 1.0.23, and this gives me back control through the sound panel to manually change from headphones to speakers.

I am not thrilled that there is no automatic headphone detection that works for me, but this is better than no sound.

I am STILL also suffering from PulseAudio issues where only one app gets the sound at a time, but I guess I'll save that for another post. 

Consider this post unsolved, but closed.
I would venture a guess that now you are back to the default configuration, the alsa-base.conf tweak should work. You could try it anyway.

---

