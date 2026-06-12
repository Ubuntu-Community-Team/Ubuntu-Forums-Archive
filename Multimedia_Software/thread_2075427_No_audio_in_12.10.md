---
title: "No audio in 12.10"
date: 2012-10-23
forum: Multimedia Software
---

### Post by frampy on 2012-10-23
Hey guys,

I did a clean install of 12.10, when I open Sound Settings in gnome the only device in the list is "Dummy Output", and sound is not working.

Sound worked fine out of the box in 12.04

I ran alsamixer, it says my card is "HDA Intel", and chip is "Realtek ALC880". The alsamixer playback output was set to mute at first, unmuting did not fix.

It looks like Ubuntu is finding my audio device correctly.

```
mike@wucade:~$ lspci -v | grep -A7 -i "audio" 00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW 
(ICH6 Family) High Definition Audio Controller (rev 03) Subsystem: Albatron Corp. Device 2668 Flags: bus master, 
fast devsel, latency 0, IRQ 40 Memory at d01c0000 (64-bit, non-prefetchable) [size=16K] Capabilities: Kernel driver 
in use: snd_hda_intel Kernel modules: snd-hda-intel

```

My motherboard is an Albatron PX915G-Pro, am I correct in assuming that the alsa driver for this device is snd-intel-hda? It's kinda hard to see on this alsa page [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

Pulling my hair out on this one.

---

### Post by alexander1 on 2012-11-01
same problem. But under kde.

Anyone know how to fix this?

---

### Post by sddfdds on 2012-11-08
same problem here, and this isnt a great solution (particularly on a clean install) but the 3.2 kernel still works.

---

### Post by KBD20 on 2012-11-08
[COLOR=Gray][I]Hi,
I am having a similar problem.
After I upgraded from 12.04 to 12.10 audio worked perfectly fine, once I booted up my computer today, the start-up sound works fine and the change volume "sound" works, other than that no media audio plays at all.
This is on 12.10 using gnome 3 (with a workaround to have it act like gnome 2 if this causes problems).
Card is HDA Intel,
and the chip is Realtek ALC888.[/I][/COLOR]

**Edit: (For anyone else with this particular issue only) It looks like it is a glitch if you switch your computer off if you leave the audio output to headphones, the computer reset it to the speakers, but the output was still technically set to headphones, switching to headphones and back fixed it.**

---

### Post by em wai zee on 2012-11-15
If alsamixer has correctly detected the soundcard, may be forcing Ubuntu to restart alsamixer will do the trick! Try this ...

> sudo alsa force-reload

---

### Post by Cavsfan on 2012-12-15
> **em wai zee said:**
> If alsamixer has correctly detected the soundcard, may be forcing Ubuntu to restart alsamixer will do the trick! Try this ...
> sudo alsa force-reload                      ^^ That fixed it for me. I just logged out and back in, had no sound and a "Dummy Output" showed up in Sound Settings.
Then I entered **sudo alsa force-reload** and voila back to normal.		 		
Thanks! :D

---

### Post by brifra on 2013-01-26
I'm having the same problem with the same device...did you ever find a solution?

---

### Post by brifra on 2013-01-31
Folks here [https://bugs.launchpad.net/ubuntu/+s...r/+bug/1106334]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1106334")

solved this problem for me! the solution was to:

edit /etc/modprobe.d/alsa- base.conf 
and add the following line
 options snd-hda-intel model=3stack

---

### Post by Cavsfan on 2013-01-31
> **brifra said:**
> Folks here [https://bugs.launchpad.net/ubuntu/+s...r/+bug/1106334]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1106334")

solved this problem for me! the solution was to:

edit /etc/modprobe.d/alsa- base.conf 
and add the following line
 options snd-hda-intel model=3stack

That is ironic. I had this same problem again the other day and **sudo alsa force-reload** entered in terminal fixed it again for me.
It got rid of the dummy output and set it correct.

Guess there are 2 ways to fix it. Myself, I find entering **sudo alsa force-reload** the easiest.

---

### Post by Yellow Pasque on 2013-01-31
> **Cavsfan said:**
> That is ironic. I had this same problem again the other day and **sudo alsa force-reload** entered in terminal fixed it again for me.
It got rid of the dummy output and set it correct.

Guess there are 2 ways to fix it. Myself, I find entering **sudo alsa force-reload** the easiest.
You have a different issue (unless you have exactly the same hardware), as audio hardware tends to be very specific, and a model hack was needed there

---

### Post by Cavsfan on 2013-02-01
> **Temüjin said:**
> You have a different issue (unless you have exactly the same hardware), as audio hardware tends to be very specific, and a model hack was needed there

Not sure why you would say that. When you login and have no sound and then look at the Sound Settings in gnome and "Dummy Output" is selected.
Then entering **sudo alsa force-reload** in terminal fixes the problem, it doesn't matter what type hardware you have.

---

### Post by trivio on 2013-05-10
> **brifra said:**
> Folks here [https://bugs.launchpad.net/ubuntu/+s...r/+bug/1106334]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1106334")

solved this problem for me! the solution was to:

edit /etc/modprobe.d/alsa-base.conf 
and add the following line
options snd-hda-intel model=3stack

> **Cavsfan said:**
> Guess there are 2 ways to fix it. Myself, I find entering **sudo alsa force-reload** the easiest.

Hi everyone. I had the same issue with the same HDA Intel (Realtek ALC880) card and doing BOTH things you suggest fixed it.
I'm using Ubuntu 13.04, so this work with this version too.

**First step:**

Open the terminal and paste this:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

Add the following line at the bottom of that file:

```
options snd-hda-intel model=3stack
```

**Second step:**

Paste this on the terminal:

```
sudo alsa force-reload
```


Thanks everyone! =D>

---

