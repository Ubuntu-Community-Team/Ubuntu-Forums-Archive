---
title: "Ardour 2.3 Will Not Install Correctly/Run...help!"
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by dbsoundman on 2008-03-20
I had Ardour running fine on my desktop computer for a while, then I idiotically decided to uninstall it because I was desperately trying to troubleshoot another problem with the sample rate being wrong. Now, I have been trying to reinstall it. I went to Synaptic but it only has the old Ardour version, and I want the new one. So I went to install it from source; I had done it before on my laptop, and it wasn't too bad once I got all the necessary packages.

I got the program all installed, but now, it won't launch. It says that it can’t find libjack.so.0; it says it doesn’t exist. It clearly does exist though, in several locations, as I revealed from a search of my filesystem. The locations IIRC included /usr/bin and other logical places. This seems to be what is stopping my launch...

At the advice of someone else, I ran a script to see the library dependencies for Ardour and their "statuses", and this is the output:
```
dan@blackdiamond:~$ LD_LIBRARY_PATH=/usr/local/lib/ardour2:$LD_LIBRARY_PATH ldd /usr/local/lib/ardour2/ardour-2.3
linux-gate.so.1 => (0xffffe000)
libardour.so => /usr/local/lib/ardour2/libardour.so (0xb7c80000)
libardour_cp.so => /usr/local/lib/ardour2/libardour_cp.so (0xb7c74000)
libatkmm.so => /usr/local/lib/ardour2/libatkmm.so (0xb7c31000)
libfftw3.so.3 => /usr/lib/libfftw3.so.3 (0xb7b3c000)
libfftw3f.so.3 => /usr/lib/libfftw3f.so.3 (0xb7a5e000)
libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7a37000)
libgdkmm2.so => /usr/local/lib/ardour2/libgdkmm2.so (0xb79f1000)
libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb79b7000)
libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb79b4000)
libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb79b0000)
libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb79ab000)
librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb79a2000)
libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb790c000)
libglibmm2.so => /usr/local/lib/ardour2/libglibmm2.so (0xb78c0000)
libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb7568000)
libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb74e2000)
libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb74c7000)
libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb74af000)
libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb74a7000)
libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb747c000)
libXext.so.6 => /usr/lib/libXext.so.6 (0xb746e000)
libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7466000)
libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb7463000)
libXi.so.6 => /usr/lib/libXi.so.6 (0xb745a000)
libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb7454000)
libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb744b000)
libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb7446000)
libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb7408000)
libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb7398000)
libX11.so.6 => /usr/lib/libX11.so.6 (0xb72a7000)
libgtkmm2.so => /usr/local/lib/ardour2/libgtkmm2.so (0xb6ff2000)
libgtkmm2ext.so => /usr/local/lib/ardour2/libgtkmm2ext.so (0xb6f7e000)
libjack.so.0 => not found
libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb6f67000)
libgnomecanvas-2.so.0 => /usr/lib/libgnomecanvas-2.so.0 (0xb6f3d000)
libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0xb6f27000)
libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb6efc000)
libgnomecanvasmm.so => /usr/local/lib/ardour2/libgnomecanvasmm.so (0xb6eb9000)
liblrdf.so.2 => not found
libmidi++.so => /usr/local/lib/ardour2/libmidi++.so (0xb6e92000)
libpangomm.so => /usr/local/lib/ardour2/libpangomm.so (0xb6e6a000)
libpbd.so => /usr/local/lib/ardour2/libpbd.so (0xb6e36000)
libsamplerate.so.0 => /usr/lib/libsamplerate.so.0 (0xb6e1a000)
libsigc++2.so => /usr/local/lib/ardour2/libsigc++2.so (0xb6e14000)
libsndfile-ardour.so => /usr/local/lib/ardour2/libsndfile-ardour.so (0xb6d79000)
libasound.so.2 => /usr/lib/libasound.so.2 (0xb6cb3000)
libvampsdk.so => /usr/local/lib/ardour2/libvampsdk.so (0xb6ca2000)
libvamphostsdk.so => /usr/local/lib/ardour2/libvamphostsdk.so (0xb6c81000)
libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb6b64000)
libxslt.so.1 => /usr/lib/libxslt.so.1 (0xb6b30000)
librubberband.so => /usr/local/lib/ardour2/librubberband.so (0xb6b07000)
libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb6a1c000)
libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb6a10000)
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb68cf000)
libjack.so.0 => not found
liblrdf.so.2 => not found
libraptor.so.1 => /usr/lib/libraptor.so.1 (0xb6889000)
libcurl.so.3 => /usr/lib/libcurl.so.3 (0xb6854000)
libgssapi_krb5.so.2 => /usr/lib/libgssapi_krb5.so.2 (0xb6838000)
libkrb5.so.3 => /usr/lib/libkrb5.so.3 (0xb67bb000)
libk5crypto.so.3 => /usr/lib/libk5crypto.so.3 (0xb6796000)
libcom_err.so.2 => /lib/libcom_err.so.2 (0xb6793000)
libkrb5support.so.0 => /usr/lib/libkrb5support.so.0 (0xb678e000)
libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb677b000)
libidn.so.11 => /usr/lib/libidn.so.11 (0xb674b000)
libssl.so.0.9.8 => /usr/lib/i686/cmov/libssl.so.0.9.8 (0xb670b000)
libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb65c9000)
libz.so.1 => /usr/lib/libz.so.1 (0xb65b5000)
liblo.so.0 => /usr/lib/liblo.so.0 (0xb65aa000)
libusb-0.1.so.4 => /lib/libusb-0.1.so.4 (0xb65a2000)
/lib/ld-linux.so.2 (0xb7f41000)
libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb6537000)
libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb6516000)
libXau.so.6 => /usr/lib/libXau.so.6 (0xb6513000)
libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb64f0000)
libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb64eb000)
```

So, libjack.so.0, libjack.so.2, and liblrdf.so.0 are not found. However I know that at least the libjack files are there, I haven’t checked on liblrdf yet. Any ideas as to what I can do? Also would it help if I could get ardour to install in /usr/bin instead of /usr/local/bin? The old Ardour install is completely gone as far as I know so there’s no reason it can’t go in the /usr/bin directory, or am I wrong? Help!

Thanks,
Dan

---

### Post by xc3RnbFO8P on 2008-03-21
In Synaptic Package Manager see if got **libjack** and **liblrdf** installed.
Here is a Ardour.deb 2.3.1: [http://www.getdeb.net/category.php?id=1]("http://www.getdeb.net/category.php?id=1")

---

### Post by dbsoundman on 2008-03-21
All the libjack files on synaptic were installed, but I didn't have liblrdf-dev installed, so I did do that.

-Dan

---

### Post by xc3RnbFO8P on 2008-03-21
When I look at the list, I would try to copy **libjack.so.0** and **liblrdf.so.2 **to: **/usr/local/lib/ardour2/** and **/lib/tls/i686/cmov/**

---

### Post by dbsoundman on 2008-03-22
OK, copying the files seems to have made the install work...but now Ardour cannot connect to JACK. Here is what I get when I start ardour2:
```
dan@blackdiamond:~$ ardour2
Ardour/GTK 2.3
   (built using 3029 and GCC version 4.1.2 (Ubuntu 4.1.2-0ubuntu4))
Copyright (C) 1999-2007 Paul Davis
Some portions Copyright (C) Steve Harris, Ari Johnson, Brett Viren, Joel Baker

Ardour comes with ABSOLUTELY NO WARRANTY
not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
This is free software, and you are welcome to redistribute it 
under certain conditions; see the source for copying conditions.
loading default ui configuration file /usr/local/etc/ardour2/ardour2_ui_default.conf
loading user ui configuration file /home/dan/.ardour2/ardour2_ui.conf
Loading ui configuration file /usr/local/etc/ardour2/ardour2_ui_dark.rc
theme_init() called from internal clearlooks engine
loading system configuration file /usr/local/etc/ardour2/ardour_system.rc
loading user configuration file /home/dan/.ardour2/ardour.rc
ardour: [INFO]: Using SSE optimized routines
ardour: [INFO]: looking for control protocols in /home/dan/.ardour2/surfaces/:/usr/local/lib/ardour2/surfaces/
ardour: [INFO]: Control surface protocol discovered: "Mackie"
ardour: [INFO]: Control protocol Tranzport not usable
powermate: Opening of powermate failed - No such file or directory
ardour: [INFO]: Control protocol powermate not usable
ardour: [INFO]: Control surface protocol discovered: "Generic MIDI"
client linked with incompatible libjack version.
could not attach to JACK server
JACK COMMAND: /usr/local/bin/jackd -p 128 -T -d alsa -n 2 -r 48000 -p 1024 -d hw:0,0 
client linked with incompatible libjack version.
could not attach to JACK server


```
I did reinstall jackd and qjackctl at one point. Actually, I tried installing the newer version of qjackctl, 0.3.2, but it wouldn't work, so I scrapped it and just kept 0.2.2. It seems that the JACK COMMAND is incorrect; -p should be 256, -n should be 5 I think, -r should be 96000, etc. How do I fix this? I tried using the Audio Setup dialog in the startup thing for Ardour (the window where it asks what you want to open), but it doesn't seem to save the settings I correct.

-Dan

---

### Post by xc3RnbFO8P on 2008-03-23
I don't know, maybe downgrade to [0.102.20.]("http://jackaudio.org/")
Look at this [application using Jack]("http://jackaudio.org/applications")

---

