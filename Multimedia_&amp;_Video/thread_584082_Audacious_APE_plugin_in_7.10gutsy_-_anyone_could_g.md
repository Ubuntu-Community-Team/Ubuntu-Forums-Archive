---
title: "Audacious APE plugin in 7.10/gutsy - anyone could get it to work?"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by ariel on 2007-10-20
Just wondering if anyone succeeded in getting ape / Monkey's audio lossless codec support to work in audacious, under gutsy / 7.10 final / fresh install.

As usual, I downloaded the plugin source code (audacious-mac-0.2.1, google for it) the attempted to compile it (after installing the build-dep)

This is what I got after the ./configure (last few lines, with the error message):


checking for AUDACIOUS... configure: error: Package requirements (audacious >= 1.3) were not met:

No package 'audacious' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AUDACIOUS_CFLAGS
and AUDACIOUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

____________________

pkg-config is installed in my system, but it looks like there is a problem with it:

~/Desktop/Builds/audacious-mac-0.2.1$ pkg-config --libs audacious
Package audacious was not found in the pkg-config search path.
Perhaps you should add the directory containing `audacious.pc'
to the PKG_CONFIG_PATH environment variable
No package 'audacious' found


Any hint, anyone?

thanks!

---

### Post by ariel on 2007-10-20
Self answer: i found the audacious ape plugin .debs for feisty, and luckily they install fine under gutsy and the default audacious version. With this, audacious can load the .cue and show track titles and all; the only caveat is that the track length is incorrect... but at least you can listen to your music :)

I attach the debs you will need (after installing the default audacious version), for your convenience.

---

### Post by ilovedvd on 2007-10-20
I will try it. thanks.

---

### Post by disturbedite on 2007-10-21
i could be wrong, but i think the ape plugin is in the "ugly" plugins package for audacious.

the reason i say that is cuz i compile mercurial (like svn) of audacious (currently using audacious 1.4 beta 2) and the plugin package does not include the ape plugin.  the listing of the packages says that the "ugly" plugins package hasn't been ready for 1.4 testing.  so that would lead me to believe the ape plugin is in the "ugly" package.
if you don't know, the ugly plugins are the ones that don't work completely/correctly all the time yet.

---

### Post by premodern on 2008-02-25
Is there a way to get APE's working in a AMD64 machine ?

I guess the audacious can play APE's only in 32 bit systems

---

### Post by ron999 on 2008-02-25
> **premodern said:**
> Is there a way to get APE's working in a AMD64 machine ?


Mine's only a 32bit system.
But I can play APE files using mplayer from the command line or with the SMPlayer GUI.
Perhaps this will work with an AMD64 machine too.
:)

---

### Post by Jose Catre-Vandis on 2008-03-31
Thanks, this worked a treat on my 32 bit gutsy. was then able to use the lame out plugin to convert to mp3

---

