---
title: "gstreamer error guint and asm error"
date: 2010-04-28
forum: Multimedia Software
---

### Post by LittleU on 2010-04-28
the below code is directly from the application programmers reference manual of gstreamer.

```


#include <stdio.h>
#include <gst/gst.h>

int
main (int   argc,
      char *argv[])
{
  const gchar *nano_str;
  guint major, minor, micro, nano;
  gst_init (&argc, &argv);
  gst_version (&major, &minor, &micro, &nano);
  if (nano == 1)
    nano_str = "(CVS)";
  else if (nano == 2)
    nano_str = "(Prerelease)";
  else
    nano_str = "";
  printf ("This program is linked against GStreamer %d.%d.%d %s\n",
          major, minor, micro, nano_str);
  return 0;
}
```i tried with the follwing command

gcc first.c 'pkg-config --cflags --libs gstreamer-0.10'  
and 
gcc 'pkg-config --cflags --libs gstreamer-0.10' first.c 

but its throughing following errors.

first.c: In function ‘main’:
first.c:8: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
first.c:8: error: ‘nano_str’ undeclared (first use in this function)
first.c:8: error: (Each undeclared identifier is reported only once
first.c:8: error: for each function it appears in.)
first.c:9: error: ‘guint’ undeclared (first use in this function)
first.c:9: error: expected ‘;’ before ‘major’
first.c:11: error: ‘major’ undeclared (first use in this function)
first.c:11: error: ‘minor’ undeclared (first use in this function)
first.c:11: error: ‘micro’ undeclared (first use in this function)
first.c:11: error: ‘nano’ undeclared (first use in this function)

please help me to solve the problem.

---

### Post by no2498 on 2010-04-28
look in the add/remove in applications
type in gstreamer 

see if you have the good, bad, ugly installed

hope this helps

---

### Post by LittleU on 2010-04-29
i solved it myself by linking glib 2.0

---

