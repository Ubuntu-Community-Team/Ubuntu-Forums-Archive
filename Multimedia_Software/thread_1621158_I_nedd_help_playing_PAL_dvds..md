---
title: "I nedd help playing PAL dvds."
date: 2010-11-13
forum: Multimedia Software
---

### Post by bofak on 2010-11-13
I'm going to resurrect this old thread because I'm trying to play some PAL DVDs, without success.  On my CD/DVD drive the light flashes for a short time, then stops.  DiskUtility tells me "No Media Detected" and SMART Status tells me "Not Supported".

I live in North America.  I'm running Maverick, 64-bit.  I have VLC Media Player (which somebody recommended) but the disk simply doesn't appear.  I have all the additives and restricted extras that come with Ubuntu.

I must be missing a plugin or something.  I'd appreciate any help.

---

### Post by Swagman on 2010-11-13
> **bofak said:**
> I'm going to resurrect this old thread because I'm trying to play some PAL DVDs, without success.  On my CD/DVD drive the light flashes for a short time, then stops.  DiskUtility tells me "No Media Detected" and SMART Status tells me "Not Supported".

I live in North America.  I'm running Maverick, 64-bit.  I have VLC Media Player (which somebody recommended) but the disk simply doesn't appear.  I have all the additives and restricted extras that come with Ubuntu.

I must be missing a plugin or something.  I'd appreciate any help.

Have you followed the destructions below ? They are available in that little blue help button on your top panel

> 
In order to play DVDs you must install some additional software. Unfortunately, DVD support cannot be provided by default in Ubuntu due to legal restrictions in some countries.

Read about  restricted formats before following the instructions below. There are some legal issues that you should be aware of.

   1.

      Install the libdvdnav4, libdvdread4, gstreamer0.10-plugins-bad and gstreamer0.10-plugins-ugly packages.

                  
   2.
      If you would like to play encrypted DVDs, press Applications &#9656; Accessories &#9656; Terminal and type the following into the screen which appears, followed by the Enter key: 

      ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```


 3.

    Enter your password if prompted. The libdvdcss2 package will be downloaded and installed from a website.

                  
   4.

 Insert a DVD into your drive. It should open automatically in the Movie Player.



---

### Post by bofak on 2010-11-13
"Install the libdvdnav4, libdvdread4, gstreamer0.10-plugins-bad and gstreamer0.10-plugins-ugly packages."

I already have these installed.

"If you would like to play encrypted DVDs,..."

I'm trying to play ordinary DVDs as sold in Europe.  My home CD/DVD player (as sold in North America) can recognize them but does funny things to the picture.

I'm aware that there is equipment on the market for converting the format, and also there are services that will do this for me.  My problem is that I have access to a fair-sized collection of PAL DVDs (not distributed in North America) and it's out of the question to convert all of them.

Thanks, Swagman, for your suggestion.

---

### Post by cariboo on 2010-11-13
This is a request for help, not a testimonial or an experience. Moved to Multimedia & Video

---

### Post by mc4man on 2010-11-14
Can you play NTSC disks, (region 1) or have you not tried?

If you can play them,  then run this, look under the *-cdrom section for the vendor of your drive. If it's MATSHITA then that's a bit of an issue with very limited options
```
sudo lshw -C disk
```

If it's not a MATSHITA drive then start vlc from a terminal, try to play a disk and post the result

---

### Post by bofak on 2010-11-14
> **mc4man said:**
> Can you play NTSC disks, (region 1) or have you not tried?

If you can play them,  then run this, look under the *-cdrom section for the vendor of your drive. If it's MATSHITA then that's a bit of an issue with very limited options
```
sudo lshw -C disk
```

If it's not a MATSHITA drive then start vlc from a terminal, try to play a disk and post the result
I don't know what I did since yesterday, but now these PAL DVDs play perfectly on my computer, using Totem.

I want to thank you guys for your suggestions, and I'll have to mark this problem as solved, but I'm afraid I can't share the solution with you because I don't know it.  Probably something very simple, involving settings.

---

