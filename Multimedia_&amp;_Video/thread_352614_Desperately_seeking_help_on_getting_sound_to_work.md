---
title: "Desperately seeking help on getting sound to work"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by wizard9999 on 2007-02-03
Folks

I bought this new machine (dell optiplex 745) - have ubuntu installed and cant get the sound to work at all.

Here are some details:
**lspci -v**
00:1b.0 Audio device: Intel Corporation HD Audio Controller (rev 02)
  Subsystem: Dell Unknown device 01da
  Flags: bus master, fast devsel, latency 0, IRQ 11
  Memory at dfdfc000 (64-bit, non-prefetchable) [size=16K]
  Capabilities: <access denied>

**uname -a**
Linux <> 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux

**sudo modprobe snd-hda-intel**
This just hangs

**aplay -l**
aplay: device_list:222: no soundcards found...

I have followed all instructions from the post:
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)
and installed and reinstalled the alsa drivers.

Can someone please help?

Thanks a lot!

-R

---

### Post by pseudonym on 2007-02-04
Have a look at [this post]("http://www.ubuntuforums.org/showpost.php?p=2013895&postcount=17") of mine from a couple of weeks back.

---

### Post by wizard9999 on 2007-02-04
Hey pseudonym

Stupid newbie question - How do I figure out the hda model number for my sound card?

Thanks

-R

---

### Post by pseudonym on 2007-02-04
> **wizard9999 said:**
> How do I figure out the hda model number for my sound card?
First check your computer/motherboard's manual to work out which codec you have (ALC880, AD1988 etc.). Then go to the snd-hda-intel list in ALSA-Configuration.txt. Then see which one of those matches your hardware.

Example - Your codec model is ALC880, and you have 6 channel with digital out. In that case, your module option would be '6stack-digout' (6 channel options also work for 8 channel sound chips - that's what I used on mine).

Bear in mind that some Dell systems have sound hardware which is peculiar to them, and may not be supported well under ALSA if they are brand new. This was the case a while back with Dell desktops that shipped with a special Dell implementation of a Soundblaster 5.1 soundcard. But it was just a matter of time before the ALSA developers addressed the issue.

---

### Post by wizard9999 on 2007-02-04
My codec model is ADI 1983 with the ICH8 chipset.   So, I am out of luck for now, I guess because I dont see it in the ALSA-Configuration.txt file.  Any other ideas?

---

### Post by stephenb on 2007-06-07
I've got exactly the same setup as you and was until a little while ago having the same problem. 

However, when I did **sudo modprobe snd-hda-intel **it didn't hang and when I did **aplay -l** I got the playback hardware devices listed. I still couldn't get sound, though. 

What fixed it for me was simply following this post: 
[http://ubuntuforums.org/showpost.php?p=2515443&postcount=20](http://ubuntuforums.org/showpost.php?p=2515443&postcount=20)

I got a device in use error with **sudo rmmod snd-hda-intel**
No problem. Then I simply ran this command to see what would happen:

[B]sudo modprobe snd-hda-intel probe_mask=8 model=auto

[/B]After that my sound worked. 

It was recommend that this line be added at the end of the **/etc/modprobe.d/alsa-base** file and to a new file called **/etc/modprobe.d/snd-hda-intel.modprobe**:

**options snd-hda-intel probe_mask=8 model=auto**

The **probe_mask=8** is to overcome a laptop modem issue. So I didn't think I needed it when I added the recommended line at the end of my **/etc/modprobe.d/alsa-base** file, like this:

[B]options snd-hda-intel model=auto

[/B]I didn't even need to create a **/etc/modprobe.d/snd-hda-intel.modprobe** file.

I just rebooted and heard the beating drums of Ubuntu for the first time on my Optiplex 745.

---

### Post by sumash on 2007-10-24
I got  the same problem with you and tried all the steps found on the web. still not work.

finally, I found I made a stupid mistake, I forgot to add my account in to the "audio" group in the /etc/group file. you can try adding your account name after audio and other device in /etc/group file. like :
audio:x:29:your-account
video:x:44:your-account

hope it be useful for you.

---

### Post by mllaneza on 2007-10-24
This just fixed my sound problems in Gutsy using a CS4630 audio chipset

[https://lists.ubuntu.com/archives/ubuntu-users/2007-August/121844.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-August/121844.html)

---

