---
title: "Help:Display problem of  Intel 865G on Kubunt 7.10"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by herbert2008 on 2007-10-27
Hi,
I reinstalled Kubuntu 7.10, but I can't make the display driver to work!
My display card is an integrated Intel 865G chipset. I have tried to install all of xserver-xorg-video-intel, xserver-xorg-video-vesa, xserver-xorg-video-i810. But it still doesn't work. 
Before I reinstalled, I used Kubuntu 7.10,too, but it worked very well.
Is there any difference between the older 7.10 and the current 7.10?That seems very funny!
I have checked the /var/log/Xorg.log.0, but I can't find any usefull infomation. There wasn't any critial error logged.
I'm very tired!
I need your help!SOS!thanks.

---

### Post by CassioBunana on 2007-10-28
Hi man! I'm experiencing a similar problem after upgrading to Kubunt 7.10. I have an intel i855 card which stop to be recognized......more interesting is the card is actually working! x log says nothing spacial but kubuntu still complaint "Screen module" not loaded....I can't figure out which mistake could be...
Have you solved such problem?

Cheers, Andrea

---

### Post by herbert2008 on 2007-10-29
I haven't got any worked solution to this problem.
I even used an older driver which have worked perfectly before, but it still didn't work.
And I rolled back to unbuntu 6.06, it works well.
I think to roll back to older version, 6.06 or 7.04 will work around the problem, even though it's not the best choice...
I guess it's not only the problem of the driver, but also some thing else.

---

### Post by Qinjuehang on 2007-10-29
I'm using the same graphics card, but on Gnome. I guess the problem lies with KDE? Maybe try installing Gnome AND KDE and see which works.

---

### Post by herbert2008 on 2007-11-04
Hi,
     I have solved the problem, wol, so great! I'd like to share my steps with you:
     1. I reinstalled the latest version of Ubuntu 7.10  from my hard disk, because there is some problem on my CDROM drive.
     2. When it asked my which software I want to install, I choose all. But   
 there is some problem and it failed, so I went back to choosed nothing, and I succeed.
     3. After the Install, I can login to the console, and configged my ubuntu to connet to the Internet.
     4. I removed all the xserver-xorg components by the following command:
     apt-get --purge remove xserver-xorg xserver-xorg-core
     make sure the xserver-xorg-video-i810 and xserver-xorg-video-intel are removed
     5. Install an older vesion of xserver-xorg-core xserver-xorg-video-i810. I get them from my Ubuntu 6.06 disk. This maybe failed, but it doesn't matter any.
     6. Reinstall them by
         apt-get -f install && apt-get install xserver-xorg-video-i810 xserver-xorg xserver-xorg-core libgl1-mesa-dri libgl1-mesa-glx xserver-xorg-input-kbd xserver-xorg-input-mouse compiz-core compiz
     7. dpkg-reconfigure xserver-xorg 
         Then choose right answers to the questions.
     8. startx
         to check that my Xwindow can start successfully, and I saw it!
     9. Then I installed other desktop components, kdm, kde-base, desktop-base and any thing I need. 
     10. At last, I got my kde desktop. That's very very great!

---

