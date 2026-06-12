---
title: "[SOLVED] PS3 Screen Messed Up"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by tomihasa on 2008-01-27
I installed Ubuntu 7.10 to my PlayStation 3. I have a HD TV, name LG 32LT75, resolution 1366 x 768, 1080P, HDMI. The resolution is so messed up (that means low), that when I click System on top, an installation program for Evolution starts (but the installation window is so big I need to close it) and I can't do much with the menus, because I get to wrong places. So is there a way manually to change the resolution to a higher one without using a graphical user interface? I'm a newbie, so I haven't changed Linux settings files manually.

---

### Post by ajmorris on 2008-01-27
> **tomihasa said:**
> I installed Ubuntu 7.10 to my PlayStation 3. I have a HD TV, name LG 32LT75, resolution 1366 x 768, 1080P, HDMI. The resolution is so messed up (that means low), that when I click System on top, an installation program for Evolution starts (but the installation window is so big I need to close it) and I can't do much with the menus, because I get to wrong places. So is there a way manually to change the resolution to a higher one without using a graphical user interface? I'm a newbie, so I haven't changed Linux settings files manually.

Hi there,
yes, this is very possible.
Open up /etc/X11/xorg.conf with a CLI file editor such as nano,
i.e:```
nano /etc/X11/xorg.conf
```

and change the default resolution in what you will have that looks a little like this:
```
Section "Screen"
SubSection      "Display"
Depth   24
Modes   "1280x800"
EndSubSection
EndSection

```


just change the Modes part to the resolution you want.

---

### Post by tomihasa on 2008-01-27
> **ajmorris said:**
> Hi there,
yes, this is very possible.
Open up /etc/X11/xorg.conf with a CLI file editor such as nano,
i.e:```
nano /etc/X11/xorg.conf
```

and change the default resolution in what you will have that looks a little like this:
```
Section "Screen"
SubSection      "Display"
Depth   24
Modes   "1280x800"
EndSubSection
EndSection

```


just change the Modes part to the resolution you want.

Thanks. What should I do about the existing lines? Remove them all? Or add the "Display" SubSection to the beginning or to the end of the "Screen" Section? My "Screen" lines are:

```

Section "Screen"
   Identifier   "Default Screen"
   Device   "Tyypillinen näytönohjain"
   Monitor   "Tyypillinen näyttö"
   DefaultDepth   24
EndSection

```

I installed the Finnish language version, so approximate translations for the Finnish parts:

"Tyypillinen näytönohjain" = "Typical graphical interface"
"Tyypillinen näyttö" = "Typical screen"

Actually the Finnish language characters (a and o with umlauts) are a mess as Linux files have been made for English talking people first (I guess), but because I found the correct Finnish language characters more easily, I used them here in this forum. :)

---

### Post by tomihasa on 2008-01-27
And I have another problem: I can't save the file. I guess I need to log in as the main user. How do I do that? I used nano on the Kboot screen, and when I nanoed the file, and tried saving it, I get this message:

"[ Error writing /etc/X11/xorg.conf: Read-only file system ]"

---

### Post by tomihasa on 2008-01-27
Hey, I can use the File Browser in the graphical user interface and I can get to the /home/bin/ directory with it. Maybe one of those programs can be used to change the screen settings also?

---

### Post by tomihasa on 2008-01-27
Still kind of talking to myself, sorry. Because I can use the File Browser, I can execute xterm from /usr/bin/, but when I try changing the user permissions for the xorg.conf file with command chmod u+w xorg.conf, I get this text:

"chmod: changing permissions of `xorg.conf´: Operation not permitted"

---

### Post by tomihasa on 2008-01-27
I did some googling and I found out I can use sudo for super user:

```

sudo nano /etc/X11/xorg.conf

```

As you guided me, I made the "Screen" section like this:

```

Section "Screen"
SubSection      "Display"
Depth   24
Modes   "1280x800"
EndSubSection
EndSection

```

But my graphical user interface didn't start anymore. Instead, I got this text at some point:

```

Loading, please wait...
usplash: No usable theme found for 576x460
screen init failed

Ubuntu 7.10 localhost tty1

localhost login:

```

So I put back the original stuff to the "Screen" Section and put the "Display" SubSection to the bottom:

```

Section "Screen"
   Identifier   "Default Screen"
   Device   "Tyypillinen näytönohjain"
   Monitor   "Tyypillinen näyttö"
   DefaultDepth   24
SubSection      "Display"
Depth   24
Modes   "1280x800"
EndSubSection
EndSection

```

Now Ubuntu's graphical user interface starts, but again with the pretty unusable low resolution. Any other suggestions? I might be closer now of resolving this problem?

---

### Post by tomihasa on 2008-01-27
I found some interesting pages:

[http://psubuntu.com/2007/02/16/fullscreen-mode-for-your-1080p-hdtv/](http://psubuntu.com/2007/02/16/fullscreen-mode-for-your-1080p-hdtv/)
[http://psubuntu.com/forum/viewtopic.php?t=13](http://psubuntu.com/forum/viewtopic.php?t=13)
[http://www.edepot.com/playstation3.html](http://www.edepot.com/playstation3.html)

Now my menus are gone, because the screen area is too big for my HD TV, but things are getting better as I now have a bigger resolution!

---

### Post by ajmorris on 2008-01-27
> **tomihasa said:**
> I found some interesting pages:

[http://psubuntu.com/2007/02/16/fullscreen-mode-for-your-1080p-hdtv/](http://psubuntu.com/2007/02/16/fullscreen-mode-for-your-1080p-hdtv/)
[http://psubuntu.com/forum/viewtopic.php?t=13](http://psubuntu.com/forum/viewtopic.php?t=13)
[http://www.edepot.com/playstation3.html](http://www.edepot.com/playstation3.html)

Now my menus are gone, because the screen area is too big for my HD TV, but things are getting better as I now have a bigger resolution!

:lolflag: good to see you made some progress there :D
This could be fixed by once again going into /etc/x11/xorg.conf and changing the resolution in there (doesnt have to be of the format i showed in my other post, do it according to your format) also, you dont have to *change* the resolution in there, you can add another resolution, giving you the option within ubuntu to change them if you need to, there is also the default resolution that you can set.

---

### Post by tomihasa on 2008-01-29
Problem solved. I started nano:

```

sudo nano /etc/kboot.conf

```

And edited kboot.conf (The end of the UUID part is hidden, just in case.) (First I used video=ps3fb:mode:133 for Fullscreen 1080p, but the menus, trash bin, etc. disappeared, so I switched the number 133 to 5.):

```

message=/etc/kboot.msg
default=linux 
timeout=100 
root=/dev/sda3 
linux="/boot/vmlinux initrd=/boot/initrd.img video=ps3fb:mode:5 root=UUID-..."

```

I started nano again:

```

sudo nano /etc/X11/xorg.conf

```

And edited xorg.conf:

```

Section "Screen" 
   Identifier      "Default Screen" 
   Device   "Tyypillinen näytönohjain"
   Monitor   "Tyypillinen näyttö"
   DefaultDepth    24 
   DefaultFbBPP    32 
   SubSection "Display" 
           Depth           24 
           FbBPP           32 
   EndSubSection 
   SubSection "Display" 
           Depth           15 
           Modes           "1024x720" "1024x768" "800x600" "640x480" 
   EndSubSection 
   SubSection "Display" 
           Depth           16 
           Modes           "576x384" "1024x768" "800x600" "640x480" 
   EndSubSection 
EndSection 

```

That file contains a bit Finnish as I installed the Finnish language version. Some approximate translations:

"Tyypillinen näytönohjain" = "Generic Video Card"
"Tyypillinen näyttö" = "Generic Monitor"

---

