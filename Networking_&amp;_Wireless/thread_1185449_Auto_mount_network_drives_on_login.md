---
title: "Auto mount network drives on login"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by ZackM on 2009-06-12
Okay... I'm a tech guy for a school corporation in Indiana. We just received a grant to get third and 6th grade laptops (2nd grade got theirs last year) and we're putting Ubuntu on them. I'm working with the 6th grade ones to network them with Microsoft's Active Directory, which I have already done. Now the problem is these kids have never had their own login before, nor have they ever had their own drive before (H:\username##$). They can get to their drive, but they have to navigate through the server, and the user pools in order to get to their specific folder in the server. I find this unacceptable. They don't have access to these folders, however I'd rather them not have to go through it that way, in order to keep some security in case something were to go wrong and they did somehow gain access. 

So I want to be able to have their drive show up automatically when they login. I don't really mind where, whether it be the desktop, the home folder, or the computer folder. Where doesn't bother me, however how is the problem. I've been working on this for a couple of days now and haven't had much luck. I found an older thread from 2006 about it and was going to ask there, however it was from 2006. I was able to get the administrative account to do what I wanted. The contents of the administrative folder in the server showed on the desktop on login without any problem whatsoever with this code:

//SERVERIP/username /home/WORKGROUP/username/Desktop smbfs credentials=/home/WORKGROUP/username/logon,uid=username,gid=106 0 0

Granted I'm not giving out any of the server information. Now I can admit I don't know everything about Ubuntu, UNIX, Linux, or any other distro out there. However, I do have mild experience. I suppose I'm an intermediate? Anyway, the point is I'm not completely stupid. Now, with that little line in etc/fstab I can get the contents to display on login, like I explained earlier. One problem, however, is that the code pulls the username and password from the logon file in the administrative folder. Now, the kids wouldn't have access to that folder anyway, considering it's in the administrative area, but they'd have access to their own. These kids like to wander and explore, which is fine but I don't want them finding this file and deleting it, nor do I really want to go through all 200+ laptops we have and write in each one. Luckily, however, the only person that will get the contents is the person designated to it, which is obvious. We'll have multiple people logging onto one computer throughout the day however. Thus a dilemma.

So, here's my question(s). Is there a way I can make that line wildcard in order to pull from each profile that logs on and grab their drive and show it?  For example, something along these lines:

//SERVERIP/%username% /home/WORKGROUP/%username%/Desktop smbfs credentials=/home/WORKGROUP/%username%/logon,uid=%username%,gid=106 0 0

Where %username% is the wildcard value that would allow the person logging in to view the contents of their drive on their desktop. I think there's a way I could do something like that, but I'm not completely sure. Having the logon in their profile still causes an issue. Perhaps making a mass logon file in the etc folder, where they couldn't read it or write to it, and have it read from there. However, I believe that would also disallow fstab to read from it as well. 

Here's the point before I start rambling off everything that's parsing through my mind. I'm at a loss. If anyone knows how to go about doing this, your help would be greatly appreciated.

Another tech admin from another school corporation suggested using Ubuntu Tweaker, but it won't download right. The server it's pulling from isn't responding, so I can try it later or something I guess. Anyway... If you know how you could do this, that'd be awesome.

Thanks

---

### Post by Iowan on 2009-06-12
[Here]("http://ubuntuforums.org/showthread.php?&t=283131") is a FSTAB How-To. I should point out that SMBFS is deprecated in favor if CIFS.  [Another]("http://ubuntuforums.org/showthread.php?t=288534") How-to that might be handy... and a [follow-up]("http://ubuntuforums.org/showthread.php?t=1169149") to help with Windows-sharing problems.  Good luck!

---

### Post by ZackM on 2009-06-15
Hey thanks a lot. I'll read up on all of that and figure out how to get it all set up. I have figured out a way to get the stuff working, but the kids would have to login and everything first, and then I'd have to go back in and mount -a. Lol, well that's a hassle. So, hopefully I'll be able to figure out something a little better from that documentation. 

Thanks again

---

