---
title: "SoundBlaster AWE 64: error following Lord Raiden's Solutions Guide"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by silbar on 2006-08-06
Greetings,

Ubuntu 6.0.6 (dapper) was installed about two weeks ago, but it did not recognize the Creative Labs AWE 64 sound card.  The Device Manager claims it is a Yamaha DS1L card (YMFPCI, YMF740), and of course it plays no sound.

On this forum, I found Lord Raiden's "Comprehensive Sound Problem Solutions Guide v0.5e", which looks like it ought to have solved this problem.  Following his instructions carefully, in the General Help section,

   ~$ sudo modprobe snd-sbawe

gave no response.  So I went on into the "Getting the ALSA drivers from a fresh kernel" section, did the purge and re-install, rebooted, and still found the 'aplay -l' command to return the YMFPCI rather than the AWE 64.

So, I then went, as per instructions, to the "ALSA driver compilation" section.  Doing the build and reconfigure, followed by

   ~$ sudo module-assistant a-i alsa-source ,

the messages did not indicate any errors.  Thus, expecting things to now
be corrected, I again did General Help Step 4,

   ~$ sudo modprobe snd-sbawe ,

to find the following error messages:

WARNING: Error inserting snd_sb_common (/lib/modules/2.6.15-26-386/updates/alsa/isa/sb/snd-sb-common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_sb16_csp (/lib/modules/2.6.15-26-386/updates/alsa/isa/sb/snd-sb16-csp.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_sb16_dsp (/lib/modules/2.6.15-26-386/updates/alsa/isa/sb/snd-sb16-dsp.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_sbawe (/lib/modules/2.6.15-26-386/updates/alsa/isa/sb/snd-sbawe.ko): Unknown symbol in module, or unknown parameter (see dmesg)

The 'aplay -l' still claims it is YMFPCI.

So, I am now stymied and am following Raiden's suggestion to start a new thread.  Anybody know what I'm doing wrong?  TIA,

   Dick Silbar

---

### Post by joecr on 2006-08-08
Is your sound card ISA or on board?

By saying nothing happened do you mean your terminal went to a new line without displaying anything?  If that is the case check out what I did in the following [post]("http://ubuntuforums.org/showpost.php?p=1317232&postcount=128").

---

### Post by silbar on 2006-08-11
Yes, when I said "no response", it just went on to the next command line.

---

### Post by joecr on 2006-08-12
Here is what you need to do then after that as ALSA sound is muted by default or something like that.  At least that is what I read at the following [article]("https://help.ubuntu.com/community/forum/hardware/OldSoundCard").
```
sudo modprobe snd-sbawe
alsamixer
```
Then check if sound works after exiting "alsamixer" by pressing the escape key.  If sound works all you need to do is make the settings sticky by doing the following.
Gnome
```
sudo gedit /etc/modules
```
KDE
```
sudo kwrite /etc/modules
```
Make sure you add the following to the last line of the file & add a blank line to the end of it.
```
snd-sbawe
```
Then assuming you only have the one sound card run the following to make your volume settings stay after reboot.
```
sudo alsactl store 0
```
If you are still having problems please say exactly what is happening or show results using the code tags.  Also state at what point the problem happened.  That will help me & anyone else trying to help you.

---

### Post by silbar on 2006-08-19
This problem has been "solved" by replacing the SB AWE 64 card with a different audio card (Sound Blaster PCI128) and going through the steps in Lord Raiden's Solutions Guide.

Thanks for the suggestions.

Dick Silbar

---

### Post by baccaruda on 2006-10-27
Many Thanks joecr,

I had no sound with my Awe64 Gold, and I followed your advice above.
Its all as you said it would be :-D 

One little bit of advice for Virgin Linux Newbies, like me, who follow this.
I would add 'how to save the file' after youve appended the 'sudo nano /etc/modules'

To save use Control+o and then use Control+x to quit

Dont just hit the close icon as I did in true newbie fassion!
Thanks again.

---

### Post by joecr on 2006-11-12
Sorry about that.  I'm new to Linux, but I have spent several years with DOS.  So for me nano was no problem.  I guess I could list GUI programs, but that would cause problems for the people on Gnome.  I know almost nothing about Gnome other then I don't really care for it.

---

### Post by joris1977 on 2007-04-07
Thanks  joecr your guide worked for me as well. On xubuntu feisty. 

Just heard the system sounds -> so next step will be how to get rid of them :)

---

