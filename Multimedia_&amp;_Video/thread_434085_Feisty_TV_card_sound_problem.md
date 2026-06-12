---
title: "Feisty TV card sound problem"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by steelfanatic on 2007-05-05
I really wanted to move up to Kubuntu Feisty, but, there is a HUGE problem: Sound works fine for regular usage .....with one hitch: my Leadtek Winfast "expert" TV card,(cx8800)  it has a audio cord that connects to my motherboard "CD" input.  I cannot get ANY sound to it, it works fine with EDGY, Dapper, Mepis, Vista (yuck)....so its definitely a Feisty problem. I have checked  for any possible alsa mixer volume combinations. The Motherboard is an ASUS P5B. Any hints? I really want to use Feisty for some of the newer packages :( 

Thanks in advance.

---

### Post by rufitos on 2007-05-14
Hello, 

Im having the same sound issues, my motherboard is ASUS P5N-E SLI and i have a Pinnacle 100i.
Also under Winblows the card works fine.
Looked everywhere to try to make it work and nothing...

Help would be great!

Best regards, 

rufitos

---

### Post by steelfanatic on 2007-05-14
This is driving me crazy, still no solution with the most popular linux distro....

---

### Post by stereophrenic on 2007-05-16
Same problem here, the audio worked for this winfast card on Egdy (at least when using tvtime, it didn't work for mythTV for me).  In frustration, I upgraded to Fiesty, but now I don't get sound from this card at all.

---

### Post by newlinux on 2007-05-17
Have you guys looked at your alsa settings (alsamixer)? Usually this means something is muted (one of the captures or inputs) or if you are using a jack from your card to an input on  sound card you may have ALSA set to capture from the wrong input (e.g. it may be set to capture from AUX when it is plugged into CD). I had this problem with Feisty, and had to change my capture device even though it worked before (in alsamixer you set the capture device with the "SPACE" bar). I also had the problem of sound in TVtime working on one of my tuners, but not myth, and this fixed this is as well.

Start with this:

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

And see if that helps. Post your results back here and I'll help where I can (and so will others). Hope this helps.

---

### Post by steelfanatic on 2007-05-18
Tried this (alsamixer) still no luck......

---

### Post by newlinux on 2007-05-18
> **steelfanatic said:**
> Tried this (alsamixer) still no luck......

What did you try? what were the results? Some of the information in the link was diagnostic, and the results could help troubleshoot the problem....

---

### Post by stereophrenic on 2007-05-18
Hi Newlinux,

I think there is something I'm not understanding properly.

I tried the following, from the website you suggested, here are the results:

**Part 1:**
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

This shows the integrated soundcard on my motherboard... But, is this supposed to show the audio decoder on the TV card too?
[B]
Part 2 (I removed irrelevant results of this command):[/B]
```
$ lspci -v
00:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: LeadTek Research Inc. Leadtek Winfast 2000XP Expert
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at e7000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/K8V Deluxe motherboard (ADI AD1980 codec [SoundMAX])
        Flags: medium devsel, IRQ 20
        I/O ports at e000 [size=256]
        Capabilities: <access denied>
```

According to [http://mythtv.org/wiki/index.php/Leadtek_WinFast](http://mythtv.org/wiki/index.php/Leadtek_WinFast) , my Winfast card uses the snd-bt87x ALSA driver.  So...
[B]
Part 3:[/B]
```
$ sudo modprobe snd-bt87x
$
```

This returns nothing.. no success message, no errors.. is this right?

**Part 4:**
I went into alsamixer and turned everything up...
I opened up TV time, tuned into a channel...

Still no sound from the TV card :(

Any clues?

Thanks for your help...

---

### Post by newlinux on 2007-05-18
Make sure in alsamixer that "View" is set to "ALL" (use the TAB key) and unmute everything.

did you trying setting different "capture" devices alsamixer. You mentioned you have the cord to the "CD" input. Try setting that or AUX or others to the capture device in alsamixer (using the space bar).

---

### Post by newlinux on 2007-05-18
Oh, and if modprobe worked properly you wouldn't see any output and all of those outputs above look normal. The Myth wiki says the btaudio may not work, but the cord to sound card does. [http://www.linuxtv.org/v4lwiki/index.php/Leadtek_WinFast_2000](http://www.linuxtv.org/v4lwiki/index.php/Leadtek_WinFast_2000)

---

### Post by steelfanatic on 2007-05-19
Newlinux, I'm sorry, I know you're trying to help, I only had a few minutes last night to mess with alsamixer, my schedule has been tight lately, when I tried  alsamixer I turned everything all the way up, when using the space bar setting capture devices, they turned to "4 lines" then came back up the same each time I hit the space bar.

---

### Post by newlinux on 2007-05-19
Alas,  unfortunately I'm out of suggestions. If you have the internal patch cord hooked up, and tried setting AUX and CD (and other devices) to capture and turning them up, and had all the devices shown in alsamixer (by setting the View to ALL) I have no other suggestions.

However, I'm not sure what you mean by turning to 4 lines, but it's late for me and I'm getting tired now :) Good luck, sorry I couldn't help more.

---

### Post by fenian on 2007-05-19
Did you try these commands...

to remove old bttv driver settings...

> sudo rmmod bt878
sudo rmmod tuner
sudo rmmod bttv

to set correct drivers (I think these are the correct values for your card)...

> sudo modprobe bttv card=34 tuner=43

check  tvtime to see if that worked,if it did make the changes permanent with...
> 
sudo gedit /etc/modprobe.d/bttv 

insert this line...
> 
options bttv card=34 tuner=43

---

### Post by stereophrenic on 2007-05-19
Fenian,  it worked for me, thanks!   Works in tvtime, works in mythtv... Oh wait, I just exitted mythtv and i can still hear the tv.  Oh well, that's a problem to solve for later, at least the sound is working.

Thanks for your help :)

---

### Post by steelfanatic on 2007-05-19
So, how would this be solved for the Leadtek Winfast "expert" TV card,(cx8800)??

On older kernels I would have to edit the etc/modules file....

---

### Post by steelfanatic on 2007-05-19
Still no sound from my tv card... looks as if I have the same tv card as stereophrenic:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
melly@bedroom1:~$

lspci -v
05:02.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: LeadTek Research Inc. Leadtek Winfast 2000XP Expert
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ec
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

### Post by fenian on 2007-05-19
In the instructions I posted above try switching 
> 
sudo modprobe bttv card=34 tuner=43

with

> sudo modprobe bttv card=34 tuner=44

you can continue switching the values (0-45) until you find the right one.Once you find the right settings make them permanent using the instructions above with the correct values.More info on tuner ids [here]("http://tldp.org/HOWTO/BTTV/modprobe.html")

---

### Post by steelfanatic on 2007-05-19
still no luck....:(

stereophrenic did an upgrade from edgy to feisty, maybe thats why it worked for him...

Just a question...why are we messing with bttv drivers with a Conexant CX23880 card?

---

### Post by steelfanatic on 2007-05-19
Ok, found out its my sound (hda intel) tried SB live and now sound works

---

### Post by k_rock923 on 2007-05-20
I'm having a similar issue.  Everything worked fine under edgy.  I formatted the machine to put Solaris on and poof.  I get picture and no sound now with feisty.

When I try to rmmod bttv, my machine freezes.

steelfanatic, can you describe in some more detail exactly what you ended up doing?  Thank you.

---

### Post by wessel_k on 2007-06-19
SOLVED!!!! I studied the board lay-out and I noticed I could use the audio out and link that to my audio in in my audio card (the blue one). Now it's working. GREAT!!!

I'm also trying to get the sound om my Leadtek Winfast TV2000 (XP) Model 1 to work. The issue here is that I don't have the option to connect the card directly to my sound card/motherboard with a cable. So I need to get the software thing working. I tried a lot. What I noticed is that I get a strange message: bt878: AUDIO driver version 0.0.0 loaded. I completely stuck here. Maybe somebody can help me out. I would love to get it the card to work under Feisty.



Regards,

Wessel

---

