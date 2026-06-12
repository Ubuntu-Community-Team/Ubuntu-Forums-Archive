---
title: "[SOLVED] &amp;quot; Hz ? &amp;quot; on ubuntu startup"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by arunvijay on 2008-01-24
when ubuntu starts and shut down, its showing a blank screen with a small box running around saying 



                                                      [COLOR="DarkRed"]  " Hz    ?"[/COLOR]

details about my moniter
[http://www.samsung.com/my/products/monitor/syncmastercdt/591s.asp](http://www.samsung.com/my/products/monitor/syncmastercdt/591s.asp)

my xorg.config file:

[http://www.shortText.com/j46rw0](http://www.shortText.com/j46rw0)

---

### Post by jpeddicord on 2008-01-25
I'm guessing that your monitor is unable to understand some of the refresh rates that are used during the startup and shutdown screens. A bouncing "Hz?" box sounds like a complaining monitor asking about the refresh rate. If it doesn't stop your work, it shouldn't become a problem.

I'm not sure if you can change the refresh rate on the console or not... anyone else know about this?

---

### Post by arunvijay on 2008-01-26
this is wat im getting

[http://picasaweb.google.com/arunnvijay/Junksz/photo#5159693075242626866](http://picasaweb.google.com/arunnvijay/Junksz/photo#5159693075242626866)

how to change refresh rates??

---

### Post by bufsabre666 on 2008-01-26
you can change the refresh rate under

system->admin-> screens and graphics

but this could also be solved by installing the startup manager ((its under system tools on the add/remove))

and fiddle with those settings till it works ((it might be that the res is too high or low try a normal setting like 1024,768 at 12 or 16bit))

---

### Post by aashay on 2008-01-26
What resolution do you run on the desktop? Does this resolution match the contents of /etc/usplash.conf ? I had a similar problem on my desktop. I forgot how exactly I fixed it. All I remember is increasing the usplash resolution. The problem is usplash is using a really low refresh rate and resolution. Your monitor probably does not support such a low resolution at such a low refresh rate. So having a higher resolution at the same low refresh rate works

---

### Post by arunvijay on 2008-01-26
no.. they dont match each other..
my current resolution is 800x600
and in usplash

# Usplash configuration file
xres=1280
yres=1024

how to increase the usplash resolution??
it is not possible to edit usplash.conf....??

---

### Post by arunvijay on 2008-01-26
any way ma problem is solved!!
i installed start up manager and changed the settings..
it showed the current resolution to be 1280x1024 i changed it to 800 x 600 and changed the colour depth to 24 bit..
now i can see the 'ubuntu' loading screen..
thanks guys!! :)

---

