---
title: "Guide for Accessing Windows 7 Shares from Ubuntu"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by pgn674 on 2010-09-29
I have never, ever been able to access any sort of Windows 7 share (folder, printer, listings, or otherwise) from Ubuntu. I can't even get Ubuntu to list what things are shared. I've tried on and off for almost a year now, looking at many guides and other forum posts, and nothing seems to work.

What I have noticed, however, is that on the Windows 7 computer, there are tons and tons of different settings that can be considered. So I think what I need is a guide that goes over every single one of what I'm sure is hundreds of settings on Windows. Things like whether or not having homegroup turned on will affect it, whether or not you should have a password on your Windows account, all of the "Advanced sharing settings", making sure all the settings in Computer Management are correct, and so forth

Does anyone know of such a guide?

If anyone is curious, right now if I, on my Ubuntu machine, go to Places > Network, I see my Windows 7 computer's name there. If I double click it, I get a box saying "Password required for <computer name>", and it asks for a username, a domain, and a password. The username is filled in with my Ubuntu user name (and that user name does not exist on my Windows 7 machine), and the domain is filled in with what I have my Windows 7 machine set to. Right now my Windows 7 machine doesn't have a password, and I would prefer ending up keeping it that way. Nothing I can think of filling in here will get me any more forward; this box just keeps coming back.

---

### Post by djkk786 on 2010-09-29
I'm a complete newbie here but have you tried to create a password on your windows computer then try to access it from Ubuntu? I know it's not something you want to do but you should try it to see if it works.

---

### Post by pgn674 on 2010-09-30
I have tried that, and using and not using the password when connecting, but to no avail.

---

### Post by jpt266 on 2010-09-30
Search this site for this topic.

Howto: Fix Windows share browsing issues

---

### Post by dmizer on 2010-09-30
> **pgn674 said:**
> Does anyone know of such a guide?

Check the 6th link in my sig :)

---

### Post by pgn674 on 2010-10-02
Thank you, both jpt266 and dmizer. You both referenced the same guide, which I somehow hadn't seen before:

[Howto: Fix Windows share browsing issues - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1169149")

The solution that worked for me was Problem 5, first paragraph under Windows 7 configuration: [Uninstall]("http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527") Windows Live ID Sign-in Assistant from the Windows machine. I found it right in Programs and Features. Now I can get into the Windows machine to see its shares (folders and printers both), and I don't need to have a password set on my Windows user or give a password from my Ubuntu machine.

The [ultimate]("https://bugzilla.samba.org/show_bug.cgi?id=7577") reason I needed to uninstall Windows Live ID Sign-in Assistant is because it changes the type or size of data being sent during the SMB handshake, and the Linux Samba program wasn't accounting for that. It's been fixed in Samba 3.4.9 and 3.5.5, released [14 September 2010]("http://samba.org/samba/history/"), but the version available in the Ubuntu lucid-updates/main repository is 2:3.4.7~dfsg-1ubuntu3.2 from [2010-09-14]("http://www.ubuntuupdates.org/packages/show/247652").

Is there a way to mark this thread as [SOLVED]?
EDIT: Click the red Thread Tools drop down menu at the top, it's in there.

---

### Post by pgn674 on 2010-10-10
I wanted to note that I've upgraded to Ubuntu 10.10, but it seems that Samba still has this problem. Right now I have version 2:3.5.4~dfsg-1ubuntu8 installed from the maverick/main (us.archive.ubuntu.com) repository from 2010-10-05.

---

### Post by ChrisTheFeral on 2010-10-12
Hi, I've been having the same problem on 10.10 (and preceding versions) and this looks like the likely solution.

I've only got two problems:
1) I can't find "Windows Live ID Sign-In Assistant" on my computer, possibly due to updates?
2) ...and as silly as this sounds, because it's MSN and all... I don't really want to break my install of MSN - unless this doesn't affect it?

---

