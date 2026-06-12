---
title: "Wired network slow after updates in 10.10"
date: 2011-12-18
forum: Networking &amp; Wireless
---

### Post by mark_antony on 2011-12-18
Hi,

I have a fileserver with Maverick Meerkat.
It boots from an 8GB USB flash drive, and has a 4 x 2TB LVM configuration. This has been working fine for a while. Until now.

Today I noticed, when checking the system monitor, that network speeds won't exceed 1.2 MiB/s anymore. I tried transferring files to the server, from the server, and downloading files with JDownloader. Nothing will exceed 1.2 MiB/s, unless I transfer in both ways at the same time. In that case, the total is just a little higher.

This used to work fine. It's connected to a router with gigabit lan, so I could copy to and from it at speeds of 50 MB/s.

I think the problems started after some automatic updates were installed. This afternoon, I saw the update manager wanted to reboot after some updates, but there was already a new update available. So I let it install the new update before rebooting. I think the problem wasn't there yet before the reboot, and it started immediately after the reboot.

You can find the package log file ( /var/log/dpkg.log ) here:
[http://justpaste.it/n4f](http://justpaste.it/n4f)

---

