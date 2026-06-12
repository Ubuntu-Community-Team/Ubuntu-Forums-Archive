---
title: "Rhythmbox playback failure"
date: 2008-09-18
forum: Multimedia Software
---

### Post by rabbit251 on 2008-09-18
Rhythmbox used to play my music just fine, but suddenly it doesn't anymore.  My library is still detected, but when I click play for any given sound file, there's no response (except that the song progress bar jumps forward one second).

I first experienced this problem soon after following ubuntu-freak's "Comprehensive Multimedia & Video Howto," so perhaps that's related.  Also, I already tried removing and reinstalling Rhythmbox, but that wasn't a fix.  

I'm running Hardy 8.04 with a Spanish language support.  Any help would be very much appreciated.

---

### Post by rabbit251 on 2008-09-20
Bump.

---

### Post by rabbit251 on 2008-09-21
Bump again.  Any ideas for how I might start troubleshooting this?

---

### Post by spotrick on 2008-09-23
I had this problem from time to time. Turned out that if I played anything with sound in Firefox, Rhythmbox would not play until I quite FF. I guess FF "grabs" access to the sound card?

I'm on Ubuntu 8.04 with FF3.

---

### Post by rabbit251 on 2009-04-25
Thanks for your reply.

---

### Post by hashan17 on 2009-04-25
You have millions of software around you.... Why stick to this Rhythmbox player? Use something like VLC player, it supports lot more multimedia formats than Rhythmbox. 

Code here will get you latest version of VLC player 
sudo apt-get install vlc

if you already have a older version of VLC pls remove it using following code or else it'll cause problems.
sudo apt-get remove vlc

---

### Post by rabbit251 on 2009-04-25
> **hashan17 said:**
> You have millions of software around you.... Why stick to this Rhythmbox player?

It's a good point. On the other hand, I think it's important to give heavy consideration to the Ubuntu defaults. I always hope they're selected at least in part for their quality, and if not then they should be concealed. A lot of users see these programs and judge the distro by them.

---

### Post by rabbit251 on 2009-04-25
Oh! also, update: the problem was as Spotrick described, except it happened with Skype as well. I had to be careful for some time about only trying to use sound on one of these apps at a time. But now (in Jaunty), the system can deal with music on Rhythmbox, a soundful video on YouTube in Firefox and an audio call on Ekiga all at the same time!

Skype still demands exclusive use of sound resources. Plus it can't handle PulseAudio (but that's another story).

---

