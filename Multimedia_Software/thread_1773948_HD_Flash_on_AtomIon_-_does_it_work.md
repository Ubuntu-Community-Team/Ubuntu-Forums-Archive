---
title: "HD Flash on Atom/Ion - does it work?"
date: 2011-06-02
forum: Multimedia Software
---

### Post by alexeix on 2011-06-02
Hi,

Having spent many hours trying to get the BBC iPlayer (and other HD Flash sites), to play back in 1080p, I have to admit defeat.

I understood that this should be possible with the latest nVidia drivers, available at this point in time, which can take advantage of hardware acceleration!?

I've followed numerous tutorials online, but cannot get it working within Firefox or XBMC!!

My question is, does anyone actually have 1080p Flash playing correctly on an Atom/Ion PC (e.g. the Acer Aspire Revo 3610)???
If so, please advise what you did to make it work.

If I can't get this working, I will have to install Windows, because I need Flash HD playback in 1080p.

Looking forward to hearing feedback based on personal experience.
Thanks.

---

### Post by lovinglinux on 2011-06-03
Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/). Run the add-on wizard. It the Tweaking options, make sure Flash-Aid detected and selected the option to *Enable Linux HWVideo Decode*. If not, then make sure you have vdpau installed.

Let me know if it doesn't detect that option, so I can troubleshoot the add-on code.

---

### Post by alexeix on 2011-06-03
Thank you for the reply.

I will certainly go ahead and troubleshoot as you advise, but please can you refer me to an HD Flash site which you can run on a similarly low-specced PC?

Nobody has yet replied to say they can do anything HD...

:(

---

### Post by alexeix on 2011-06-06
I installed Flash Aid and HD Flash performance has improved, but is still choppy; it's not good enough for using a Linux box as a media center for Flash video.

To confirm, I did tick 'Enable Linux hwvideo decode'.

Is there anything else to try?

---

### Post by lovinglinux on 2011-06-06
> **alexeix said:**
> I installed Flash Aid and HD Flash performance has improved, but is still choppy; it's not good enough for using a Linux box as a media center for Flash video.

To confirm, I did tick 'Enable Linux hwvideo decode'.

Is there anything else to try?

See [http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization](http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization)

---

### Post by alexeix on 2011-06-08
Thanks for the link.

I tried those suggestions (or rather, those that I could).
Under CompizConfig Settings Manager, I didn't have the Unredirect Fullscreen Windows option.

I didn't touch the Xorg tweaks either, because although competent, I've been burned by messing with Xorg in the past.

Unfortunately, HD Flash still doesn't play back properly.

It's quite telling that nobody has actually confirmed that they CAN watch HD BBC iPlayer content - or from any other site for that matter.
I suspect this is just a limitation of Flash on Ubuntu for now.

:(

---

### Post by lovinglinux on 2011-06-08
> **alexeix said:**
> It's quite telling that nobody has actually confirmed that they CAN watch HD BBC iPlayer content - or from any other site for that matter.
I suspect this is just a limitation of Flash on Ubuntu for now.

BBC iPlayer, Hulu and similar sites works on Linux, but sometimes they stop working with some updates. I don't know about your specific hardware tho.

I don't have access to those sites, because I live in Brazil, but I can watch flash HD on my desktop. However I have a low-end notebook that has problems playing flash even in low res.

---

