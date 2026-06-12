---
title: "playing video on pvr-350 tv-out"
date: 2008-06-24
forum: Mythbuntu
---

### Post by hylsan on 2008-06-24
Hi
Ive got latest mythbuntu, a pvr-350 with tv-out enabled just for mythtv (ie not running X on tv, that part handle a pc-monitor).

Live-tv and recorded shows works just fine, but transcoded materials (xvid) will only show on the pc-monitor.

Is there any solution to this?
Or cant mythtv show "external" videos on tv-out?

btw Ive set .avi to use internal viewer.
can I set something in Xine to use tv-out?

Thanks in Advance!
/Hylsan

---

### Post by cgmarsh on 2008-08-17
I am having the same problem. Is there a way to configure "external" videos to play through the pvr-350 tv-out like live and recorded programs? I am using a monitor for x.

---

### Post by ian dobson on 2008-08-17
Hi,

I believe you can use xine -v and then tell it which video driver to use, have a look in the documentation.

I imagine you'll have to use something like:-
xine -v /dev/video16

Regards
Ian Dobson

---

