---
title: "Banshee ipod sync error"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by DJMattB241 on 2007-11-05
I've tried a bunch of media managers and it seems that at this point Banshee is the best option (I'm not super happy with any of them).

There are a few smaller gripes I have with Banshee, but the main one is that when I try to sync my ipod with it, it stalls before it can get to the sync. Running it through the terminal produced these results:

First of all, when I first connect the ipod, it does this:

```

** (Banshee:5999): CRITICAL **: ipod_device_parse_serial: 
assertion `strlen(serial) == 11' failed
Debug: [11/1/2007 11:22:31 PM] (DAP has been added) - 
Banshee.Dap.Ipod.IpodDap: /org/freedesktop/Hal/devices/volume_uuid_2FB9_FAEA
```

and then gives the following message about 10 times in a row:

```
(Banshee:5999): GdkPixbuf-WARNING **: GdkPixbufLoader finalized 
without calling gdk_pixbuf_loader_close() - this is not allowed. 
You must explicitly end the data stream to the loader before 
dropping the last reference.
```

Neither of which look very good... when I try to sync, it gives me this:

```
Unhandled Exception: System.IO.FileNotFoundException: Could not find file "/#0%!.mp3".
File name: '/#0%!.mp3'
  at System.IO.FileInfo.get_Length () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.FileInfo:get_Length ()
  at IPod.Track.set_Uri (System.Uri value) [0x00000] 
  at Banshee.Dap.Ipod.IpodDap.Synchronize () [0x00000] 
  at Banshee.Dap.DapDevice.Transcode () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
```

I don't know why it's looking for a file named /#0%!.mp3 but I've tried deleting the database and running the program like new a few times, and the error has been consistent.

Any ideas?

---

### Post by Blackcomb on 2007-11-05
Can you please tell us what type/generation of iPod you have?

regards

---

### Post by DJMattB241 on 2007-11-05
Sure, it's a 4th Gen iPod Photo 60Gb.
I would be asking this on the Banshee forums, but I tried registering and it requires an admin authorization... which I have yet to recieve (always a good sign...)

---

### Post by Blackcomb on 2007-11-05
Have you got (the latest update of) libipod? -> [http://libipod.sourceforge.net/](http://libipod.sourceforge.net/)
You could also try Amarok (very good player) or GTKpod.

You iPod should be supported by this software.

---

