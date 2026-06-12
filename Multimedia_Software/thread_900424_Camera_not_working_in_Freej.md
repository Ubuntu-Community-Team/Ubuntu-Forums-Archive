---
title: "Camera not working in Freej"
date: 2008-08-25
forum: Multimedia Software
---

### Post by ToulCit on 2008-08-25
Hi people,

i got this dvcamera connected via firewire.
But the main problem is i can't get it to work in Freej,
because i have no clue how to do so.
I know i can get it to work in kino, because i activated
the raw1394 module.

but when i try to open it in Freej it says;

 [*] Closing video4linux grabber layer
 closing video4linux device 6
 can't create a layer with /dev/dv1394/0
 layer creation aborted

i suppose the firewire camera would be located in /dev/dv1394/0
but i could be mistaken.

this is my grep 1394 output:

description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394

i hope someone can help me with this because i really don't know what to do anymore and my vj gig is within a month

, Jeroen

---

### Post by xcreations on 2009-03-29
did you ever get this to work because i also need this?

---

### Post by viroos on 2009-10-29
Hi,
I see it's very old thread, but unfortunately I have the same problem.

Probably I will try to use dv4l, but it can only support single camera. I need to use two cameras.

Maybe it's possible to grab dv stream using vlc or dvgrab and pipe output to freej?

TIA

regards,
Maciej Sawicki

---

