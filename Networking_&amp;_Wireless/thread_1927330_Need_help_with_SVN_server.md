---
title: "Need help with SVN server"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by Kentucky88 on 2012-02-17
I installed an SVN server under Ubuntu.  My SVN address is something like:

svn://192.168.1.143/home/mi/svnrepos

But depending on what orders the computers are turned on, the IP address allocated to the computer by DHCP might give:

svn://192.168.1.144

This of course makes it necessary to relocate all my projects to the new address which takes some time.  Other than switching to static IP allocation, is there a better way to address my SVN server without relying on the IP address?  And how would I do that?

---

### Post by Perkins on 2012-02-21
Multicast DNS should work for you, it's enabled by default on newer versions of Ubuntu and lets you use "hostname.local" addresses.  If it's not enabled on your machine, check out [http://www.sherman.ca/archives/2005/03/19/zeroconf-under-debian-linux/](http://www.sherman.ca/archives/2005/03/19/zeroconf-under-debian-linux/)

It *should* work from OSX as well, and it's theoretically possible to set it up on Windows, but I've never actually tried either.

---

