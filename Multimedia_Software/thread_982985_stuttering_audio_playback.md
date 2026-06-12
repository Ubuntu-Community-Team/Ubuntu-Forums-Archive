---
title: "stuttering audio playback"
date: 2008-11-15
forum: Multimedia Software
---

### Post by omarabbas on 2008-11-15
Hello,

i've been struggling with this problem for weeks... :the sound stutters when i play any video or mp3.
it started with flash content first, but now it happens when i attempt to play anything.
i have tried every guide i could find, i fixed pulse-audio, fixed alsa, and even converted to oss and back, but in all my attempts the problem stays exactly the same.
this started before i upgraded to intrepid and continued after the upgrade, even when i tried installing it from scratch, i still have the exact same problem :stuttering playback.

i have to add that i'm a complete newbie to linux so i don't really know if there are further information that i can add to this thread, but i follow instructions very well! 

thanks

---

### Post by omarabbas on 2008-11-16
bummer

---

### Post by m4lte on 2009-01-07
I have the same problem when playing music in Rhythmbox or Banshee. Flash (e.g. youtube) seems to work.

Using ubuntu 8.10.

Is there anything to do?

---

### Post by markbuntu on 2009-01-07
If you find the sound stuttering etc, you can try editing the /etc/pulse/daemon.conf file. At the end of the file are two lines like this:
```

;default-fragments = 8
;default-fragment-size-msec = 5

```
Change them to look like this :
```

default-fragments = 5
default-fragment-size-msec = 25

```
Save the file and restart Pulse Audio.
```

killall pulseaudio

pulseaudio -D

```

See if that helps.

---

### Post by Steve H on 2009-02-22
> **markbuntu said:**
> If you find the sound stuttering etc, you can try editing the /etc/pulse/daemon.conf file. At the end of the file are two lines like this:
```

;default-fragments = 5
;default-fragment-size-msec = 25

```
Change them to look like this :
```

default-fragments = 8
default-fragment-size-msec = 5

```
Save the file and restart Pulse Audio.
```

killall pulseaudio

pulseaudio -D

```

See if that helps.

Thanks for that, I was having similar problems with my m-audio 2496 stuttering when apps were running in the background. The settings you put there didn't quite work for me, but it put me on the right track. I've found another [thread]("http://ubuntuforums.org/showthread.php?t=1057649") advising and so ended up putting the settings as 25 for both and voila! no stuttering so far.

Thanks for the heads up!!

---

### Post by markbuntu on 2009-02-22
Well actually I did that backwards. sorry, but I am glad it got you one the right track

---

### Post by KaiFrost on 2009-02-24
> **markbuntu said:**
> If you find the sound stuttering etc, you can try editing the /etc/pulse/daemon.conf file. At the end of the file are two lines like this:
```

;default-fragments = 5
;default-fragment-size-msec = 25

```
Change them to look like this :
```

default-fragments = 8
default-fragment-size-msec = 5

```
Save the file and restart Pulse Audio.
```

killall pulseaudio

pulseaudio -D

```

See if that helps.

I have the exact problem. When I tired to do that fix above, this happens:"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again." Please help! This has been going on and on... the only way to make the stuttering to stop it to mute everything.

---

### Post by markbuntu on 2009-02-24
You need root permission to edit that file
Try

sudo gedit /etc/pulse/daemon.conf

btw, I wrote that backwards, you want

default-fragments = 5
default-fragment-size-msec = 25

---

### Post by KaiFrost on 2009-02-25
> **markbuntu said:**
> You need root permission to edit that file
Try

sudo gedit /etc/pulse/daemon.conf

btw, I wrote that backwards, you want

default-fragments = 5
default-fragment-size-msec = 25

My code was 

default-fragments = 4
default-fragment-size-msec = 25
And I changed it to

default-fragments = 5
default-fragment-size-msec = 25
And still the same problem... :(

---

### Post by Steve H on 2009-02-25
Have you looked around for other people with your particular sound card, and what settings work for them? Mine requires 25 for both settings and I'm running a M-audio 2496.

Also are any other processes eating memory or processor time? I noticed on my system that the sound probs were worse when bittorrent or BOINC was doing things in the background.

;)

---

### Post by KaiFrost on 2009-02-25
> **Steve H said:**
> Have you looked around for other people with your particular sound card, and what settings work for them? Mine requires 25 for both settings and I'm running a M-audio 2496.

Also are any other processes eating memory or processor time? I noticed on my system that the sound probs were worse when bittorrent or BOINC was doing things in the background.

;)
I have a HP Pavilion Laptop, and my drivers aren't popular so there kind've unknownish... heres a link to see my laptop:
[http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&dlc=en&cc=us&lang=en&product=3806991#](http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&dlc=en&cc=us&lang=en&product=3806991#)
Hope you guys can help :'(
[Edit]: Link directly to the specs:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01607717&lc=en&dlc=en&cc=us&lang=en&product=3806991](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01607717&lc=en&dlc=en&cc=us&lang=en&product=3806991)

---

### Post by Steve H on 2009-02-25
> **KaiFrost said:**
> I have a HP Pavilion Laptop, and my drivers aren't popular so there kind've unknownish... heres a link to see my laptop:
[http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&dlc=en&cc=us&lang=en&product=3806991#](http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&dlc=en&cc=us&lang=en&product=3806991#)
Hope you guys can help :'(
[Edit]: Link directly to the specs:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01607717&lc=en&dlc=en&cc=us&lang=en&product=3806991](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01607717&lc=en&dlc=en&cc=us&lang=en&product=3806991)

I'm not seeing any specific audio chip info on the specs page, just say audio = Lansing speakers. Do you know the make/model of the audio chipset?

---

### Post by KaiFrost on 2009-02-25
Um, I believe its Intel.
 	  IDT High-Definition Audio CODEC Driver: Thats the driver that I would need if I had vista on this computer. My volume options displays: "HDA Intel (Alas Mixer)"

---

### Post by KaiFrost on 2009-02-27
-Bump-

---

### Post by MarblePanther on 2009-02-27
Have you tried as suggested to change *both* to 25?

It worked for me, and I had the same problem.

---

### Post by m4lte on 2009-05-05
I tried setting default-fragments and default-fragment-size-msec to 8/10 (default), 5/25 and 25/25.
No success.

Any ideas what I can do? Not being able to listen to music is horrible!

---

### Post by Roger80 on 2009-05-05
i'm also having the same problem. i will try this one. thanks!

---

### Post by m4lte on 2009-05-05
In the discussion of this bug report ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627)) someone mentioned that the problem is fixed in some package that is in the proposed repositories. I didn't quite get which package, so I enabled the propose repos ([https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)) and downloaded all updates.
So far my sound is working well, but that might be coincidence. I'll test it for a while and then report back.


**EDIT:**
It didn't solve the problem for me :(

---

### Post by wpwend42 on 2009-05-28
I'm having the same problem in Banshee since upgrading to 9.04.  Very disappointing.  Everything always worked in previous versions of Ubuntu just fine.

---

### Post by m4lte on 2009-05-29
I recentyl installed 9.04 from scratch and now I don't have any audio problems any more. (Before, when I upgraded from 8.10 to 9.04 the problem was not solved)
I have no idea what was the reason. And it's obviously a big step to install the system from scratch :>

---

### Post by wpwend42 on 2009-05-29
Oh, yes, I did that too.  I had a lot of trouble going from 7.10 to 8.04 so I made sure to do a completely fresh install.

---

### Post by oogmsn on 2009-07-28
> **markbuntu said:**
> If you find the sound stuttering etc, you can try editing the /etc/pulse/daemon.conf file. At the end of the file are two lines like this:
```

;default-fragments = 8
;default-fragment-size-msec = 5

```
Change them to look like this :
```

default-fragments = 5
default-fragment-size-msec = 25

```
Save the file and restart Pulse Audio.
```

killall pulseaudio

pulseaudio -D

```

See if that helps.
Nice one..this problem been irritating me...since initially I thought it is about my NAS box setting that is causing the latency issue...fixed mine but using "25" as the value for both.

One thing still puzzling me...this stuttering issue will usually happens for me only after a period of time..for mine will be most of the time during my nights...anyone knows why?

---

### Post by oogmsn on 2009-07-28
ok just happened to hit on the stuttering for awhile just now :( ...but it was for a minute..keeping my fingers crossed!

---

### Post by igorzwx on 2009-07-28
there are also some evil kukies,
or something of the sort
see:

~/.pulse

---

### Post by oogmsn on 2009-07-28
That didnt work for me, suddenly starts to stutter again...so I'm suspecting that it is due to my ext partition where ubuntu is installed is lacking in space..had it for 5.5gb initially...have now repartitioned it for 15gb...rebooted, so far it seems ok...but keeping fingers crossed again!

Btw igorzwx - when I tried the command, it gives me: bash: /home/tutubu/.pulse: is a directory?
*Sorry am only a week old for ubuntu.

---

### Post by igorzwx on 2009-07-28
it is a hidden folder

View - in file manager

show hidden files

it is in your home folder

for me 

~/.pulse

is the same as

/home/igor/.pulse

"~/" is a kind of abbreviation

---

### Post by Xpander69 on 2010-01-08
old Thread but i was searching days how to fix sound stuttering with pulse and wine. theres a package wine with pulseaudio also, but this didnt want to compile with newer wine versions. so i searched for other options.

for me the working numbers where:
in /etc/pulse/daemon.conf

default-fragments = 25
default-fragment-size-msec = 4


tryed several other numbers also, still stuttered, but this seems to work fine. hope it helps someone.

---

### Post by Nicmyster on 2012-09-15
Hello, I tried the fixes in here and none of them helped.
Found this fix on a differnt page and it worked for me so I thought I'd post the fix here also.
Open a terminal and type: sudo gedit /etc/modprobe.d/alsa-base.conf

add this line to the end of the file: options snd-hda-intel model=generic

then hit save and restart your computer.  eliminated all pops and stutters for me :p

---

### Post by wildmanne39 on 2012-09-17
Thanks for sharing. Thread Closed.

---

