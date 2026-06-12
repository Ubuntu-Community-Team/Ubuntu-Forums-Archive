---
title: "Issue with TVTuner"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by ZKjellberg on 2007-06-23
Hello, I have a **PCMCIA AVerMedia Cardbus Plus E501R TV Tuner** which I am trying to use with **TVTime**.

With some help from a friend, I have been doing the following:

I went to this page: [http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134) and tested many different drivers using the following scheme, replacing ## with different cards.

"rmmod saa7134_alsa
rmmod saa7134
modprobe saa7134 card=##"

I have tried almost every AverMedia ## listed on that page, but every time I have it give me 'TV, Composite1, Composite2, S-Video" And the console is always 'Composite2' but never has sound. The card seems to be #46 because I found this page(which is sadly in Russian.. :( [http://linuxtv.org/v4lwiki/index.php/AVerMedia_Cardbus_Plus_E501R](http://linuxtv.org/v4lwiki/index.php/AVerMedia_Cardbus_Plus_E501R)
The page seems to list the card as 'card=46'. The drivers for that seems to work better than the others due to the fact the blue light on the tv tuner turns on and it only gives the options to show 'TV, Composite1, and S-Video', except like the others, I am unable to get sound to work, and  oddly it lags a little when switching modes, whereas the other drivers never did that, and the tv tuner seems to be making a very low pitch beeping noise now. =|

I am new to Linux, so maybe those pages actually have the answers, but I am unable to resolve the issue myself.

---

### Post by Jose Catre-Vandis on 2007-06-23
Which version of Ubuntu are you using?
What happens when you try to tune with TVtime? Anything, or just a blue screen?
What do you mean by "console is always Composite2" ?
Does the card come equipped with a sound module or does it use your PC's sound facilities?
Does it work under Windows OK on the same machine?
what TV format do you need to use... PAL/NTSC/Secam ??
Did you try:
```
sudo rmmod saa7134
sudo modprobe saa7134 card=46 tuner=12
```

feedback with the output of the following:

```
lsmod
```
```
lspci -v
```
```
dmesg
```

It also looks like, from the wiki page, that new entries are needed in the saa7134 module, but this may be for an older kernel, with a more up to date kernel it may now be included?

This should start giving us clues as to where the problem lies...........

---

### Post by ZKjellberg on 2007-06-23
> 1.Which version of Ubuntu are you using?
2.What happens when you try to tune with TVtime? Anything, or just a blue screen?
3.What do you mean by "console is always Composite2" ?
4.Does the card come equipped with a sound module or does it use your PC's sound facilities?
5.Does it work under Windows OK on the same machine?
6.what TV format do you need to use... PAL/NTSC/Secam ??

1. Ubuntu 7.04, Feisty Fawn

2.TVTime shows my Nintendo Wii through the RCA cables plugged into the video card, except there is no sound. The input mode is set to as 'Composite1' and does not play any sound.

3.Composite2 showed up for almost every driver installed, which was odd to me, because the card only has 'coaxial, component, and s-video so I just found it odd that it was playing off composite2. When I use the #46 driver it plays on Composite1 and has no composite2 which seems more accurate.

4. I'm unsure of what you mean, but it is a pcmcia card which has the sound playing through the laptop's speakers.

5. I tested today, and it plays fine on Windows.

6. My tv is NTSC and is set to that mode in TVTime.

> sudo rmmod saa7134
sudo modprobe saa7134 card=46 tuner=12

I tested this, and it acts the same. Still no sound, but video works still.

Will post lsmod, lspci -v, and mesg shortly, pastebin acting really slow to me atm.

lsmod: [http://pastebin.com/934993](http://pastebin.com/934993)
lspci -v: [http://pastebin.com/934994](http://pastebin.com/934994)
dmesg: [http://pastebin.com/934995](http://pastebin.com/934995)

---

### Post by Jose Catre-Vandis on 2007-06-24
OK, it all seems tikety boo from the outputs you have posted. What SAA7134 usually does is create a second sound device, needed to issue forth sound from the card.

If you have a sound icon in your panel, right click and "open volume control"

from the dialog, go File>Change Device and select "SAA7134 (Alsa Mixer)"

Make sure you have Line-in or similar enabled and it does not have a red cross at the bottom and the levels are up @ 80%

Does this make any difference.

Alternately, do you have a sound out jack on the card? if so you may need to route this to your "sound in" on the PC to get sound ( I have a PCI card that requires you to connect a cable from the output on the card to the motherboard to get sound, it is not transferred via PCI)

Also, if you are simply trying to get your Wii working via RCA, can you run a direct sound cable from the Wii to the PC (workaround I know, but perhaps you are not pushing through any sound with the RCAs? Composite usually only carries video?)

---

### Post by david_2001 on 2007-06-24
> **ZKjellberg said:**
> Hello, I have a **PCMCIA AVerMedia Cardbus Plus E501R TV Tuner** which I am trying to use with **TVTime**.

Way back in February I became embroiled in a lengthy thread trying to persuade one of these cards to work.  We got there eventually - take a look at [http://ubuntuforums.org/showthread.php?t=352196](http://ubuntuforums.org/showthread.php?t=352196).  If you read to the end, that's where we got sound working.

---

### Post by Jose Catre-Vandis on 2007-06-24
> **david_2001 said:**
> Way back in February I became embroiled in a lengthy thread trying to persuade one of these cards to work.  We got there eventually - take a look at [http://ubuntuforums.org/showthread.php?t=352196](http://ubuntuforums.org/showthread.php?t=352196).  If you read to the end, that's where we got sound working.

david_2001

Great thread!  You have the patience of a saint and the perseverance of a migrating Wildebeest ! :D

This should provide the solution for ZKjellberg. :)

---

### Post by ZKjellberg on 2007-06-24
I'll check out that thread, thankyou.

---

### Post by ZKjellberg on 2007-06-26
I worked on the stuff in the thread, and used this command.

tvtime -d /dev/video0 -b /dev/vbi0 | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -

Sound seems to work, cept only for TV, which I can test soon.(Every time I boot up TVTime using that command, it destroys my ears with tv static noise. Not fun.) But, oddly component still is getting no sound. Going to troubleshoot it more. Ah well, good thing out of this is I'm learning linux. Troubleshooting is best way to learn.

*Update* Tried using tv, and tv doesn't work. =[ I have a cable box, and if the tv is on channel 3, it gets the digital signal, but the tv tuner gets no signal.

*~*~*~*~*~*~*

So, right now heres what i'm doing.

```
sudo rmmod saa7134_alsa
sudo rmmod saa7134_dvb
sudo rmmod saa7134
sudo modprobe saa7134 card=46 alsa=1
```

It gets component cable to show up as Composite1 but there is no sound.

```
tvtime -d /dev/video0 -b /dev/vbi0 | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -
```

Is supposed to get sound to work, but only seems to give me static with 'no signal' in tv mode, and video still works for my Wii, but no sound is coming through.

I tried this post here, but i'm unsure what its purpose is: [http://ubuntuforums.org/showpost.php?p=2161903&postcount=40](http://ubuntuforums.org/showpost.php?p=2161903&postcount=40)

The first command does nothing, the 2nd gives this > /etc/modprobe.d/alsa-base:# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
/etc/modprobe.d/alsa-base:install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
/etc/modprobe.d/alsa-base:options saa7134-alsa index=-2

And the third gives this: > /etc/modprobe.d/aliases:alias char-major-81-* videodev


I followed this thread to try to get sound to work: [http://ubuntuforums.org/showpost.php?p=2166610&postcount=46](http://ubuntuforums.org/showpost.php?p=2166610&postcount=46)

The file it created has this:
> ctl {
	alsactl1 {
		name hw:0
		comment 'Physical Device - Intel ICH6 with STAC9750,51 at 0xdfebfe00, irq 16'
	}
	alsactl2 {
		name hw:1
		comment 'Physical Device - saa7133[0] at 0x54000000 irq 17'
	}

---

### Post by Jose Catre-Vandis on 2007-06-26
How are you getting your component sound into your PC?
(You should have yellow for video, and red and white for stereo sound, yes?)

---

### Post by ZKjellberg on 2007-06-26
Yes, I am using RVG(Red, White, Yellow) for my console input into the tv tuner.

---

### Post by RayVad on 2007-07-22
I have had this error in Gentoo and solved it by loading the tuner driver befor the bttv driver.
But how is this been done in Ubuntu?
I have put it in /etc/modules but seems it is not working. Is it realy loaded befor the bttv driver?

[http://forums.gentoo.org/viewtopic-t...ime+sound.html](http://forums.gentoo.org/viewtopic-t...ime+sound.html)


I can confirm this by doing(in exactly this order!!):

rmmod bt878
rmmod bttv
rmmod tuner

then do:
modprobe tuner
modprobe bt878
modprobe bttv

End then the sound works!

Now we just need to find out how it can be done in Ubuntu automaticly....

---

