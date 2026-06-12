---
title: "need help with video capture card? Leadtek Winfast VC100 XP"
date: 2011-02-04
forum: Multimedia Software
---

### Post by DarthFennec on 2011-02-04
I'm running Kubuntu 10.10. I bought a Leadtek Winfast VC100 XP from Newegg because all the reviews said it worked out-of-the-box with Linux. When I plug it in the computer can see it fine, so I open Cheese and the input is ... really weird. Here's a screenshot:

[IMG]http://img9.imageshack.us/img9/6383/20110122145605.jpg[/IMG]

I have a feeling it's not supposed to look like that. Can anyone get me on the right track, concerning how I can fix this? Thanks in advance. I've been pulling my hair out over this for a couple of weeks now :P

---

### Post by DarthFennec on 2011-02-16
Bump.

Since I haven't been getting any replies on here, I decided to return the card and get a different one (a [Hauppauge ImpactVCB 558](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116021)), which is giving me exactly the same result.

I also tried using it in other PCI ports and such, no change, and other PCI cards (audio and such) are working in all the ports just fine. Also tried many different RCA devices and cables, with no effect. I think it's safe to assume that this is a problem with software, not hardware.

Still trying to figure out how to fix it. If anyone wants to help I would appreciate it greatly. Considering how much help I've had so far (on all the forums I posted on, zero replies) I think I can assume that I'm on my own with this. But I like to try to stay optimistic about these things.

---

### Post by inobe on 2011-02-16
that image, is it a camera connected to the card?

trying to get an idea what your using it for, tv or webcams....

---

### Post by DarthFennec on 2011-02-16
Thank you for the response ^.^

That picture is from a camcorder connected to the card, but the camcorder outputs fine to the tv and anything else I stream into the card looks just like that, so it's not the camcorder's fault.

I want to use this for Let's Plays on Youtube, to record output from my game consoles. That's what I'm using it for.

---

### Post by inobe on 2011-02-17
i'm not stating to not use the camcorder, but have you tried recording directly from the game console, maybe hook your cable line to it and watch tv?

only to rule out some things!

1) maybe the issue is with the camcorder connected and nothing else.

2) a crappy driver.

basically, lets try other things, if you get the same results, we can go from there.

---

### Post by DarthFennec on 2011-02-17
Okay, I've made some progress. Now I need to make sense of it.

First of all, I understand what you're saying, and I have tried it with the game console and it gives me the same kind of output, so I don't think the problem is with the camcorder.

That said, yes, I have ... kind of fixed it. I don't know why though. See, I thought the problem might have had something to do with the settings in Cheese, because I know that program is primarily for webcams and it might not be suited to something like this by default. So I tried out some other programs, and I found one called Zapping. It had a problem with my audio so I'm not going to use it to record, but I've found that if I run Zapping and then close out, and then I open Cheese, the stream looks perfect, and it continues to be for the rest of the session.

This is working for me, though I don't understand it at all. Right now I'm contemplating whether I should try to make sense of it, or just be thankful that I have a way to make it work, and move on.

The only clue I have as to why this is happening in the first place is something I found while messing with options in Zapping. When I open Zapping, the picture is clear. However, when I change the video standard from NTSC to PAL, I get something extremely similar to what I was getting in Cheese, so I think it might have something to do with the video standard. I don't know for sure though, I really don't know much of anything about this video capture thing :P

---

### Post by inobe on 2011-02-17
i think you found bugs in apps which are worthy enough to be reported.

have you monitored the dependencies being installed after Zapping?

zapping may have installed missing dependencies, if yes, match them to the requirements for cheese.

i have had this problem with a few apps.

```
Cheese currently requires:
  - glib-2.0 >= 2.16.0
  - gobject-2.0 >= 2.12.0
  - gio-2.0 >= 2.16.0
  - gtk+-2.0 >= 2.17.4
  - gdk-2.0 >= 2.14.0
  - gnome-desktop-2.0 >= 2.26.0
  - gconf-2.0 >= 2.16.0
  - gstreamer-0.10 >= 0.10.20
  - gstreamer-plugins-base-0.10  >= 0.10.20
  - gstreamer-plugins-good-0.10  >= 0.10.8
  - gnome-vfs-2.0
  - dbus-1
  - dbus-glib-1
  - hal
  - cairo
  - pango
  - librsvg >= 2.18.0
  - libebook-1.2 (evolution-data-server)
  - postr for Flickr export (optional)
  - f-spot for F-Spot export (optional)
  - nautilus-sendto for better export mechanism (optional)
  - a webcam
  - a brain

```

if you view cheese website you can get more information.

[http://projects.gnome.org/cheese/](http://projects.gnome.org/cheese/)

---

### Post by DarthFennec on 2011-02-17
All of those were definitely installed before I installed Zapping. And installing Zapping didn't fix Cheese, running it does. I have to run it every time I restart, so I don't think it's because anything new is installed ...

---

