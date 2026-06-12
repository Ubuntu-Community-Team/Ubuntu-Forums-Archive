---
title: "Radeon 9600Pro...'interlace' screen! Help!"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by veron123 on 2008-03-08
Hi there,
I am using radeon 9600pro desktop.
I was testing around with the options in 'screen and graphics'
I installed the 'VESA' driver under ATI wrongly and 
when I got logged out and re entered ubuntu,
the screen was filled with many lines and I can't identify any icons.
Any way I can restore it back to the previous state?
Any help will be greatly appreciated.
Thanks!!!

---

### Post by steefjeqv on 2008-03-09
Hi,

You can do the following (in terminal) :

sudo dpkg-reconfigure xserver-xorg

This will let you reconfigure your xorg.conf file.
When you reach the part concerning the graphics driver you can select the driver by using your space bar.

"radeon" or "ati" if you're using the open source driver.
"fglrx" when you want to use the ATI closed source driver. 

Greetings,
Steven

---

