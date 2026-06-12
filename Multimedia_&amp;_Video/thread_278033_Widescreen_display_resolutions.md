---
title: "Widescreen display resolutions?"
date: 2006-10-15
forum: Multimedia &amp; Video
---

### Post by neptune on 2006-10-15
Hi,

I have an Acer AL1916W widescreen LCD display capable of 1440x900 resolution.
However, Ubuntu doesn't seem to have that resolution as an available choice. How can I set my display to the correct resolution? 

Help is appreciated.

Thanks!

---

### Post by Narzuhl on 2006-10-15
Try 
sudo gedit /etc/X11/xorg.conf

In terminal and manualy add the 1440x900
Thats what i did for my 1680x1050 works great.
You will have to restart X after and the display sould be back up.

---

### Post by Omegatron on 2006-10-15
> **Narzuhl said:**
> Try 
sudo gedit /etc/X11/xorg.conf

In terminal and manualy add the 1440x900
Thats what i did for my 1680x1050 works great.
You will have to restart X after and the display sould be back up.

Where do you add that?  I have a 1680x1050 and I don't know what to add.

---

### Post by Kateikyoushi on 2006-10-15
To the display subsection which looks similar to this but you most likely have more than just one resolution listed there.

```
 SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
```

Do not forget to make a backup of your xorg.conf before editing.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_old
```

---

### Post by Omegatron on 2006-10-15
> **Kateikyoushi said:**
> To the display subsection which looks similar to this but you most likely have more than just one resolution listed there.

```
 SubSection "Display"
```


I'm in Kubuntu and my section looks like this:

```
Section "Screen"
  Identifier "Default Screen"
  Device "NVIDIA Corporation NV34M [GeForce FX Go5200]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1792 1344
    modes "1600x1200@60" "1680x1050@60" "1792x1344@60" "1400x1050@60" "1280x1024@60" "1280x960@60" "1280x854" "1152x768@54" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
  EndSubSection
EndSection
```

I added the 1680x1050 but it doesn't seem to do anything.

---

### Post by kuja on 2006-10-15
If you can find the horizontal sync and the vertical refresh rates for your monitor, you can do a sudo dpkg-reconfigure xserver-xorg, and select advanced for the monitor section, pop in those two ranges and then restart x, and you should be good to go.

---

### Post by Omegatron on 2006-10-15
> **kuja said:**
> If you can find the horizontal sync and the vertical refresh rates for your monitor, you can do a sudo dpkg-reconfigure xserver-xorg, and select advanced for the monitor section, pop in those two ranges and then restart x, and you should be good to go.

I don't see them online anywhere.  Where would I find them?  Is this something I could discover by navigating around in /proc/ or something?  It's a Dell Inspiron 8600 1680x1050.

---

### Post by kuja on 2006-10-15
> **Omegatron said:**
> I don't see them online anywhere.  Where would I find them?  Is this something I could discover by navigating around in /proc/ or something?  It's a Dell Inspiron 8600 1680x1050.
The first place you should check is Dell's website. If you have trouble finding it there, perhaps you could find the information in your monitor or computer manual, presuming you have such things.

Edit: I just took a look on Dell's website, and came up with something that looks like it might be [a match](http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&cs=19&sku=320-4688) for your monitor. If nothing else it's the same resolution, and it's the only thing made by dell that came up in my search.

---

