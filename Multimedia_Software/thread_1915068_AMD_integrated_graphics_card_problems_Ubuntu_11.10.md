---
title: "AMD integrated graphics card problems Ubuntu 11.10"
date: 2012-01-25
forum: Multimedia Software
---

### Post by Axess_Denied on 2012-01-25
After a fresh install of Ubuntu 11.10 and installing Gnome Shell, I attempted to activate the proprietary drivers for the AMD Radeon HD 4200 integrated chipset. 

This solution worked for two issues I noticed upon boot:

     1. Activating the proprietary driver allowed the chipset to
        send audio through HDMI without requiring me to change my 
        configuration in Grub.

     2. Activating the proprietary driver allowed me to get clean 
        1920 x 1080 resolution when selecting this display option
        from the Catalyst Control Center.

This solution also posed a significant problem:

     When using the proprietary driver, every dropdown menu
     (including some windowed content) showed horrible tearing.

Tearing is not an option when utilizing apps with UI. Also, it leads to much frustration when trying to speed up interfacing with a machine by right-clicking on the mouse. 

My solution was to reinstall Ubuntu 11.10. However, I had to reconfigure Grub to allow for audio through HDMI and am unable to attain a clear image when selecting 1920 x 1080 in the display settings (System Settings > Displays).

Are there any suggestions to get full 1920 x 1080 HD resolution?

---

### Post by Axess_Denied on 2012-02-05
Still having no luck with this problem. Every post I have come across either recommends installing Catalyst (which doesn't work) or running the open-source drivers (which I am doing but not able to get 1920 x 1080.

---

### Post by Axess_Denied on 2012-02-24
<bump>

---

### Post by gordintoronto on 2012-02-24
"I attempted to activate the proprietary drivers for the AMD Radeon HD 4200"

What did you do, exactly?

---

### Post by BicyclerBoy on 2012-02-24
You might be better off trying to fix the vsync tearing nonsense with the desktop effects manager.
Desktop effects programs use redirection & blitter to draw the desktop.

The AMD APU real needs to use a recent kernel & the AMD driver.

When you say Gnome shell, do you mean Gnome 3 desktop?
I recall this uses either mutter/clutter/metacity desktop effects manager.

If you turn off desktop effects does the tearing stop ?

There should be a config tool for effects mangler; should be able to enable vsync &/or set it to match screen &/or set autodetect.

You could try to set vsync in the AMD Catalyst config tool..

---

### Post by Axess_Denied on 2012-02-29
> **gordintoronto said:**
> "I attempted to activate the proprietary drivers for the AMD Radeon HD 4200"

What did you do, exactly?

@gordintoronto:

I looked at "Additional Drivers" first. Here I selected the AMD/ATI proprietary driver and activated it. 

Following problems with that, I did a fresh install and attempted to install the driver from AMD's website. Again, same problems as described above.

I am using the open-source driver now. I am able to select 1900 x 1080 as a resolution but it pixelates and overscans off the panel.

---

### Post by Axess_Denied on 2012-02-29
> **BicyclerBoy said:**
> You might be better off trying to fix the vsync tearing nonsense with the desktop effects manager.
Desktop effects programs use redirection & blitter to draw the desktop.

The AMD APU real needs to use a recent kernel & the AMD driver.

When you say Gnome shell, do you mean Gnome 3 desktop?
I recall this uses either mutter/clutter/metacity desktop effects manager.

If you turn off desktop effects does the tearing stop ?

There should be a config tool for effects mangler; should be able to enable vsync &/or set it to match screen &/or set autodetect.

You could try to set vsync in the AMD Catalyst config tool..

I believe that the kernel is the most up-to-date.

Gnome shell as my display manager, not Unity.

I can find no way to turn off desktop effects, so I am not sure.

The refresh rate on the GPU stops at 60Hz, my HDTV is telling it that it's refreshing at 75Hz? VSync is set by the panel I believe.

---

