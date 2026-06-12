---
title: "GThumb / Camera Detect"
date: 2008-06-21
forum: Multimedia Software
---

### Post by JemW on 2008-06-21
Hi,

I can import photos from my Fuji F610 manually using gThumb with no problem. How do I make gThumb pop-up automatically when I switch my camera on, prompting me to import...

F-Spot used to do this but I've removed F-Spot as I prefer gThumb.

Thanks

---

### Post by JemW on 2008-06-21
> **JemW said:**
> Hi,

I can import photos from my Fuji F610 manually using gThumb with no problem. How do I make gThumb pop-up automatically when I switch my camera on, prompting me to import...

F-Spot used to do this but I've removed F-Spot as I prefer gThumb.

Thanks

Anyone? See attached image from Nautilus Preferences which shows 'No Applications Found'. I've re-installed gThumb to no effect...

---

### Post by TenPlus1 on 2008-06-21
Go into System -> Preferences - Removable Drives and Media

in the Digital Camera box, put "gnome-volume-manager-gthumb" without the quotes and made sure Import is ticked...

---

### Post by JemW on 2008-06-21
> **TenPlus1 said:**
> Go into System -> Preferences - Removable Drives and Media

in the Digital Camera box, put "gnome-volume-manager-gthumb" without the quotes and made sure Import is ticked...

I'm afraid that didn't work - nothing happens.

---

### Post by TenPlus1 on 2008-07-06
If you have done a fresh Hardy install then you need to install gthumb again since it was removed for f-spot...

---

### Post by sstalpers on 2008-07-19
This seems to be a bug in Hardy, also discussed in [this thread]("http://ubuntuforums.org/showthread.php?t=835715&highlight=automount+f-spot&page=2") by Piukku "removable storage has suddenly split to nautilus preferences and to removable drives and media and these two don't seem to cooperate". Auto import preferences of Removable Drives & Media no longer works, and nautilus preferences does not give the option of importing using other applications than f-spot. I'm a bit of a newbie, does anyone know if we should file a bug report or something?

---

### Post by bleigtn on 2008-11-15
I had the same problem as JenW and the solution suggested by TenPlus1 worked for my Ubuntu 8.04 system with a Canon Powershot camera. As soon as I plug my camera in and turn it on gThumb starts up automatically and offers to load my pictures to the folder on the hard drive where I want them.  Thanks TenPlus1!

---

