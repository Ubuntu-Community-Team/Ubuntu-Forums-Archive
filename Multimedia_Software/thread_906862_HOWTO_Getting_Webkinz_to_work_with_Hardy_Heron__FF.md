---
title: "HOWTO: Getting Webkinz to work with Hardy Heron / FF3"
date: 2008-08-31
forum: Multimedia Software
---

### Post by john8791 on 2008-08-31
I just wanted to pass this along as I have seen several posts on Flash player issues while searching for a solution to my own problem getting Webkinz to work with Firefox 3.0.1.  **Note that I am using the Firefox that was provided with the standard distro of Ubuntu 8.04.**

1.) Install "flashplugin-nonfree" through Synaptic with multiverse repository enabled.  (This installed 9.0.124.0ubuntu2).

2.)  Copy /usr/lib/flashplugin-nonfree/libflashplayer.so to /usr/lib/swfdec-mozilla/

3.) Make a backup copy of existing libswfdecmozilla.so in /usr/lib/swfdec-mozilla/

4.) Rename the libflashplayer.so you copied earlier to libswfdecmozilla.so

5.) Restart Firefox, verify through "about : plugins"

This took care of not only Webkinz but a lot of other flash problems.

---

### Post by maroshi on 2009-06-19
Very good working solution.
Here is an update to **Ubuntu 9.0.4 Jaunty. With Firefox 3.0.11**

1.) Install "flashplugin-nonfree" through Synaptic with multiverse repository enabled.  (This installed 10.0.22.87.0ubuntu2).
2.) Open a terminal and run [FONT=Courier New]su[/FONT]. To act as root.
3.)  Copy /usr/lib/flashplugin-installer/libflashplayer.so to /usr/lib/swfdec-mozilla/
[FONT=Courier New]cp /usr/lib/flashplugin-installer/libflashplayer.so  /usr/lib/swfdec-mozilla/[/FONT]
4.) Make a backup copy of existing libswfdecmozilla.so in /usr/lib/swfdec-mozilla/
[FONT=Courier New]cp /usr/lib/swfdec-mozilla/libswfdecmozilla.so /usr/lib/swfdec-mozilla/libswfdecmozilla.so.org
[/FONT]5.) Rename the libflashplayer.so you copied earlier to libswfdecmozilla.so
[FONT=Courier New]mv /usr/lib/swfdec-mozilla/libflashplayer.so [/FONT][FONT=Courier New]/usr/lib/swfdec-mozilla/[/FONT][FONT=Courier New]libswfdecmozilla.so
[/FONT]6.) Restart Firefox, verify through "about : plugins"
7.) Exit [FONT=Courier New]su[/FONT] Shell.
[FONT=Courier New]exit[/FONT]

Works and fix many Flash application.

Joy and happiness
David

---

### Post by Revolutionary101 on 2009-06-19
You could also go to the Adobe website and download the Debian package from their website.

I think that this is the best way to do it.

Hope you get it fixed.

---

