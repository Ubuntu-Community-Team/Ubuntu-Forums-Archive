---
title: "OSD on Mythtv 0.21 flickering only during live TV"
date: 2008-03-13
forum: Mythbuntu
---

### Post by Hugolp on 2008-03-13
Hi

I am running Ubuntu Gutsy on a server runing only Mythtv backend and two computers running Mythtv front-end. Yesterday I upgraded to .21 and everything is fine except on one anoying detail. While watching liveTV or a recording the OSD flickers badly and constantly. The video is fine, no problem whatching the video stream when the osd is on screen (nor when is off screen). It doesnt happen in MythVideo. When I  am watching a movie the OSD is fine. No problem at all. Its only watching tv and tv recordings. This happens on both front-ends.

The hardware is quite linux friendly and both were fine in .20 Both video cards are Nvidia using propietary drivers (7100GS and 6150), AMD CPU's and enough RAM in all of them. Not CPU usage not RAM hits even above 65% on any of the computers.

One detail is that the OSD only flickers when the tv video is playing. There is 1 or 2 seconds delay when I hit LiveTV and the OSD shows but there is no video yet. Then the OSD doesnt flicker, but as soon as video comes in the OSD starts flickering.

I have tryed different OSD's and the problem remains.

I am not english native so for me flicker means that it looks like the OSD is going on/off very quick, so you cant see it going off or on but theres are artifacts, its not solid. Hope flicker is the apropiate word in english.

Anyone having this issue or any solution?

Hugo

PD: I have added this as a Mythbuntu bug. In case anyone having the same problem or is interested -> [https://bugs.launchpad.net/mythbuntu/+bug/201869](https://bugs.launchpad.net/mythbuntu/+bug/201869)

---

### Post by RobJohnston on 2008-03-13
I'm having the same problem.

All my frontends now have a flickering OSD, both with live and recorded this.

There's a blue line appeared along the top of the screen which seems to be causing it, but I can't see any recent posts about this.

Rob.

---

### Post by Hugolp on 2008-03-13
> **RobJohnston said:**
> I'm having the same problem.

All my frontends now have a flickering OSD, both with live and recorded this.

There's a blue line appeared along the top of the screen which seems to be causing it, but I can't see any recent posts about this.

Rob.

RobJohnston can you go to the bug report on launchpad (you have the link in my previous post) and leave a message confirming this bug, so developers are aware that is happening to different people?

Hugo

---

### Post by mwc on 2008-03-13
I think you will find this is caused by the Bobx2 deinterlacer which is now used by default in .21.

Bobx2 has always had this issue, I don't think it is considered a bug as from what I understand there is no way around it.

Cheers

---

### Post by Hugolp on 2008-03-14
Yes, it was the bob2 isue. Once I selected other deinterlacing method the flickering was gone.

Thanks

Hugo

---

### Post by p$y on 2008-03-14
where can I change the bob2 setting?

---

### Post by Hugolp on 2008-03-14
> **p$y said:**
> where can I change the bob2 setting?

Settings -> TV Settings -> Reproduction -> third page (named Playback profiles)

---

### Post by p$y on 2008-03-14
Thanks Hugolp,

and what I have to change there? the default playback profile was CPU+, now I will try "normal".

EDIT: 

I had to change the settings of the profile and on "next" you can change the deinterlace options. I disabled booth and now I've a huge CPU improvement.

---

### Post by roazena on 2008-03-30
Thanks billions to everyone here. This fixed it on mine as well.

---

### Post by semidark on 2009-08-25
Yes. This helped a lot. Now everything runs much smoother.

Ubuntu Intrepid Ibex
geforce 9600 GT 

Thanks a lot

---

