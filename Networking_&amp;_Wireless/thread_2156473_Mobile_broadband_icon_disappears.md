---
title: "Mobile broadband icon disappears"
date: 2013-06-21
forum: Networking &amp; Wireless
---

### Post by endangst on 2013-06-21
It worked perfectly fine on 11.10, 12.04 and 12.10 but on 13.04 the mobile broadband icon (nm-applet) will disappear after a while.

I then restart it manually by typing nm-applet in the terminal.

The icon won't disappear if I start it manually but many error messages show up in the terminal.

```
nm-applet
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 71: Invalid UTF-8 encoded text in name - not valid 'Mobile broadband connection '\xd0\u0007\x8a\u0002' active: (83%)'

(nm-applet:3044): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(nm-applet:3044): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(nm-applet:3044): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(nm-applet:3044): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(nm-applet:3044): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
```

I appreciate any help. Thanks in advance.

---

### Post by danielglz on 2013-09-05
Hello:

I have the same problem. I am running Ubuntu 13.04 64 bits on Toshiba Portege Z930-145. I am conecting my mobile phone through bluetooth. An output excerpt after running "dmesg" command in a terminal shows this:

[   87.872429] Bluetooth: TIOCGSERIAL is not supported
[   90.219006] Bluetooth: TIOCGSERIAL is not supported

I don't know if this is related. Some times, after using mobile broadband conection, my system doesn't boot correctly, and I get a black screen with white letters claiming "panic kernel". May be all this related to bluetooth hardware incompatibility??. Thank you.

Daniel.

---

