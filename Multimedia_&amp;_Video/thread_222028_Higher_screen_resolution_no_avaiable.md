---
title: "Higher screen resolution no avaiable"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by okok on 2006-07-24
I tried the latest Ubuntu live CD. The display reslution chosen automatically was 1024x768, and the correct resolution for my LCD monitor, 1280x1024, was not available on the list when I tried to change the resolution manually. The highest option was 1024x768.

Is this a matter of incorrect hardware detection? Will this be the same if I install the OS the my HD?

My display adapter is an integrated Intel Graphics Media Accelerator 950 and I use a Samsung 740B LCD monitor.

---

### Post by arkangel on 2006-07-24
that happened to me  first time  i was testing the live cd, because my widescreen resolution was not listed 

what i did was:  i edited the  /etc/X11/xorg.conf

and in the section "Screen "  and the corresponding subsection  I added the proper resolution(s) so mine is :

SubSection "Display"
 Depth     24
 Modes    "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "800x600" "640x480"
EndSubSection 

(the modes are in a single line) if your card is not capable of one resolution it wont change anything 

then ctrl+alt+bkspc  , to restart X  and  log in again  , in system>>screen resolution  menu should be listed your max res

hope it helps

---

### Post by Dr. Nick on 2006-07-24
EDIT
Yeah what he said :)
EDIT

when you boot the live cd their are options to pick to manually configure your screen resolution, I dont remember the extent of flexablility they offered though.

Once you install it you can edit the resolution options in the file /etc/X11/xorg.conf
I have a brief howto on this in my signature, It may be possible to try this on the live cd, once you done though do not restart or it will lose the settings, simply log off and log back in if possible on the live cd

[http://www.geocities.com/aebcoat/index.html](http://www.geocities.com/aebcoat/index.html)

---

### Post by okok on 2006-07-24
Thank you both very much!

---

### Post by el_rawyy on 2007-09-29
Try this command it was very helpful to me:
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by lennartack on 2007-09-29
There's an ubuntu help page about this: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by skyjacker on 2007-09-29
> **el_rawyy said:**
> Try this command it was very helpful to me:
sudo dpkg-reconfigure -phigh xserver-xorgHit the spacebar to choose the resolutions you want to add. This will place a + sign to the left of the line (in the blank square). Hit the Enter key when finished, and finally hit Ctrl,Alt, Backspace to restart X. When you log back in the new Resolutions should be available.

---

### Post by creepandpeep on 2007-09-29
Im having this problem with an old laptop of mine, has ati rage mobility card.  In a previous installation of ubuntu server, there were no problems with resolution at all, would go to 1280x768 - but after reinstall it will only go up to 1024. . .

the xorg.conf has all the entries for the higher resolutions, but it will not run them. . .when i do a xrandr, it doesnt list the higher resolutions, only up to 1024.  Have tried using the ati and vesa driver with the same result. . .

Anyone have any ideas? Ive worked through the suggestiosn on here and in other forums with no luck!  Frustrating me, seeing as it was working fine before!

---

