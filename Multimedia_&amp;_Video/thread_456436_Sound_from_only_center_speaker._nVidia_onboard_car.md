---
title: "Sound from only center speaker. nVidia onboard card."
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by Sean K on 2007-05-27
Hello,

I recently upgraded from 6.10 to 7.04 and subsequently lost most functionality of my speakers. I have a Creative 5.1 surround system. My sound card is onboard and when I look under Hardware Information it shows up as:

Vendor: nVidia Corporation
Device: MCP51 High Definition Audio

The problem I'm facing is that I only get sound from the front center speaker, and the sound is very unclear at that. The other four speakers don't work, but the bass does.

I've tried the Comprehensive Sound Problem Solutions Guide, and I get as far as Step 3. When I go to the ALSA site ([http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)) and check under nVidia, I don't know what to do past this. I'm taken to this page:

[http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia](http://bugtrack.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia)

What do I do from here? Any ideas for what I can try?

Thanks in advance!

**EDIT:** I tried to install my sound card driver using the Solutions Guide. I followed the steps under ALSA Driver Compilation, but when I ran the last command:

sudo module-assistant a-i   alsa-source

It doesn't go to 100%. Here is the error message:
```

Package alsa-source was not built successfully, see
/var/cache/modass/alsa-source*buildlog* for details!

```

The driver I selected was the 'hda-intel" one because on this page ([http://www.nvidia.com/object/linux_nforce_1.21.html](http://www.nvidia.com/object/linux_nforce_1.21.html)) it says so. Note that on the website it has an underscore rather than a hyphen.

Any ideas?

**EDIT #2:** I tried following the instructions on this page: [http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://bugtrack.alsa-project.org/main/index.php/Matrix:Module-intel8x0)

I realize the page is for intel8x0, but I thought it might work... it didn't. Here is what I got:

```
ALSA modules were successfully compiled.

if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/sean/Desktop/alsa-driver-1.0.14rc4/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
install: cannot create directory `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
make: *** [install-headers] Error 1

```

I then tried to replace intel8x0 with hda_intel, but it didn't work either. This is what I got:

```
ALSA modules were successfully compiled.

if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/sean/Desktop/alsa-driver-1.0.14rc4/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
install: cannot create directory `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
make: *** [install-headers] Error 1

```

Any ideas? Thanks! :)

---

### Post by Sean K on 2007-05-28
I see a lot of threads about sound having to do with nVdidia, but none of them have any answers that work. Does anybody know whats going on?

---

### Post by Sean K on 2007-05-29
Can someone please just reply and tell me whether or not there is a fix? Does nobody know what's going on?

---

### Post by dr-nix on 2007-06-01
> **Sean K said:**
> Can someone please just reply and tell me whether or not there is a fix? Does nobody know what's going on?
I also had problems when i upgraded from 6.10 to 7.04 today. I have a realtek (or nvidia, whatever) sndcard though (laptop). 

 Anyways i also use snd_hda_intel, but i couldn't understand why it didn't work, xmms, vlc and so on played just fine and xmms acted as if the soundcard was working fine. The only problem as a total lack of sound out of my speakers (or my headphone-jack). I finally found out it is an issue with the kernel. I solved it by simply rolling back the kernel to 2.6.20.10 and now everything works fine. I guess you could probably modify your current kernel. 

If you don't want to try kernel 2.6.20-10 you can just make sure to remove the kernel-support of hda-intel and download the latest alsa-driver instead.

---

### Post by drago1231 on 2007-09-03
I got the same message saying "Permission denied." I went into the properties of the folder (/usr), clicked the permissions tab, and found that I could not edit the permissions because I was not the owner. the owner was listed as root, not as my username. To not get the "permission denied" messages, do the following.

-write down the path of the folder with the install file/alsa driver folder
-logout of your account
-at the login screen hit ctrl+alt+f6
this will bring you to the terminal
-it should say the following
name-desktop login:
-instead of putting your username, type root and press enter
-the password should be the same as your account, so type that in.
(if it is not the same, press ctrl+alt+f7, log back into your account, goto system --> administration --> users and groups --> click root, then properties, then edit the password)
-at the command line, you just do whatever you tried before. in my case, i went to the folder of the install file, which i downloaded to the desktop, and installed it. i did this using the following commands.

cd /(full filepath)
./install

or

cd /(filepath)/alsa-driver-1.0.xx
./configure
make
make install
./snddevices

....etc.


hope this helps.

---

### Post by lowville on 2007-12-15
I had the same problems. I found that the permission problems went away if I entered:

sudo ./configure

then

sudo make

then

sudo make install

-----------
sudo makes the command execute with the permissions of root. the problem is that novices like me and the others in this thread wouldn't know that if one enters:

sudo ./configure ; make ; make install

then only the first command gets the root permissions.

---

