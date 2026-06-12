---
title: "Flash player will not work."
date: 2008-11-09
forum: Multimedia Software
---

### Post by ttylerr on 2008-11-09
I have flash player installed, but Firefox refuses to recognize it.  I have tried installing it through the installer from adobe as well as flashplugin-nonfree through synaptic, but with no luck.  I can get gnash to work, but it takes forever to load or does not load at all in most cases.  Before I upgraded to 8.10, flash was working fine.  I think my graphics card is blacklisted because I cannot get desktop effects to work; however, gnash still works so I don't know if my graphics card is the problem.

---

### Post by jdunn on 2008-11-09
The plugin should be in your Firefox/plugins directory...either your local one or /usr/lib/firefox/plugins.  Next, type "about(colon)plugins" in your browser URL field to confirm it is recognized by Firefox.  Finally, if you are using Noscript or Adblock, make sure the sites you are visiting are allowed.

---

### Post by ttylerr on 2008-11-09
> **jdunn said:**
> The plugin should be in your Firefox/plugins directory...either your local one or /usr/lib/firefox/plugins.  Next, type "about(colon)plugins" in your browser URL field to confirm it is recognized by Firefox.  Finally, if you are using Noscript or Adblock, make sure the sites you are visiting are allowed.

the file is in the right directory, but firefox still does not recognize it.  it still will not show up in about(colon)plugins, and none of my addons are blocking it.

---

### Post by psyke83 on 2008-11-09
> **ttylerr said:**
> I have flash player installed, but Firefox refuses to recognize it.  I have tried installing it through the installer from adobe as well as flashplugin-nonfree through synaptic, but with no luck.  I can get gnash to work, but it takes forever to load or does not load at all in most cases.  Before I upgraded to 8.10, flash was working fine.  I think my graphics card is blacklisted because I cannot get desktop effects to work; however, gnash still works so I don't know if my graphics card is the problem.

Please follow these steps precisely:

1. Cleanup your system:
```
$ sudo apt-get remove --purge flashplugin-nonfree adobe-flashplugin
$ sudo updatedb
$ locate libflashplayer.so
```
Manually delete all "libflashplayer.so" files identified by the "locate" command (important). 

2. Reinstall Flash:
```
$ sudo apt-get install flashplugin-nonfree
```

3. Paste the output of the following command:
```
$ ldd /usr/lib/flashplugin-nonfree/libflashplayer.so
```

Finally, let me know if you're using the 32bit or 64bit version of Intrepid.

---

### Post by ttylerr on 2008-11-09
psyke83, thanks for your response.  i followed your instructions, and here are the results:
```
	linux-gate.so.1 =>  (0xb7f2f000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb73b9000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb73a0000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb72b0000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb72a1000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0xb7250000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb71da000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb71ad000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb6e0f000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb6d82000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb6d66000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb6d4c000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb6d41000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb6cfe000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb6c8b000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb6c4c000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb6c47000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb6c43000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb6b8c000)
	libnss3.so => not found
	libsmime3.so => not found
	libssl3.so => not found
	libplds4.so => /usr/lib/libplds4.so (0xb6b87000)
	libplc4.so => /usr/lib/libplc4.so (0xb6b82000)
	libnspr4.so => /usr/lib/libnspr4.so (0xb6b4c000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb6b25000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb6b16000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb69b8000)
	/lib/ld-linux.so.2 (0xb7f30000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb69b5000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb699c000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb6998000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb698f000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb6977000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb6961000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb693a000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb6935000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb6932000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb692d000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0xb68c5000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb689d000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb6892000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb688f000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb6885000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb687e000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb6875000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0xb6832000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb680c000)
	libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0xb6807000)
	libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0xb67ff000)
	libpcre.so.3 => /lib/libpcre.so.3 (0xb67d5000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb67cf000)
	libselinux.so.1 => /lib/libselinux.so.1 (0xb67b5000)

```

i am using 64-bit.  flash is still not working :(

---

### Post by psyke83 on 2008-11-09
Were you using Fabien Tassin's PPA, by any chance? Paste the output of:

```
$ dpkg -S libnss3.so libsmime3.so libssl3.so
```

...and:

```
 $ apt-cache policy libnss3-1d
```

---

### Post by ttylerr on 2008-11-09
I am not sure if I was using the PPA.  I've tried so many workarounds it may have gotten lost, but I don't remember using it.

First result:
```
thunderbird: /usr/lib/thunderbird/libnss3.so
libnss3-0d: /usr/lib/libnss3.so.0d
libnss3-1d: /usr/lib/libnss3.so.1d
thunderbird: /usr/lib/thunderbird/libsmime3.so
libnss3-0d: /usr/lib/libsmime3.so.0d
libnss3-1d: /usr/lib/libsmime3.so.1d
libnss3-0d: /usr/lib/libssl3.so.0d
libnss3-1d: /usr/lib/libssl3.so.1d
thunderbird: /usr/lib/thunderbird/libssl3.so
```

Second Result:
```
libnss3-1d:
  Installed: 3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy
  Candidate: 3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy
  Version table:
 *** 3.12.1~cvs20080501t1828-0ubuntu1~fta1~hardy 0
        100 /var/lib/dpkg/status
     3.12.0.3-0ubuntu5 0
        500 http://ubuntu-mirror.cs.colorado.edu intrepid/main Packages

```

---

### Post by psyke83 on 2008-11-09
Ok, you are (or rather, were) using Fabio Tassin's (aka ~fta's) Hardy PPA for updated Mozilla packages - there's a bug in his packages that causes trouble when users upgrade to Intrepid. 

1. Go to System/Administration/Software Sources, and click on the "Third-Party Software tab". Uncheck fta's repository; it'll be something like:

```
http://ppa.launchpad.net/fta/ubuntu hardy main
http://ppa.launchpad.net/fta/ubuntu hardy main (Source Code)
```

Click "Close", and reload the software repository lists when prompted.

2. [COLOR="Red"]N.B. Half your system may get uninstalled if you do not read this warning[/COLOR]: Before accepting the solution for apt-get, verify that it will *not* remove any packages. 

In other words, you will see: "0 upgraded, x newly installed, x reinstalled, **[COLOR="Red"]0[/COLOR] to remove** and 0 not upgraded." (the entries marked x are not so important)

Once you have read the disclaimer, run:
```
$ sudo apt-get install xulrunner-1.9/intrepid xulrunner-1.9-gnome-support/intrepid firefox/intrepid firefox-3.0/intrepid firefox-3.0-branding/intrepid firefox-3.0-gnome-support/intrepid firefox-gnome-support/intrepid libnspr4-0d/intrepid libnss3-1d/intrepid libnss3-0d/intrepid
```

If the output says "0 to remove", it's safe to allow the operation. You may want to paste your apt-get output here, nevertheless. 

If the output says to remove any number of packages, paste the full apt-get output here *and choose **n**o* to cancel the operation.

---

### Post by ttylerr on 2008-11-09
i do not have any of those repositories on the third-party software list.

---

### Post by psyke83 on 2008-11-09
> **ttylerr said:**
> i do not have any of those repositories on the third-party software list.

That's ok, simply ignore step 1. You must follow step 2, however (keeping the warnings in mind).

---

### Post by ttylerr on 2008-11-09
thank you so much! flash is working now. you have redeemed my faith in ubuntu. great people here :)

---

### Post by psyke83 on 2008-11-09
> **ttylerr said:**
> thank you so much! flash is working now. you have redeemed my faith in ubuntu. great people here :)

You're welcome ;). I just hope that your system isn't in an inconsistent state. Take a look at Synaptic's "Status/Installed (local or obsolete)" section. If you see any entries there that may be related to any Mozilla apps, you may have trouble with Firefox in the future.

---

### Post by coop0311emt on 2008-11-10
I am having the same problem with flash player not working but was unsuccessful in getting some of the steps in this thread to work also I pretty much need things broke down Barney style because I am really new thanks Coop

---

### Post by blinkingbee on 2008-11-10
After several hours of fruitless searching, I tried your solution and it worked for me. I did not have any unwanted repositories so I just used step 2. Thanks

---

