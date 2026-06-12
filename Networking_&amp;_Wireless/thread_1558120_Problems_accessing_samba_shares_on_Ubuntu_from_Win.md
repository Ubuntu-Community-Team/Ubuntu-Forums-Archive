---
title: "Problems accessing samba shares on Ubuntu from Windows 7"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by rage_311 on 2010-08-21
Hi all,

I've been pulling my hair out with this one... I've searched all over and tried everything I could think of before posting here.

My goal is to set up a samba/ftp/print server with a few other things on it.  I've got samba all set up pretty well, and any shares that don't require a username/password work just fine from my Windows machine.  I can browse to those and read them just fine.  The problem happens when I try to browse to a share that requires a valid user to log in.  If I browse to it in the network in Windows, it pops up with the Windows log-in window.  When I enter in the appropriate username/password combination, it just tells me that the "specified network password is incorrect."  I'm not sure whether the problem lies in my samba config on my linux box, or the way that Windows tries to send the login info to it.  Here's what the login window looks like in Windows (note the Domain portion, which bothers me).

[IMG]http://i11.photobucket.com/albums/a158/rage_311/LoginBox.jpg[/IMG]

I've tried to do a backslash before the username so that it no longer says I7 for the domain, but that still doesn't get me anywhere.

Thanks in advance for any help!

---

### Post by rage_311 on 2010-08-21
Well... I feel a little silly now.  I just figured it out.  It was because I had "security = share" in smb.conf instead of "security = user" like it needed to be to get this to work properly.  I'm still not entirely sure of the difference, but that got it to work the way I wanted!

---

