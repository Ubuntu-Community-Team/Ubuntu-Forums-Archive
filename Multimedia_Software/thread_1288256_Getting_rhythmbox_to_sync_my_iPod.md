---
title: "Getting rhythmbox to sync my iPod"
date: 2009-10-11
forum: Multimedia Software
---

### Post by Green_Mac on 2009-10-11
I've got Rhythmbox 0.11.5, which is the latest version Synaptic will give me.  The help file appears to be telling me that it won't write to an iPod (it can read from my shuffle quite happily) so I'd like to upgrade to the latest version, 0.12.5, which looks as if it can write to the iPod.  I've downloaded the source code, but when I try to ./configure it, I get the message:

checking for RHYTHMBOX... configure: error: Package requirements (		  gtk+-2.0 >= 2.12.0					  glib-2.0 >= 2.16.0	  gio-2.0 >= 2.16.0					  gio-unix-2.0 >= 2.16.0  gnome-media-profiles >= 2.8 		  libsoup-2.4 >= 2.26.0			  libsoup-gnome-2.4 >= 2.26.0			  libgnomeui-2.0) were not met:

No package 'gnome-media-profiles' found
No package 'libsoup-2.4' found
No package 'libsoup-gnome-2.4' found
No package 'libgnomeui-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables RHYTHMBOX_CFLAGS
and RHYTHMBOX_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Now I'm completely lost!

---

### Post by lian1238 on 2009-10-11
When compiling from source, you're likely to run into dependency problems. You need to find and install the missing packages mentioned in the error.

Step 1: try finding them in Synaptic.
Go for the ones postfixed with "-dev".

If you can't find a package there, you may need to google it and probably need to compile THAT from source, and so on.

Hope that helps.

---

