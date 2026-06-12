---
title: "Suspend issues with Vesa driver?"
date: 2008-12-22
forum: Multimedia Software
---

### Post by heluani on 2008-12-22
Running the binary nvidia on a MacBook Air 2.1 doesn't allow to change brightness on X

Open source nv does not support the video card ```
lspci -v
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9400M (rev b1)
	Subsystem: Apple Computer Inc. Device 00ab

```

So I'm trying vesa. 

When returning from suspend the screen is black. Tried going to TTY and then back to X (used to work when had this issue years ago) but no avail.

This does not happen if I load the binary driver. 

Any ideas?

R.

---

