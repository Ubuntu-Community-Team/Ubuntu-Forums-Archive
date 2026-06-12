---
title: "newb: File sharing questions"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by gihe on 2010-09-01
Hi. I installed 10.04 last night for the first time ever - always used Windows in the past - and I'm a bit perplexed by file sharing.

There seem to be several options:
1) Install Samba and set up shares via the Samba Server Configuration window
2) Right-click a folder and choose Sharing Options..
3) Personal File Sharing in System>Preferences

What are the differences between these methods?

The reason I ask is because I originally set up a share using Samba and got my Windows 7 box to read/write to it pretty easily. My XP box, however, could only see the share - any attempt to delve into it resulted in permission denied.

So I deleted the Samba shares and tried method (2), simply right-clicking the folder and setting up the share. Again, my XP box can see the share but not access it. Win7 is fine.

I haven't tried method 3 because it tells me I haven't got the required packages installed.

I've got to the point where I'm not sure what I'm doing anymore and would appreciate some basic guidance (and I mean, basic!)

Thanks.

---

### Post by gihe on 2010-09-01
Anyone?

---

### Post by gihe on 2010-09-02
OK - last try. If anyone wishes to help, then I'd appreciate it.

If not, then I guess I'll go back to XP.

---

### Post by sikander3786 on 2010-09-02
You should use Samba for file sharing between Ubuntu and Windows. I haven't used Personal File Sharing and am not sure if it is able or not to share files with other OS.

Right clicking on a folder and sharing it via nautilus uses Samba. There is no difference except that the shares are not listed in Samba configuration file.

Windows 7 can access the same shares and Windows XP can't. Seems to be an authentication issue. What are the permissions on the shares? Which user account for accessing the shares? Try accessing from Windows XP with the same user account as on Windows 7 (if not already doing that).

Post back for further help.

---

### Post by Dragonbite on 2010-09-02
I think the file share handles adding Samba, etc.

You say you can't see it, but can you pull it up by using the IP address (in Windows, use \\192.168.1.1 or whatever)?  It may be just not showing up on your network.

---

### Post by sikander3786 on 2010-09-02
> **gihe said:**
> If not, then I guess I'll go back to XP.

I didn't read this post at first. Thought it was a formal bump. But it isn't.

You should use whatever OS you want to use, the one that satisfies you the most. Anyone is not here for stopping one from switching OS, we are here for volunteer support. I am not trying to be rude but please be patient while asking for help.

---

### Post by Dragonbite on 2010-09-02
> **gihe said:**
> OK - last try. If anyone wishes to help, then I'd appreciate it.

If not, then I guess I'll go back to XP.

You cannot expect to have your questions answered in one day!  You didn't even give it 12 hours before you started bumping.

---

### Post by gihe on 2010-09-02
> **Dragonbite said:**
> You cannot expect to have your questions answered in one day!  You didn't even give it 12 hours before you started bumping.

Actually, I first posted yesterday afternoon, waited about 12 hours for the first bump and then another 16 after that - sorry if that's considered too impatient - I realise there's a lot of activity on the board and my message had slipped off the radar before I could blink. Not sure how to do a formal bump...

Anyway, it's sorted. It was simply due to the user account in XP having a different username. And my main question about the various sharing options has been answered by sikander3786 - so all happy this end.

---

