---
title: "Muine crashing"
date: 2008-05-23
forum: Multimedia Software
---

### Post by laki42 on 2008-05-23
Hi everybody,
I've found out that muine would be the perfect music player for me, especially because of its simplicity. The only problem is that it keeps crashing every time I hit the buttons "Play Song" or "Play Album" and I get this:
```
(muine:25061): Gtk-CRITICAL **: gtk_tree_model_row_inserted: assertion `path != NULL' failed

(muine:25061): Gtk-CRITICAL **: gtk_tree_model_row_inserted: assertion `path != NULL' failed

<THIS KEEPS ON GOING MANY MANY TIMES>

...
...


(muine:25061): Gtk-CRITICAL **: gtk_tree_model_row_inserted: assertion `path != NULL' failed

(muine:25061): Gtk-CRITICAL **: gtk_tree_model_row_inserted: assertion `path != NULL' failed
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Muine.AddSongWindow.GetTitle (Muine.Song song) [0x00000] 
  at Muine.AddSongWindow.SetText (Gtk.CellRendererText cell, TreeIter iter) [0x00000] 
  at Muine.AddSongWindow.CellDataFunc (Gtk.TreeViewColumn col, Gtk.CellRenderer cell, TreeModel model, TreeIter iter) [0x00000] 
  at GtkSharp.TreeCellDataFuncWrapper.NativeCallback (IntPtr tree_column, IntPtr cell, IntPtr tree_model, IntPtr iter, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GtkSharp.TreeCellDataFuncWrapper.NativeCallback(IntPtr tree_column, IntPtr cell, IntPtr tree_model, IntPtr iter, IntPtr data)
   at GtkSharp.TreeCellDataFuncWrapper.NativeCallback(IntPtr , IntPtr , IntPtr , IntPtr , IntPtr )
   at Gtk.TreeView.gtk_tree_view_set_cursor(IntPtr , IntPtr , IntPtr , Boolean )
   at Gtk.TreeView.gtk_tree_view_set_cursor(IntPtr , IntPtr , IntPtr , Boolean )
   at Gtk.TreeView.SetCursor(Gtk.TreePath path, Gtk.TreeViewColumn focus_column, Boolean start_editing)
   at Muine.HandleView.SelectFirst()
   at Muine.AddWindow.Search()
   at Muine.AddWindow.Reset()
   at Muine.AddWindow.ResetFunc()
   at GLib.Idle+IdleProxy.Handler()
   at GLib.Idle+IdleProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Muine.Global.Main(System.String[] args)
```

Can anybody help me getting muine work on my Hardy?

---

