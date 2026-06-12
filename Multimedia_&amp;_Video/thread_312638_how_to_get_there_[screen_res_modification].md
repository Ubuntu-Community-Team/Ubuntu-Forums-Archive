---
title: "how to get there [screen res modification]"
date: 2006-12-04
forum: Multimedia &amp; Video
---

### Post by b3ttty on 2006-12-04
below is an excerpt from an ubuntu help page for screen resolution fixes.  my resolution on my powerbook with xubuntu installed is at least 1/2 if not more below it's capability.  this link pasted below is helpful but i do not kno how to get to where i am supposed to make adjustments [in the command line?].  i have been thru my entire system in mac OS 9.2.2 with RESEDIT for several years so i am not fearful of change, surgery or problem solving..  i just do not kno how to get to where i need to make adjustments in xubuntu.
thank u in advance for any help.  
******************************
******************************
Run the Autodetect Script Again

I'm not sure that this is the solution that works for the most people actually, but it most certainly is the quickest and easiest one. All we're doing is running the same script that tried to detect your video hardware when you initially installed. Sometimes this does help. Run the following command. 

For Ubuntu 6.06 (Dapper Drake): 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg

---

