---
title: "XBMC and ubuntu 8.04 desktop/samba"
date: 2009-03-29
forum: Multimedia Software
---

### Post by buck2825 on 2009-03-29
Hi all thanks in advance for any help ya'll are the best.  

setup
file share on ubuntu 8.04 desktop running all kinds but mainly mdadm for RAID 1, that is were media is stored OS is on a third 40 gb. media is mounted to /mnt/storage.  samba share to lan.  

problem
i'm having this same problem on both my xbox (original) and laptop running ubuntu 8.10 

once I launch xbmc, drill down the any movie I with to watch, then start to watch everything is fine for a little while.  I'm not giving a time because it changes.  While watching the movie/clip the system acts like I pressed pause.  About 5-10 sec. later the system begins playback again but for only 1/4 of a sec.  then the file is stopped.  If I rerun the same file it will do it again, just in a different point in the movie, sometime sooner, sometime later.  All my movies do this, mpeg, avi.. you name it.  I have been working with the maintainer of XBMC for the xbox and he is puntting to the problem being on my samba "server" (desktop os)  any help would be great.  Thanks      

to be very clear this problem is accruing on XBMC compiled for the xbox and the version complied for ubuntu 8.10.

---

### Post by Linoobius on 2009-03-30
buck2825,

What happens if you play one of the affected video files with a stand alone media player on the ubuntu 8.10 machine? Does it play smoothly all the way through or does it exhibit playback issues like it does through XBMC? I think this would help isolate whether it's an XBMC issue or a Samba issue.

Linoobius

---

### Post by buck2825 on 2009-04-05
Ok, I checked this out this weekend.  tried to us totem, it didn't work real well.  Never showed any video some audio.  so i tried VLC worked great.  up until it paused. just like XBMC only when VLC started to play again, VLC started playing again as if nothing had happened.  Later is paused again this continued until I stopped the video.  I'm thinking I have a problem with my software RAID 1 timing out?  any RAID experts?

---

### Post by buck2825 on 2009-04-07
my file server has three hard disks one 40gb os drive and two 1.5 tb mirror for file storage.  

moved a movie to my desktop on the OS drive and shared it.  it worked perfect both in VLC, and XBMC on my laptop and XBMC on my xbox.

This seems like a definite RAID issue I'm using mdadm to run my software raid.  

Help please.

---

