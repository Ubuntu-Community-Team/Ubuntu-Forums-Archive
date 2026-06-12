---
title: "TV Capture Card not detected -- AverTV Hybrid Volar Max"
date: 2009-05-08
forum: Multimedia Software
---

### Post by saites on 2009-05-08
I'm having quite a bit of trouble attempting to connect my AverMedia AverTV Hybrid Volar Max capture card. AverMedia provides drivers [here]("http://www.avermedia.com/avertv/Product/ProductDetail.aspx?Id=431&tab=APDriver"), but so far, I've been unsuccessful in getting them installed.

When I run the install program, it gets to "Rebuilding Kernel Module Dependencies" and then gives me this message:

> FATAL: Error inserting h826d (/lib/modules/2.6.28-11-generic/kernel/drivI assume there's more to the message, but the rest is cut off by the GUI the install comes with. 

I'm using the new 9.04 ubuntu release, so that's technically not on their supported list, but it seems to me (with my limited knowledge on the subject) that there should be a way to make it work. 

Does anyone have any knowledge on the subject? I've tried Aver's support forums, but, unfortunately, they simply told me to install an older version of ubuntu :(

Thanks in advance

---

### Post by alexandros. on 2009-05-11
Same problem here.

---

### Post by faskunji on 2009-05-14
+1 
on 9.04

AverTV Hybrid Volar HX  (HX uses same driver as MAX)
Driver downloaded from here: [http://www.avermedia.com/avertv/Product/ProductDetail.aspx?Id=293&tab=APDriver](http://www.avermedia.com/avertv/Product/ProductDetail.aspx?Id=293&tab=APDriver)

---

### Post by saites on 2009-06-10
Aver released a new driver for the 9.04 release. It didn't work for me, though; I got the exact same error. Anyone else?

---

### Post by tmclaugh on 2009-07-15
I'm assuming due to the lack of posts that everyone has pretty much gotten this to work.  If not, it actually did work for me.  I installed it without the adapter plugged in and it worked like a charm (had to install "dialog") Next problem - I cannot get this to work what so ever.  I've spent an hour trying to get Me TV but it will only scan certain DVBs, I've tried a few other programs to no avail.  I've also tried setting up a channels.conf with scantv and w-scan.  Both return errors.  Aside from that, it seems to lock up the usb key and I have to unplug it and switch ports and/or manually kill certain programs using it after I've closed them.

Anyone?

---

### Post by saites on 2009-07-15
I stopped posting because I was out of ideas. I (still) couldn't get it to install, let alone work. You can try a different TV application, but without success myself, I'm not so sure what else to suggest. 

Have you tried (and failed) to get it to install before, and this new one worked for you? Or did this work the first time right away?

---

### Post by tmclaugh on 2009-07-15
First time was a charm for me.  The only thing I did was to make sure the USB tuner was unplugged while I was installing it.  Not that it matters but I installed both of the dialog programs (shell and X windows).  I'm running 9.04 and have a Zotac 9300 with wireless board.  

I'm having serious issues trying to locate the device, I don't think the drivers really worked.  But it installed correctly...

*Edit*  Are you downloading the x86 version or the x64 version?

"Edit Redux* Can someone tell me what I should see in my "dev" folder... I'm pretty sure it's not there.  There is a DVB folder with some other folder and three files that have 0 bytes.  No /dev/video0 or v4l files.

---

### Post by dradak1 on 2012-08-31
> **tmclaugh said:**
> First time was a charm for me.  The only thing I did was to make sure the USB tuner was unplugged while I was installing it. ..."


If I remember correctly tmclaugh is right (was 2 years back) tuner must be unplugged.

---

### Post by wildmanne39 on 2012-09-02
Thanks for sharing. Thread Closed.

---

