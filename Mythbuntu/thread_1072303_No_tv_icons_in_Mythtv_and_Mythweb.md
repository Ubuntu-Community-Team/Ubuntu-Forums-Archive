---
title: "No tv icons in Mythtv and Mythweb"
date: 2009-02-17
forum: Mythbuntu
---

### Post by Martin B on 2009-02-17
Hi,

I have a Ubuntu 8.10 Server acting as backend for my Mythtv-setup. I also have two frontends.

It has all been running smoothly for more than a year until recently I cannot see the channel icons any more anywhere...
I have verified that they are still there in /home/user/.mythtv/channels but they do not show up in Frontends or Mythweb any more.
I use the Swedish Grabber "Swedb".
As a last resort I even reinstalled xmltv and the grabber last night, to no avail.

The only thing I have not checked is the actual Mythconverg database to see if it might point to the wrong path, do not know how/where...

Grateful for any help with this, it is a minor problem bu nonetheless annoying.

//Martin

---

### Post by Archmage on 2009-02-17
Use the channel editor in the mythtv-setup to add the icons. Don't ask me why they disapear at the first place.

---

### Post by Martin B on 2009-02-17
> **Archmage said:**
> Use the channel editor in the mythtv-setup to add the icons. Don't ask me why they disapear at the first place.

Hi,

I have the channel icons downloaded, I get them together with the EPG data from the Grabber when I run "Mythfilldatabase". The problem is that I cannot see them in the guide or in Mythwen. Must be a wrong path/broken link or something of the kind...
Any other suggestions??

---

### Post by Martin B on 2009-02-17
The oddest thing just happened...
I thought to try and run Mythfilldatabase logged in as root; whatdoyouknow, all of a sudden a channels folder was created and filled with icons and everything worked (except for one icon which does not show).
The funny thing is that in setup I clearly specify the path to be /home/user/.mythtv/channels/xxx.png.
I would very much like to know why the above mapping does not work.

---

### Post by uMuppet on 2009-02-17
Perhaps a permissions problem.  The icons were there, the path was correct but Mythtv did not have read permissions, OR mythtv was looking at /home/mythtv/.mythtv/channels/.... instead.

If you want to look at the database use MySQL Query Browser which is available through apt.

---

