---
title: "nVidia 8200 720p resolution not working"
date: 2009-07-17
forum: Mythbuntu
---

### Post by yeppp on 2009-07-17
[SIZE=3]I am using an nVidia 8200 integrated graphics card in my myth system hooked up to my 720p/1080i lcd tv through hdmi.  I am using the nVidia driver and at installation my tv was dectected at 1080i.  Football season is soon coming so I decided I wanted to use 720p to help with the motion (on smaller tvs there isn't much difference between 1080 and 720). The problem is when I changed the resolution in the nVidia X server settings from 1920x1080 to 1280x720 it came out zoomed in like it was the incorrect resolution.  My tv does both 1080i and 720p and automatically adapts to what input it is given.  Any ideas on the problem and how to fix it to get 720p?  Thanks![/SIZE]

---

### Post by ian dobson on 2009-07-17
Hi,

Why not leave the resolution at 1920x1080 and let the Graphic card do the scaling?

Regards
Ian Dobson

---

### Post by yeppp on 2009-07-18
thanks for helping me out. The main reason I'm looking at using 720p is better accounting for motion on my LCD tv. I know that myth can do the deinterlacing but then once the information is given to my tv in a 1080i formate the picture is displayed in an interlaced fashion.  I would like to see if there is a difference in a picture with a great deal of motion with 720p.  The problem is just getting it to work. Would it be helpful fore to post my xorg.conf file? Thanks!

---

### Post by David Grigor on 2009-07-20
while you TV can accept both 720p and 1080i input. Only one of them is the native resolution and the TV will scale/convert to the native.  So attempting to force 720p on a TV that it isn't the native resolution will not give the benefit your looking for.

---

