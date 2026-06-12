---
title: "Brasero vs. cd-text"
date: 2010-05-13
forum: Multimedia Software
---

### Post by julio_cortez on 2010-05-13
That is. I've just installed Xubuntu last night on a spare drive because I really wanted to try it out. Install and initial setup (upgrades, extras and so on) worked like a charm, then I got to burn an audio cd with Brasero starting from some mp3s floating around my external media drive.

The burn process itself went good and the CD is fully readable, but I notice that CD-text is missing.

So, when I added files to the main window of Brasero id3 tags were there (I've seen them, plus I set each and every of them via Easytag before putting the files in my external media drive so I'm sure of that), but once the CD was finished there was no CD-text at all.

Is there a way to fix it?
Maybe I just have to download some additional packages which aren't included in Brasero or have missed some menu item about CD-text?

Thanks in advance!!

---

### Post by zajc on 2010-06-05
I have exactly the same issue. CD-text is missing. Anybody have a solution?

Brasero 2.30.0-0ubuntu1

---

### Post by zajc on 2010-06-06
Brasero 2.30 have bug when burning image
> stderr: wodim: The cuefile= option only works with -dao

I "solved" this by running this command (I got the information in brasero-session.log) with -dao switch
> wodim -v dev=/dev/sr1 speed=8 driveropts=burnfree fs=16m -text cuefile=/tmp/brasero_tmp_I3BTDV.cue -dao

And it works.

:guitar:

How I find a "solution":
1.) Create AUDIO CD (.wav, .mp3...) and add CD text information
2.) Burn AUDIO CD with default options ("burn directly" must be disabled)
3.) Brasero will "probably" return "Unknown error"
4.) Save .log file
5.) From .log file extract command line.
6.) Run command with -dao switch.

I have tested this and CD text is now shown on my CD player.

---

### Post by julio_cortez on 2010-06-14
I'll give it a go then (even if I'm back to Kubuntu right now).. Sorry but I completely overlooked the thread as I didn't burn any CD since..

For the moment, thank you!!

---

### Post by mocha on 2010-06-14
> **zajc said:**
> I have exactly the same issue. CD-text is missing. Anybody have a solution?

Brasero 2.30.0-0ubuntu1

Yeah, use k3b.  Brasero has been broken in various ways since at least after Hardy.  I gave up on it unfortunately cause I did like it's simplicity and Gnome-ish-ness.

---

