---
title: "Quiet sound with Intel HD Audio"
date: 2006-08-26
forum: Multimedia &amp; Video
---

### Post by ese5 on 2006-08-26
After installing Ubuntu I'm left with extremely quiet sound even with all the channels turned up (I've verified with the ncurses version of alsamixer.)  I have intel High Definition audio and the hardware is being properly detected as far as I know...   from lspci:

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

Anyone have any ideas why my sound would be so quiet?  I can barely hear most things even with the volume at 100%

---

### Post by vladsinger on 2006-08-31
I have the exact same problem. Doesn't anyone have an idea?

---

### Post by Malnilion on 2006-09-01
I have the same problem. I also find the audio quality quite shitty. Nothing like the quality I experience in Windows.

---

### Post by crispy_420 on 2006-09-01
Stupid question:

Do you have alsa mixer installed and cranked up the volume?

---

### Post by ese5 on 2006-09-02
Yeah the levels are all cranked.

It turns out this is a known bug with the HD audio driver.  Some people were suggesting using a USB sound adapter until this is fixed.  Here is another (awkward and very annoying) workaround that I've found:

1..  Boot linux
2..  Hibernate
3..  Turn the computer back on and boot into windows
3..  Make sure all the levels are up
4..  Restart windows and choose linux when GRUB comes back up

Volume should be working now.   Pain in the ***, but works.

---

### Post by Harksaw on 2006-09-13
Ah, well at least I know now that it's a known bug. I have the same problem in addition, the sound is crackly.

Is there some kind of bug homepage I can check on to see progress and when it gets fixed?

---

### Post by Daniel15 on 2006-09-26
I have the same audio controller. The volume works fine for me, but the sound 'stutters' in some games. Normal applications seem to work fine... Is this another known bug?

---

### Post by cwkx on 2006-10-24
> **ese5 said:**
> Yeah the levels are all cranked.

It turns out this is a known bug with the HD audio driver.  Some people were suggesting using a USB sound adapter until this is fixed.  Here is another (awkward and very annoying) workaround that I've found:

1..  Boot linux
2..  Hibernate
3..  Turn the computer back on and boot into windows
3..  Make sure all the levels are up
4..  Restart windows and choose linux when GRUB comes back up

Volume should be working now.   Pain in the ***, but works.

Tried that, it didn't work. I updated my version of alsa to the latest too, that didn't work. This is a real problem for me and making me boot windows for every media file that I wish to play. The sound is really really quiet and it also isn't surround sound (its just coming out the sub)

My lspci -v:

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Sony Corporation: Unknown device 81e7
        Flags: bus master, fast devsel, latency 0, IRQ 74
        Memory at 5a400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

I hope people can help look into it, my friend with the same computer has the exact same problem (VGC-RC202). We're both barely using ubuntu now because of it wheras we normally don't use windows at all.

Chris

---

### Post by Ryanmt on 2006-11-07
ive got the same problem. anybody solved this yet?

---

### Post by howlingmadhowie on 2006-11-09
hi, i also have intel hda sound on one of my laptops, and it also switched itself off after installation (it works fine on the live cd). i found that the headphone socket still worked fine and stragely, after having used the headphone socket, the main speakers started working again. weird. so now i have sound again.

---

### Post by commonplace on 2006-12-27
Any fix for the quiet sound? The volume works on my wife's new laptop (Compaq Presario C301NR, with Intel 82801 ICH7 rev2 HDA), but it's very quiet. I've gone into alsamixer and gnome-volume-controls, but it was already up all the way and it's still very quiet. The volume was at least 3-4 times louder in Windows (which I blew away altogether).

Has this been fixed? I've read a lot of people having problems with the microphone port with this audio card (which I haven't even tested yet), but not as much about the volume problem.

---

### Post by pirithiumx on 2007-10-10
Ditto Running a Toshiba Satellite A105-S4384, Trying to send Vista to hell. Love Kubuntu, But looking bad not having the sound work, in front of the Vista Guys. Love to Know if a Fix is available?

---

### Post by ldesilva on 2007-10-12
> **ese5 said:**
> Yeah the levels are all cranked.

It turns out this is a known bug with the HD audio driver.  Some people were suggesting using a USB sound adapter until this is fixed.  Here is another (awkward and very annoying) workaround that I've found:

1..  Boot linux
2..  Hibernate
3..  Turn the computer back on and boot into windows
3..  Make sure all the levels are up
4..  Restart windows and choose linux when GRUB comes back up

Volume should be working now.   Pain in the ***, but works.
It's weird, I have followed the instruction, the sound only comes on when I plug in a head-phone into the jack. When head-phone is off, no sound coming from the speakers. Any solutions?

BTW, I have Ubuntu 7.10 RC installed on my laptop.

I did a lspci -v and this is my results:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Unknown device 0113
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

Thank you.

---

### Post by Berryjiveuptown5 on 2007-10-13
I also have the hda intel ich7 family sound card on my desktop.  Guess I really don't have to mention that I have absolutely no sound.  There are some fixes for those of you with laptops.  However, if you have a desktop, I don't recommend trying them.  I'll try to find the exact link, but you can paste an extra line into the etc/modprobe.d/alsa-base.txt file and all you sound problems will be fixed (including the speaker/headphone issue).  However, when I followed this advice for my desktop with the same soundcard, I got an error screen on startup/login.  Heard the congo error sound though!  


Here's the link:
[HTML]http://ubuntuforums.org/showthread.php?t=314383[/HTML]

---

### Post by ldesilva on 2007-10-13
Thanks, follow the article for my Acer laptop and everything works :)

---

