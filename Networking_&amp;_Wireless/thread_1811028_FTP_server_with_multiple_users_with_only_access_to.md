---
title: "FTP server with multiple users with only access to their own web root"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by MockY on 2011-07-24
I find FTP server software confusing in Linux. Using ServU for Windows for an example, all I need to do is to create users via the ServU interface and choose a folder I want that user to have access to and their permissions, and viola, they can connect to that directory, and that directory only.

But in the the land of Linux, it apparently can't be managed this easy. I have a web server with multiple domains, and therefore multiple users need access to their own web root. So with that in mind, what FTP server software should I use (there are plenty out there) and how would I go about to create a user per domain, so that they can log in using FTP to manage their site, and only have access to their own web root, and nothing else?

Any pointers are highly appreciated.

---

### Post by tturrisi on 2011-07-24
I don't use any FTP servers on my machines.  I use ssh. (install openssh-server)

Clients connect to their /home/username directories using any FTP client that supports ssh, most do.  Linux users can use gftp and Windows users can use WinSCP, but most all FTP clients today support ssh & ssh2.

No configuration is necessary, just install the package.  Clients, by default, are restricted to their own directories.

---

### Post by MockY on 2011-07-29
I don't want a system user for every FTP account (that would be over 50 different ones), and even if I did go that route, it would be a administrative nightmare if I had to softlink their webroot to their home folder, as well as chroot these users to their respective home folder. Maybe it's not in reality, but to me that seems like a lot of work.

I found that PureFTP has support for virtual users, and this accomplishes exactly what I want. A steeper learning curve than I may have wanted, but once I started fiddling around, PureFTP runs like a champ. Now, if only I could get the passive ports forwarding to properly work.

---

