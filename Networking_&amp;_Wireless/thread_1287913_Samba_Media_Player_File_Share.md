---
title: "Samba Media Player File Share"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by kdmcmullan on 2009-10-10
Hi.

I'm reasonably new to Linux, but not to networking. I decided to take the plunge and installed Ubuntu. So far so good. I have installed Samba and shared some folders.

Now, we have a Clarus Magicbox internet radio and an Emprex ME1 video media player. The ME1 is able to open my shared video folder no probs. However, the internet radio is unable to open my shared MP3 folder.

When I browse down through the network neighbourhood, to my Samba server, select it, the radio reboots!

Anyone ever tried to share MP3s with an internet radio before?

Here's some odd behaviour: When I browse the tree from my XP machine, I can see the MP3 folder OKay, but the video folder asks me for a password. This is really odd because the two sections in my smb.conf are identical.

I do restart the daemons after each smb.conf edit.

Here (I think) are the important bits:

```
[MP3]
    comment = MP3 Folder
    locking = no
    path = /home/public/MP3
    guest ok = yes
    writeable = no
    browseable = yes

[Video]
    comment = Video Folder
    locking = no
    path = /home/public/Video
    guest ok = yes
    writeable = no
    browseable = yes

```

Is it significant that when I attempt to **sudo smbpasswd -a -n guest**, I'm told it can't add or modify the user?

The other potentially pertinent thing is that I can't seem to telnet to the machine! I can VNC to it and (as mentioned above) some other members of my network seem able to SMB to it.

Anyone any ideas, please?

---

### Post by kdmcmullan on 2009-10-23
I got a note from the manufacturer that the Internet Radio needs to be able to write to the shared directory and have modified the share accordingly. Still no joy.

This is doing my head in. Has anyone got any clues? The box reads a directory shared from a Windows XP machine.

Alternatively, I wonder if it's using SMB at all. Can anyone recommend a uPnP media sharing thingy for Ubuntu?

---

### Post by dmizer on 2009-10-23
Does the internet radio support m3u playlists? If so, you could try this: [http://www.gnu.org/software/gnump3d/](http://www.gnu.org/software/gnump3d/)

---

### Post by vinutux on 2009-10-23
mm..very informative...........

---

### Post by dmizer on 2009-10-23
> **vinutux said:**
> mm..very informative...........

In my experience, these special devices like this internet radio and many NAS devices just don't play well with Samba. Sometimes it's easier to try an alternative rather than to spend days trying to figure out how to make Samba work.

If Samba is the only option, that's another story. But I was hoping that gnump3d could provide a quick simple solution.

---

### Post by kdmcmullan on 2009-10-23
> **dmizer said:**
> In my experience, these special devices like this internet radio and many NAS devices just don't play well with Samba.

THAT is probably the most useful piece of information I've had on the matter! It's probably been time saving to know that it simply might not work. It's irritating, though, that it appears to work with Micro$oft's SMB implementation. (Or maybe it's using something different, but just not apparent.

> **dmizer said:**
> Sometimes it's easier to try an alternative rather than to spend days trying to figure out how to make Samba work.

I've already spend days on it. A few hours here and there probably amounts to *weeks*.

> **dmizer said:**
> If Samba is the only option, that's another story. But I was hoping that gnump3d could provide a quick simple solution.

Well, guess what? I took a fit of the headstaggers and installed MediaTomb. The HTTP based front end is not terribly functional. I think it's essentially a headerless, or commandline tool and teh front end has been added as an afterthought. I normally shy away from such software, but I was desperate.

Without turning this into a review, it detected up my MP3 collection instantly (not to mention my photos and videos) and with absolutely no configuration at all, I was playing music in seconds.

**/me is very, very pleased.**

If I'm honest, it was the suggestion of "alternatives" that reminded me that my player does UPnP.

Thanks, all. Case closed.

---

