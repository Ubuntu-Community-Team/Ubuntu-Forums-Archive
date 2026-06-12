---
title: "GLX not loaded automatically ?"
date: 2010-02-11
forum: Multimedia Software
---

### Post by akwatve on 2010-02-11
Hi,

I am unable to use k3d or blender due to a weird graphics related problem. It says glx is not loaded. I tried to put Load "glx" line in my xorg.conf but no success :-(
Even glxinfo and glxgears complain for the extension glx
> a@pc1:/etc/X11$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


My xorg.conf is :
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerFlags"
    Option "DontZap" "False"
EndSection

Section "Module"
    Load        "glx"
EndSection

```

---

### Post by lykwydchykyn on 2010-02-11
It may be your graphics card doesn't support GLX, or you aren't using a driver for your card that supports GLX.

To know which, we'll need to know what your card/chipset is.

If you don't know, running this command and posting the output here would be helpful:

```

lspci |grep -i vga

```

---

### Post by akwatve on 2010-02-11
I think I have NVidia Card. here is the output of the command you suggested.

```
a@pc1:/etc/X11$ lspci |grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
```

---

### Post by lykwydchykyn on 2010-02-11
> **akwatve said:**
> I think I have NVidia Card. here is the output of the command you suggested.

```
a@pc1:/etc/X11$ lspci |grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
```

Yes, and a fairly old one at that.  I have similar models in my computers at home, and I'm not sure I could get compositing in KDE working on them.

Run the hardware drivers tool and make sure you're running the proprietary driver.  Compositing may or may not work with the proprietary driver, but it most certainly won't work with the default FOSS driver.

---

### Post by akwatve on 2010-02-11
Ahh
That solution worked like charm.
Thanks a lot for your help.

---

### Post by dave-o-dave on 2010-04-30
Hi, 

I have pretty much the same problem. I am trying to install freewrl-1.22.5 on a sony vaio with ubuntu 9.10. 
In my /etc/X11/xorg.conf it says driver 'vesa'. 
The output from the command discussed above is: 

```

 david@david-laptop:~$ lspci |grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation Device 0a75 (rev a2)

```I think the software is installed correctly, but when I try to open one of the files with it I get the error

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
FreeWRL can not find an appropriate visual from GLX

```Coud you offer some more detail on how to :
> 
Run the hardware drivers tool and make sure you're running the proprietary driver. Compositing may or may not work with the proprietary driver, but it most certainly won't work with the default FOSS driver.
or any other advice. 

Thanks in advance!

---

### Post by akwatve on 2010-04-30
The tool you need is called jockey-kde or jockey-gtk
In adept, search for jockey and you should be able to find it.
Install and run it to enable/disable drivers.

Cheers,

---

### Post by dave-o-dave on 2010-04-30
I have just noticed this is a Kubuntu thread, where as I am runnung Ubuntu. 

Would your advice still be the same? 

I just checked my synaptic and jockey-gtk is installed. As is jockey-common and fglrx-modliases. 


Are there any further suggestions ?

---

### Post by akwatve on 2010-04-30
I have never used ubuntu. But try running 
```
sudo jockey-gtk
```
I am quite optimistic it will let you enable proprietary drivers if they are installed.

---

### Post by dave-o-dave on 2010-04-30
This has brought up the hardware drivers menu ( I am sure you knew it would do that.) 

i tried activating them in an earlier attempt. 
I selected NVIDIA accelerated graphics driver (version 185) recommended 
and clicked activate. 

However when I then reboot, my desktop and graphical interface etc will not start up. The boot process does not go past the ubuntu logo. 

I then have to go into recovery mode and replace /etc/X11/xorg.conf with xorg.conf.failsafe to get out of this again.

---

### Post by akwatve on 2010-04-30
Hmmm
That is strange.
Did jockey display any errors while activating ?
Where did you get your drivers from ? Try the ones in the repos first.

I would also try unintalling and re-installing the drivers. And try to see if there is some configuration problem while installation.

I am no driver expert. So if nothing works, then just wait for some expert to respond

---

### Post by dave-o-dave on 2010-04-30
Don't know where the drivers are from. I haven't knowingly downloaded any additional drivers. 

How do I 'try the ones in the repos' ?

---

### Post by akwatve on 2010-04-30
Hmm then most probably you have the drivers from the ubuntu repository.

---

### Post by dave-o-dave on 2010-04-30
hmm...well i am starting to worry a little now. but thanks for your help anyway. 

is there anyone out there with some other ideas? 

a friend has suggested starting again and installing ubuntu 10.04. 
is this likely to help?

---

