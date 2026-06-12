---
title: "How to mount NRG images? I have exhausted all means."
date: 2011-08-20
forum: Multimedia Software
---

### Post by xieqiao on 2011-08-20
I have some NRG images built with Nero burning software, and I can mount them with Daemon Lite virtual CD-ROM program under MS Windows environment.  But under 64-bit Ubuntu, there is no equivalent software to resolve my problem. I have installed Furius ISO,  AcetoneISO,  MountManager, Gmount-iso, ISO Master and cdemu. But none of them worked. Only Furius ISO Mount Tool could seemingly mount an NRG image, but there is only blank related to the image folder within the Nautilus file manager.  I don't want to convert NRG to ISO. Could anyone help me? I even tried the following command lines.  But I'm really not good at command lines in a terminal.  I read the following instructions, and experimented, but to no fruition.  Are there other simpler means to mount an NRG image?  

[https://help.ubuntu.com/community/ManageDiscImages](https://help.ubuntu.com/community/ManageDiscImages)

To Mount

sudo mkdir /media/example 

sudo mount -o loop,offset=307200 /path/to/example.nrg /media/example

---

### Post by shantiq on 2011-08-20
sorry misread you ( had not seen you said you were not keen on iso )==


but if you wanted to try the iso route   NRG is really a NERO file and NERO is really not Linux

you could try this


Install nrg2iso in Ubuntu

```
sudo apt-get install nrg2iso

```


**then**

```
nrg2iso image.nrg image.iso
```


then play the iso in say VLC


see if maybe that works for you...

---

### Post by SidebySide on 2011-08-20
I just can help you via terminal(CLI):
1. 
```
sudo mkdir /media/iso
```2.  run iso file with:[FONT=Verdana]
[/FONT]```
sudo mount -o loop /DIRECTORY/iamge.iso /media/iso
```or below form, that I don't know different between them:[FONT=Verdana]
[/FONT]```
sudo mount -o loop -t iso9660 /DIRECTORY/iamge.iso /media/iso
```[LEFT]Close the terminal window and then:
4. Go to the Ubuntu Main Menu
5. Click Places and select iso
6. The file browser will open, displaying the contents of the ISO image.
* To unmount the file, use this command in a terminal window:sudo umount /media/iso
To mount **[SIZE=3][COLOR=red]nrg[/COLOR][/SIZE]** formt files, replace iso with nrg in upstairs! commands.
-------------------------------------------------------------------------------

fuseiso (software-center)
... it can also mount single-tracks bin, mdf, [COLOR=Red]nrg[/COLOR] and img.
[http://fuse.sourceforge.net/](http://fuse.sourceforge.net/)
[/LEFT]

---

### Post by xieqiao on 2011-08-20
> **shantiq said:**
> sorry misread you ( had not seen you said you were not keen on iso )==
  
you could try this
Install nrg2iso in Ubuntu
 see if maybe that works for you...

Thank you. I converted the nrg image to iso by installing nrg2iso, and running it in  a terminal. But the converted iso file still could not be recognised by all the above-mentioned programs.  When I tried to play the iso with VLC, the 64-bit  Ubuntu 11.04 OS froze, and I had to reset and reboot the whole OS manually.  This is the first time the 11.04 OS has crashed. 

I have even installed a Nero Linux for Ubuntu. But it can only burn an NRG file into a CD instead of mounting it.  The past 2 days have been quite frustrating for me in my desperate attempt to figure out a way to mount NRG files in Ubuntu.  By the way, I don't want to convert, I just want to mount. Conversion is actually meaningless in the first place.  I have a big library of NRG image files.  Pray to God for a miracle in the name of Jesus Christ!

---

### Post by xieqiao on 2011-08-23
I have tried Wine + Daemon Lite, but Daemon Lite could not be run under the Wine environment.

---

### Post by xieqiao on 2011-08-26
I have just found that some NGR images can actually be mounted using Furius ISO.  But those NRG images backing up music CDs, VCD and DVD videos that I bought cannot be mounted under the Ubuntu environment.

---

### Post by petsam on 2013-01-22
I found this info for nrg images
[http://ubuntuforums.org/archive/index.php/t-1514244.html](http://ubuntuforums.org/archive/index.php/t-1514244.html)

Says that audio nrg images cannot be mounted/converted by the proposed programs, but can be handled by with CDemu.
Instructions for use and installation are included.
I haven' t tested yet.
Hope it works...

---

