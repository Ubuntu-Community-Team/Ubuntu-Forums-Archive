---
title: "Poll - upgrading, no upgrading, upgraded"
date: 2011-05-02
forum: Mythbuntu
---

### Post by earlneath on 2011-05-02
Some of the stories about ir keyboard repeats, nvidia drivers, video playback and so on read as though it would be best to hold off upgrading to Natty for mythbuntu users. So please mythbuntu users respond to the poll to state your experiences and intentions with Natty!

---

### Post by ian dobson on 2011-05-02
Hi,

Upgraded my backend and frontend from 10.10/Mythtv 0.23 to 11.04/Mythtv 0.24 everything went OK, afew minor problems:-

1) Double keys on the remote, fixed by editing the remotes configuration file and deleted duplicate remote definitions
2) The backend forgot that the EPG came through EIT for my tuners, ran mythtv-setup and corrected that
3) Tmdb stopped working on the frontend. Screwed about with the database table and ended up manually recreating it. It's still not 100% perfect but better than nothing.

Open points:-
1) When I delete a recording on the backend through mythweb while watching are recording the playback on the frontend stutters for afew seconds.
2) The frontend complains that it can't adjust the alsa audio buffer size, I can't even edit it as root!
3) Mythgame doesn't work anymore. I don't use it that often so I'm not sure if that's a new or old problem.
4) I still need to use vlc for playing back mkv's as the internal player has problems with some of my films. The quality of the rip isn't that good/the h264 stream isn't 100% standards conform.

All in all the upgrade went alot better than I though it would. On a positive note checking my large (6Tb) RAID5 array (first sunday of the month) on the backend only takes about 6hours under 11.04, under 10.10 it took about 12hours.

Regards
Ian Dobson

---

### Post by LowSky on 2011-05-02
fresh install and my hd pvr and hvr-2250 both wouldnt work. did an upgrade sequence from 10.04 and it worked fine... go figure.

with 11.04 i cant run unity without it messing up mythtv. had the issue with the remote where each press counted as two.. fixed with rerunning the setup on control center.

---

### Post by Dan_R on 2011-05-02
I had been running 10.10 with mythtv 0.24 fixes and had a few things  that were broken, such as WOL and ACPI wake up (unrelated to each  other), so I decided to upgrade to 11.04 and things only got worse. One  problem that arose right from the attempt to upgrade, leaving me with a  blank screen not knowing if the install was done. I then burned  mythbuntu 11.04 to a cd and upgraded that way.

Other problems from the upgrade include the HDPVR v4l drivers not  working, so live TV was broken, but I could still record fine. Playback  of recordings resulted in audio delays using regular analog ALSA. MySQL  was quirky, only allowing remote frontends to connect half the time, and  it would now take 2 tries to connect to the local master backend.  Mythweb audio streaming broke, but I was able to fix that. Mythfrontend  would often get stuck in a crash/reload loop. 

Because this did not resolve my WOL issues, which I really need to work,  I backed up everything and downgraded back to 10.04 when I had no  problems. I am now better off than when I had 10.10, all previous issues are gone.

---

### Post by nickrout on 2011-05-03
Why oh why do people do it? Upgrading is a recipe for disaster. Mythbuntu is an APPLIANCE, not a desktop machine. It's sole purpose is to provide a mythtv box. And the LTS version (10.04) provides the the latest mythtv packages.

---

### Post by ian dobson on 2011-05-03
Hi nickrout,

why not?

For me I upgraded my backend server to 11.04 as I needed a newer kernel for other work that I do on the box. As that involved upgrading mythtv to 0.24 I had to atleast upgrade mythtv to 0.24 on the frontend.

Linux is all about choice isn't

Regards
Ian Dobson

---

### Post by nickrout on 2011-05-03
Fair enough, a kernel upgrade is a genuine reason to upgrade. However most people don't have that reason, so why potentially bork a working system?

There have been a large number of threads on here to the effect that upgrades have produced serious problems, hence my recommendation.

---

### Post by agamotto on 2011-05-03
I no longer upgrade my linux systems until the 'new' version has something compelling that I 'must' have.  I will keep my configured, working system exactly as it is - working!  If I wanted to be a test subject for software/OS purposes, I would sign up as a developer...

---

### Post by pitbullofprogramming on 2011-05-03
Fresh install of 11.04 and it crashed after a while editing file with emacs. 
My screen just locked up.

---

### Post by nickrout on 2011-05-03
> **pitbullofprogramming said:**
> Fresh install of 11.04 and it crashed after a while editing file with emacs. 
My screen just locked up.


vi?

---

### Post by dsbw on 2011-05-03
> **nickrout said:**
> Why oh why do people do it? Upgrading is a recipe for disaster. Mythbuntu is an APPLIANCE, not a desktop machine. It's sole purpose is to provide a mythtv box. And the LTS version (10.04) provides the the latest mythtv packages.

Cool stuff. I try not to upgrade in-between releases. But it's cool that even though the front-end of the box isn't working, I can actually stream recorded stuff. 

This is my...5th upgrade, and every one I've done has fixed some things and improved others.

---

### Post by vanbob on 2011-05-05
I was running Mythbuntu 10.10 fine with the HVR-2250 and upgraded to 11.04.  Now it appears Mythbuntu can't find the necessary information from the card.  It looks like the same drivers/firmware from LowSky's post are still there, so something broke.

By the way, this started with my receiving the message "MythTV is using all inputs, but there are no active recordings?"  After messing around with this for quite a while, I found the setup of the capture cards "Could not get the info for card /dev/dvb/adapter0/frontend0 Subtype: Unknown  Error", which is probably reasonable since the directory /dev/dvb is no longer there after the update.

---

### Post by nickrout on 2011-05-05
That means the drivers are not loading. Try looking at the output of dmesg, and try loading the modules manually using modprobe.

---

