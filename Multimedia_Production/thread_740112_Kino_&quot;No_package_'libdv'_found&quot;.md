---
title: "Kino &quot;No package 'libdv' found?&quot;"
date: 2008-03-30
forum: Multimedia Production
---

### Post by Tsu Dho Nimh on 2008-03-30
Trying to install 1.3.0 on a 64-bit AMD with Ubuntu 7.04 and Kino is not finding what it needs.

Here's the error message: 

[I]configure:21602: $PKG_CONFIG --exists --print-errors "libdv >= 0.103"
Package libdv was not found in the pkg-config search path.
Perhaps you should add the directory containing `libdv.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libdv' found[/I]


I have libdv4. Is that acceptable? Which of these would be the right one?
/usr/lib/libdv.so.4.0.3
/usr/lib/libdv.so.4


How do I "add the directory containing `libdv.pc' to the PKG_CONFIG_PATH environment variable"? Where is this variable?

And if it can't find libdev, why does it want the path to libdv.pc
Where is libdv.pc ?

*********
[I]Alternatively, you may set the environment variables LIBDV_CFLAGS
and LIBDV_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/I]

The manpage is not helpful. If I understood what it was talking about, I'd be a l33t Linux d00d and not be asking these questions.

What should these variables be set to? Where can they be found?

---

### Post by Creative2 on 2008-03-31
well there is a package on getdeb .... :)
[http://www.getdeb.net/app/Kino](http://www.getdeb.net/app/Kino)

---

### Post by Irihapeti on 2008-03-31
If you are compiling from source, you need libdv4-dev, and the -dev version of any other libraries that it asks for.

---

### Post by Tsu Dho Nimh on 2008-03-31
> **Creative2 said:**
> well there is a package on getdeb .... :)
[http://www.getdeb.net/app/Kino](http://www.getdeb.net/app/Kino)

Yes, I tried that: it refuses to install because I have the wrong CPU. I have 64-bit AMD, 64-bit Ubuntu (so I can run Cinelerra). 



> If you are compiling from source, you need libdv4-dev, and the -dev version of any other libraries that it asks for.

Thank you.  I'll try it and report back.  This is my first try compiling from source - I'm that desperate to get a feature that Kino 0.9 lacks.

---

### Post by Creative2 on 2008-03-31
well but there is 64bit version for package... have you tried that ?

---

### Post by Tsu Dho Nimh on 2008-03-31
> **Creative2 said:**
> well but there is 64bit version for package... have you tried that ?

64-bit version of Kino?  What version of Kino? And where might it be?  
I need some features that are not in the official Ubuntu distro.

**(adding - the URL you gave was not the one where I got the distro that would not install. It installed!!!) **



By repeatedly running ./configure and installing anything it reported was missing  I managed to get ./configure to complete

Now it's erroring out on make ... giving errors like "Error 1", which is totally meaningless to me.

---

### Post by Creative2 on 2008-04-01
on that page...i found 
Latest versions:
 Ubuntu Gutsy 32 bits -  1.3.0 
 Ubuntu Gutsy 64 bits -  1.3.0 
 Ubuntu Feisty 32 bits -  1.1.1 
 Ubuntu Feisty 64 bits -  1.1.1

---

