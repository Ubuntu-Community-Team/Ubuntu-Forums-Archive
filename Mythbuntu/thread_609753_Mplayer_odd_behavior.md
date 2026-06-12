---
title: "Mplayer odd behavior"
date: 2007-11-11
forum: Mythbuntu
---

### Post by govee on 2007-11-11
when I select a play dvd from Myth it plays, but It ignores the dvd menu and starts the movie without selelection and if I select menu I see it for a second it it goes right back to the movie. Also when not in Myth Mplayer fails to open DVD.

---

### Post by warp99 on 2007-11-11
Mplayer has no support for DVD menus. You should replace the command string for mplayer with xine. In Mythtv go to Utilities/Setup > Setup > Media Settings >  DVD Settings > Play Settings and change the DVD command to the following:

**xine -B -f -I --no-logo --no-splash dvd:// %d**

and your DVD menus will be available for selection. You may need to use your mouse or keyboard to choose the DVD menu items if you don't have LIRC setup for xine and your particular remote. :)

---

### Post by govee on 2007-11-11
Ok now Xine says missing plugin to load DVD//: and I just get a blank screen.

---

### Post by warp99 on 2007-11-11
Did you put a space between dvd:// and %d?

edit: Plus it's not DVD//: but dvd:// as the extension. :)

---

### Post by govee on 2007-11-11
yes I did. I als tried /dev/dvd

---

### Post by warp99 on 2007-11-11
Are you playing encrypted DVDs and have libdvdcss installed?

edit: Also the switch after -f is a capital "i" not the number one. It's the switch for no-gui, you don't really need it.

---

### Post by govee on 2007-11-11
looked at further and saw an unreadable plugin directory /andy/.xine/plugins

---

### Post by govee on 2007-11-11
yes the libdvdcss is installed and it is a movie from a DVD so I think the answer is yes.

---

### Post by warp99 on 2007-11-11
Well if you played encrypted DVDs before then you have libdvdcss, so bad on my part. It seems that that xine may have an incorrect pointer to the dvd drive.

Try just using xine with no switches or using dvd:// , then check setup in the drop down list from the xine gui to check if xine is pointing to the correct  terminal, which is /dev/dvd.  You should be able to run a DVD with xine from the gui if this is correct, so the problem is with the command string.

I would add the switches one by one and see where the error is. Also check the help file of xine by using the switch --help at the command line. You may be missing something I can't see.

---

