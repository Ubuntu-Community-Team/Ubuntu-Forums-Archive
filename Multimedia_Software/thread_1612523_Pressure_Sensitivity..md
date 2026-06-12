---
title: "Pressure Sensitivity."
date: 2010-11-03
forum: Multimedia Software
---

### Post by The_Orange on 2010-11-03
My tablet's pressure sensitivity is not working. I've looked through the help files on here including:
[http://manpages.ubuntu.com/manpages/jaunty/man4/wacom.4x.html](http://manpages.ubuntu.com/manpages/jaunty/man4/wacom.4x.html)
[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)
[http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1)

I've done just about everything on all those pages plus some other sites that aren't supported by Ubuntu.

I have a Bamboo Fun CTE-450, registered with Wacom. I downloaded a package from some where ( forgotten the site now ) for back when I had Lucid Linux 10.04. I've just upgraded to Maverick. Everything but the pressure sensitivity works. The pad:screen ratio is perfect, I can use all my pen buttons, and it paints/erases perfectly in GIMP. ...Except I need it to have pressure sensitivity.

Any help would be awesome. Thanks.

---

### Post by Favux on 2010-11-03
Hi The_Orange,

Well you should have pressure.

I gather you've configured the extended input devices in Gimp?
> I downloaded a package from some where ( forgotten the site now ) for back when I had Lucid Linux 10.04. 
What does this mean?

---

### Post by The_Orange on 2010-11-03
> **Favux said:**
> I gather you've configured the extended input devices in Gimp?

I don't exactly know what that is, but if it was on the other pages above, then I've probably done it.

When I ran 10.04 I was able to find some package on a website that I downloaded though the command line and it made the pressure work. I don't remember the website or the package, it's been a while. Once I upgraded to Maverick, the file got erased or changed or something 'cause now the pressure doesn't work anymore.

---

### Post by Favux on 2010-11-03
Well the Wacom wiki you linked shows you how to configure extended input devices near the bottom.

Let's look at your output of:
```
xinput --list
```
and
```
xsetwacom list
```
in a terminal.

Also we'll probably need to look at your Xorg.0.log.  It's in /var/log.

---

### Post by The_Orange on 2010-11-03
Wow, I feel stupid. Haha. I was so sure I had to download something that I didn't even think of doing the input thing. Works like a charm now. Thanks so much. <3

---

### Post by Favux on 2010-11-03
No worries.  :)

Everyone is entitled to a brain fart now and then.

---

