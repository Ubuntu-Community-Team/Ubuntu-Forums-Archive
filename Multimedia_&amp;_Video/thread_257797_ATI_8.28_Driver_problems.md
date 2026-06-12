---
title: "ATI 8.28 Driver problems"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by agustin.g on 2006-09-15
Hello, i'm having issues with an ATI Radeon 9250 graphics card running on the ATI 8.28.8 on Dapper. I followed the instructions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) 

for Method n. 2 : "Generating/Installing Ubuntu packages for the 8.28.8 drivers in Ubuntu Dapper Manually". The graphics card is now working except for the fact that neither the login window nor any user accounts except from the first user (UID 1000) appear (everything seems to work, i can login and hear the "welcome sound", but there is no image on the screen,the monitor says "out of range"), which is also the account on which i was logged on when installing the drivers. Does anyone know how i could fix this?

Here is some information i thought could come in handy
```
carlos@carlos-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

```

and **dmesg | grep fglrx** isn't giving me any output. I have read the info in /var/log/Xorg.0.log can be helpful as well, but i consider it to be a bit long and will post it upon request.

Another fact worth mentioning is that Method 1 found in the link posted above was used before to install this graphics card, but the X server got messed up after we changed the card's location on the motherboard (changed PCI slots) so I reverted to a backup of the **xorg.config** file from before the installation. I ran the commands ```
sudo dpkg -r fglrx-control
sudo dpkg -r fglrx-kernel-source
sudo dpkg -r xorg-driver-fglrx
``` 
to try and remove components of the earlier installation so they wouldn't interfere with this one

I think i'm going to try doing the complete installation one more time, but in the meantime any help is greatly appreciated

thank you
agustin

---

