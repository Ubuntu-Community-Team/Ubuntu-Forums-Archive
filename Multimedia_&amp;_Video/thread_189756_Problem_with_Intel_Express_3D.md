---
title: "Problem with Intel Express 3D"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by martijn hoekstra on 2006-06-05
Heya people

I have a sucky Intel express 3D card. I'm not planning on doing anything fancy with it so it suits my needs just fine. The problem is I don't knwo how to properly set it up. The automatic script makes a mess out of my xorg.conf, where i'm stuck in 640. I edited so that it works, I can now use a resolution up to 1024 and a refreshrate over 60 Hz.:grin: 

See, im easy to satisfy. Problem still is, my video card isn't set up *propery* and simple things like scrolling still don't work like they should. This seems like the right time for a snippet from xorg.conf:


```
Section "Device"
	Identifier	"Intel Corporation i740"
	Driver		"i740"
	BusID		"PCI:2:0:0"
EndSection
```


Now there is one thing correct:"Intel Corporation" 
I'm not particularly sure of "PCI:2:0:0".
And one bad: i740. (Its double bad cause its there twice).

Now what I first and formost would like to know is: How do I make it work? I'd guess  I have to find out if the driver of the Intel Express 3D gaphics card is supported by Ubuntu, if so, what its name is, and then change the value at "Driver".

Now if someone could tell me how to fix it, I'd be happy. If someone could tell me how I should have looked it up myself I'd be extatic. Yeah, im easy to please like that.

For extra information: the intel website doesn't help, It doesnt provide a driver for Linux.

P.S. I Originaly put this up in the Breezy Forums. A placeholder is still there. If any moderator sees this message please be so kind to delete the duplicate in the breezy forum

---

### Post by martijn hoekstra on 2006-06-05
I have found the following on Intels website:

> Linux* Drivers for the Intel® Express 3D Graphics Card and 3rd Party Cards Based on the Intel740™ Graphics Accelerator
Linux* drivers for the Intel(R) 740-based graphics adapters have been in the major distributions for many years. Please refer to either your distribution or XFree86* for Linux drivers. Please note that this is not an Intel site and Intel is not responsible for the drivers on this site or the content of this site. Use of these drivers should be done at your own discretion. 

Can anyone tell me what to do from here?

---

