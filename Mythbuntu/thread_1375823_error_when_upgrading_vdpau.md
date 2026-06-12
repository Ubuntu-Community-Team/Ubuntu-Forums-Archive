---
title: "error when upgrading vdpau"
date: 2010-01-08
forum: Mythbuntu
---

### Post by jfenton78 on 2010-01-08
I'm using the Karmic vdpau ppa to upgrade vdpau, but I get the following error in synaptic

E: /var/cache/apt/archives/nvidia-glx-185_185.18.36-0ubuntu10~karmic~nvidiavdpauppa4_i386.deb: trying to overwrite '/usr/lib/libvdpau_nvidia.so.185.18.36', which is also in package nvidia-185-libvdpau 0

How can I do an upgrade? If I go into the restricted drivers I see options for version up to 195, but none of them work. It tried to down load, but fails.

jeff

---

### Post by emoguitarist06 on 2010-01-16
> **jfenton78 said:**
> I'm using the Karmic vdpau ppa to upgrade vdpau, but I get the following error in synaptic

E: /var/cache/apt/archives/nvidia-glx-185_185.18.36-0ubuntu10~karmic~nvidiavdpauppa4_i386.deb: trying to overwrite '/usr/lib/libvdpau_nvidia.so.185.18.36', which is also in package nvidia-185-libvdpau 0

How can I do an upgrade? If I go into the restricted drivers I see options for version up to 195, but none of them work. It tried to down load, but fails.

jeff

I get the same error!!

Can anyone help?

---

### Post by azmyth on 2010-01-16
Uninstall the the nvidia-xxx-libvdpau and nvidia-xxx-libvdpau-dev. Where xxx is the version number. The ppa use a packed called libvpau1 and libvdpau-dev instead.

---

### Post by emoguitarist06 on 2010-01-16
> **azmyth said:**
> Uninstall the the nvidia-xxx-libvdpau and nvidia-xxx-libvdpau-dev. Where xxx is the version number. The ppa use a packed called libvpau1 and libvdpau-dev instead.

OK i removed nvidia-185-libvdpau & I didn't have nvidia-xxx-libdvdpau-dev installed.

I ran sudo apt-get upgrade and this is what I got

```
~$ sudo apt-get upgrade      
The following pakcages will be upgraded:
 nvidia-glx-185
Preparing to replace nvidia-glx-185 185.18.36-0ubuntu9 (using .../nvidia-glx-185_185.18.36-0ubuntu10~karmic~nvidiavdpauppa4_i386.deb) ...
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
Unpacking replacement nvidia-glx-185 ...
dpkg: error processing /var/cache/apt/archives/nvidia-glx-185_185.18.36-0ubuntu10~karmic~nvidiavdpauppa4_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libvdpau_nvidia.so.185.18.36', which is also in package nvidia-185-libvdpau 0:185.18.36-0ubuntu9
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace ubuntu-tweak 0.5.1-0~20100115~karmic1 (using .../ubuntu-tweak_0.5.1-0~20100116~karmic1_all.deb) ......
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-185_185.18.36-0ubuntu10~karmic~nvidiavdpauppa4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
~$ 
```  

?????????

---

### Post by azmyth on 2010-01-16
Are you sure you removed the proper package?

$ apt-file search libvdpau_nvid
nvidia-185-libvdpau: /usr/lib/libvdpau_nvidia.so
**_nvidia-185-libvdpau_: /usr/lib/libvdpau_nvidia.so.185.18.36**
nvidia-185-libvdpau: /usr/lib32/libvdpau_nvidia.so
nvidia-185-libvdpau: /usr/lib32/libvdpau_nvidia.so.185.18.36

I would then manually install the 195 driver with 

sudo apt-get install nvidia-195-kernel-source,nvidia-195-modaliases,nvidia-glx-195,libvdpau1

---

### Post by emoguitarist06 on 2010-01-16
> **azmyth said:**
> Are you sure you removed the proper package?

$ apt-file search libvdpau_nvid
nvidia-185-libvdpau: /usr/lib/libvdpau_nvidia.so
**_nvidia-185-libvdpau_: /usr/lib/libvdpau_nvidia.so.185.18.36**
nvidia-185-libvdpau: /usr/lib32/libvdpau_nvidia.so
nvidia-185-libvdpau: /usr/lib32/libvdpau_nvidia.so.185.18.36

I would then manually install the 195 driver with 

sudo apt-get install nvidia-195-kernel-source,nvidia-195-modaliases,nvidia-glx-195,libvdpau1

MUAHAHAHA!!! Thank You Thank You Thank You!!

It worked!!

---

### Post by frediE on 2010-01-26
this worked for me also... thanks!

---

### Post by Nullexe on 2010-03-16
Worked for me thanks!

---

### Post by markackerman8@gmail.com on 2010-03-25
ARGHHHH sooo confusing 2 days back to Ubuntu and everything is a mess

I don't know if this is the right thread, but I am pulling my hair out trying to have the NVidia 195 driver along with MythTV.

I have re-installed the 195 driver as stated above (after deleting nvidia-185-libvdpau: /usr/lib/libvdpau_nvidia.so.185.18.36).  Rebooted, and my fix package error was gone, but after I reinstalled MythTV (it was removed when I reinstalled the NVidia drivers), the error which brought me to search for a vdpau solution came back, i.e.) uddate continually complains of a missing package "nvidia-185-libvdpau" and tries to install it and I get the error

E: /var/cache/apt/archives/nvidia-185-libvdpau_185.18.36-0ubuntu9_amd64.deb: trying to overwrite '/usr/lib/libvdpau_nvidia.so', which is also in package nvidia-glx-195 0

and when I try to run mythbackend I get this related error

ack@Zeus:~$ mythbackend
mythbackend: error while loading shared libraries: libvdpau.so.1: cannot open shared object file: No such file or directory
ack@Zeus:~$ 

and using package manager, I see that libvdpau1 isn't installed and if I try to install it it removes all of MythTV

ARGHHHH sooo confusing 2 days back to Ubuntu and everything is a mess, HELP this old newbie!

---

### Post by ivanxuu on 2011-03-05
I solved it doing:
```

sudo apt-get purge libvdpau1 #will remove libvdpau1* mplayer*
wget http://ubuntu.wallawalla.edu/ubuntu//pool/restricted/n/nvidia-graphics-drivers-180/nvidia-185-libvdpau-dev_185.18.36-0ubuntu9_i386.deb
sudo dpkg -i nvidia-185-libvdpau-dev_185.18.36-0ubuntu9_i386.deb
sudo apt-get install mplayer

```

---

