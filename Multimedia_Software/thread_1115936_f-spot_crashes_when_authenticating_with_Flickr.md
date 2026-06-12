---
title: "f-spot crashes when authenticating with Flickr"
date: 2009-04-04
forum: Multimedia Software
---

### Post by gdi2k on 2009-04-04
I'm having trouble getting f-spot authenticated with Flickr. As soon as I press the "Authorise" button to begin the authentication process, f-spot crashes. When run from the command line, the following shows: 

```
[Info  19:20:08.096] Initializing DBus
[Info  19:20:08.411] Initializing Mono.Addins
[Info  19:20:08.871] Starting new FSpot server
[Info  19:20:14.481] Starting BeagleService
[Info  19:20:14.481] Hack for gnome-settings-daemon engaged

(f-spot:18644): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.

(f-spot:18644): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
FlickrNet.FlickrWebException: HTTP Error 403, Forbidden ---> System.Net.WebException: The remote server returned an error: (403) Forbidden.
  at System.Net.HttpWebRequest.CheckFinalStatus (System.Net.WebAsyncResult result) [0x00000] 
  at System.Net.HttpWebRequest.SetResponseData (System.Net.WebConnectionData data) [0x00000] --- End of inner exception stack trace ---

  at FlickrNet.Flickr.DoGetResponse (System.String url, System.String variables) [0x00000] 
  at FlickrNet.Flickr.GetResponse (System.Collections.Hashtable parameters, TimeSpan cacheTimeout) [0x00000] 
  at FlickrNet.Flickr.GetResponseNoCache (System.Collections.Hashtable parameters) [0x00000] 
  at FlickrNet.Flickr.AuthGetFrob () [0x00000] 
  at FlickrRemote.TryWebLogin () [0x00000] 
  at FSpotFlickrExport.FlickrExport.Login () [0x00000] 
  at FSpotFlickrExport.FlickrExport.HandleClicked (System.Object sender, System.EventArgs args) [0x00000] 
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)

```

With it being a 403 error, it may well be a problem with Flickr's servers, but I haven't seen anyone else report the issue, which makes me suspect. 

Is there anyone else having similar trouble or does it work ok for you?

---

### Post by gdi2k on 2009-04-06
Sorry, just realised why this is: flickr has been blocked by the local authorities, making it inaccessible from with f-spot.

---

### Post by directhex on 2009-04-06
> **gdi2k said:**
> Sorry, just realised why this is: flickr has been blocked by the local authorities, making it inaccessible from with f-spot.

It still shouldn't crash. File a bug upstream.

---

