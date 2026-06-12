---
title: "Boot resolution"
date: 2007-04-06
forum: Multimedia &amp; Video
---

### Post by graeme_p on 2007-04-06
During boot up and shutdown my monitor complains of an unsupported mode, and the refresh rates it reports are rather high.

Once GDM starts, things go back to normal.

Settings in xorg.conf appear to be OK.

How can I change the boot video mode? Without affecting other settings which are fine.

---

### Post by heimo on 2007-04-06
I'd try to change resolution in menu.lst to something lower than currently, if you have a CRT (not LCD/TFT) monitor. CRTs support higher refresh rates with lower resolutions. Here's how to change the value:
[http://ubuntuforums.org/showthread.php?t=396347](http://ubuntuforums.org/showthread.php?t=396347)

And the second table on this page looks like it has the options for different resolution/colordepth combinations:
[http://tuxmobil.org/compaq_presario1600xl155_e.html](http://tuxmobil.org/compaq_presario1600xl155_e.html)

---

### Post by graeme_p on 2007-04-06
It is an LCD, so I do need to change the refresh rate.

I am both confused by this, and a little nervous as I have not messed around with boot options before.

---

### Post by heimo on 2007-04-06
Type:
```
cat /etc/usplash.conf 
```

Does it match with your LCD's native resolution?

---

### Post by graeme_p on 2007-04-07
Checked usplash.conf. Yes, the resolution is the LCD's native resolution.

This has changed when I upgraded to Edgy recently. Before that (with Dapper) I could see the boot messages, but the resolution was definitely not the LCD's native resolution (visibly blurry).

---

### Post by heimo on 2007-04-07
I searched forums and Google, but couldn't find a definitive answer. I think the key lies in grub's menu.lst or usplash's configuration. One thing you could do, is to disable or uninstall usplash (the nice graphics during boot). Not optimal solution, but at least it'd be usable in case it gets stuck during boot, and throws some error.

After boot, run
```
dmesg | less
```and watch for any warnings/errors that might be related. It shows you boot messages.

---

### Post by graeme_p on 2007-04-07
I have disabled usplash. Being able to troubleshoot is something goes wrong is more important than it looking pretty.

Thanks for your help. I appreciate the time you put into trying to find an answer.

---

### Post by graeme_p on 2007-04-15
menu.lst got overwritten by a recent  update. Time to file abug report I think.

---

### Post by graeme_p on 2007-05-22
OK, it appears to be a known bug, but I have found a sort-of workaround

If you swtich to a virtual terminal during boot (i.e. ctl-alt-F3, other function kes will work), then you see the text login messages.

Worth doing at least when you think something is wrong.

---

