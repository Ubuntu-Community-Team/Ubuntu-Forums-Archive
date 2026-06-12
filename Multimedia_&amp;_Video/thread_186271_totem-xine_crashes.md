---
title: "totem-xine crashes"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by jpeddicord on 2006-06-01
Whenever I try to start totem (xine) without any parameters, it crashes on startup. It can play movies fine when opening them directly, but I cannot start totem without it crashing otherwise. It opens the GUI, then it appers to load xine and I see a blue screen for 1/10 of a second, then it just dies.

Here is some terminal output:
```
jacob@linux:~$ totem
GTK Accessibility Module initialized
Bonobo accessibility support initialized
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 69 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```I also tried --sync but it added no more debugging information.

Does this happen with anyome else? I also tried a fresh Ubuntu install because of the final, but I get the same result.

---

### Post by mattkenn4545 on 2006-06-01
Why not use totem-gstreamer?

Just make sure you have these packages installed and you should be able to play just able everything (and have to firefox pluging to play videos online)

gstreamer0.10-ffmpeg
gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
totem-gstreamer-firefox-plugin

the gstreamer0.10-pitfdll allows gstreamer to use the win32 codecs (very good was the only reason I still used the totem-xine before this)

also do you have the win32 codecs installed if not you should?

---

### Post by jpeddicord on 2006-06-01
[QUOTE=mattkenn4545](very good was the only reason I still used the totem-xine before this)[/QUOTE]Ah, I couldn't figure out how to get those to work in gstreamer, thats why I wanted Xine. Thanks for the info!

---

### Post by shadowhunter on 2006-06-02
because with totem-gstreamer you can't have any menus in your dvd...

Geert.

---

### Post by jpeddicord on 2006-06-02
[QUOTE=shadowhunter]because with totem-gstreamer you can't have any menus in your dvd...

Geert.[/QUOTE]
Then how can I stop totem-xine from crashing? ](*,)

---

### Post by mattkenn4545 on 2006-06-02
Use Gxine (or something like that) for DVD'd and totem for everything else

---

### Post by IcemanV9 on 2006-07-04
Today (Jul 4th), I just found out that Totem(-xine) crashes. Same error message as jacobmp92's. If I use command in the terminal, totem <whatever file>, then it'll work. It does NOT work without a file. It IS a bug issue #[35229]("https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229").

I hope it will be fixed in the near future!

---

### Post by burt_57 on 2007-05-20
Here goes nothing
Totem require pluging to play DVD ... but which one ?
gxine does not work either for DVD viewing.
What am I doing wrong ?  :(

---

