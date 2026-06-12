---
title: "Sound Juicer is a terrible ripper"
date: 2008-07-27
forum: Multimedia Software
---

### Post by bsmith1051 on 2008-07-27
I can't begin to tell you how frustrated I am with Sound Juicer (and Ubuntu) right now.  I have spent HOURS simply trying to rip some new CDs to MP3.  I know, the zealots out there will say, "Just use ogg," but unfortunately none of my portable media players support it.

***ALL THE BS I'VE GONE THROUGH***

I'd previously spent hours figuring-out how install and configure LAME, plus create the appropriate link-file.  After the upgrade?  BZZZT! Broken.

I read dozens of posts re MP3 and Sound Juicer but didn't see anything new to try.  So I gave-up on Sound Juicer and tried installing various other MP3 rippers.  BZZZT! None of them could find the CD.  Apparently Hardy only 'half' mounts Audio CDs?

Finally, I decided to just fall-back to my old Windows ripper, running inside VirtualBox.  BZZZT!  Same half-mounted problem, so VB couldn't detect the disc.

Since I was totally screwed otherwise, I re-read all the posts I'd previously located and finally realized I needed to install 'gstreamer0.10-plugins-ugly-**multiverse**' and not merely 'gstreamer0.10-plugins-ugly' (which was already installed).  Finally, Sound Juicer allowed me to select MP3 as the one/only encoding option.  **BZZZZZZZZZZZT**!  It still encodes everything as OGG.   WTF?!

***CONCLUSION***

It is totally obscene that it should take so much work to do something so common.  This has really burned me on Ubuntu, and I am no longer going to recommend it to anyone.  Considering what a fanboi I've been over the past several years, this is a real reversal.

**UPDATE**:
And here's still more b.s.  In Hardy there's no longer an option under System > Preferences > Removable Media to control the default Audio CD app.  I tracked-down the 'gconf-editor' app but the option for Desktop > Gnome > Volume Manager > autoplay_cda was already disabled.  Enabling it didn't have the opposite effect, i.e., disabling it, nor did subsequently re-disabling the checkbox.  

Basically, nothing works the way it's supposed to.  Count me as unimpressed...

---

### Post by cariboo on 2008-07-27
HAve you looked at any other ripping software, I find Sound Juicer pretty basic and not very user friendly. I used grip to rip my cd's. It is pretty easy to setup, no linking with lame or anything. You set what you want to rip the cd to, set the bitrate and even which encoder you want to use. It usually works right out of the box if you already have lame installed.

Jim

---

### Post by bsmith1051 on 2008-07-28
thanks, yeah, I tried Grip but I couldn't get it to read my CD drive.

UPDATE: I figured it out! I had to update the Config > CDrom Device setting to /dev/scd0.  I'll give it another try now.

---

