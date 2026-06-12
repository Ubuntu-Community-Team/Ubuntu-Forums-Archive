---
title: "FSpot crashes w/ dbus output attached"
date: 2008-11-03
forum: Multimedia Software
---

### Post by firstc624 on 2008-11-03
for some reason when i try to run fspot it crashes, here is the output of dbus

firstc624@firstc624-laptop:~$ dbus-launch f-spot
[Info  16:46:30.385] Initializing DBus
[Info  16:46:30.473] Initializing Mono.Addins
[Info  16:46:30.614] Starting new FSpot server
[Info  16:46:31.572] Starting BeagleService
[Info  16:46:31.572] Hack for gnome-settings-daemon engaged
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at FSpot.Tag.get_SizedIcon () [0x00000] 
  at TagSelectionWidget.IconDataFunc (Gtk.TreeViewColumn column, Gtk.CellRenderer renderer, TreeModel model, TreeIter iter) [0x00000] 
  at GtkSharp.TreeCellDataFuncWrapper.NativeCallback (IntPtr tree_column, IntPtr cell, IntPtr tree_model, IntPtr iter, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GtkSharp.TreeCellDataFuncWrapper.NativeCallback(IntPtr tree_column, IntPtr cell, IntPtr tree_model, IntPtr iter, IntPtr data)
   at GtkSharp.TreeCellDataFuncWrapper.NativeCallback(IntPtr , IntPtr , IntPtr , IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)
firstc624@firstc624-laptop:~$ 


Any help would be nice

---

### Post by waal on 2008-11-04
Same problem here. First it worked fine, but after adding a new picture-category it crashed. 

Now it crashes on opening. i have tried reinstalling F-spot and rebooting, but that doesn't help.


[Info  10:56:24.750] Initializing DBus
[Info  10:56:24.906] Initializing Mono.Addins
[Info  10:56:25.157] Starting new FSpot server
[Info  10:56:26.867] Starting BeagleService
[Info  10:56:26.868] Hack for gnome-settings-daemon engaged
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at FSpot.Tag.get_SizedIcon () [0x00000] 
  at TagSelectionWidget.IconDataFunc (Gtk.TreeViewColumn column, Gtk.CellRenderer renderer, TreeModel model, TreeIter iter) [0x00000] 
  at GtkSharp.TreeCellDataFuncWrapper.NativeCallback (IntPtr tree_column, IntPtr cell, IntPtr tree_model, IntPtr iter, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GtkSharp.TreeCellDataFuncWrapper.NativeCallback(IntPtr tree_column, IntPtr cell, IntPtr tree_model, IntPtr iter, IntPtr data)
   at GtkSharp.TreeCellDataFuncWrapper.NativeCallback(IntPtr , IntPtr , IntPtr , IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)

i use:
f-spot version 0.5.0.3-0ubuntu3
ubuntu 8.10

---

### Post by directhex on 2008-11-04
Programs and their data are not stored in the same place. Typically, reinstalling an app is pointless, as the app is dying on bad user data.

First, try deleting ~/.gnome2/f-spot/addin*

If that doesn't work, delete ~/.gnome2/f-spot - but you'll lose all your photo tags doing this one

---

### Post by waal on 2008-11-04
> **directhex said:**
> 

First, try deleting ~/.gnome2/f-spot/addin*




Thanks!!! F-spot is working again, after deleting addins-setup.config.

Only problem remaining: 
When i try to open the sub-labels below people it crashes again. This is where I created a sublabel just before f-spot crashed the first time.

Can i delete a sublabel somewhere?

---

### Post by waal on 2008-11-04
> **waal said:**
> 
Only problem remaining: 
When i try to open the sub-labels below people it crashes again. This is where I created a sublabel just before f-spot crashed the first time.


I tried adding a label to a picture. Here i could choose from the sublabels. There was no icon attatched to my new sub-label. By rightclicking on the new label, f-spot added the picture as an icon, now everything is working fine again.

---

### Post by waal on 2008-11-04
It seems adding a new label causes f-spot to cras each time. 

I think because there is no icon for the new label. When i add a new label by right-clicking on a picture -> add label -> create new tag, it works ok. Then the selected picture is added as icon for that label.

---

### Post by directhex on 2008-11-04
If in doubt, file a bug. Especially if it's 100% repeatable

---

### Post by pgmac on 2008-11-04
Hi,
I have a similar problem, except that it relates to my photos.db file.  Here's my error code:
[Info  06:02:43.244] Initializing DBus
[Info  06:02:43.399] Initializing Mono.Addins
[Info  06:02:43.661] Starting new FSpot server
[Info  06:02:45.360] Starting BeagleService
[Info  06:02:45.361] Hack for gnome-settings-daemon engaged
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at FSpot.Tag.get_SizedIcon () [0x00000] 
  at TagSelectionWidget.IconDataFunc (Gtk.TreeViewColumn column, Gtk.CellRenderer renderer, TreeModel model, TreeIter iter) [0x00000] 
  at GtkSharp.TreeCellDataFuncWrapper.NativeCallback (IntPtr tree_column, IntPtr cell, IntPtr tree_model, IntPtr iter, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GtkSharp.TreeCellDataFuncWrapper.NativeCallback(IntPtr tree_column, IntPtr cell, IntPtr tree_model, IntPtr iter, IntPtr data)
   at GtkSharp.TreeCellDataFuncWrapper.NativeCallback(IntPtr , IntPtr , IntPtr , IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)


I can see that it's failing on the GetSizedIcon call.
If I remove ~/.gnome2/f-spot/photos.db all works again, except that I have no photo's (and tags obviously).  I have a couple of thousand photo's and really don't like the idea of having to go back through every photo and re-tagging, etc.

Is there any way of parsing the sqlite updated photos.db file at all?

Cheers,
Paul

---

### Post by pgmac on 2008-11-04
After doing a little more looking around, I've run f-spot in debug mode to get this:

$ f-spot --debug
** Running f-spot in Debug Mode **
** Running Mono with --debug   **
Xlib:  extension "RANDR" missing on display ":0.0".
[Info  06:21:10.706] Initializing DBus
[Debug 06:21:10.959] DBusInitialization took 0.1864s
[Info  06:21:10.959] Initializing Mono.Addins
[Debug 06:21:11.339] Mono.Addins Initialization took 0.379515s
[Info  06:21:11.349] Starting new FSpot server
[Debug 06:21:11.814] Db Initialization took 0.244457s
[Debug 06:21:12.450] QueryToTemp took 0.08807s : SELECT id, time, uri, description, roll_id, default_version_id, rating, md5_sum FROM photos  WHERE id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC
[Debug 06:21:12.777] PhotosPerMonth took 0.051408s
[Debug 06:21:12.788] TimeAdaptor REAL Reload took 0.267266s
[Debug 06:21:12.928] Query took 0.066427s : SELECT * FROM photoquery_temp_0 LIMIT 100 OFFSET 0
[Debug 06:21:13.154] QueryToTemp took 0.112949s : SELECT id, time, uri, description, roll_id, default_version_id, rating, md5_sum FROM photos  WHERE id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time ASC
[Debug 06:21:13.241] Query took 0.065681s : SELECT * FROM photoquery_temp_0 LIMIT 100 OFFSET 0
[Debug 06:21:13.261] open uri = file:///home/paul/Photos/2008/05/08/P5080001.JPG
[Debug 06:21:13.316] open uri = file:///home/paul/Photos/2008/05/08/P5080001.JPG
[Debug 06:21:13.479] PhotosPerMonth took 0.100834s
[Debug 06:21:13.480] TimeAdaptor REAL Reload took 0.322183s
[Debug 06:21:13.713] Reloading the query took 0.672417s
[Info  06:21:13.915] Starting BeagleService
[Debug 06:21:13.917] BeagleService startup took 2.4E-05s
[Info  06:21:13.917] Hack for gnome-settings-daemon engaged
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at FSpot.Tag.get_SizedIcon () [0x00000] 
  at TagSelectionWidget.IconDataFunc (Gtk.TreeViewColumn column, Gtk.CellRenderer renderer, TreeModel model, TreeIter iter) [0x00000] 
  at GtkSharp.TreeCellDataFuncWrapper.NativeCallback (IntPtr tree_column, IntPtr cell, IntPtr tree_model, IntPtr iter, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GtkSharp.TreeCellDataFuncWrapper.NativeCallback(IntPtr tree_column, IntPtr cell, IntPtr tree_model, IntPtr iter, IntPtr data)
   at GtkSharp.TreeCellDataFuncWrapper.NativeCallback(IntPtr , IntPtr , IntPtr , IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)
[Debug 06:21:14.178] Finalizer called on FSpot.Category. Should be Disposed
[Debug 06:21:14.178] Finalizer called on FSpot.Category. Should be Disposed
[Debug 06:21:14.178] Finalizer called on FSpot.Category. Should be Disposed
[Debug 06:21:14.179] Finalizer called on FSpot.Category. Should be Disposed
[Debug 06:21:14.179] Finalizer called on FSpot.Category. Should be Disposed
[Debug 06:21:14.179] Finalizer called on FSpot.Category. Should be Disposed
[Debug 06:21:14.179] Finalizer called on FSpot.Category. Should be Disposed
[Debug 06:21:14.179] Finalizer called on FSpot.Category. Should be Disposed

I've run the queries listed here using a SQLite Database Browser ([http://sqlitebrowser.sourceforge.net/](http://sqlitebrowser.sourceforge.net/)) and all, except the query on photoquery_temp_0, execute perfectly.

How can I better track down where the error is occurring?  Could be it working my way through the source code and trying to find what code and data is coming back at my failure point?

Cheers,
Paul

---

### Post by pgmac on 2008-11-04
Don't worry about this anymore, my problems have been fixed with the new daily update from the "proposed" update list.

Cheers,
Paul

---

