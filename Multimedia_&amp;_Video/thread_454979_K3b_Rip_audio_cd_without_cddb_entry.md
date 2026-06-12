---
title: "K3b: Rip audio cd without cddb entry"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by shaun.nolan@gmail.com on 2007-05-26
Does anyone know how I can rip an audio cd with k3b if there is no cddb entry?  k3b is giving me a 5 second message that there is no cddb entry and then it disappears and leaves me back at the main menu screen.  Surely there must be a way of ripping a cd without needing a cddb entry.

---

### Post by fishoutofwater on 2007-06-18
I have a problem like this too: when I go to rip a cd (which I am sure will have a cddb entry) k3b sees the files but it says it can't find a cddb entry so I should enable remote cddb in k3b settings - I checked this and the box is already ticked.    It rips the tracks ok, just without any tags or filenames.

Anyone know what I can do about that please?   (I am a newbie so please spell it out for me if its complex!!)

Thanks

Andy

---

### Post by jrullan on 2007-12-25
I am having the exact same problem with Kubuntu 7.10. Apparently K3b has a bug. Someone please shed some light.

---

### Post by perrishm on 2008-01-03
same problem on Kubuntu 7.10. work around is to run as root. I did a #kdesu k3b it queried online for my CD's and saved to a local cache /root/.cddb/ abd you can add this to your profile when run. I copied mine to ~/.xine/cddbcache which I use with Amarok. nonetheless you should be able to run and rip as root.
hope this helps

---

### Post by David Canarias on 2008-07-13
I am having the same problems with K3b and up popping the cddb icon. Doesn anyone have a solution as I just can't burn an mp3 CD no matter how I try. It's very frustrating.
Thanks

---

