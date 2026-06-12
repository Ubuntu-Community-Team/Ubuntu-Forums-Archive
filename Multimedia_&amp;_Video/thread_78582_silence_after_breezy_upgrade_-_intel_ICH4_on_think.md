---
title: "silence after breezy upgrade - intel ICH4 on thinkpad"
date: 2005-10-18
forum: Multimedia &amp; Video
---

### Post by noamr on 2005-10-18
Hello,

I recently upgraded to breezy, and I have no sound. Everything seems to work without any error messages, there is just no sound from applications (power beep is working, and its volume even changes with the volume up/down buttons!).

I have turned everything on in alsamixer.

I have thinkpad R50e. Relevant lspci:
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

kernel: 2.6.12-9-686

Thank you,
Noam Raphael

---

### Post by jimmystewpot on 2005-10-22
I am having an identical issue to that, it worked fine in hoary, as soon as I upgraded nothing works. The modules are loaded, the pci shows up, everything looks good but no sound. Have you resolved the issue?

---

### Post by antineutrinos on 2005-10-22
Not really original, but I have the same problem... I don't have a clue on how to make it work back.
Anyone???

---

### Post by chuvisco on 2005-10-30
I had the same problem after upgrading to Breezy.  I fixed it by running alsamixer (in a terminal) and then unmuting "External" (use arrow keys to highlight "External" and then press "m").  If that doesn't work, you might try playing with some of the other settings there.

---

### Post by clamhead on 2005-10-31
[QUOTE=jimmystewpot]I am having an identical issue to that, it worked fine in hoary, as soon as I upgraded nothing works. The modules are loaded, the pci shows up, everything looks good but no sound...[/QUOTE]
Exact same problem here. Sound worked fine on Hoary, but upgrade to Breezy meant no sound whatsoever. Sound continues to work fine in Windows XP on this dual-boot box.

Nothing muted, card recognized, modules loaded, the [Ubuntu No Sound Troubleshoot]("http://linux.iuplog.com/default.asp?item=94639") followed, [DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems") used, followed all recommendations in [Howto: Happy ALSA, OSS, ESD, with Duplex - Sound Settings]("http://ubuntuforums.org/showthread.php?t=44753"), tried all combinations of default sinks and sources in System -> Preferences -> Multimedia Systems Selector.

In addition, the Ubuntu Bugzilla [Bug #15585 - Muted sound after dist-upgrade from Hoary to Breezy]("http://bugzilla.ubuntu.com/show_bug.cgi?id=15585") might prove helpful to others, but I followed the recommendation there (set Headphone Jack Sense and Line Jack Sense off) and had no success. 

I'm getting real familiar with running [FONT="Courier New"]/usr/bin/speaker-test[/FONT]. 

Has anyone else had any success in addressing this issue?

```

$ lsmod | grep snd
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

$ lspci | grep audio
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 12)

```

---

### Post by clamhead on 2005-11-07
Well, don't that beat all -- I ran
```
/etc/init.d/alsa-utils reset
```
and then was able to hear the test sound when setting my default sink to ALSA in System -> Preferences -> Multimedia Systems Selector. It's hard to believe, but it's possible that my mixer levels weren't initialized. I guess I don't understand why that would be, since running alsamixer in a terminal showed me that all levels were high enough to hear.

See [https://bugzilla.ubuntu.com/show_bug.cgi?id=16996#c2](https://bugzilla.ubuntu.com/show_bug.cgi?id=16996#c2) for where I got the idea.

---

### Post by anthony43 on 2005-11-12
Hi all !
Following this : 
[I]I had the same problem on my IBM T43:
Headphone Jack Sense AND Line Jack Sense need to be muted to make it work again.[/I]
 and shutting down many other useless outputs, I got it working !!
See this page for more info :
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15585]("http://bugzilla.ubuntu.com/show_bug.cgi?id=15585")

---

### Post by jliedeka on 2005-11-12
I've been having issues with intel8x0 on my Sony VGN-S270.  I fiddled with alsa-base in /etc/modprobe.d, tried /etc/init.d/alsa-utils restart, rebooted and still no joy.

I think what finally made it work was to add a file to /etc/devfs/conf.d with these lines:
LOOKUP snd MODLOAD ACTION snd
REGISTER ^sound/.* PERMISSIONS root.audio 660
REGISTER ^snd/.* PERMISSIONS root.audio 660

I got that from the ALSA-Configuration.txt file in the kernel docs.  Now alsa aware apps have sound.  Next job is to get sound working for that damn flash plugin.  I'm jonesing for Neurotically Yours.

     Jim

---

### Post by npcomplete on 2007-04-24
> **chuvisco said:**
> I had the same problem after upgrading to Breezy.  I fixed it by running alsamixer (in a terminal) and then unmuting "External" (use arrow keys to highlight "External" and then press "m").  If that doesn't work, you might try playing with some of the other settings there.

Thanks a lot! I fixed my Intel ICH3 AC97 sound card on my IBM Thinkpad X24. Just unmuting
each item shown in alsamixer.

---

### Post by omlx2 on 2007-07-05
hi to all 
am using lenovo  ibm 3000 v100
n have a problem in the sound 
exactly when i use my  headphoe the sound should be only in the headphone but its not ,the main builtin i mean the speaker in my laptop 
am using ubuntu 7.04

---

### Post by John W on 2007-07-05
I am also having sound problems. I just upgraded to 7.04(I was able to listen to CD's and streaming radio prior to upgrade), I had tried to get sound to work on websites but ended up with a crashed system, so I upgraded to Feisty and now have no sound except for login drum sound. I typed in totem in terminal and this is what I got.

In the terminal:
```
johnwelk@WelkComp1:~$ totem
main.c: WARNING: called SUID root, but not in group 'pulse-rt'.
main.c: WARNING: called SUID root, but not in group 'pulse-rt'.
main.c: WARNING: called SUID root, but not in group 'pulse-rt'.
** Message: Error: Resource not found.
gstjackaudiosink.c(363): gst_jack_ring_buffer_open_device (): /autoaudiosink0-actual-sink-jackaudio:
Cannot connect to the Jack server (status 17)

main.c: WARNING: called SUID root, but not in group 'pulse-rt'.
main.c: WARNING: called SUID root, but not in group 'pulse-rt'.
```

On the desktop:
```
The requested audio output was not found. Please select another audio output in the Multimedia Systems Selector
```

Ran alsamixer in the terminal and nothing is muted. I could not find the following System -> Preferences -> Multimedia Systems Selector. Multimedia systems selector doesn't exist in preferenes, anybody know where else I might find it. My kids are begging for sound, I need help.

---

### Post by John W on 2007-07-05
I found System -> Preferences -> Multimedia Systems Selector, I had to first go to System -> Preferences -> Main Menu and enable it in the menu. I then chose ALSA as my plugin(it was on autodetect) and enabled my soundcard, now I can hear a CD but still nothing on websites.

---

