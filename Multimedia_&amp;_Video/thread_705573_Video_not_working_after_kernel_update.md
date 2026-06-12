---
title: "Video not working after kernel update"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by Dark Neutron on 2008-02-23
Okay, the other day, I updated my kernel from 2.6.20-16 to 2.6.22-14. After I rebooted, the video no longer works.

Specifically, after getting through the GRUB screen, the monitor says it is no longer receiving a signal and stays that way. Before the update it had been doing the same thing, but would eventually get a signal again and show the login screen.

I tried logging in with the old kernel, but no luck. I also tried changing the xorg.conf file (using failsafe mode) to use the generic 'nv' driver instead of the restricted 'nvidia' one, but that did not work either.

I also tried logging into failsafe mode and switching to init 5 from there. The computer locked up after the line saying "loading local boot scripts: /etc/rc.local". I also tried to start the X server from failsafe mode and it worked, but I could not find anything that would allow me to boot normally.

I am not sure if it makes a difference, but I have both Gnome and KDE4 installed...

---

### Post by sanddgroper on 2008-02-23
I think after a kernal update you need to reload the restricted drivers.
But it is odd that the nv driver dosen't work.
Have you tried downgrading again to the vesa driver.
From what I see in here upgrading seems to be fraught  with danger.
seems much better to do a fresh install.

Cheers
Sandy

---

### Post by ktulu1115 on 2008-02-24
> **Dark Neutron said:**
> Okay, the other day, I updated my kernel from 2.6.20-16 to 2.6.22-14. After I rebooted, the video no longer works.

Specifically, after getting through the GRUB screen, the monitor says it is no longer receiving a signal and stays that way. Before the update it had been doing the same thing, but would eventually get a signal again and show the login screen.

I tried logging in with the old kernel, but no luck. I also tried changing the xorg.conf file (using failsafe mode) to use the generic 'nv' driver instead of the restricted 'nvidia' one, but that did not work either.

I also tried logging into failsafe mode and switching to init 5 from there. The computer locked up after the line saying "loading local boot scripts: /etc/rc.local". I also tried to start the X server from failsafe mode and it worked, but I could not find anything that would allow me to boot normally.

I am not sure if it makes a difference, but I have both Gnome and KDE4 installed...

No... it's not you.  I normally don't touch upgrades and just take care of it with the new release (fresh install), but this time I decided to update and had the same exact issue as you.  I was able to get into X with binary driver after doing an 'apt-get install nvidia-glx' to set up the driver again.  Having difficulty enabling desktop effects though, I just can't believe I havn't seen tons of postings over this.

---

### Post by ktulu1115 on 2008-02-24
Apparently, a simple manual install of the nvidia drivers resolved all my issues.  Give it a shot.

---

### Post by Dark Neutron on 2008-02-24
Okay, tried the vesa driver but nothing changed.

ktulu1115, I tried what you said, and here is what happened:

when I tried to install nvidia-glx, it said nvidia-glx-new was already installed. I told it to go ahead (can't be worse then what it is now). Then it said it could not find the mirror to download it from.

Figures. The Ethernet port does not work from failsafe mode, and I am unable to get to init 5 either from a normal boot or manually.

Any other ideas?

P.S. Let me try init 3 and see if that will let me download stuff...

[Edit]

I tried to go to run level 3, but it locked up at the same place (right after "loading local boot scripts: /etc/rc.local"). Maybe this is not a graphics problem after all?
Another thing to search the forums for.

---

### Post by Dark Neutron on 2008-02-24
So it is *not* a graphics problem.

I looked up the "loading local boot scrips" lockup, and one post said that there computer did eventually boot up after 30 minutes.

It only looked like a graphics problem because my new monitor (a 19" wide screen LCD) always looses the signal when ubuntu is booting (not sure why). When the computer took  30 minutes to boot, I assumed it had booted fine but the graphics were not working.

Now I have an even harder problem to solve...

(Thank goodness for dual booting. So far, at least one OS works at any one time.)

---

### Post by ktulu1115 on 2008-02-24
Hmm...  in that case I'm not entirely sure what the issue may be.  I was going to suggest using wget and providing you the URL to download the latest NVIDIA driver from, then manually install.  Since it's some other issue you're having I do not know what to suggest.

Perhaps if you could post some more details, symptoms, relevant error messages in /var/log/messages, etc...   it would help to pinpoint the problem.

---

