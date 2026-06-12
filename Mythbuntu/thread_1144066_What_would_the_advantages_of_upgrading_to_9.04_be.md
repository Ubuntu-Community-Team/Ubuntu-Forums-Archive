---
title: "What would the advantages of upgrading to 9.04 be?"
date: 2009-04-30
forum: Mythbuntu
---

### Post by Caps18 on 2009-04-30
[http://www.mythbuntu.org/9.04/Release_notes](http://www.mythbuntu.org/9.04/Release_notes)'

I've read the release notes, but I am interested in knowing what would be better if I wanted to upgrade to the latest Mythbuntu OS?  I am happy with my system right now, and only have a few issues (MythVideo organization/IMDB downloading, multiple USB IR receivers, and handling running out of hard drive space)  But I am not too interested in dealing with the headaches that might come from upgrading at this time.  That is unless there is something great that I don't know about.  7.10 is still working and if I ever got around to fixing MythVideo and entering in/downloading the correct movie posters it would be perfect.

---

### Post by jbman on 2009-04-30
The way I see it, if you have a working system leave it until 0.22 comes out as you will need to upgrade for QT4 support.

---

### Post by ian dobson on 2009-05-01
Hi,

I'm staying with 8.10. Running the VDPAU 0.21 backport and everythings working well, so no need to update. Until maybe 0.22 is out and running well.

Regards
Ian Dobson

---

### Post by Dewey_Oxberger on 2009-05-01
Newer version of the NVidia drivers.  The nvidia/alsa combo does audio over hdmi on 7000 series right out of the box.  That might be a plus.

---

### Post by jaketrunk on 2009-05-01
For me, the faster boot time was a real plus -- I now power off my front-ends when not in use.  I''m waiting to upgrade my backend until .22 comes out.

---

### Post by AlecJ on 2009-05-01
I'm on 8.10 now for the second time, but it's hard work! For me 8.04 was the most stable.

But with the new Nvidia drivers and the JYA backport's it's working well.

No I'm not going to 9.04 till I'm 100% that it will work, I've moved the desktop PC to 9.04 and so far so good..

---

### Post by Caps18 on 2009-05-04
Would it be possible to run a 9.04 frontend with a 7.10 backend(& frontend) system?  

I have a spare desktop that isn't doing anything right now, and this would solve my usb remote problem in the second room.  If it boots up in under 30 seconds, and if I can turn the front end computer on & off from the remote, I might do this.

---

### Post by klc5555 on 2009-05-04
> **Caps18 said:**
> Would it be possible to run a 9.04 frontend with a 7.10 backend(& frontend) system?  

I have a spare desktop that isn't doing anything right now, and this would solve my usb remote problem in the second room.  If it boots up in under 30 seconds, and if I can turn the front end computer on & off from the remote, I might do this.

Yes. In that you can link 9.04 to your 7.10 backend. (Assuming you've installed the Myth 0.21 Gutsy backports, of course). 9.04 does not boot in 30 seconds, however.

I did this for about a week with an old Thinkpad T23 that I used as a 9.04 Frontend (Regular Ubuntu + Mythtv packages, with disabled automatic mythbackend and MySQL startup) to my (then) 7.10 Master Backend/Frontend to see how the new version would handle. Worked perfectly.

---

### Post by Caps18 on 2009-05-04
I'm more concerned about the ability to turn the frontend on and off via remote than the amount of time it takes to startup actually.  That and having a working TV that turns on would be nice.

Is there any way to tell if I have installed the Myth 0.21 backports?  Is setting up the network stuff 'easy' (as easy as it could be in Linux)?

---

### Post by agamotto on 2009-05-11
None that I can see.  I tried 9.04 on my system as a clean install and the same things that didn't work in my current 8.04 setup still don't work.  IE - Archive DVD still crashes/dies at 'creation' time.  MythStream seems to no longer be able to parse wwitv or WWMP streams.  On the Hauppauge PVR 1800, the analog still doesn't work.  

Given the above, I just restored my 8.04 from my tank drive, and gave up.  To record DVDs, I just take the .mpg files out of /var/lib/mythtv/recordings, put them on a stick, then run DeeVeeDee to create the iso and burn to disc.

---

### Post by klc5555 on 2009-05-11
> **Caps18 said:**
> 

Is there any way to tell if I have installed the Myth 0.21 backports?  Is setting up the network stuff 'easy' (as easy as it could be in Linux)?

Two simple ways:

1) In System Status (from the frontend)

2) From synaptic.


Setting up the backend/frontend networking is pretty standardized across all Mythtv 0.21. Doesn't particularly matter if it's on Ubuntu 7.10, 8.04, 9.04, Slackware 12, or Knoppix Whatever, as long as the necessary Mythtv 0.21 pieces are there and running.

---

