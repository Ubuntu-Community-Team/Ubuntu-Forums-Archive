---
title: "TV Card &amp; Webcam (gspca)"
date: 2008-07-26
forum: Multimedia Software
---

### Post by tqft on 2008-07-26
Fresh after latest kernel update linux-2.6.24-20-generic webcam (microdia xc45:6008) works after installing gspcav1-20071224

I have the sn9c102 module blacklisted as everytime I do something with webcam and it loads system goes wacko and needs hard reset.

TV card DViCo FusionHDTv Pro is half recognised it kind of wants to start but fails - some cx28??? kernel modules loaded but obviously not quite correct.

Install specific driver for TV card and it works ([http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/)) but now webcam fails.

Interestingly enough before installing TV card driver in prev paragraph, /dev/video0 and /dev/video1 both exist - after installing TV card driver only /dev/video0 is there.  gspca module is not there.

I restarted machine to get everything loaded properly, I know there exists ways off doing this without restart but I don't have enough detail to make it work reliably.

Specific question: how can I convince system (udev in particular I think from googling) to create /dev/video1 when webcam is connected?

---

