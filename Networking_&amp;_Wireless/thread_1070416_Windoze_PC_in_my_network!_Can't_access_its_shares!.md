---
title: "Windoze PC in my network! Can't access its shares! :::"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by DexterLB on 2009-02-15
aaah, this is driving me crazy! I've been struggling to fix it all day, with no luck.

I've got a Win98 computer upstairs, and it's connected to my network. Its shares are visible through "nautilus smb:///" but when I try to mount the share (using HAL) I get a password prompt. And when I enter the password, I get "Error: Failed to mount Windows share". If I remove the password from the share, trying to mount it with HAL actually mounts it and everything works. But I want to have a password.

From dad's Vista laptop, entering "dexterlb-server\guest" for user and entering my password does mount the share. I tried to put "dexterlb-server\guest", "dexterlb-server/guest" and "guest@dexterlb-server" in the user field on the Ubuntu machine, but the same error appears.

Trying to mount it with ```
 sudo mount -t smbfs //192.168.1.3/DRIVE_E /media/server_drive_e
``` asks me for the password and outputs this error: "mount error 112 = Host is down" When I remove the password from the share, it outputs the same error! Though HAL does mount it with no password! That's a double problem, please help!

---

### Post by graysky on 2009-02-15
Windows 98!  You're kidding, aren't you?  In any case, read [my post in this thread](http://ubuntuforums.org/showthread.php?t=1070308) for syntax using usernames/passwords.  I dunno if it'll work since I haven't tried connecting to a w98 share, but I don't see why it wouldn't work for you.

...what are you using the win98 box to do if I may ask?  Just as an FYI, that O/S hasn't been updated/security patched in years and is very insecure.  I wouldn't use that box to access the internet at all.

---

### Post by DexterLB on 2009-02-15
Well, if I can't get windoze 98 to work with those shares, I'll install xubuntu on that machine, but dad won't be very happy. As for security - I have nothing vital on that box - I just use it as an IRC and torrent server. Now I am at a friend's house, when I get back I'll try the syntax from the thread you posted a link to. Thanks for your reply!

---

### Post by graysky on 2009-02-15
> **DexterLB said:**
> As for security - I have nothing vital on that box - I just use it as an IRC and torrent server.

Dude, IRC and torrent serving are pretty dangerous since you're open to the WAN!  I wouldn't do that from Win98.  Also, even though you have nothing of value on the box, consider a hacker gaining access to it and doing stuff from it.  That is the greater fear.  Plus, theoretically, this person could gain access to other machines on your LAN from that box too.  Bad idea.

> **DexterLB said:**
> Now I am at a friend's house, when I get back I'll try the syntax from the thread you posted a link to. Thanks for your reply!

Why not just ssh into the box?  You can even use VNC secured via ssh.

Two guides on these topics:
[HOWTO: Secure vnc or apache via ssh tunnels to keep your box hacker-free](http://knoppmyth.net/phpBB2/viewtopic.php?t=19211)
[HOWTO: Run vnc4server for totally parallel sessions](http://knoppmyth.net/phpBB2/viewtopic.php?t=19428) and for a Gnome-specific configuration, see [this post](http://forums.debian.net/viewtopic.php?t=31848).

If parallel vnc isn't your think, simple enable vino/remote desktop from within Gnome.  That's lame though since it requires you to be logged in to work whereas vnc4server can be started/stopped from a shell (via ssh if you're away) and doesn't require any physical access to the box at all.

---

