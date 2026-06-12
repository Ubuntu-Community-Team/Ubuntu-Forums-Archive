---
title: "can't change my resolution"
date: 2009-06-01
forum: Multimedia Software
---

### Post by concherover on 2009-06-01
Hey guys i'm pretty new to ubuntu and linux so be nice...lol.. ah i'm trying to change my resolution i'm using my redeon x1300 card but i'm using a 47" lcd tv for a monitor.  I need to change the resolution cause I can't get some the bottons.  

any way I tryed the following

adam@adam-desktop:~$ sudo cp /etc/x11/xorg.conf
[sudo] password for adam: 
Sorry, try again.
[sudo] password for adam: 
cp: missing destination file operand after `/etc/x11/xorg.conf'
Try `cp --help' for more information.
adam@adam-desktop:~$ 

any help would be great.  

cheers 

Concherover

---

### Post by madverb on 2009-06-01
You need to say where you want the file copied to. Are you trying to open the file to edit it?
```
gksu gedit /etc/X11/xorg.conf
```
If you are trying to make a backup of it you can do;
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Also remember that files in Linux are case sensitive. It has to be **X**11

---

### Post by concherover on 2009-06-01
I'm still not getting it this is what i've done 
I went into the terminal and entered 
gksu gedit /etc/X11/xorg.conf

I changed some of these setting 
like HorizSync to 31-72 and also the resolution to 1280 to 800 


Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       31-72
        VertRefresh     50-120
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
             SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes           "1280x800"
             EndSubSection


and nothing changes what do I do next?


Cheers 
Concherover

---

### Post by MichaelSammels on 2009-06-01
If you are using an nvidia card, install the nvidia server settings via synaptic? That helped me.

---

### Post by concherover on 2009-06-01
no its a ATI Radeon x1300

---

### Post by MichaelSammels on 2009-06-01
Try this:

[http://ubuntuforums.org/archive/index.php/t-616786.html](http://ubuntuforums.org/archive/index.php/t-616786.html)

---

### Post by mhgsys on 2009-06-01
well, if you adjust your xorg.conf settings you'll need to restart gdm for the settings to take effect.

I recommend to go to console ((ctrl+alt+f1) (f2,f3 etc)

login, 
type

```

sudo /etc/init.d/gdm stop

```
this will stop gdm

```

sudo /etc/init.d/gdm start

```
this will start gdm 


Since you didn't make a backup first;
When your settings fail go back to console 
(ctrl+alt+f1) (f2,f3 etc)

and type:
```

sudo dpkg-reconfigure xserver-xorg

```

then again type:
```

sudo /etc/init.d/gdm stop

```
```

sudo /etc/init.d/gdm start

```

*notice, you can also use 
```
sudo /etc/init.d/gdm restart
```
but in my experience I've had some errors with that command like sometimes X was still running on :0
that's why I recommend to start , stop gdm manually.

---

