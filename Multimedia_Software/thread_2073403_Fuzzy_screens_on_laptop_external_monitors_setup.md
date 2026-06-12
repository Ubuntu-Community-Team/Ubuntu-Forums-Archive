---
title: "Fuzzy screens on laptop external monitors setup"
date: 2012-10-19
forum: Multimedia Software
---

### Post by Cyclops_ on 2012-10-19
Just a little while ago, I bought a new laptop.  An ASUS with newer video card tech than the last one.  This one comes equipped with:


NVidia GeForce GT 630M


When buying it, I thought to myself: self, that seems like it should be an upgrade.  Apparently, I purchased it too soon.  It has Optimus technology, and I'm seeing that good Optimus support isn't there yet for Ubuntu.

That said, here's what I'm dealing with.  I have an external video card thing called a Matrox DualHead2Go.  It allows me to use a single VGA port and output to two external monitors (thus giving me 3 monitors in all).

This setup was working on my old pre-Optimus laptop, but on the new one, I get two fuzzy screens when I try to do the max resolution (which is 3840x1200 (i.e. 1920x1200x2)).

I know the card/computer support that resolution because (and here's the rub).... it works in Windows (on both systems).

I have Compiz running, and I've tried setting the refresh rate  to different values (as well as letting it detect the refresh rate).

One last piece of the puzzle:  If I set my resolution to half resolution, I get one external monitor (as expected), but it's *not fuzzy*....   So there's something going on with the higher resolution.

Any thoughts/help would be totally appreciated!

THANKS!

---

### Post by GreenTaurus on 2012-10-19
We have a few of those matrox boxes here in the office (mostly from Lenovo laptops) and honestly they look fuzzy at very high resolution in Windows too -- it seems a hardware issue.

With a docking station and one digital/one analog monitor we have no issues.

---

### Post by Cyclops_ on 2012-10-19
So... I can decrease the size, but maintain the ratio to 3360x1050.  This takes away the fuzziness, but introduces a different weirdness:  The left monitor's display is larger than the monitor itself.

Then, if I decrease it a little more to 2880x900, I'm back to fuzziness, but now it's a bit more active (it jumps quite a bit).

In Windows, it's not fuzzy a bit, even at the highest resolution.

---

### Post by Cyclops_ on 2012-10-19
At my wits end trying everything.  Is there a way to set color depth maybe?  I was just playing in Windows, and got it to look fuzzy (though a different quality of fuzzy) with the color depth set to 16 bit.

BTW - The fuzziness in Linux is a kind of fuzziness that makes the monitors unusable altogether.

The only thing I can think of here is that there is some Resolution-Refresh Rate-Color Depth mismatch and I can't figure it out.

Any ideas?!

---

### Post by BicyclerBoy on 2012-10-19
Did you see this ?
[http://wiki.hackspherelabs.com/index.php?title=Matrox_DualHead2Go_%28and_possibly_TripleHead2Go%29_on_Linux](http://wiki.hackspherelabs.com/index.php?title=Matrox_DualHead2Go_%28and_possibly_TripleHead2Go%29_on_Linux)

I guess you then need to set the video modeline with xrandr or in /etc/X11/xorg.conf..
This is not too bad as long as the video mode is a std mode.

---

### Post by Cyclops_ on 2012-10-22
Bicycler Boy -

Heh, funny thing is that that wiki looks like it was started based on an old forum post of mine :)  (Based on my adventures with the old laptop.)

I'll look into the XRandr.  Thanks :)

---

### Post by BicyclerBoy on 2012-10-22
I guess you are not using BumbleBee ?
You are using the intel iCPU/GPU ?

nVidia have stated that they are working on optimus support.
But the kernel developers are rejecting nVidia's proposed use of some GPL buffer structure..

Hard to really help having never used one of those matrox devices..

---

### Post by Cyclops_ on 2012-10-25
Yep.  Using Bumblebee.  Not sure what the deal is...

---

