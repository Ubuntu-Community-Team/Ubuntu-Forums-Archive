---
title: "Problems getting Nvidia driver to work"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by slickwilly on 2006-12-10
A couple of days ago I had to reinstall Ubuntu as I downloaded the newer Nvidia driver and well it did bad things to my computer.  So I pulled out my Dapper Kubuntu install disc and set about the all day process of getting Edgy back onto my system.
Mostly everything went smoothly, except now that I'm trying to get the standard Nvidia drivers to work with my system they just won't, argh!

Here is the message I get upon running nvidia-glx-config enable in the shell:

Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

uname -a shows : Linux overlord 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux

So ok I have the wrong restricted drivers installed, ok I go into Synaptic and remove the restricted drivers and reinstall them for 386, still no joy, so now I'm getting annoyed.

So I take them out again, download Automatix2 and try and let it install the driver, maybe I'm making an idiotic mistake, well instead it appears to make one, it installs generic restricted modules instead of i386 ones so still I get the message about being unable to load the module, argh yet again.

So then just for fun, I remove the i386 kernel and replace it with the generic one, nope yet again.

Any clue at all to what mistake I'm making in my process here, this is really starting to get upon my last nerve!  Any help would be greatly appreciated.

Slick

---

### Post by spd106 on 2006-12-10
Yeah, I know just how you feel, I want through this yesterday trying to get the new 9631 driver installed. I thought I would try envy, big mistake especially when I noticed that it was removing the xserver-xorg package.

Check that the 386 kernel was removed and generic is there.
Remove nvidia-glx and the restricted modules.
Run apt-get autoremove to clear out any unused packages.
Comment out any third party repos in /etc/apt/source.list
Reload package cache i.e. apt-get update
Check xserver-xorg is present.
Install nvidia-glx and l-r-m
Restart

You should be back up and running.

As I was installing the new driver from alberto milone's repos I found that I had to check the nv module wasn't disabled in the /etc/default/linux-restricted-modules-common file.

---

