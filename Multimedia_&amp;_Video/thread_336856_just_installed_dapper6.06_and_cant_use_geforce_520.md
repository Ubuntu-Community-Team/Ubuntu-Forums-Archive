---
title: "just installed dapper6.06 and cant use geforce 5200 fx"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by learninglinux on 2007-01-12
hi im new to this distro and forums in general so excuse any uneeded waffle 
iv just installed dapper 6.06 from the shipit cd only to find i cant use my nvidia graphics card i can only relate this too a similar problem i had using suse 10.2 where there cli sax2 -c 1 was able to rectify the problem then via yast set up and adding nvidia into the sources i was able to update both kernal and driver i have been informed the problem is caused mostly by my onboard graphics chip competing against my pci card even though i changed the primary video adapter to pci as my m/b has no agp slot 
i should no doubt mention that in order to install ubuntu iv had to revert back to on board graphics as the xserver failed to start as it couldnt decided which graphics i was using nvidia or intel i810 so i guess my query is really how do i tell it which one to use as mentioned in suse i used sax to set it up then yast to update being new to both ubuntu and gnome im feeling both lost and out of my depth so if some one could spare the time to point me in the right direction how to conf the Xserver so i can use my graphics card i would be eternally grateful thankyou in advance :confused:

---

### Post by an.echte.trilingue on 2007-01-12
First, enable the [universe and multiverse ]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096")repositories.

Then install the nvidia driver and kernel (if there is one i forget).

Then edit /boot/grub/menu.list to boot from your nvidia kernel (if there is one).

Reboot into text mode

run the command sudo ```
dpkg-reconfigure xserver-xorg
```

this will launch a ncurses wizard to configure xserver

select your card and the driver.

reboot.

---

