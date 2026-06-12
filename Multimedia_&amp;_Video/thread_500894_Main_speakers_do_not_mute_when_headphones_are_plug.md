---
title: "Main speakers do not mute when headphones are plugged in"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by jmcantrell on 2007-07-14
My machine is a Dell Dimension XPS gen 4 with an audigy sound card (emu10k1). I'm using ubuntu feisty with alsa version 1.0.13.

When I plug headphones in to the front headphone jack sound comes through them, but sound continues to play through the main speakers. There isn't an option in the mixer settings for 'headphone jack sense'.

I've been trying to find a solution to this since the release of breezy. PLEASE HELP :-)

---

### Post by pontifex3 on 2007-07-15
help pleeeeease, i have the same problem

---

### Post by jmcantrell on 2007-07-15
out of curiosity.. what kind of machine are you using? same symptoms?

---

### Post by Mr. Win on 2007-07-17
Im using a Compaq R3000 and I'm having the exact same problem.

---

### Post by Mr. Win on 2007-07-17
> **Mr. Win said:**
> Im using a Compaq R3000 and I'm having the exact same problem.

Wow... Really simple problem to solve. 

Right click your speaker/volume icon

Then mute master. 

volia problem solved!

---

### Post by Cold-Gin on 2007-07-17
- Right click on your speaker icon (upper righthand corner of your desktop)
- Choose "Open volume control"
- Click the Switches tab
- Check "Headphone Jack Sense"

---

### Post by jmcantrell on 2007-07-17
did you even read my original post?...

"There isn't an option in the mixer settings for 'headphone jack sense'."

---

### Post by jmcantrell on 2007-07-17
that isn't the problem. it's easy enough to hit the mute button, but when every other OS on the planet works as expected, it's kind of ridiculous to have to manually mute the master channel.

---

### Post by jubjubrsx on 2007-07-17
damn it took me forever to remember what file it was to edit......

sudo gedit /etc/modprobe.d/alsa-base


add the line

 options snd-hda-intel model=laptop

where u see all the other options...restart X should work fine....

thinking about it u might have to edit the option a touch but....god damniit sliced my fimger hard to type....u can fingure it out

---

### Post by jmcantrell on 2007-07-19
i'm not sure if that would work. my card is an audigy and the driver emu10k1, and it's not a laptop.

---

### Post by Doytch on 2007-07-24
I want to give this a bump.  I have the same problem, but with the integrated Realtek ALC889A audio on my GA-P35-DS3R.  No jack sense in my eq either.

---

### Post by yamraaj on 2007-07-27
same issue...please help. sound card is different though

$ lspci | grep -i audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xc0000000 irq 17
$ dpkg -l 'alsa*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  alsa           <none>         (no description available)
ii  alsa-base      1.0.13-3ubuntu ALSA driver configuration files
un  alsa-oss       <none>         (no description available)
ii  alsa-utils     1.0.13-1ubuntu ALSA utilities

---

### Post by doutdes on 2007-07-27
Have the same issue, unable to deactivate the main speakers when having the headphones plugged in.

I have a dv2000z
the sound is HDA Nvidia, using ALSA

and in the Switch tab in the volume control the LineIn is checked

---

### Post by yamraaj on 2007-07-28
problem escalated!!! just got some new nvidia drivers installed by the hp servce guys (for winxp). since then sound has totally vanished :( someone pl help!!!

---

### Post by ACGarib on 2007-08-07
I have the same problem with my Dell Vostro 1500. my sound card info is ```
~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

In my volume control settings, it says I have a sigmatel STAC9205 sound card.

I can't mute the speakers when I have headphones on. The only option in the volume control is playback. If I hit mute, everything is muted.

---

### Post by jmcantrell on 2007-08-12
I'm willing to try to find a solution to this myself, if someone can give me a little guidance on where to look. Either way, I'd really like to get this solved.

---

### Post by ayu on 2007-08-14
> **ACGarib said:**
> I have the same problem with my Dell Vostro 1500. my sound card info is ```
~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

In my volume control settings, it says I have a sigmatel STAC9205 sound card.

I can't mute the speakers when I have headphones on. The only option in the volume control is playback. If I hit mute, everything is muted.

How did you get the speakers working?  I have the 1400 (similar to inspiron 1420) and got audio working via dell's wiki [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly).  Speakers turn off when I plug headphones into the left jack.  Btw, dell's method changes the device to HDA intel (alsa) vs the original sigmatel (OSS)

---

### Post by adlaiff6 on 2007-08-25
Same problem, Dell Inspiron E1505

```
 $ lspci
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

```
 $  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

```
 $ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefffc000 irq 19
```

```
 $ dpkg -l 'alsa*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
un  alsa                        <none>                      (no description available)
ii  alsa-base                   1.0.14-1ubuntu1             ALSA driver configuration files
un  alsa-oss                    <none>                      (no description available)
ii  alsa-tools                  1.0.14-1                    Console based ALSA utilities for specific hardware
ii  alsa-utils                  1.0.14-1ubuntu3             ALSA utilities
```

I've tried the following options after 'options snd-hda-intel' in /etc/modules.d/alsa-base (and have done a full-reboot after changing to each one):

```
model=dell
model=laptop
model=dell-laptop
model=ref
```

None of them have worked (even without that line at all).  I'm running gutsy, and it was only a couple days ago (presumably after an update) when the problem started occurring.

Does anyone have any ideas, or a link to a bug report that we can go provide data for?

---

### Post by jmcantrell on 2007-08-25
if it was working before an update, and now it doesn't (and you're using gutsy, which hasn't even been released), then it really doesn't apply to this thread.

---

### Post by strabes on 2007-08-25
I'm using Gutsy Tribe 5. Same problem with a dell inspiron E1705. > 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

---

### Post by benbelly on 2007-08-27
I have this problem using Feisty Fawn.  I have an Asus P5N32-E SLI.  This works in windows (dual boot for games), but not in Linux.  I don't have the above mentioned options in my volume control either.  -sigh-

---

### Post by jppinto on 2007-10-16
I have a new HP pavillion dv2000 with Feisty. And I have the same problem. Sound works great. Mic works great. But, when I plug the phones the main speakers continue to play.

... any solution is welcomed :)

---

### Post by BoomShaka on 2007-10-16
bump.
edit: [http://ubuntuforums.org/showthread.php?t=485605](http://ubuntuforums.org/showthread.php?t=485605)
perhaps some helpfull info here... I am still looking :/

---

### Post by apauloisdead on 2007-10-17
Same problem here, if i check the headphones box, sound comes out the headphones and my laptop speakers.

---

### Post by ElVirolo on 2007-10-29
Same problem here : 

> elvirolo@elvirolo-laptop:~/Desktop$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


---

### Post by slimdanny on 2007-10-30
same issue here Dell Inpiron 1520
```

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

---

### Post by dmgthe2nd on 2007-10-31
This might fix the problem for some of you out there.  I had the same bug and this fixed it.

[http://ubuntuforums.org/showthread.php?p=3679576&posted=1#post3679576]("http://ubuntuforums.org/showthread.php?p=3679576&posted=1#post3679576")

Good luck.

---

### Post by sscott on 2007-11-26
I had the same problem on my Dell Latitude D830.  I added the following in /etc/modprobe.d/alsa-base and it fixed it:

options snd-hda-intel model=auto

Read about it originally in this post: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93859)

---

### Post by ocarinahuff on 2008-02-05
Try installing linux-backports-modules and asound2-plugins.  That worked for me, I have a Dell Vostro 1500, have been using a 'crutch' solution that wasn't pretty to use for months.  I stumbled across this new solution while I was fooling around with Pulseaudio for Gutsy.

linux-backports-modules gets the sound working.  The asound2-plugins has some stuff in there that makes the headphones work right(it might be something like pulseaudio, or at least a piece of it.)

Don't worry, in the next release, the all-new Pulseaudio should make all these sound nightmares a passing dream.

:popcorn:

---

### Post by myddewji13 on 2008-02-06
I have the exact same prob...all the other solutions around dont seem to work (btw...i have a hp pavilion dv2708ca -dv200 series laptop)..

---

### Post by myddewji13 on 2008-02-07
edit** dv2000 series

---

### Post by myddewji13 on 2008-02-08
bump...anyone got a fix...

---

### Post by Hayke on 2008-02-09
> **jubjubrsx said:**
> damn it took me forever to remember what file it was to edit......

sudo gedit /etc/modprobe.d/alsa-base


add the line

 options snd-hda-intel model=laptop

where u see all the other options...restart X should work fine....

thinking about it u might have to edit the option a touch but....god damniit sliced my fimger hard to type....u can fingure it out


This solved the problem  on my Compaq C700![

```
lspci | grep Audio

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

---

### Post by bonusiso on 2008-03-23
i have the same audio device but the method you follow didn`t work. 

i have changed my notebook really recently, it`s a hp pavillion dv2700. 

it has 2 headphone jack, so i thought that could make a problem... 

i don`t know how to solve it?..

Does someone?

> $ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


---

### Post by myddewji13 on 2008-03-23
HEY,,,, i got a dv2700 too... i tried everything but it didnt help... although the problem is fixed in hardy!!! (im running the beta with no probs... :D )

---

### Post by bonusiso on 2008-03-23
thanks for great support, i m downloading it now!.. :D

---

### Post by hanswehr on 2008-03-24
Hello all. I'm having exactly the same problem. I have an Advent laptop and like the other users I have no option called 'Headphone Jack Sense'. Muting the main volume doesn't work - it just mutes the headphones too. I don't know anything about computers and wouldn't know how to do the file edit thingy above. So if someone could give me an extremely simple, idiot-proof solution, that would be amazing! Cheers

---

### Post by bonusiso on 2008-03-25
Hello,

in order to do the file edit thing follow these steps below:

Open The terminal (at the very top and left corner of screen Aplications/Accesories/Terminal)

then copy the line below;
sudo gedit /etc/modprobe.d/alsa-base

and paste it into terminal by right click / paste or with mouse wheel click (crtl+V doesn't work)

then a text editor will show up, add the line below to the end of file
options snd-hda-intel model=laptop

then close the file

to restart X 
Ctrl + Alt + Backspace

for me its not working!!!
i hope it will work for you

---

### Post by fleque on 2008-04-07
Hi,

I had the same problem on my ASUS V1S and wanted to mention two URLs that helped me very much: 

The first one: [http://forum.chip.de/linux/ubuntu-7-10-linux-kernel-2-6-22-14-generic-gnome-2-20-1-a-996437.html](http://forum.chip.de/linux/ubuntu-7-10-linux-kernel-2-6-22-14-generic-gnome-2-20-1-a-996437.html) suggested to install alsa alsa-driver-1.0.15 (instead of alsa-driver-1.0.14 that ships with 7.10 (Gutsy)) it also includes a nice sequence of commands to download, compile and install the module

The second one: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) pointed me to the  where I could find the correct option for the 'option snd-hda-intel model=MODEL' option.

check your model with 
```

$ cat /proc/asound/card0/codec\#*|grep Codec
Codec: Realtek ALC660-VD
Codec: Generic 1543 Si3054

```
then see the ALSA documentation for the right option for you model (in my case ALC660-VD). The documentation for 2.6.22 kernels can be found here: [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

Strangely, though in my case - having an ASUS with - setting the option to 'asus' as suggested in the document, did not work. Setting it to 'lenovo' did work though ;-)

Regards
Alex

---

