---
title: "ubuntu &quot;torrent&quot; server"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by xwizzard on 2009-05-26
Ok, I have Ubuntu Server (AMD64) set up as a file and print server. I installed the ubuntu (GNOME) desktop and have several "desktop user" accounts setup to use the XDMCP remote login if needed. All the users can access the files and printers with Windows via SAMBA sharing, or through the XDMCP login. In short, file and printer sharing are enabled before any session login actions take place.

I would like to do the same thing with a torrent program that I have in place with the file and print sharing. I have Transmission configured to auto-load torrent files from a private, admin-only folder; and deposit the download/seeding files to a shared folder. Currently the program does what I want, but requires an admin login locally or via XDMCP.

Is there some way to start and run Transmission during boot, before login?

---

### Post by Barry Cent on 2009-06-11
Hey,

Im right in thinking that your using transmission-daemon aren't you? If that's the case, it should be firing up with Ubuntu Server at boot...

Barry

---

