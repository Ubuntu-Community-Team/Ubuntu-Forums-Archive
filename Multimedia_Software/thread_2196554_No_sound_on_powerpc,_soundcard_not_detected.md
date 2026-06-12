---
title: "No sound on powerpc, soundcard not detected"
date: 2013-12-30
forum: Multimedia Software
---

### Post by rdh61 on 2013-12-30
Hi,

I am running Lubuntu 13.10 on, among other machines, a Mac iBook G4.

I hear the signature sound on turning the machine on, but there is no sound when playing audio or video.

```
robert@lubuntu-ibookg4:~$  aplay -l
aplay: device_list:268: no soundcards found...

```

I have read the advice here, and everything appears in order: [https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)

My sound does not appear to be muted*.

Modules:

snd-powermac is loaded.

The following are blacklisted:
snd-aoa
snd-aoa-fabric-layout
snd-aoa-soundbus
snd-aoa-i2sbus
snd-aoa-codec-tas

(* The above link gives the advice: "You need to check more than just your master volume, 
for example the volume of the PCM channel maybe set to zero". However, I do not know how to 
check the "PCM channel". I have installed gnome-alsamixer, but it does not appear to open properly i.e.
the GUI opens but without any controls, just a blank window).

Any help gratefully received.

Many thanks.

---

### Post by rdh61 on 2013-12-30
I found this but have no idea what, exactly, to do with the patch:

[http://lists.debian.org/debian-powerpc/2013/09/msg00031.html](http://lists.debian.org/debian-powerpc/2013/09/msg00031.html)

---

### Post by rdh61 on 2014-01-03
I now realise that this patch wouldn't help, as it is for an iBook requiring the snd-aoa module, whereas mine apparently should require the snd-powermac module.

Still looking for a solution...

> **rdh61 said:**
> I found this but have no idea what, exactly, to do with the patch:

[http://lists.debian.org/debian-powerpc/2013/09/msg00031.html](http://lists.debian.org/debian-powerpc/2013/09/msg00031.html)

---

### Post by rdh61 on 2014-01-04
For anybody who's interested, the problem was that I had failed to consider that I might have both the wrong sound module loaded AND one of the volume controls muted. Thus when I tried with the other sound modules I did not at the same time re-try with alsamixer. (Reading above, see that alsamixer would not show any controls with snd-powermac loaded).

The solution was to ensure that these modules were loaded:

snd-aoa
snd-aoa-fabric-layout
snd-aoa-soundbus
snd-aoa-i2sbus
snd-aoa-codec-tas

and this one blacklisted:

snd-powermac

i.e. the opposite of the configuration installed by default.

Details here: [https://wiki.ubuntu.com/PowerPCFAQ#W...ve_no_sound.3F]("https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F")

Then, from a terminal I opened alsamixer, which now displayed normally. I toggled "PCM" to unmuted by selecting it and typing "m", then crucially I did the same with "Headphone". Without this last step there was still no sound, although what this has to do with it I don't know as I don't have any headphones attached.

Anyway, that worked.

---

### Post by Hamish_MacLeod on 2014-11-11
THANK YOU!!! I can confirm the above worked for me on:
Mac mini G4 (PowerMac10,1)
Ubuntu 14.04.1 LTS
AppleOnbdAudio

---

### Post by rdh61 on 2015-04-10
Update: Since posting the above 16 months ago, I recently did a fresh install, and came up against the same problem again. But I had difficulty following my own instructions above, which I realise need clarification. This then is the solution:

First see here: [https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)

BUT, contrary to what is suggested there:

The solution is to ensure that these modules are loaded:

snd-aoa
snd-aoa-fabric-layout
snd-aoa-soundbus
snd-aoa-i2sbus
snd-aoa-codec-tas

and this one blacklisted:

snd-powermac

How?

1. in /etc/modprobe.d/blacklist.local.conf comment out the blacklisted modules that are in fact required to be loaded:

```
blacklist snd-aoa
blacklist snd-aoa-fabric-layout
blacklist snd-aoa-soundbus
blacklist snd-aoa-i2sbus
blacklist snd-aoa-codec-tas
```


 and uncomment the following:

```
# blacklist snd-powermac
```

2. In /etc/modules add:

```
snd-aoa
snd-aoa-fabric-layout
snd-aoa-soundbus
snd-aoa-i2sbus
snd-aoa-codec-tas
```

Then, from a terminal open alsamixer, which will now display normally. Toggle "PCM" to unmuted by selecting it and typing "m". Then, I don't know why but to get sound but I had to do the same with "Headphone", even though I don't have any headphones attached.

---

### Post by mmw-canada on 2016-02-05
Thanks for this post, here is an update for getting ubuntu 15.10 up and running on a mac mini model a1103(PPC)

Download the ubuntu server 15.10 iso
Install the vanila server, then run apt-get install lubuntu-desktop(run's ok, web browsing a bit weak)
reboot

There were two immediate issues:
- screen would freeze then flick on and off every couple of seconds until you reboot.  This would only happen when I made a program full screen.
- No Sound

To fix the video, I followed [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) and changed yaboot parameter radeon.agpmode=-1

To Fix the sound I followed rdh61's fix, but replaced:
snd-aoa-codec-tas
WITH
snd-aoa-codec-toonie

You will need to adjust this codec if you have a different model mac, see: [https://wiki.debian.org/PowerPC/SoundCards](https://wiki.debian.org/PowerPC/SoundCards)

I will put a request in with the "ppc known issues" wiki page to have it updated...

---

### Post by fidelis2 on 2016-02-18
> **mmw-canada said:**
> You will need to adjust this codec if you have a different model mac, see: [https://wiki.debian.org/PowerPC/SoundCards](https://wiki.debian.org/PowerPC/SoundCards)

How would I find from this list the needed "snd-aoa-codec-XYZ" for my machine?
I tried your hints concerning "etc/modules" but neither the codec "snd-aoa-codec-toonie" nor "snd-aoa-codec-tas" works for me.

So I can't get sound to work with Ubuntu 15.10 on my PPC iBook G4. :-(

Some kernel log file lists the exact machine ID as: *G4 iBook2 (PowerBook6,5)*
According to your linked debian list my audio chipset would be "Snapper", and via some other information I found the audio ID being hex 26 aka decimal 38.

In the other [thread]("https://wiki.ubuntu.com/PowerPCKnownIssues#A14.04_Trusty_Tahr") there's a patch which is said to work also for this audio hardware (PowerBook6,5) with Ubuntu 14 and Kernel 3.x , but we've got Ubuntu 15.10 and Kernel 4.x .

Any help much appreciated.

---

