---
title: "Banshee run error"
date: 2011-12-15
forum: Multimedia Software
---

### Post by spiderfracture on 2011-12-15
I recently installed 11.10 on my hp Pavillion laptop and Banshee ran fine for a couple of days, but now it refuses to open at all. I'm completely new to Ubuntu and have tried every tutorial I could find, and even uninstall/reinstalling. My music files run fine on Clementine, however :/ 

When I attempt to run Banshee in Term, this is what I get >_<

```
holly@nanami:~$ banshee
[Info  16:10:27.255] Running Banshee 2.2.1: [Ubuntu 11.10 (linux-gnu, x86_64) @ 2011-11-10 06:05:59 UTC]

(Banshee:32001): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:32001): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:32001): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:32001): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentException: Value does not fall within the expected range.
  at Hyena.Gui.Canvas.Rect.set_Height (Double value) [0x00000] in <filename unknown>:0 
  at Hyena.Gui.Canvas.Rect.op_Explicit (Rectangle rect) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Gui.ListView`1[Banshee.Collection.AlbumInfo].OnSizeAllocated (Rectangle allocation) [0x00000] in <filename unknown>:0 
  at Gtk.Widget.sizeallocated_cb (IntPtr widget, IntPtr allocation) [0x00000] in
```If anyone can help a girl out, that'd be greatly appreciated :] I'm about to start yanking my hair out.

---

### Post by jerrrys on 2011-12-17
this seems to be a bug with a fix already released

[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/889017](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/889017)

Maybe you need to update banshee

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=banshee+Gtk-WARNING+**%3A+Unable+to+locate+theme+engine+in+module_path%3A+%22pixmap%22&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=banshee+Gtk-WARNING+**%3A+Unable+to+locate+theme+engine+in+module_path%3A+%22pixmap%22&sa=Search&cof=FORID:9)

---

