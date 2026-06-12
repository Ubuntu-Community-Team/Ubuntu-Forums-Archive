---
title: "Problems Gettin my Thinkpad T42's Radeon Mobility 7500 to Detect"
date: 2008-06-18
forum: Multimedia Software
---

### Post by Blur2040 on 2008-06-18
Greetings,

After getting tired of how outdated Debian etch was getting...and hearing about how easy Ubuntu supposedly is, I decided to try it...

But I've hit an issue...after a relatively unproblematic installation, I've hit a snag getting my video working properly.

Xorg is repeatedly automatically detecting my laptop's video as generic and as such is using the Vesa driver.

I have tried doing "sudo dpkg-reconfigure xserver-xorg" but it keeps on giving me the same xorg.conf...and not changing my driver over to radeon.

I can gather that I need to set my driver to "Radeon" under device....but beyond that, I don't really know what to do.  Things still work when I switch to the Radeon Driver...but my issue is that I can't access the 1024x768 video mode...

I imagine I have to either add a modeline...or set something else to make it available...but I don't really know...as I'm used to Debian doing all of this stuff for me...

I've googled looking for a good xorg.conf...but I can't find anything that works for me.

Any ideas?

Thanks

---

### Post by Fire_Chief on 2008-06-18
Have you tried installing the ATI driver using Envy (or EnvyNG if running Hardy Heron)? That usually takes care of most issues except for custom monitor modes.

Cheers!

---

### Post by Blur2040 on 2008-06-18
> **Fire_Chief said:**
> Have you tried installing the ATI driver using Envy (or EnvyNG if running Hardy Heron)? That usually takes care of most issues except for custom monitor modes.

Cheers!

As I understand it, Mobility 7500 is incompatible with the proprietary ATI driver...meaning that I have to use the "radeon" driver...which I had working fine on Debian Etch...but I don't have that xorg.conf anymore...

Thinkwiki has a partial xorg.conf, 

( [http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500) )

but after I write add that into my xorg.conf and save AND restart X (CTRL+ALT+BKSPACE), it doesn't work...it still only gives me 800x600 and 640x480 video modes in the screen resolution selecter.

Can anyone give me any further guidance...or sugggest anything for me?  Cmon...don't make me go back to Debian...  Thanks!

---

### Post by Fire_Chief on 2008-06-19
Could you please post your current xorg.conf?

Also, are you running Ubuntu 8.04? 7.10? other?

Thanks!

---

### Post by greenit on 2008-11-30
I have the same computer, i tried that thinkwiki xconf.org file however I only starts in 800x600. Can anyone help? I really want to get this to work. I am using the new 8.10.

Thanks in advance.

---

