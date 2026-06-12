---
title: "USB headset now only playing out one side"
date: 2008-05-30
forum: Multimedia Software
---

### Post by richardq on 2008-05-30
I'm having a weird problem. I have a Logitech USB stereo headset with mic. I have used it under Ubuntu for a couple of years now. I upgraded to Hardy and installed Pulse Audio and everything has worked fine for a few weeks since I upgraded. But now I'm having a problem. Last night I noticed that it was only playing out the right side. It would record properly, and I checked the Pulse Audio monitors and it showed sound levels coming out both left and right, but no sound out one of the earpieces.

I immediately assumed the wire was crimped under my chair or some other sort of damage so I went and bought a new headset (Logitech ClearChat). Plugging it in tonight, I get the same behaviour - sound out only the right side. Again I checked all the pulse audio stuff and it all shows two channel output. 

So I'm obviously thinking it was not the headset, but a system problem. Any clues as to what it might be?

I like Pulse Audio since it lets me switch back and forth from my speakers to headset, but obviously not having stereo output on the headset is unacceptable, especially since it was working fine two nights ago. I don't know the inner workings of Pulse Audio, but I've got the default server, sink and source set to default. 

Any ideas what other things I should check?

Thanks. RQ

---

### Post by tweston on 2008-05-30
Did you check the PCM volume control? Open volume applet on the toolbar with a right click and "open volume control". Then File > Change Device and select the USB sound device by name. Make sure both channels of the PCM sound are OK.

---

### Post by richardq on 2008-05-31
> **tweston said:**
> Did you check the PCM volume control? Open volume applet on the toolbar with a right click and "open volume control". Then File > Change Device and select the USB sound device by name. Make sure both channels of the PCM sound are OK.

You are on the right track here I think. I right-clicked the volume control on the Gnome toolbar and changed the device to my headset. The left volume slider was indeed set to zero.. however, the controls act wonky. I cannot seem to lock the left and right together, and cannot move the left side slider up smoothly. It jumps up and down as soon as I try to drag or move it. I have managed (through a bunch of clicking) to get both sides to an even level of about 20% and sound plays out both sides of the headphones.

I'm not sure why I can't just lock the two sides or why it's acting so funny. For instance, if I have both set to 20% and then drag the right slider upward, the left side jumps back down to zero. It's not a smooth movement either. Clearly something is screwy here. 

I'll leave it at whatever I can get for now, but I'm confused as to how this volume control is supposed to work with in conjunction with the Pulse Audio volume control.

I may uninstall Pulse and get things working properly again and re-install it to see if that clears up the problem.

Thanks for the suggestion because it definitely pointed to where the problem lies (or at least gave me a way to get some even sound and confirm that the headsets are not the problem).

RQ

---

### Post by richardq on 2008-05-31
A little more research on this indicates that I'm not alone in the problem. No solution yet, and no clear indication of what's now causing it but it sounds like it's being looked into:

[http://bugzilla.gnome.org/show_bug.cgi?id=497795](http://bugzilla.gnome.org/show_bug.cgi?id=497795)

---

### Post by richardq on 2008-05-31
W00t! While I didn't solve the problem, I found that I was able to up the volume to a decent level on the left and right channels if I hovered over each slider and used the mouse wheel. Obviously this isn't a solution to why the controls are acting wacky, but at least I solved my specific problem in this case. :)

---

