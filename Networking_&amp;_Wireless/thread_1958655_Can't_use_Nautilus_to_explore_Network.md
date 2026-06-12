---
title: "Can't use Nautilus to explore Network"
date: 2012-04-14
forum: Networking &amp; Wireless
---

### Post by klyndt on 2012-04-14
I'm having a problem connecting using SMB using the desktop Places -> Connect To Server 
or Places -> Network
or in Nautilus -> Location -> smb://xxxx.
I also can not connect any longer using Gigolo.

When I go to Connect to Server, my only option is Custom Location for the Service type.  Windows Share (and others) should be in there, but they are not.

What I can do is use the terminal window to connect to my various network drives using smbclient.  I can even use firefox to explore the drives using smb://xxxx in the address field.  Samba itself seems to be working but not the Nautilus interface?  What about Gigolo? This used to work fine, but some update I got several months ago broke it. I'm now really needing to fix this interface.

I have tried reinstalling ubuntu-desktop and nautilus and Samba to no avail.  I'm using Lucid 10.04 LTS.  After spending all morning reading and trying different things, I need some new suggestions (or some suggestions I may have missed).
Thanks,
Klyndt

---

### Post by JRV on 2012-04-14
Open a terminal and try:```
nautilus smb://HOST_NAME/SHARE_NAME
```

Running it from the terminal will show you the error messages, so you can figure what's wrong.

The terminal is your friend.

---

### Post by Morbius1 on 2012-04-14
Along with what JRV just posted the only thing I can think of that ties Nautilus and Gigolo together is gvfs.

Either you don't have the following packages installed:
gvfs-fuse
gvfs-backends

Or you are not a member of the fuse group:
```
sudo gpasswd -a username fuse
```After you add yourself to the group logoff and logon again for the group membership to take affect.

---

### Post by klyndt on 2012-04-14
I ran nautilus from the terminal and all I got was a pop-up window saying that it couldn't handle smb locations.

I checked my membership in fuse and I was a member.

Then I wanted to double check the gvfs packages mentioned and I noticed the backends was not installed for some reason.  I installed it and all is now well.  I'm not sure how that was uninstalled, but thank you for mentioning that.

Klyndt

---

