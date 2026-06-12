---
title: "sound problem: /dev/dsp disappeared"
date: 2007-03-28
forum: Multimedia &amp; Video
---

### Post by insert_name_here on 2007-03-28
Recently, my sound stopped working, testing it gives this error: > audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing.

I tried to fix tihs by messing with permissions on /dev/dsp (/dev/sound and /dev/mixer didn't exist).

Just now, I don't have a /dev/dsp anymore!  My card is an "Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)".

It used to be recognized and work fine under edgy, but then kinda spontaneously broke...  I didn't change hardware, software or anything on this machine (Lenovo t60)

---

### Post by insert_name_here on 2007-03-28
Hmm, I reinstalled linux-sound-base, alsa-base and alsa-utils (as well as ubuntu-desktop and gdm, which is important to do!) and now I have /dev/dsp /dev/audio and /dev/mixer back, however I still have no sound.

Are the ls -l entries for these supposed to be: > crw-rw---- 1 root audio    14,   3 2007-03-28 13:37 dsp
crw-rw---- 1 root audio    14,   3 2007-03-28 13:37 dsp
crw-rw---- 1 root audio    14,   0 2007-03-28 13:37 mixer


Should I just reinstall ubuntu?  Could it matter that I installed kdm and kubuntu-desktop before this happened?

---

### Post by derdoe on 2007-04-07
for me it worked by granting write permission to the device for users.. 
although i think adding your user to group "audio" should to the job for you.
(the latter is probably the better way)

---

### Post by insert_name_here on 2007-04-07
I got it fixed... (my friend helped me out)

The problem, in case this happens to anyone else, was twofold:  First, the module snd-hda-intel (or something like that) wasn't loaded correctly - i had to add it to /etc/modules (or something like that).  IN addition, the alsamixer levels changed after reboot to numbers greater than 100.  This caused alsa to get confused and not do anything.  So, if sound doens't work, check those levels to make sure they are between 0 and 100.

---

