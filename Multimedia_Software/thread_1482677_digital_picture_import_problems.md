---
title: "digital picture import problems"
date: 2010-05-13
forum: Multimedia Software
---

### Post by shadowcrunch on 2010-05-13
Hello! I'm hoping someone can shed a little light on this. I was trying to import some pictures from my digital camera using f-spot, and it wouldn't open. I tried just running f-spot from the menu and I got a little f-spot pop-up box that vanished right away. From a post in the forums I tried running f-spot through terminal and got:

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
mike@mike-desktop:~$ f-spot

(/usr/lib/f-spot/f-spot.exe:15348): GLib-WARNING **: g_set_prgname() called multiple times
[Info  19:58:35.037] Initializing DBus
[Info  19:58:35.169] Initializing Mono.Addins
[Info  19:58:35.346] Starting new FSpot server (f-spot 0.6.1.5)

** (/usr/lib/f-spot/f-spot.exe:15348): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:15348): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:15348): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:15348): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:15348): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  19:58:36.125] Starting BeagleService
[Info  19:58:36.143] Hack for gnome-settings-daemon engaged

(/usr/lib/f-spot/f-spot.exe:15348): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.

(/usr/lib/f-spot/f-spot.exe:15348): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale: assertion `GDK_IS_PIXBUF (dest)' failed
The program '/usr/lib/f-spot/f-spot.exe' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 3256 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
mike@mike-desktop:~$ 

A different forum I'm a member of mentioned I should NOT have an EXE in there. I uninstalled f-spot, reinstalled from synaptic, and got the exact same error. Getting frustrated about the import, I installed digikam, which was working great until I tried importing pics. It found the pics in my camera and I selected them all...when I tried downloading them from the camera digicam closed and an error window popped up with more info I don't understand. If anyone wants, I can try it again and try copy/pasting the error from digikam. At the moment I think I would rather use digikam than f-spot, but more importantly I would just like to be able to plug in my camera and have one of them open and get ready to import my pics. Any help is greatly appreciated.

---

### Post by WinterRain on 2010-05-13
> **shadowcrunch said:**
> I uninstalled f-spot, reinstalled from synaptic, and got the exact same error.

In linux, when you want to try the old windows-like trick of reinstalling an app to make it work right, you must do:
```
sudo apt-get clean && sudo apt-get autoremove
```
after uninstalling said app, and before installing new. Otherwise you will just wind up with the same problems.

Anyway, you could try Gthumb for digital photos. Just go to file>import photos. Works great with my kodak camera.

---

### Post by shadowcrunch on 2010-05-13
thanks for the info! I will try Gthumb, but I will definitely spend some time on the apt-get command you mention so I have a better understanding of what I'm doing.

---

### Post by lyall on 2010-05-13
also take look at digiKam it is in the Ubuntu Software Center

good luck and have fun learning

---

### Post by shadowcrunch on 2010-05-13
I did try digikam, but got errors when trying to import pics. Guy at another forum is currently going through screenshots of my synaptic to see if it's from my not having needed packages installed. As of right now, all of the digital picture programs I try either won't work or won't import.

---

