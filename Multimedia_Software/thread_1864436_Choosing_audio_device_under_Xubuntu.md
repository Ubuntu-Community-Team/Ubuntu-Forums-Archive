---
title: "Choosing audio device under Xubuntu"
date: 2011-10-18
forum: Multimedia Software
---

### Post by Compgeke on 2011-10-18
I've got a clean install of Ubuntu 11.04, with the exception of an installation of Open Office. My problem is I can't change the default audio device. I'm trying to use a USB Plantronics headset rather than the internal audio but I can't find where to change this and I can't find padevchooser and after some more research I found that this package isn't used anymore, is that right?

My system is a Dell Latitude D820 running Xubuntu 11.04 AMD64. The internal audio is basic Intel HD audio and the headset is a Plantronics Audio 510.

The reason for running Xubuntu over Ubuntu is because I prefer XFCE over Unity and Gnome.

Thanks!

---

### Post by Rodney9 on 2011-10-19
I am using Xubuntu 11.10 and I just used 
```
sudo apt-get install pavucontrol
``` 
and it installed ok and it comes up under Multimedia and works perfectly.

---

### Post by Compgeke on 2011-10-19
Thank you, that is exactly what I needed. I was using padevchooser back in Xubuntu 8.04 or something so I was stuck on that (and was getting errors when trying to compile it after installing g++).

---

### Post by thelamer on 2011-10-25
Does not work for me when I try to launch pavucontrol I get 

```
pavucontrol: error while loading shared libraries: libatkmm-1.6.so.1: cannot open shared object file: No such file or directory

```

And yes the libs are installed: 

```
sudo apt-get install libatkmm-1.6-1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libatkmm-1.6-1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Anyone else getting this? 

Fresh install of 11.10 xubuntu

---

### Post by thelamer on 2011-10-26
filed bug report: 

[https://bugs.launchpad.net/ubuntu/+source/pavucontrol/+bug/881797](https://bugs.launchpad.net/ubuntu/+source/pavucontrol/+bug/881797)

---

### Post by Toz on 2011-10-26
Looks like a 64-bit issue. Fresh 32-bit install here and pavucontrol installed and works (don't have 64-bit install available to test).

Out of curiosity, what do the following return:
```
ldd `which pavucontrol`
```
```
ls -l /usr/lib/libatkmm*
```

---

### Post by thelamer on 2011-10-30
```
	linux-vdso.so.1 =>  (0x00007fffbb544000)
	libgtkmm-3.0.so.1 => /usr/lib/libgtkmm-3.0.so.1 (0x00007f5df7cac000)
	libatkmm-1.6.so.1 => not found
	libgdkmm-3.0.so.1 => /usr/lib/libgdkmm-3.0.so.1 (0x00007f5df7a6d000)
	libglibmm-2.4.so.1 => not found
	libsigc-2.0.so.0 => not found
	libcanberra-gtk3.so.0 => /usr/lib/libcanberra-gtk3.so.0 (0x00007f5df7867000)
	libcanberra.so.0 => /usr/lib/libcanberra.so.0 (0x00007f5df7657000)
	libgtk-3.so.0 => /usr/lib/libgtk-3.so.0 (0x00007f5df7008000)
	libgobject-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007f5df6db6000)
	libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007f5df6ac0000)
	libpulse-mainloop-glib.so.0 => /usr/lib/x86_64-linux-gnu/libpulse-mainloop-glib.so.0 (0x00007f5df68bb000)
	libpulse.so.0 => /usr/lib/x86_64-linux-gnu/libpulse.so.0 (0x00007f5df6673000)
	libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f5df636c000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f5df6156000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f5df5f38000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f5df5b99000)
	libatkmm-1.6.so.1 => not found
	libgiomm-2.4.so.1 => not found
	libpangomm-1.4.so.1 => not found
	libglibmm-2.4.so.1 => not found
	libcairomm-1.0.so.1 => not found
	libsigc-2.0.so.0 => not found
	libgdk-3.so.0 => /usr/lib/libgdk-3.so.0 (0x00007f5df591b000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f5df5696000)
	libgiomm-2.4.so.1 => not found
	libglibmm-2.4.so.1 => not found
	libcairomm-1.0.so.1 => not found
	libsigc-2.0.so.0 => not found
	libgdk_pixbuf-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0 (0x00007f5df5475000)
	libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007f5df513d000)
	libvorbisfile.so.3 => /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3 (0x00007f5df4f34000)
	libtdb.so.1 => /usr/lib/x86_64-linux-gnu/libtdb.so.1 (0x00007f5df4d23000)
	libltdl.so.7 => /usr/lib/libltdl.so.7 (0x00007f5df4b19000)
	libpangocairo-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0 (0x00007f5df490c000)
	libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007f5df4705000)
	libatk-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libatk-1.0.so.0 (0x00007f5df44e3000)
	libcairo-gobject.so.2 => /usr/lib/x86_64-linux-gnu/libcairo-gobject.so.2 (0x00007f5df42da000)
	libcairo.so.2 => /usr/lib/x86_64-linux-gnu/libcairo.so.2 (0x00007f5df401b000)
	libgio-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 (0x00007f5df3cd9000)
	libpangoft2-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0 (0x00007f5df3aae000)
	libpango-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0 (0x00007f5df3863000)
	libfontconfig.so.1 => /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 (0x00007f5df362d000)
	libgmodule-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007f5df3429000)
	libgthread-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0 (0x00007f5df3223000)
	libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007f5df301b000)
	libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f5df2dde000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f5df2bd6000)
	libpulsecommon-1.0.so => /usr/lib/x86_64-linux-gnu/libpulsecommon-1.0.so (0x00007f5df2978000)
	libjson.so.0 => /usr/lib/x86_64-linux-gnu/libjson.so.0 (0x00007f5df276f000)
	libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007f5df252c000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f5df8360000)
	libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007f5df2319000)
	libXinerama.so.1 => /usr/lib/x86_64-linux-gnu/libXinerama.so.1 (0x00007f5df2115000)
	libXi.so.6 => /usr/lib/x86_64-linux-gnu/libXi.so.6 (0x00007f5df1f05000)
	libXrandr.so.2 => /usr/lib/x86_64-linux-gnu/libXrandr.so.2 (0x00007f5df1cfc000)
	libXcursor.so.1 => /usr/lib/x86_64-linux-gnu/libXcursor.so.1 (0x00007f5df1af1000)
	libXcomposite.so.1 => /usr/lib/x86_64-linux-gnu/libXcomposite.so.1 (0x00007f5df18ee000)
	libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007f5df16eb000)
	libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f5df14ce000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f5df12ca000)
	libvorbis.so.0 => /usr/lib/x86_64-linux-gnu/libvorbis.so.0 (0x00007f5df109d000)
	libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007f5df0e96000)
	libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007f5df0bfe000)
	libpixman-1.so.0 => /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x00007f5df0989000)
	libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007f5df0762000)
	libxcb-shm.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0 (0x00007f5df055e000)
	libxcb-render.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-render.so.0 (0x00007f5df0355000)
	libXrender.so.1 => /usr/lib/x86_64-linux-gnu/libXrender.so.1 (0x00007f5df014a000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f5deff31000)
	libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007f5defd13000)
	libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007f5defaf8000)
	libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007f5def8cd000)
	libwrap.so.0 => /lib/x86_64-linux-gnu/libwrap.so.0 (0x00007f5def6c4000)
	libsndfile.so.1 => /usr/lib/x86_64-linux-gnu/libsndfile.so.1 (0x00007f5def45c000)
	libasyncns.so.0 => /usr/lib/x86_64-linux-gnu/libasyncns.so.0 (0x00007f5def256000)
	libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007f5def052000)
	libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007f5deee4c000)
	libnsl.so.1 => /lib/x86_64-linux-gnu/libnsl.so.1 (0x00007f5deec31000)
	libFLAC.so.8 => /usr/lib/x86_64-linux-gnu/libFLAC.so.8 (0x00007f5dee9e7000)
	libvorbisenc.so.2 => /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2 (0x00007f5dee518000)

```

The libs are not there

---

### Post by Toz on 2011-10-30
Try reinstalling:
```
sudo apt-get --reinstall install libatkmm-1.6-1
```

---

### Post by Psyael on 2011-10-30
I'm not the OP, but pavucontrol did help me get sound over HDMI, thanks. Only complaint is, now the volume up/down panel widget (with the keyboard controls) doesn't work. Apparently it's tied to the system's Mixer app in some way.

---

### Post by Toz on 2011-10-30
> **Psyael said:**
> I'm not the OP, but pavucontrol did help me get sound over HDMI, thanks. Only complaint is, now the volume up/down panel widget (with the keyboard controls) doesn't work. Apparently it's tied to the system's Mixer app in some way.

In a terminal window, run the following:
```
wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh; chmod +x ./alsa-info.sh; ./alsa-info.sh
```
...and when it asks you if you want to automatically upload your information to [www.alsa-project.org](www.alsa-project.org), say Y. It will do so then provide you with a link to access the report. Post that link back here.

Here is a reference link: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure"). It sounds like you are trying/wanting to change the default sound device in your system. Step 17 should help.

---

### Post by Psyael on 2011-10-30
> **Toz said:**
> In a terminal window, run the following:
```
wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh; chmod +x ./alsa-info.sh; ./alsa-info.sh
```
...and when it asks you if you want to automatically upload your information to [www.alsa-project.org](www.alsa-project.org), say Y. It will do so then provide you with a link to access the report. Post that link back here.[http://www.alsa-project.org/db/?f=f4441c7159e711b99276e71b33e5fb478cb91159](http://www.alsa-project.org/db/?f=f4441c7159e711b99276e71b33e5fb478cb91159)

> Here is a reference link: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure"). It sounds like you are trying/wanting to change the default sound device in your system. Step 17 should help.
Thanks. I'm turning in for the night but will look at it tomorrow.

---

### Post by Psyael on 2011-10-30
Update: I uninstalled PulseAudio volume and set things back the way they were, and tried the step 17 instructions to make my HDMI the default sound device.

It worked, but I still can't control the output volume with system volume, which I can in Ubuntu and what I wanted. For now, I have to turn my speakers up and down.

---

### Post by aaricus on 2012-01-12
> **Rodney9 said:**
> I am using Xubuntu 11.10 and I just used 
```
sudo apt-get install pavucontrol
``` 
and it installed ok and it comes up under Multimedia and works perfectly.

THANK YOU SO MUCH!

This application is exactly what I was looking for.

I have a HP DV6 Laptop and wanted to use some USB speakers, but when I plugged them in I found that Xubuntu 11.10 does not have an option to change the audio output device which will hopefully be corrected in the next release because that's kind of important to have.

But this application did exactly what I wanted, worked first go and it's great, it should really be included instead of what Xubuntu actually comes with now.

Actually I'm bookmarking this thread incase I need to reinstall :)

---

