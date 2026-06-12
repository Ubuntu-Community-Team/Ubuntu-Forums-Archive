---
title: "Configuring widescreen (nvidia geforce 7400)"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by Seine on 2006-09-04
I have a widescreen format laptop with an nvidia geforce 7400. In the screen resolution applet my resolution choices are all standard format dimensions.

After recently enabling nvidia drivers (thanks guys for your help!) I now have a fuzzy, stretched display. By 'fuzzy' I mean strongly anti-aliased.

Is there any way to enable a wide-screen display?

Thanks
Jem

---

### Post by tseliot on 2006-09-04
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by djRobbieF on 2006-09-04
Make a backup copy of /etc/X11/xorg.conf - just in case... THEN:

Ubuntu:  sudo gedit /etc/X11/xorg.conf
Kubuntu:  sudo kate /etc/X11/xorg.conf

Then, add the desired resolution to the front of each line that lists all the resolutions - you'll see several lines that look like (example) "1024x768" "800x600" "640x480"...  so just add your desired resolution "1280x800" for example.

Then, restart your X session (either reboot, or press CTRL-ALT-BACKSPACE and then type X).

That should add the widescreen resolution to the options for you... at least, that's the way I would do it.

Obviously, make sure it's a resolution supported by your laptop / monitor.

---

### Post by Seine on 2006-09-06
I didn't reply with a Thank You? How damn rude of me.

Thanks guys!

---

