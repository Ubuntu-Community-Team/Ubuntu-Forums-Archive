---
title: "Nvidia Settings and Overscan"
date: 2011-03-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Buschbarber on 2011-03-21
I output video from my 9800GTX+ to my 50" HDTV using a DVI to HDMI cable. Since I started using this method I have had to deal with an Overscan problem where the edges of the Ubuntu Desktop are cut off.

Newer Nvidia drivers have resolved this problem since, like the Windows version, I can ReSize the Desktop to fit in the frame of the HDTV.

My problem is that every time I reboot Ubuntu, I have to open Nvidia Settings and then close it, again, in order for the display to resize. I do not have to touch the Overscan slider, I just have to open Nvidia Settings, and then close it again.

Is there an easy way to eliminate the need to do this

---

### Post by mc4man on 2011-03-21
I have no need to do what you're doing but maybe try this - 
open nvidia-settings and click on the bottom line - "nvidia-settings-Configuration"
Then click on "Save Current Configuration"
By default it will save .nvidia-settings.rc to your home dir. - let it do so

By default nvidia X server settings should be enabled in your Startup Applications - check and see (it should load your nvidia-settings.rc when the desktop appears

---

### Post by t1497f35 on 2011-03-21
Here with Lucid amd64 I have the same issue with the startup apps checkbox for "nvidia settings" checked. That is I have to start nvidia settings dialog box each time after reboot for my custom brightness settings for XVideo to come into effect, though I can't say/remember if I have to do this after each reboot.
So I definitely think it's some (obscure) Nvidia bug.

---

