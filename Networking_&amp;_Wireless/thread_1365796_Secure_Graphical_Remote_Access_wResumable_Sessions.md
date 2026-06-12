---
title: "Secure Graphical Remote Access w/Resumable Sessions"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by PsCYcho on 2009-12-27
Hi Everyone.  I'm pretty new to Linux & Ubuntu, but I've been doing this on Windows for a couple years, so I know that this can be done.  Problem is I don't know if this is the best way to do things on Ubuntu, or even how to do it.  

Here's my situation...  I've got a machine at home that I'm using for a File/Media server, but that I also want to have secure graphical remote (via Internet) access to.  Ideally, I'd like to be able to log in remotely from the login screen, fresh from a boot, when no X window session previously existed.  And I'd like to be able to close my (VNC or whatever) session and resume it later. (I'm asking for a lot, I know)

Previously I was running Windows Vista on the box, with Cygwin, OpenSSH, and MS Remote Desktop.  I'd then SSH to the box and use RDP to get a desktop session. This was fine before, but since I've moved to Linux I'm trying to figure out the best way to accomplish this same functionality.

I currently have a basically virgin box running Karmic (desktop) which has OpenSSH installed.  I've seen a number of tutorials online, but many reference XDMCP (which I understand has security issues) or refer to versions of Ubuntu prior to Karmic (which I understand includes some significant changes).

If anyone has recommendations, and wouldn't mind walking me through how to get this up and going, I'd greatly appreciate it!

---

