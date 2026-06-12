---
title: "Geforce 7300 GS not working?"
date: 2009-07-09
forum: Multimedia Software
---

### Post by Tomickescape on 2009-07-09
Hi all,

After 2 days of searching trough the net (mainly ubuntuforums) I still have the " desktop could not be enabled" 

I have this Nvidia driver: ```
05:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
```"compiz" at terminal gives me this:

```
tomickescape@tomickescape-desktop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1152x864) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

at hardware drivers it says " no propietary drivers are in use on this system" and the screen below is blank


I tried envy, which crashed.

I tried A lot of things, but none of them really worked, I hope you can help me? =)

Ow yeah, I am using Ubuntu 8.04.

Greetz,

Mick

---

### Post by d_liebscher on 2009-07-09
Hi,

as far as i know, there are two possibilities:
first: upgrade to Intrebit Ibex or higher, then it should work out of the box.

second: install grafik driver from nvidia manually:
there are a lot of manuals so here's just a short form:

[LIST=1]
[*]Backup your data!
[*]Backup your xorg.conf
[*]Download Linuxdriver from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
[*]stop your XServer and change to shell
[*]run installation
[*]reboot
[/LIST]
I tried this for my GTX260 last year, cause there was no driver "out of box" and everything worked fine.

If something go wrong, recover the xorg and everything should be like before.

I hope this is usefule for you.
Daniel

---

### Post by Tomickescape on 2009-07-09
> **d_liebscher said:**
> Hi,

as far as i know, there are two possibilities:
first: upgrade to Intrebit Ibex or higher, then it should work out of the box.

second: install grafik driver from nvidia manually:
there are a lot of manuals so here's just a short form:

[LIST=1]
[*]Backup your data!
[*]Backup your xorg.conf
[*]Download Linuxdriver from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
[*]stop your XServer and change to shell
[*]run installation
[*]reboot
[/LIST]
I tried this for my GTX260 last year, cause there was no driver "out of box" and everything worked fine.

If something go wrong, recover the xorg and everything should be like before.

I hope this is usefule for you.
Daniel

Which application do I need for a .run file? (the file that you download at Nvidia)
And how do I know if I have 32 or 64 bit?

And I am a newb....I dunnow how to backup xorg.conf....

I don't have any files currently on ubuntu (only on my external drive)

Thanks

---

### Post by d_liebscher on 2009-07-09
Hi,

ok:

backup your xorg

1. open a Konsole
2. enter sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
    this will copy the xorg file to a backupfile
    it will be useful to copy this file to a USB storage device (is it usb-stick in english too?), too

3. exit X Server with
    sudo /etc/init.d/gdm stop if you use Gnome
    sudo /etc/init.d/kdm stop if you use KDE


4. install should work with
```
sudo sh ./NVIDIA-Linux-x86-185.18.14-pkg1.run
```follow Instructions ;)

If something go wrong: run following command from shell (worst case from Live CD) 
```
 cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf 
```Daniel

---

### Post by Tomickescape on 2009-07-09
```
tomickescape@tomickescape-desktop:~$ sudo sh ./NVIDIA-Linux-x86-185.18.14-pkg1.run
[sudo] password for tomickescape: 
sh: Can't open ./NVIDIA-Linux-x86-185.18.14-pkg1.run
tomickescape@tomickescape-desktop:~$ 

```

Maybe it is at the wrong location?  =/

---

### Post by d_liebscher on 2009-07-09
Sry, I'm not at home at moment, so I must remember all these things.

try ```
sudo ./NVIDIA-Linux-x86-185.18.14-pkg1.run
```after exiting XServer (I've added some lines to my last answer)

PS: you can switch shells after stopping XServer by Alt+F1 (tty1), XServer runs on tty7, so it is Alt+F7

---

### Post by Tomickescape on 2009-07-09
Got this:

```
tomickescape@tomickescape-desktop:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
[sudo] password for tomickescape: 
tomickescape@tomickescape-desktop:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
tomickescape@tomickescape-desktop:~$ sudo sh ./NVIDIA-Linux-x86-185.18.14-pkg1.run
sh: Can't open ./NVIDIA-Linux-x86-185.18.14-pkg1.run
tomickescape@tomickescape-desktop:~$ sudo ./NVIDIA-Linux-x86-185.18.14-pkg1.run
sudo: ./NVIDIA-Linux-x86-185.18.14-pkg1.run: command not found
tomickescape@tomickescape-desktop:~$ 
```

Yes it is USB-stick...where are you from? ^^ =P

Anywayz It didn't work as you can see....=(

---

### Post by ptn107 on 2009-07-09
I would advise against the drivers from the nVidia website, unless your ready to troubleshoot problems and reinstall them with every kernel update.  You should install these packages from the official Ubuntu repositories to avoid future problems.  They are stable and work fine.  You need to be running Ubuntu 8.10 or higher:

nvidia-71-modaliases
nvidia-96-modaliases
nvidia-173-modaliases
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-180-libvdpau
nvidia-common
nvidia-glx-180
nvidia-settings

After you'll need to run 'sudo nvidia-xconfig' from a terminal to set it up.  That's it.

---

### Post by d_liebscher on 2009-07-09
@ptn107: Upgrading to 8.10 or higher was the first solution, but it seems Tomickescape would not do this. 

> nvidia-71-modaliases
nvidia-96-modaliases
nvidia-173-modaliases
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-180-libvdpau
nvidia-common
nvidia-glx-180
nvidia-settingsThe packages will not work on Ubuntu 8.04!!!

@Tomickescape : it's right, the driver must be reinstalled after ever Kernelupdate.
and I agree with ptn107: 
The packages from the official Ubuntu repositories are the best solution!

however, it should work to install the driver, hm:
you downloaded the driver from nvidia...where stored you the file?

(It is USB-Stick in Germany, but I was not sure if it is a "false friend" ;) )

---

### Post by zolero on 2009-07-09
Hi Tomickescape!

I have nearly same graphics card as you (nVIDIA GeForce 7300 GT Silent, manufactured by ASUS) working well with self built driver package version 185.18.14 on Hardy self-compiled kernel 2.6.30-rc6.

I suggest you to use my packages if you're on Hardy. They're kernel-independent and can be found (with some usage help) here: [http://ubuntuforums.org/showthread.php?t=1180364](http://ubuntuforums.org/showthread.php?t=1180364)

Hope this helps...

---

### Post by Tomickescape on 2009-07-10
> **d_liebscher said:**
> @ptn107: Upgrading to 8.10 or higher was the first solution, but it seems Tomickescape would not do this. 

I never said I don't want to update to 8.10....is it easy? and is it stable? =)  were can I do it? =)

The packages will not work on Ubuntu 8.04!!!

> @Tomickescape : it's right, the driver must be reinstalled after ever Kernelupdate.
and I agree with ptn107: 
The packages from the official Ubuntu repositories are the best solution!

however, it should work to install the driver, hm:
you downloaded the driver from nvidia...where stored you the file?

(It is USB-Stick in Germany, but I was not sure if it is a "false friend"  ;) ]I stored the file from nvidia in .tmp map (the default map for the downloads at mozilla, and yes I know it means temporary =P)... I also to tried to store it to desktop...but when I click on it, it still says " choose an application" 








p.s.Ich kan ein klein bisschen Deutsch reden, aber sehr slecht.
Ich komme von die Niederlande. ;)

Haha

---

### Post by Tomickescape on 2009-07-10
> **zolero said:**
> Hi Tomickescape!

I have nearly same graphics card as you (nVIDIA GeForce 7300 GT Silent, manufactured by ASUS) working well with self built driver package version 185.18.14 on Hardy self-compiled kernel 2.6.30-rc6.

I suggest you to use my packages if you're on Hardy. They're kernel-independent and can be found (with some usage help) here: [http://ubuntuforums.org/showthread.php?t=1180364](http://ubuntuforums.org/showthread.php?t=1180364)

Hope this helps...

I installed 
[nvidia-source_185.18.14_zolerubuntu1_all.deb]("http://rapidshare.com/files/241613263/nvidia-source_185.18.14_zolerubuntu1_all.deb")  that version

but it still doesn't work =/  still can't enable my desktop effects....

Thanks for trying ;)

---

### Post by d_liebscher on 2009-07-10
ok,

this is zoleros turn now ;)

If it just don't work after all, you have a few possibilities left (upgrading to 8.10 or 9.04, compile your own...and so on)
anyway, II will follow this Thred   ;)

Daniel

PS: Sehr interessant :)

---

### Post by Tomickescape on 2009-07-10
> **d_liebscher said:**
> ok,

this is zoleros turn now ;)

If it just don't work after all, you have a few possibilities left (upgrading to 8.10 or 9.04, compile your own...and so on)
anyway, II will follow this Thred   ;)

Daniel

PS: Sehr interessant :)

U seem to know a lot 2...could you please take a look at my another thread?

[http://ubuntuforums.org/showthread.php?t=1206588](http://ubuntuforums.org/showthread.php?t=1206588)

It still don't have adobe flashplayer working =(

I got gnash player or something like that now...but it doesn't really work...it has a lot of bugs...it can't play veoh.com clips....(anime)   I can change volume of video clips at youtube...etc....

Thanks in advance ^^'

Ow yeah, And I hope zeloro can help me 2 =)

---

### Post by Tomickescape on 2009-07-11
I may got some more info....I have another intern hard drive...with windows xp on it...it had the blue screen of death, so I am going to re-install it after this reply...

Anyway, I was checking if there are any files on that drive that I need to save...then I bumped into a map called  NVIDIA the next map was called WIN2K en the map after that was called **169.21**  could it be, that is the driver type I need......?

Maybe that could help =/ =)

---

### Post by zolero on 2009-07-11
Dooi Tomickescape.

Did you **compiled and installed** the NVIDIA kernel module as I describet in my other post? Did you removed **any previous** NVIDIA module from kernel? And finally: did you installed the driver package too?

If you can answer positively to questions above, try rebooting in recovery mode (choose root shell when asked) and issue this command at prompt:

```
nvidia-xconfig
```

Cheers.

---

