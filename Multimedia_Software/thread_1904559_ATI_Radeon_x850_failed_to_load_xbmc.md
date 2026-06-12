---
title: "ATI Radeon x850 failed to load xbmc"
date: 2012-01-05
forum: Multimedia Software
---

### Post by rickdai on 2012-01-05
my system: ubuntu 11.10, xbmc eden, 

I replaced my failed nvidia card with this relatively newer Ati radeon  x850 pro 256mb video card. It was fine before the nvidia card died, now I  put in the ati card, I can't load xbmc anymore. It's giving me error  "xbmc needs hardware accelerated openGL rendering. Install an  appropriate graphic driver."

I have searched many forums and sites, tried purged the fglrx following this [URL="https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch"]link.
[/URL] 
Tried installed the driver from ati at this [URL="http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English"]link , which gives me error because that only supports up to 9.04.
[/URL] 
I am running out of ideas.

---

### Post by QIII on 2012-01-05
You may end up making a trip to Best Buy, I'm afraid.  That's a legacy card that takes the legacy driver which won't work with recent versions of X server.  I also doubt it ever supported OpenGL.  That's just a way old card probably from before AMD bought ATI.   Linux was not on ATI'S radar.  But neither was good driver support in general.

---

### Post by rickdai on 2012-01-05
I can run xbmc live with that card fine though.

I followed the steps at the [link]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide") for installing catalyst manually. Everything installs fine, but when I tried to run sudo aticonfig, it gives me error: sudo: aticonfig: command not found. I found the aticonfig file in /usr/lib/fglrx/bin/, run it there still the same error. I though I was very close, but no.

---

### Post by rickdai on 2012-01-06
Installed 10.04 lucid, and it works. Now the problem the s-video is not sending signal to TV. Both DVI and VGA works fine.

---

