---
title: "Network slows down randomly"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by DragonSpawn on 2010-02-02
Hello.
I have had some trouble with networking on my little barebone (Asus Pundit, Ubuntu 9.10, Nforce ethernet integrated) for a while.
At random intervals a random amount of my computers in my home network get extremely poor speeds from my server.
For example:
Right now if I try to transfer a file from my barebone to this computer I will only get 300kbyte/sec. It does not help to reboot either computers, shut them down, switch cables etc etc. However if I try to do the same from the girlfriend's computer she gets like 40mbyte/sec. Just the other day the situation was swapped, I got great speeds and she got almost no speed at all. Other times neither of us has any problems and, of course, sometimes it works for neither of us.
If I do an online bandwidth tester during these periods it shows absolutely no problems at all, it shows the proper 100/10 speeds.

I have had this problem for a very long time and I previously used Debian and the situation was the same there. We are using a gigabit switch for our network and all our network cards are gigabit as well.

The files are usually transferred via samba to our Windows 7 computers (has previously been as far back as windows xp with the same issues). However it is not limited to samba, it gives the same result if one goes via proftpd or the webserver.

Any advice would be appreciated. I have not mucked about with the network settings at all so it is configured just as it was when Ubuntu was installed on it.

Could it be an nforce driver issue? Wonky network setting?

---

