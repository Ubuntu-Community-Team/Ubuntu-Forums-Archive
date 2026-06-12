---
title: "Auto login/mount OSX to Samba"
date: 2006-09-05
forum: Mac OSX
---

### Post by jonkun227 on 2006-09-05
I'm fairly certain this is possible, but haven't gotten around to doing it before. Can anyone tell me how to set OSX to auto login to a Samba server at startup or wakeup? I'm not sure how complicated this is, especially since I find myself using multiple networks through a single day. At home I have a file server for my own photography business (RAID, network access storage), and at work a similar setup for similar purposes.

So the more complicated question is: (Assuming I can make it log in automatically) Can I tell it to only attempt to log in to a certain network depending on which wireless network is available?


Thanks!


- Jon

---

### Post by kidders on 2006-09-05
I doubt that kind of auto-login scenario is terribly easy ...

You'd have to tweak several config files during boot to get OSX to authenticate against a different domain controller in the first place, and then tinker with the settings governing the username & password used to log into your machine. Any idea where they're stored?

I'm afraid I have no idea how to handle doing all that when your computer wakes up from sleep :(

---

### Post by jonkun227 on 2006-09-07
Yeah, I figured it was a long shot. Thanks, though!


- Jon

---

### Post by mike3k on 2006-09-12
I use an NFS server (my Ubuntu box), which I find works a lot better than Samba. The easiest way is to simply place an alias of the server volume in your login items.

---

### Post by kidders on 2006-09-12
NFS is only a filesharing protocol though :-(

---

### Post by jonkun227 on 2006-09-19
> **mike3k said:**
> I use an NFS server (my Ubuntu box), which I find works a lot better than Samba. The easiest way is to simply place an alias of the server volume in your login items.

Can you please elaborate on how NFS works better than Samba? I just reformatted everything (I screwed up way too many files and had nothing irreplaceable on the machine yet, plus I installed 2 new SATA drives for a RAID 1), and haven't yet set up the share. Any knowledge you can share here would be greatly appreciated. My network will be only Linux and OSX. No Windows allowed. (Well, I haven't started looking yet, but if I can't get Andrea Mosaic ([www.andreaplanet.com](www.andreaplanet.com)) to work in Wine I'll need to install VMware, as I need that program. But that will be on the same box as the server, so the share would be irrelevant, right?)

Thanks!


- Jon

---

### Post by kidders on 2006-09-19
Hi again,

Basically, Microsoft does as bad a job with filesharing as it does with most other things. Windows filesharing is overcomplicated, slow, and prone to idiotic glitches. NFS is faster and much more straightforward, but can perform dismally on slow networks nonetheless, because it's missing some common-sense random access tricks. If you're only using Macs & Linux on your LAN, you might want to consider Apple's filesharing protocol. Samba's only advantage is its wide recognition.

> Can anyone tell me how to set OSX to auto login to a Samba server at startup

I seem to have misinterpreted your initial question ... I took this to mean that you were running a samba PDC that you needed to log into at startup. It looks as though you don't want to log into the server at all, but just auto-mount a few shares at startup. Oops! Having fileshares mount automatically for you in OSX is fairly trivial, but you'll find that Windoze fileshares will fail to automatically reconnect after you wake your machine up from sleep. NFS or AFP are definitely far better choices for you :-)

One other consideration is file management. Both of your underlying operating systems support all kinds of nice things like permissions management and fairly unrestricted filenames. As a simple example, using samba would mean that you could be prevented from copying a file called ".#$$ C:", simply because it would upset Windows. There would also be tons of unnecessary ownership/permissions mapping going on that has the potential to cause all kinds of pointless headaches.

> The easiest way is to simply place an alias of the server volume in your login items.

Mike's suggestion will work perfectly, provided your computer isn't a laptop that might periodically find itself outside your own LAN. A slightly more robust solution would be to write a quick applescript to detect your location before mounting your shares.

---

### Post by jonkun227 on 2006-09-19
Yeah, I guess I didn't word my original request very well. Basically at work we have a Samba server because the sales guys won't use Macs. Every time I want to mount the fileserver I have to actively click on the alias in the finder for it to mount. Even then it doesn't consistently automatically use the password from the keychain. Sometimes I have to click "okay" or whatever the prompt is, with the username and password already filled in. Not sure why.

Anyway, at home I'm setting up a file server for my own photography business. So the original question was complicated because I'm not always on the same network and therefore not always connecting to the same server. 


Thanks for your input. It makes perfect sense. The naming restrictions alone are a good reason for me to not use smb. 


- Jon

---

### Post by kidders on 2006-09-19
Hi Jon,

Perhaps you could give AppleScript a try in that case :-) You could use something like your IP address to guess what network you're on, and mount the right set of shares at login that way. Hitting CMD+K every now and then is hardly back-breaking work, but I find it irritating too :-P

---

