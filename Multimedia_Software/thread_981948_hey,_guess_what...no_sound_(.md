---
title: "hey, guess what...no sound :("
date: 2008-11-14
forum: Multimedia Software
---

### Post by newguyjo on 2008-11-14
first off, i'm a ubuntu rookie
my first entry into linux was 8.04 (hardy)  the main problem i had was no sound.  like none, no startup/shutdown sounds, no little system beeps, no music, no flash, no youtube....nothing.  so i scoured the forums and tried everything i could find that seemed like it might help...nothing
so i updated to 8.10 (intrepid)....and still nothing....no sound anywhere.  so i re-scoured the forums and tried everything i could find.  still nothing.  i'm now mucho frustrated.  so, i post:

output from aplay -l:
-------------------------------------------------------------------
   **** List of PLAYBACK Hardware Devices ****
   card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
     Subdevices: 1/1
     Subdevice #0: subdevice #0
   card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
     Subdevices: 0/1
     Subdevice #0: subdevice #0
----------------------------------------------------------------

relevant output from lspci -v:
---------------------------------------------------------------
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
----------------------------------------------------------------

so, to my understanding, it looks like i have two sound cards?  i didn't know i did but the aplay -l looks like it lists two devices.  interestingly though the output from cat /proc/asound/modules is:
-----------------------------------------------------------------
 0 snd_hda_intel
-----------------------------------------------------------------
that's it.  only one card?  i'm confused.

i've put the snd-hda-intel at the end of the /etc/modules folder(file? extension? what do you call it in linux?)

i've tried getting rid of pulseaudio and installing esound and that just got me locked up on start up when it tried to play the startup sound even though i'd disabled it.  so i got rid of esound and reinstalled pulseaudio.  

in system>preferences>sound i think i've tried every combination of selections.  right now they're all on autodetect but i've tried all alsa and bunches of combinations thereof.  there's like five or six choices in each dropdown menu, is that normal?  

any help that anyone could offer would be greatly appreciated!  
thanks.

---

### Post by carlo bolzonello on 2008-11-14
Hey,

I have the same issue, different hardware. I have logged it with the BUG team. Does your sound icon have a red no go sign though it?

Hve you looked at this?

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by carlo bolzonello on 2008-11-14
if you don't come right, go here 

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

follow the ubuntu tab to log the case.

---

### Post by slimx3m on 2008-11-14
newguyjo,

i had kind of a similar sound problem.  after researching for a month and trying different things i resolve my audio problem with a single click.  maybe this problem of yours would be resolve the same way.  here is the link that you might want to take a look at before you continue changing settings [http://www.backports.ubuntuforums.org/showthread.php?t=161193&page=2]("http://www.backports.ubuntuforums.org/showthread.php?t=161193&page=2") post #13.

hope this helps

---

### Post by newguyjo on 2008-11-14
carlo bolzonello:
my icon doesn't have a red no-go sign through it...i just looks normal.  i have acutally looked at the link you posted...still didn't help, i haven't reported as a bug yet though, thought i'd try here first.

slimx3m:
i'm away from the ubuntu machine right now but i'll try that when i get home, thanks

---

### Post by newguyjo on 2008-11-14
slim:
no joy, thanks for the try though.  any other tips?

---

### Post by zenithdave on 2008-11-14
Go to synaptic and delete Pulseaudio from your system , at your own risk of course but every time i dont have sound on the many installs i have performed removing Pulseauido  works everytime.

I really dont know why its installed by default, how many sounds systems do we need ?!?!?! ALSA works just fine :D

Im  NOT linux savvy but this works evertime.

Good luck

---

### Post by slimx3m on 2008-11-14
> **newguyjo said:**
> slim:
no joy, thanks for the try though.  any other tips?

sorry to hear that :( i'll see if i could find something for you at all.

if i was you i would check to make sure that alsa volume is up and not disable.

---

### Post by zenithdave on 2008-11-14
> **slimx3m said:**
> sorry to hear that :( i'll see if i could find something for you at all.

if i was you i would check to make sure that alsa volume is up and not disable.


Do that by typing alsamixer into terminal prompt. Move **left** and **right** with arrow keys and vol-up with arrow **up** key.

---

### Post by psyke83 on 2008-11-14
> **zenithdave said:**
> Do that by typing alsamixer into terminal prompt. Move **left** and **right** with arrow keys and vol-up with arrow **up** key.

Some more information:

Invoke alsamixer by explicitly requesting access to your hardware sound card (this is necessary when PulseAudio is active):
```
$ alsamixer -Dhw
```

Aside from checking the usual mixer setting (PCM, Master), also try toggling the "External amplifier" switch. Some laptops (and possibly desktop cards) need this enabled or disabled, depending on the model.

---

### Post by newguyjo on 2008-11-16
@zenithdave: so i went into synaptic and found the entry that just said pulseaudio, there's a bunch of others too that are related.  do i "mark for complete removal"? or just mark the individual pulseaudio entry?  i tried to just mark the pulseaudio entry but it tried to force me to also mark something called ubuntu-desktop for removal too...and that sounded kinda important when i read the description.  so i didn't do anything...i chicken out.  so i haven't done anything else for fear of messing things up completely.  so, which do i do?

@everyone else, thanks for all the tips.  i've already done the alsamixer stuff...everything is turned on and up all the way.  i don't have an external amplifier so that's not on, all i could find was an extmic entry, that's off.  also, i've turned off or down all the stuff related to capture since i don't use any microphone or any sound input. is that right or do i need all that on too?

thanks all, you guys are great!

---

### Post by newguyjo on 2008-11-25
so, still no sound...anyone out there want to help a new guy out?

---

### Post by psychomichael on 2008-11-25
heck, I've been fighting with this issue for a couple of months...submitted a bug report that was never acted upon and generally nearly gave up. 

I installed new memory (had 2.5GB RAM, now have 6GB) and now it works just fine for files on the hard drive, but still doesn't work on YouTube videos...the vids work but with no sound.

---

### Post by markbuntu on 2008-11-25
There are links for specific hda issues here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by psychomichael on 2008-11-26
> **markbuntu said:**
> There are links for specific hda issues here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

that looks specific to 8.04, though...is it the same procedure for 7.10?

I'm also not using Pulseaudio...just ALSA. I have a friend who owns a computer shop locally that deals exclusively in Linux and he doesn't know why  it's doing this...so I know I'm definitely in strange territory.

---

### Post by markbuntu on 2008-11-26
> **psychomichael said:**
> that looks specific to 8.04, though...is it the same procedure for 7.10?

I'm also not using Pulseaudio...just ALSA. I have a friend who owns a computer shop locally that deals exclusively in Linux and he doesn't know why  it's doing this...so I know I'm definitely in strange territory.

The HDA part should be the same but you may need to upgrade ALSA to a later vesion that has more HDA support. I don't know which version of alsa 7.10 uses but in any case 7.10 will only be supported for another 5 months so you should start thinking about upgrading your entire system anyway.

---

### Post by psychomichael on 2008-11-26
> **markbuntu said:**
> The HDA part should be the same but you may need to upgrade ALSA to a later vesion that has more HDA support. I don't know which version of alsa 7.10 uses but in any case 7.10 will only be supported for another 5 months so you should start thinking about upgrading your entire system anyway.

I'll see if that's possible. 

I'm probably going to go to another linux distro though because I fear Ubuntu has fallen prey to spies from Macroshaft...releasing things before they are truly stable, moving away from what works in favor of frills. It's just a major pain in the *** to have to move everything to external drives every time that something doesn't work right. :mad:

---

### Post by markbuntu on 2008-11-26
I was having great success with the new Mandriva2009 until i upgraded my mobo and cpu. Both of my Ubuntu installs went through the process with flying colors but my Madriva will not boot, even with a clean install, boo hoo. 

But then again, I am still using 8.04 which seems to finally have worked out most of the bugs. I will probably try to get Intrepid working sometime soon, no success with that so far.

If you are looking for stability above all, I would reccomend Debian. Even though the new Lenny has been delayed for some minor bug fixes, it is far more stable than any other "new" distro out there.

Debian might be waiting for the other players to get their acts together, alsa for one, xorg for another.

---

### Post by psychomichael on 2008-11-26
> **markbuntu said:**
> I was having great success with the new Mandriva2009 until i upgraded my mobo and cpu. Both of my Ubuntu installs went through the process with flying colors but my Madriva will not boot, even with a clean install, boo hoo. 

But then again, I am still using 8.04 which seems to finally have worked out most of the bugs. I will probably try to get Intrepid working sometime soon, no success with that so far.

If you are looking for stability above all, I would reccomend Debian. Even though the new Lenny has been delayed for some minor bug fixes, it is far more stable than any other "new" distro out there.

Debian might be waiting for the other players to get their acts together, alsa for one, xorg for another.

hehe...I liked the way Mandriva looked but Ubuntu just seemed easier and Mandriva wouldn't even liveboot on one of my older machines.

I've heard the same thing about Debian being very stable, and that's probably the direction I'm heading...someone mentioned MEPIS as well.

---

