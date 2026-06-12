---
title: "amarok and gtkpod dont see iphone mount point"
date: 2008-06-08
forum: Multimedia Software
---

### Post by bobdobbs on 2008-06-08
Hi all.

I've been using this doc (amongst others) as a guide on how access my iphone and get it working with the amarok on ubuntu heron.

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone).


The iPhone is mounted at /media/iphone, and I can see the dir's of the iPhone if I ls from a terminal.

But Amarok can't see the iphone. 
When I attempt to detect the iPhone, it tells me that the mount point doesn't exist.
However, I know it exists - I created it, and can see it with ls.

Gtkpod does something similair.
When I attempt to configure the mount point for a new device, gtkpod refuses to see the mount point.

This problem persists, even after I set the permissions so that both /media and /media/iphone are set to be world-readable and writable.
Hell, the problem persists even when I set /media and /media/iphone to be world executable as well

What is broken here?
How can I fix it?
How can I convince amarok or gtkpod that /media/iphone actually exist?

**update:** If I do iphone-mount as normal user, rather than root, I get different errors, but still no positive results.
If I do iphone-mount as normal user, something interesting happens. When I 'ls', the directory listing is different. Amarok doesn't complain about the mount not existing. But it still doesn't see the device.

This is getting pretty damn frustrating. What do I have to do to get my ubuntu systems talking to an iphone? I'm running ubuntu on both my laptop and my PC. And I'm having the exact same problem with both.

---

