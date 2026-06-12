---
title: "Banshee Help"
date: 2009-01-17
forum: Multimedia Software
---

### Post by TheRockfight on 2009-01-17
Hi, 

I am new to Ubuntu, and have been trying to install Banshee, I first come across problems with gettext not being installed, which I overcome by re installing gettext.

I now have the following error

[I]checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for GST... configure: error: Package requirements (gstreamer-0.10 >= 0.10.3
		gstreamer-base-0.10 >= 0.10.3
		gstreamer-plugins-base-0.10 >= 0.10.3
		gstreamer-controller-0.10 >= 0.10.3
		gstreamer-dataprotocol-0.10 >= 0.10.3) were not met:

No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'gstreamer-controller-0.10' found
No package 'gstreamer-dataprotocol-0.10' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GST_CFLAGS
and GST_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/I]




I am running 8.10 The Interprid Ibex, and used a regular install from the Ubuntu web site.


Thanks in advance

---

### Post by sasquatch74 on 2009-01-17
Hello,

I am no expert, but I can give you a couple of tips.
First, how are you trying to install banshee?
Did you follow the instructions on [this]("https://edge.launchpad.net/~banshee-team/+archive/ppa") page?

Also, looks like you need glib.
Search in synaptic for libglib.  
You may need to install the development files,
The one listed as libglib2.0-dev

Oh, and to get gstreamer, I believe you need to enable the multiverse repositories, which you can find in synaptic>settings>repositories. 

Good luck!

---

### Post by TheRockfight on 2009-01-19
I managed to fix this problem, thanks for the reply.It's surprising how learning the solution to this problem led me know how to approach a few other problems I had .


:P

---

