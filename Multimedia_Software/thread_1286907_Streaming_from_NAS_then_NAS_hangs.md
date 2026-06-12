---
title: "Streaming from NAS then NAS hangs"
date: 2009-10-09
forum: Multimedia Software
---

### Post by thedouchebag on 2009-10-09
Hi all,

I have 4 systems all running Ubuntu 9.04[INDENT]A server that is my acting NAS
A laptop 
My old desktop
My new desktop
[/INDENT]The problem that I seem to be having is that when I try to stream media (specifically video) from my NAS to my new desktop, the server hangs after a few minutes of streaming. This was not the case with my old desktop, and is not the case when I stream via my laptop.

Given that all the computers are running the same version, I am very confused by this. Originally I installed the new desktop with 8.04 (long term release). Once this problem came up I decided that it could be because of the version, so I upgraded. Since upgrading and still having the problem, I am dumbfounded. I was able to copy about 20GB to the NAS from the new desktop without problem.

---

### Post by dannyboy79 on 2009-10-09
you'll need to explain how your streaming media? are you mounting the server shares on the new desktop via samba or nfs OR what program are you using to stream media, VLC, mplayer, totem, or what? What kind of network do you have, swithes, router, 100baseT or Gigabit ethernet? please give more details or it'll be impossible to help.

---

### Post by thedouchebag on 2009-10-09
NAS is mounted as a shared drive (NFS)
Network is wired gigabit (between the desktops) and wireless-G to the laptop (or gigabit if plugged in)

Opening the files from the mount with VLC player, file plays for what seems to be a random amount of time (anywhere from 1 minute to 12 minutes) then the NAS hangs.  Can not access the drive (via NFS), can't SSH to the box, can not even ping it.

---

### Post by dannyboy79 on 2009-10-10
> **thedouchebag said:**
> NAS is mounted as a shared drive (NFS)
Network is wired gigabit (between the desktops) and wireless-G to the laptop (or gigabit if plugged in)

Opening the files from the mount with VLC player, file plays for what seems to be a random amount of time (anywhere from 1 minute to 12 minutes) then the NAS hangs.  Can not access the drive (via NFS), can't SSH to the box, can not even ping it.

if the server is dieing then it almost sounds like you have a configuration problem on the NAS server. I could see if just the NFS mounted share stopped responding but if you can't even ssh into the server or even ping it then I would say you need to view the cpu usage and what not when streaming from the NAS server and watch it. it sounds like its locking up. what are the hardware specs of the NAS server? also does this happen when opening files with mplayer from the remote machines? i would try other players. can you also post your /etc/exports file so I can see how you're sharing your NFS shares? also your remote machines /etc/fstab entries for mounting those shares?

---

