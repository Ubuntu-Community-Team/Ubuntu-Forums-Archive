---
title: "weird Xauthority"
date: 2008-06-28
forum: Multimedia Software
---

### Post by Dbugger on 2008-06-28
I've been looking for ages why my ATI drivers in hardy give me a black freeze screen, and after a lot of investigating, I found what may be the cause of it. Look at this:

> dbugger@kristie:/etc/gdm$ cat /home/dbugger/.Xauthority 
kristie1MIT-MAGIC-COOKIE-1{
                                8&#65533;&#65533;&#65533;&#65533;&#65533;
                                      &#65533;}&#65533;&#65533;'&#65533;kristie0MIT-MAGIC-COOKIE-1u&#65533;&#65533;&#65533;&#65533;A&#65533;&#65533;&#65533;&#65533;&#65533;localhost.localdomain0MIT-MAGIC-COOKIE-1u&#65533;&#65533;&#65533;&#65533;A&#65533;&#65533;

it's japanese!!! How the ### did it got there?? :confused::confused:

Anyway, the important part, and my question is: Can anyone help me fix this file?

Thank you.

---

