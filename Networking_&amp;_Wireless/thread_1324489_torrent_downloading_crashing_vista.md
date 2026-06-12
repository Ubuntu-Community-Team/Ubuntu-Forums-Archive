---
title: "torrent downloading crashing vista"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by nitstorm on 2009-11-12
used transmission client to download torrents first. when i booted into vista and used vuze to re-check the local contents that i had downloaded on ubuntu so as to continue with it  while working on vista,it took a long time to connect to the peers and finally started downloading and then my system just crashed!!! tried doing the same thing with vuze on both ubuntu and vista, still crashes!!! any solutions :S??

---

### Post by nitstorm on 2009-11-24
still no replies???? is this solvable?? jus curious if this has a solution, gonna get rid of windows in two weeks or so.. but still .. curiousity kills the cat :P

---

### Post by nitstorm on 2009-11-25
bump?

---

### Post by doas777 on 2009-11-25
sounds like it's either a problem network card, router, or isp. theoretically some one could be trying to dos you, but I would guess that it is your net card. prolly throwing a fit once the connection count hits a certain threshold.

by "crashed" do you mean that one second it is on, and the next it is rebooting/off? if that is the case, then you either need a new nic or a new/bigger powersupply.

---

### Post by nitstorm on 2009-11-25
yup jus reboots by itself but only wen i use vuze from where it left off on linux...

---

### Post by doas777 on 2009-11-25
> **nitstorm said:**
> yup jus reboots by itself but only wen i use vuze from where it left off on linux...

that usually indicates a hardware or system corruption problem. 
Linux is designed to allow programs to crash without taking the system with them.

are you saying that if you start a torrent from within vista and use only it to complete the download, that it works fine? how about the same scenario in ubuntu?

---

### Post by nitstorm on 2009-11-25
everything works perfect in ubuntu, its only wen i download the same file in vista from where i left off in ubuntu that the system crashes, on ubuntu it works super-smooth...
jus curious to know why its happening although i use vista very rarely these days, 

wondering if u could take a look at this doas777 its been bugging me for a while and no one seems to reply...  [http://ubuntuforums.org/showthread.php?p=8385247#post8385247](http://ubuntuforums.org/showthread.php?p=8385247#post8385247)

---

### Post by doas777 on 2009-11-25
in that case, all I can recomend is remember the old joke:
a guy goes in to the dr and says, "hey doc, my arm hurts if I do this", to which the dr responds (in a groucho marx voice), "then don't do that".

---

### Post by nitstorm on 2009-11-25
he he doing that exactly... :P

---

### Post by nitstorm on 2011-04-16
I finally think the problem lies coz of Vuze downloading to NTFS on Linux. I now use rtorrent to download to Ext4 when I am on Ubuntu, and rarely when I have to switch to windows, i copy the files from the Ext4 to NTFS partition and hash-check it there. When I do this, the system doesn't crash. Also the downloaded files are not corrupted. (Some of them were unusable on Windows after I downloaded them to NTFS from linux)

Took me a while to figure this out, considering the thread started out in '09 :P  But still, Thread Solved :D Cheers guys!

---

### Post by 3177 on 2011-04-16
I do believe the thread is not solved as you used transmission originally. You used rtorrent so the thread does still technically remain unsolved.

---

### Post by nitstorm on 2011-06-04
I think the problem was found - the downloading to NTFS partition was proving to be the problem. Download with any client to Ext4 and move the downloaded content to NTFS and things will stay fine when on Windows. Hence the thread is indeed solved.

---

