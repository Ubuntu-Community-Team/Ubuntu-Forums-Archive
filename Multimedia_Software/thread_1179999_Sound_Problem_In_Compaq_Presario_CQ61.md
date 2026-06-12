---
title: "Sound Problem In Compaq Presario CQ61"
date: 2009-06-06
forum: Multimedia Software
---

### Post by n00buntu on 2009-06-06
Hello,

I installed 9.04 on a Compaq Presario CQ61. All works great except that there is no sound. Tried following various posts, but no success. Here's
the output of aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0

What should I do?

Thanks & Bye,

TD

---

### Post by Admiral Nesquick on 2009-06-06
**Hold on tight before reading this !**

Your High definition audio hardware is actually the so feared Win hardware. Much work has, and is being done to get this hardware working in open source operating systems. And development is fast paced. So you should try the newest version of ALSA. And the only way to use the most new version is to compile it yourself. [url=https://help.ubuntu.com/community/HdaIntelSoundHowto]Here is the Ubuntu community documentation for doing this.[/url. **But be very careful and follow every step closely !**

Then this will be the easiest solution.

---

### Post by n00buntu on 2009-06-06
Hi,

  Many thanks for the quick and useful answer! I will follow these steps.

  Thanks & Bye,

  TD

---

### Post by nioreeves on 2009-08-21
Here are the solution for the audio
[http://ubuntuforums.org/showthread.php?p=7717667&highlight=compaq+cq61#post7717667](http://ubuntuforums.org/showthread.php?p=7717667&highlight=compaq+cq61#post7717667)

Parfect, it Works on my new compacq Presario CQ61 110ep.

---

### Post by nioreeves on 2009-08-21
Sorry, the correct link:
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

Here are the solution for the audio

Parfect, it Works on my new compacq Presario CQ61 110ep.

Ubuntu Jaunty 9.04 is coming by default with the version 1.0.18rc3 of Alsa so I decided to upgrade to the last verison wich is 1.0.20.

---

### Post by Valpskott on 2009-11-04
I have a Compaq Presario CQ61-225EO and I had sound through headphone jack but not from speakers.
The following solution fixed my audio problem in both Jaunty and Karmic Koala.


> sudo gedit /etc/modprobe.d/alsa-base.conf

At the end of the file, add these lines

> options snd slots=snd-hda-intel
options snd-hda-intel model=hp-hdx
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

---

### Post by wescorp on 2009-12-05
This fixed my issues perfectly.  Thank you.

---

### Post by coru-mx on 2009-12-16
> **Valpskott said:**
> I have a Compaq Presario CQ61-225EO and I had sound through headphone jack but not from speakers.
The following solution fixed my audio problem in both Jaunty and Karmic Koala.




At the end of the file, add these lines

Perfect, works on Compaq CQ61-200 ;)

---

### Post by save2 on 2010-01-09
Hi 
for my Compaq CQ61-120EJ all this worked only !! after upgrading (manual download and compile) ALSA driver to the latest one 1.0.20

all other forums advices didnt help.

now I have speakers working (before I had only headphone jack working).

---

### Post by lkraemer on 2010-01-10
Valpskott,
THANK YOU!  Your edits fixed Ubuntu 9.10 on my Daughters Compaq CQ61.

I had been searching everywhere for information on how to fix it.

lk

---

### Post by hans.mussmann on 2010-01-12
Cool the sound now works on the laptop!

Did both the 

[LIST]
[*]upgrade to small version .20 -- from .18
[*]and added the "options" to the alsa-base.conf
[/LIST]
I did a "sudo alsa force-reload" after the restart.

Tested it works by going the System>>Preferences>>Sound.

Thanks for the info.

---

### Post by km10982 on 2010-02-23
> **Valpskott said:**
> I have a Compaq Presario CQ61-225EO and I had sound through headphone jack but not from speakers.
The following solution fixed my audio problem in both Jaunty and Karmic Koala.




At the end of the file, add these lines

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-hdx
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

This worked great on my CQ61-420US. Thanks much!

---

### Post by qaseemibnusina on 2010-04-16
hello...m a linux newbies...i got same problem with my compaq CQ35...my speaker icon is unmuted...but there is still no sound at all...tq for any help....

---

### Post by pingu1 on 2010-07-06
Hi good ubuntu-people.
I actually went into a store to try the live cd on compaq Presario, but it would only boot up windows at first. I then finally got it to boot the live-cd (10.04), but after about 10 seconds with the pink-ish background (the first image you get on the live-cd) - it gave me a fullscreen of some commands/text and nothing more happened. My guess is that the cd I burned is bad?
Anybody agree with me?

Am I going to be happy if I buy a compaq presario for ubuntu use?
Or am I going to face tons of problems?

I am looking specially at this one:
[http://www.komplett.no/k/ki.aspx?sku=602561](http://www.komplett.no/k/ki.aspx?sku=602561)
You can check the specs by pressing the "utvidet info"-button...

---

### Post by cpmman on 2010-07-06
@pingu1 : Almost the same specs as my CQ61-427SA which works well (not sure about gaming as I don't do games).  

Make sure you load/install the W7 provided and make the three DVD disk restore disks.  You may want to use the Windows partition manager or (second choice)Gparted the partitions as they came on my machine with all four primaries utilised for the W7 installation including a recovery sector (not needed if you create the 3 DVD as above).

My Radeon 4200 driver was auto installed by System - Hardware Drivers ; the mic, sound and webcam worked immediately in Skype ; Flash was solved by Firefox - Tools - install Flash-aid (by lovinlinux - his football judgement may be suspect but he has no peer in Linux/Firefox add-ons).

Recommended for all but games.

---

### Post by pingu1 on 2010-07-06
Did the sound work instantly for you, without work-around?

---

### Post by cpmman on 2010-07-06
> **pingu1 said:**
> Did the sound work instantly for you, without work-around?

Yes - just had to set sound preferences as they start off with system sounds muted and output sounds at about 60%.

---

### Post by pingu1 on 2010-07-06
Sounds great. I am then going to buy a HP.... I am going to bring a cd and a USB-stick to a store today just to check that there aren't any major hickups... last time I tried a live-cd in a store - I didn't even get the "try ubuntu without changes"-menu...

---

### Post by pingu1 on 2010-07-06
I am sorry to ask, but I have to:
How do you make a DVD/CD to recover/re-install windows 7 ?
I ask because the computer doesn't come with a Win 7 cd.... I really couldn't care less,
but since I have paid for the motherf/#¤ I would like to have it... ...

---

### Post by cpmman on 2010-07-06
> **pingu1 said:**
> I am sorry to ask, but I have to:
How do you make a DVD/CD to recover/re-install windows 7 ?
I ask because the computer doesn't come with a Win 7 cd.... I really couldn't care less,
but since I have paid for the motherf/#¤ I would like to have it... ...

The instructions that come with the CQ61 not only tell you how to make the recovery dvds but sensibly **recommend** it.  It is on a menu - simples.

Obviously you have to provide the blank discs.

---

### Post by pingu1 on 2010-07-06
I got the Compaq Presario CQ61 today. I've backuped windows, and installed 10.04.
The only annoying thing is that the wireless-button/indicator (the button right under the screen) flashes from red to blue constantly.... Does anybody know?

Edit: Just so that is said - I have searched the forum, but I only found a script to solve the situation... Anything better to solve it?
I would love the light to not work rather than flashing 100% of the time. If I disconnect - it stops... 
Please? Is it solved in 10.04 ? Updating now from installation...

---

### Post by pingu1 on 2010-07-07
After update - the light now flashes only when there is an active download/upload process.
I can live with that... ...

---

