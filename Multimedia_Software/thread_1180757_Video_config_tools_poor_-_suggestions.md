---
title: "Video config tools poor - suggestions?"
date: 2009-06-07
forum: Multimedia Software
---

### Post by jcoles on 2009-06-07
I am struggling to get my 1440x900 DVI monitor working properly in Hardy. The poor configuration tools do not help. 

System > Preferences > Screen Resolution (Gnome)
-- both of my screens (DVI and VGA) show the same content, regardless of the Clone Screens setting
-- with Clone Screens disabled, I see two screens represented, but no way to determine which one is for which monitor
-- widescreen resolutions are not available for either monitor

displayconfig-gtk
-- I learned about this in a thread that I read
-- Screen tab shows two screens, both labelled "Screen1", with no way to determine which represents which monitor
-- Either monitor can be enabled, but not both. Secondary option is only available with malfunctioning proprietary driver
-- one Screen1 shows Model as Plug 'n Play. I can change it to widescreen LCD Panel 1440x900 and select 1440x900, but the resolution is unchanged
-- Graphic Card tab shows two: ATI Radeon and VESA driver (generic), corresponding to my DVI and VGA connections
-- Driver for ATI Radeon says None. You can select a different driver, but selection always returns to None.

Are there better tools than this?

---

