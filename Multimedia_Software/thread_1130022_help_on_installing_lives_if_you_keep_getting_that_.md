---
title: "help on installing lives if you keep getting that CFLAGS thing"
date: 2009-04-19
forum: Multimedia Software
---

### Post by Joshua Wells on 2009-04-19
i have something for anyone failing to be able to install LiVES to try.
do you keep getting 
No package 'gtk+-2.0' found
#
 
#
Consider adjusting the PKG_CONFIG_PATH environment variable if you
#
installed software in a non-standard prefix.
#
 
#
Alternatively, you may set the environment variables GTK_CFLAGS
#
and GTK_LIBS to avoid the need to call pkg-config.
#
See the pkg-config man page for more details.



if so, you may want to try this:
export GTK_CFLAGS=`pkg-config gtk+-2.0 --cflags` GTK_LIBS=`pkg-config gtk+-2.0 --libs`
just paste that, and try again. i got this from a good friend [actually i don't think i have evr engaged in conversation with him but oh well] on freenode, madmartian. i hope this helps. :D

---

