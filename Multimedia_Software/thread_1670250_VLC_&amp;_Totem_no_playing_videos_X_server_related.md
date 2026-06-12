---
title: "VLC &amp; Totem no playing videos X server related"
date: 2011-01-18
forum: Multimedia Software
---

### Post by marisdembovskis on 2011-01-18
Manually setting displays. Turning off laptop display and reset external display. Video card is Intel. 

 
Everything seems to be fine, but when I start some movie, after some seconds VLC player crashes and shows blue screen. Totem is not even starting. Here is terminal information. 
If I dont reset it with xrandr, external display is wrong resolution. 

rouzy@rouzy-M3N:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
rouzy@rouzy-M3N:~$ lspci | grep Display
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
rouzy@rouzy-M3N:~$ 

rouzy@rouzy-M3N:~$ xrandr --output LVDS1 --off 
rouzy@rouzy-M3N:~$ xrandr --output VGA1 --mode 1280x1024
rouzy@rouzy-M3N:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x925c914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb74d30d4, 0xb74d3048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1295758612)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:1577): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
rouzy@rouzy-M3N:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x86f2914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb753f0d4, 0xb753f048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1295228144)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:1701): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
rouzy@rouzy-M3N:~$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 135 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
rouzy@rouzy-M3N:~$ totem --sync
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 115 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
rouzy@rouzy-M3N:~$

---

### Post by marisdembovskis on 2011-01-18
don't care much about totem. 
Bun on Vlc I did:
Preferences, Output, X11 output XCB. 

EVERYTHING IS PERFECT!

---

