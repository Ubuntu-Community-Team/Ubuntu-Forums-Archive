---
title: "Screen resolution G965 LCD TV"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by bedfojo on 2007-06-24
I have a new box with an Intel G965 graphics chipset. I also have an LCD TV model Thomson Scenium 30LCDB03B. This is a widescreen TV, with a PC input socket and with a theoretical maximum screen resolution of 1280x768.

Ubuntu 7.04 defaults into a 1024x768 resolution however on this screen. This displays OK in the centre of the TV display but of course there are empty black bands on either side as the full widescreen is not being used.

 I have installed the xserver-xorg-video-intel package and I have tweaked the xorg.conf file so that I have the option in System > Preferences > Screen Resolution for a 1280x768 display. However when I select it, the PC outputs 1280x768 but the TV continues to display it in the same shaped box (i.e. with the black bands either side) which suits a 1024x768 output. The display is therefore squashed horizontally. The TV info claims the display is still 1024x768.

Somehow I need to be able to persuade the TV that it is getting 1280x768 to display it widescreen. I note that during the Ubuntu bootup sequence, the text is displayed widescreen (where the TV claims a resolution then of 720x400). I have a suspicion the TV does not provide accurate EDID information to the graphics chipset.

My xorg.conf file is attached.

All help gratefully received. The new box is intended as a media centre PC and I want to be able to use it with my widescreen TV! NB The TV works fine with widescreen TV and DVD input.

---

### Post by Opeth115 on 2007-06-24
> **bedfojo said:**
> I have a new box with an Intel G965 graphics chipset. I also have an LCD TV model Thomson Scenium 30LCDB03B. This is a widescreen TV, with a PC input socket and with a theoretical maximum screen resolution of 1280x768.

Ubuntu 7.04 defaults into a 1024x768 resolution however on this screen. This displays OK in the centre of the TV display but of course there are empty black bands on either side as the full widescreen is not being used.

 I have installed the xserver-xorg-video-intel package and I have tweaked the xorg.conf file so that I have the option in System > Preferences > Screen Resolution for a 1280x768 display. However when I select it, the PC outputs 1280x768 but the TV continues to display it in the same shaped box (i.e. with the black bands either side) which suits a 1024x768 output. The display is therefore squashed horizontally. The TV info claims the display is still 1024x768.

Somehow I need to be able to persuade the TV that it is getting 1280x768 to display it widescreen. I note that during the Ubuntu bootup sequence, the text is displayed widescreen (where the TV claims a resolution then of 720x400). I have a suspicion the TV does not provide accurate EDID information to the graphics chipset.

My xorg.conf file is attached.

All help gratefully received. The new box is intended as a media centre PC and I want to be able to use it with my widescreen TV! NB The TV works fine with widescreen TV and DVD input.

Do

```
sudo dpkg-reconfigure xserver-xorg
```

then at the end when it gets to your monitors configuration choose the correct resolution and then once u get through all of the configuration dialogs hit ctrl + alt + backspace and it should put u into the correct resolution.  It works for me, whenever i do a fresh install my xorg defaults me at 1024x768 also.

---

### Post by bedfojo on 2007-06-24
Thanks for the tip but I have already tried that. I have the resolution available but the TV refuses to display it properly.

---

