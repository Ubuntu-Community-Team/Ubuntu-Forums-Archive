---
title: "Samba time-out during copy of large file"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by thoughton on 2011-05-08
Hi all,

I'm running Ubuntu 11.04 (natty), kernel 2.6.38-8-generic, GNOME 2.32.1.

I also have a Synology DiskStation DS207 NAS connected to my home network. Both of these devices are connected to the network via wired gigabit ethernet.

I access the NAS via Samba on the Ubuntu box.

My problem is that every time I try to copy a large file from one of the NAS's Samba shares to the Desktop on the Ubuntu box using Nautilus,  the operation times-out and fails about a third of the way through the copy (roughly about 3 mins into the operation).

I have retried the copy 3 times and the same thing has happened every time.

However, I also have a Windows 7 drive in the same PC as my Ubuntu install, and if I boot into Windows 7 and try to copy the file using that OS instead then it works perfectly.  This proves to me that the file and the network connection and hardware are actually all fine.

So does anyone have any ideas about what might be going wrong when trying to copy the file in Ubuntu? Is there simply a "samba keep-alive" setting or similar that I need to set somewhere?

By the way, here's a screenshot of the error I get:

[IMG]http://img852.imageshack.us/img852/2909/failedsmbcopy.png[/IMG]

Any help would be much appreciated.

Cheers,

thoughton.

---

