---
title: "amd/ati hd video decoding (preferably vlc)"
date: 2011-07-01
forum: Multimedia Software
---

### Post by black-beard on 2011-07-01
I am a complete noob with ubuntu.

I can't get vlc to decode video via my graphics, 720p uses about 80% of cpu and 1080p uses 125% (then crashes). I believe I have correctly installed the xvba driver and I think I just need to setup vlc correctly but I am not sure of this. I have read that people have had this board running full hd with about 15% cpu usage so I am sure it has something to do with the way I have things set.

I am running a 
  MSI E350IA E45   (amd / ati 6310)
  4gb ddr3 (running at 1333mhz)
  Ubuntu 11.04 64bit
  

As I said I am completely new to ubuntu so no doubt this has probably been answered numerous times but I couldn't find a fully explained guide for an amd setup.

Thanks for your help in advance.

---

### Post by BicyclerBoy on 2011-07-02
You might be best to search/follow some of the linux-VAAPI-AMD zacate/fusion threads on XBMC forums

[http://forum.xbmc.org/archive/index.php/t-99154.html](http://forum.xbmc.org/archive/index.php/t-99154.html)

Most of this will be applicable & useful for debugging even if you want to use VLC.

But the whole zacate/fusion does not seem in anyway close to working out-of-the-box with linux.
You may be able to find a XBMC Live build for zacate/fusion..

---

### Post by black-beard on 2011-07-10
thanks.

I have been trying this but cannot even complete stage 1

when I enter
sudo apt-get install linux-headers-2.6.39-0 linux-headers-2.6.39-0-generic linux-image-2.6.39-0-generic --fix-missing
I am getting unable to locate linux-headers-2.6.39 and then more rrors relating to this file being missing.

any ideas?

---

### Post by BicyclerBoy on 2011-07-11
You need a headers package that matches your current kernel..this is easier to manage if you are using the std release kernel package of 11.04..

If you use synaptic manager you should find a kernel package that auto-magically links to the latest release kernel image.
(linux-image-generic, linux-generic)

There is also a kernel headers package that does the same..(linux-headers-generic).

If you use this method the headers package will always match any kernel updates..

But if you need a specific kernel release this method will not work..
Pre-release & proposed backports may give you more options..

---

