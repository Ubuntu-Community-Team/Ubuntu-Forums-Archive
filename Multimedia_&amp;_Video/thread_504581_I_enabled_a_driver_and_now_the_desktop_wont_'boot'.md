---
title: "I enabled a driver and now the desktop wont 'boot'."
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by Colin-uk on 2007-07-19
Hi all,

I finally got my ubuntu install how I like it and decided i'd like to try and get dual monitors working, so after reading a few threads and instructions about how to do it, i went ahead and installed something which i think was called nvidia-settings via the synaptics manager thing, and rebooted, there didnt seem to be any new menu options, then I noticed something called Restriced driver managment so I opened that and found a nvidia driver listed. I clicked enable thinking it would enable dual monitors but when i restarted it just gave me a command prompt. 

heres the error information I managed to get:

```
Error. API Mismatch: The nVidia kernal module has the version 1.0-9755 but this X module has the version 1.0-9631

Please make sure the kernal module and the nvidia driver components have the same version. 
(EE) Nvidia(0) failed to inialize the nvidi kernal module please ensure that there is a supported nvidia gpu in the system and that the nvidia files have been created properly.

Consult Nvidia readme for details 

Screen found but none have usable configuration.
```

So does anyone have any idea how to fix this? Im pretty new at ubuntu so im a bit lost really...

Thanks,
Colin

---

### Post by tgm4883 on 2007-07-19
Im guessing your installed the nvidia driver from the nvidia website?  You will need to reinstall that, as what you have done is install an older version of the file which is incompatible with the kernel module.

---

### Post by Colin-uk on 2007-07-19
Well I opened synaptics and searched for it there, found it and installed it. 

I'll have a look on the nVidia website and see if there is a compatible version, will the version numbers be the same? Should I be looking for version 1.0-9755 or version 1.0-9631?

Thanks for th help!

Thanks,
Colin

---

### Post by tgm4883 on 2007-07-19
> **Colin-uk said:**
> Well I opened synaptics and searched for it there, found it and installed it. 

I'll have a look on the nVidia website and see if there is a compatible version, will the version numbers be the same? Should I be looking for version 1.0-9755 or version 1.0-9631?

Thanks for th help!

Thanks,
Colin

Which card do you have?

---

### Post by hequ on 2007-07-19
> **Colin-uk said:**
> Well I opened synaptics and searched for it there, found it and installed it. 

I'll have a look on the nVidia website and see if there is a compatible version, will the version numbers be the same? Should I be looking for version 1.0-9755 or version 1.0-9631?

Thanks for th help!

Thanks,
Colin

First install the driver from nvidia website, then edit your /etc/default/linux-restricted-modules-common so it looks following:

```

DISABLED_MODULES="nv nvidia_new"

```

After that it should work.

---

### Post by tgm4883 on 2007-07-19
Actually, I wouldn't install the driver from the nVidia website.  You already had it working once, and that driver will cause you more work over time when updating and such

---

### Post by Colin-uk on 2007-07-19
> Which card do you have? 

My graphics card is an nVidia FX 5200 

not sure which version I need from here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

-Colin

---

### Post by tgm4883 on 2007-07-19
> **Colin-uk said:**
> My graphics card is an nVidia FX 5200 

not sure which version I need from here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

-Colin

lets try this first
sudo apt-get install nvidia-glx

---

### Post by Colin-uk on 2007-07-19
Ok I tried that. It told me that nvidia-glx is allready the latest version. 

-Colin

---

### Post by tgm4883 on 2007-07-19
> **Colin-uk said:**
> Ok I tried that. It told me that nvidia-glx is allready the latest version. 

-Colin

Thats what I thought it would say.

Lets do 
sudo apt-get remove nvidia-glx nvidia-kernel-common

Then

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

---

### Post by Colin-uk on 2007-07-20
Ok, I entered those commands and the last one gave this: 

```
 Using X Configuration File /etc/X11/xorg.conf
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup
New configuration file written to /etc/X11/xorg.conf

``` 

So I rebooted and the debug information screen now gives me this information: 

```

FATAL: Error running install command for NVIDIA.
(EE) NVIDIA(0) Failed to load Nvidia kernel module!
(EE) NVIDIA(0) *** Aborting *** 
Screen(s) found, but none have a usable configuration.

```

-Colin

---

### Post by tgm4883 on 2007-07-20
> **Colin-uk said:**
> Ok, I entered those commands and the last one gave this: 

```
 Using X Configuration File /etc/X11/xorg.conf
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup
New configuration file written to /etc/X11/xorg.conf

``` 

So I rebooted and the debug information screen now gives me this information: 

```

FATAL: Error running install command for NVIDIA.
(EE) NVIDIA(0) Failed to load Nvidia kernel module!
(EE) NVIDIA(0) *** Aborting *** 
Screen(s) found, but none have a usable configuration.

```

-Colin

Now lets do this
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Colin-uk on 2007-07-20
Ok, done, It gave with a list of what i think were drivers, i choose "nvidia" (is that the right one?) and pressed ok. then it asked me for my resolution, and I chose 1280x1024 and pressed ok and it took me back to the command prompt. 

Restarting gives me the same debug information as before.

-Colin

---

### Post by tgm4883 on 2007-07-20
> **Colin-uk said:**
> Ok, done, It gave with a list of what i think were drivers, i choose "nvidia" (is that the right one?) and pressed ok. then it asked me for my resolution, and I chose 1280x1024 and pressed ok and it took me back to the command prompt. 

Restarting gives me the same debug information as before.

-Colin

The same no usable screens?

---

### Post by Colin-uk on 2007-07-21
Yeah :(

---

### Post by RomeReactor on 2007-07-21
Hi. I'm not sure how to remove the problematic driver, nut I think you can get your desktop back by doing:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
as **tgm4883** said, and choosing **nv** as the driver. This at least should restore your graphical desktop, though without acceleration. But it will be easier for you to troubleshoot this further this way.

---

### Post by DDRFreak21 on 2007-07-21
Similar problem i just posted on:
[http://ubuntuforums.org/showthread.php?p=3057189#post3057189]("http://ubuntuforums.org/showthread.php?p=3057189#post3057189")

---

### Post by Colin-uk on 2007-07-21
Ah, ive done it, the first time I did the previous command i chose "nvidia" instead of "nv" so it didnt work.

I did it again and chose "nv" this time and now it works, and has booted to the desktop ok :) 

I think i'll give up on trying to get dual monitors to work for now, its so confusing (and annoying when it doesnt work) lol.

Thanks for all your help, its much appreciated :) 

-Colin

---

### Post by tgm4883 on 2007-07-21
> **Colin-uk said:**
> Ah, ive done it, the first time I did the previous command i chose "nvidia" instead of "nv" so it didnt work.

I did it again and chose "nv" this time and now it works, and has booted to the desktop ok :) 

I think i'll give up on trying to get dual monitors to work for now, its so confusing (and annoying when it doesnt work) lol.

Thanks for all your help, its much appreciated :) 

-Colin

The nv driver is the open source drivers, they work pretty well.  As for adding a second screen.  [http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_setup_Dual_Monitors_with_NVidia_in_Feisty_Fawn](http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_setup_Dual_Monitors_with_NVidia_in_Feisty_Fawn)

---

### Post by Colin-uk on 2007-07-21
Thanks, but when it comes to the part of the guide where I have to restart X, it doesnt restart, it just gives me the screen with the same debug info on it.

Even without following any guides, just restarting X gives me a "connection to server lost" error message..

-Colin

---

