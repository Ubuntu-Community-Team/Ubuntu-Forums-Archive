---
title: "x300 on Hardy (fine in Gutsy)"
date: 2008-04-26
forum: Multimedia Software
---

### Post by rossmoore on 2008-04-26
Hi all,

I have an ATI x300 card. It worked fine in Gutsy, running Compiz really well, video was fast and smooth, no problems at all.

I've just upgraded to Hardy. I had some initial problems with my wifi (a 7051 - I finally figured out that the rt2500usb driver had been re-enabled after I blacklisted it in Gutsy, so I re-blacklisted it) - I'm putting this in on the off-chance it's relevant.

I've had lots of problems now getting my video to work. I've removed and reinstalled the ATI restricted drivers, xserver-xgl, compiz and emeraled.

With xserver-xgl not installed, and the ATI restricted driver installed, I get an output from fglrxinfo indicating the ATI driver is working.

When I then install xserver-xgl, it seems to revert to Mesa.

I currently have Compiz installed and working - but it's slow at certain things (scrolling), fast at others (rotating the cube is fine), and video just can't run for more than a few seconds.

Any help would be great. It's a lovely day here, and I don't want to spend any more of my day pulling what's left of my hair out.

Thanks,
Ross

---

### Post by rossmoore on 2008-04-26
I think everyone's busy today (and it's only now morning on the West coast of the US...).

I've fixed my problems now though, so here's my solution if anyone has similar problems.

I wanted to use compiz, and have fast 3D accelerated graphics using my X300 graphics card. The answer - don't use xserver-xgl.

I was under the impression, from previous how-to articles written for gutsy, that you needed xserver-xgl in order to use compiz. You don't.

Just use the open driver xorg-driver-fglrx, or (as I am) the proprietary one from ATI in restricted drivers. Then install compiz. Easy.

Video and compiz effects are now fast and smooth, glxgears (just type it in the console, it's a useful way of benchmarking your 3D rendering capabilities) gives me over a 1000fps, which is fine for now, and glxinfo | grep direct shows that direct rendering is indeed switched on.

Thank you to all the articles I read to figure this out.

---

### Post by rossmoore on 2008-05-01
I'm not quite sure how or when, but direct rendering is now off. I've raised this problem in a new thread.

---

