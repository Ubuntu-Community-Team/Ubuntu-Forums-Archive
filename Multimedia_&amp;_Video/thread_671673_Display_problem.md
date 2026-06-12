---
title: "Display problem"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by maxnik on 2008-01-18
Hello,
I' m new to Ubuntu. I have Ubuntu 7.10. I run AMD 2 64  on Asrock motherboard and use Nvidia 7900 GS video card. And I created this problem for myself. I was trying to get display to work with a resolution higher then 1024x768. I guess I picked resolution that the monitor cannot support. So now I get black screen once boot process goes past Ubuntu symbol. I can run commands, but nothing graphical. Is there an easy way to fix it?
thank you for your help.
-maxnik

---

### Post by rcmn on 2008-01-18
are you familiar with the file 
/etc/X11/xorg.conf

if yes just restart in (recovery mode) to access it you have to esc or delete to view the booting console.

then your system will boot on a console prompt.
At this point just login with your user.

then use this command:
```
sudo nano /etc/X11/xorg.conf
```

this will open the configuration file of your X windows.
then try to find the lines similar to this :
  ```
  SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection

```
just replace "1680x1050" with the settings you need.
then reboot and pray .good luck.

---

### Post by maxnik on 2008-01-18
thank you,
i did find the place. However that line has multiple resolutions with different frequencies. What do I do in this case?

---

### Post by maxnik on 2008-01-18
thank you very much, i got it fixed. I added resolution and frequency, that worked before,in that line with resolutions and was able to load the screen.

---

### Post by rcmn on 2008-01-19
correct the multiple resolution can be trim to the one you need.

---

