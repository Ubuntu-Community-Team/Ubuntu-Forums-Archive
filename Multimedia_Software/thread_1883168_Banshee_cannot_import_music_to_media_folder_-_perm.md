---
title: "Banshee cannot import music to media folder - permission denied."
date: 2011-11-18
forum: Multimedia Software
---

### Post by Biopyro on 2011-11-18
Any time I try to import music to banshee, it will not, and gives me the following error:

Error creating directory: Permission denied.

I have tried simply changing the folder access permissions of the parent folder, but this did not work. Both folders are on a separate partition to banshee and the home folder, but this should not make a difference?

This is the readout from running it in terminal:

```
pcuser@pcuser-System:~$ banshee
[Info  19:48:24.828] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, i686) @ 2011-09-23 04:51:00 UTC]

(Banshee:9615): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", **added note: this happens for running most programs, doesn't seem to do anything, can it be solved easily?**

(Banshee:9615): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:9615): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:9615): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
[Info  19:48:29.045] Updating web proxy from GConf
[Info  19:48:29.182] All services are started 3.313665
[Info  19:48:31.689] nereid Client Started
[Info  19:48:32.164] GStreamer version 0.10.35.0, gapless: True, replaygain: False
[Error 19:48:47.488] file:///home/guy/Downloads/Waffles.fm/After%20banshee/Amon%20Tobin%20-%20ISAM%20(Deluxe%20Digital%20Version)%20%5B2011%20-%20V0%5D/11%20-%20Night%20Swim.mp3 - Error creating directory: Permission denied
[Error 19:48:47.677] Creating Source.UniqueId for Errors (type ErrorSource), but TypeUniqueId is null; trace is    at System.Environment.get_StackTrace()
   at Banshee.Sources.Source.get_UniqueId()
   at Banshee.Sources.SourceSortType+SourceComparer.Compare(Banshee.Sources.Source a, Banshee.Sources.Source b)
   at System.Array.qsort(Banshee.Sources.Source[] keys, Banshee.Sources.Source[] items, Int32 low0, Int32 high0, IComparer`1 comparer)
   at System.Array.qsort(Banshee.Sources.Source[] keys, Banshee.Sources.Source[] items, Int32 low0, Int32 high0, IComparer`1 comparer)
   at System.Array.SortImpl(Banshee.Sources.Source[] keys, Banshee.Sources.Source[] items, Int32 index, Int32 length, IComparer`1 comparer)
   at System.Array.Sort(Banshee.Sources.Source[] array, Int32 index, Int32 length, IComparer`1 comparer)
   at System.Collections.Generic.List`1[[Banshee.Sources.Source, Banshee.Services, Version=2.2.0.0, Culture=neutral, PublicKeyToken=null]].Sort(IComparer`1 comparer)
   at Banshee.Sources.SourceSortType.Sort(System.Collections.Generic.List`1 sources, Boolean separateTypes)
   at Banshee.Sources.Source.SortChildSources()
   at Banshee.Sources.Source.OnChildSourceUpdated(System.Object o, System.EventArgs args)
   at <Module>.invoke_void__this___object_EventArgs(System.Object , System.EventArgs )
   at <Module>.invoke_void__this___object_EventArgs(System.Object , System.EventArgs )
   at Banshee.Sources.Source.OnUpdated()
   at Banshee.Sources.ErrorSource.AddMessage(Banshee.Sources.Message message)
   at Banshee.Sources.ErrorSource.AddMessage(System.String title, System.String details)
   at Banshee.Collection.Database.DatabaseImportManager.LogError(System.String path, System.String msg)
   at Banshee.Collection.Database.DatabaseImportManager.LogError(System.String path, System.Exception e)
   at Banshee.Collection.Database.DatabaseImportManager.OnImportRequested(System.String path)
   at Banshee.Collection.ImportManager+ImportElement.ProcessItem(System.String item)
   at Hyena.Collections.QueuePipelineElement`1[[System.String, mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]].Processor(System.Object state)
[Error 19:48:47.678] file:///home/guy/Downloads/Waffles.fm/After%20banshee/Amon%20Tobin%20-%20ISAM%20(Deluxe%20Digital%20Version)%20%5B2011%20-%20V0%5D/12%20-%20Dropped%20from%20the%20Sky.mp3 - Error creating directory: Permission denied
[Error 19:48:47.925] file:///home/guy/Downloads/Waffles.fm/After%20banshee/Amon%20Tobin%20-%20ISAM%20(Deluxe%20Digital%20Version)%20%5B2011%20-%20V0%5D/01%20-%20Journeyman.mp3 - Error creating directory: Permission denied
[Error 19:48:48.074] file:///home/guy/Downloads/Waffles.fm/After%20banshee/Amon%20Tobin%20-%20ISAM%20(Deluxe%20Digital%20Version)%20%5B2011%20-%20V0%5D/05%20-%20Lost%20%26%20Found.mp3 - Error creating directory: Permission denied
[Error 19:48:48.168] file:///home/guy/Downloads/Waffles.fm/After%20banshee/Amon%20Tobin%20-%20ISAM%20(Deluxe%20Digital%20Version)%20%5B2011%20-%20V0%5D/03%20-%20Goto%2010.mp3 - Error creating directory: Permission denied
[Error 19:48:48.336] file:///home/guy/Downloads/Waffles.fm/After%20banshee/Amon%20Tobin%20-%20ISAM%20(Deluxe%20Digital%20Version)%20%5B2011%20-%20V0%5D/07%20-%20Mass%20%26%20Spring.mp3 - Error creating directory: Permission denied
[Error 19:48:48.465] file:///home/guy/Downloads/Waffles.fm/After%20banshee/Amon%20Tobin%20-%20ISAM%20(Deluxe%20Digital%20Version)%20%5B2011%20-%20V0%5D/13%20-%20Morning%20Ms%20Candis.mp3 - Error creating directory: Permission denied
[Error 19:48:48.668] file:///home/guy/Downloads/Waffles.fm/After%20banshee/Amon%20Tobin%20-%20ISAM%20(Deluxe%20Digital%20Version)%20%5B2011%20-%20V0%5D/02%20-%20Piece%20of%20Paper.mp3 - Error creating directory: Permission denied
[Error 19:48:48.815] file:///home/guy/Downloads/Waffles.fm/After%20banshee/Amon%20Tobin%20-%20ISAM%20(Deluxe%20Digital%20Version)%20%5B2011%20-%20V0%5D/04%20-%20Surge.mp3 - Error creating directory: Permission denied
[Error 19:48:48.914] file:///home/guy/Downloads/Waffles.fm/After%20banshee/Amon%20Tobin%20-%20ISAM%20(Deluxe%20Digital%20Version)%20%5B2011%20-%20V0%5D/08%20-%20Calculate.mp3 - Error creating directory: Permission denied
[Error 19:48:49.090] file:///home/guy/Downloads/Waffles.fm/After%20banshee/Amon%20Tobin%20-%20ISAM%20(Deluxe%20Digital%20Version)%20%5B2011%20-%20V0%5D/09%20-%20Kitty%20Cat.mp3 - Error creating directory: Permission denied
[Error 19:48:49.248] file:///home/guy/Downloads/Waffles.fm/After%20banshee/Amon%20Tobin%20-%20ISAM%20(Deluxe%20Digital%20Version)%20%5B2011%20-%20V0%5D/10%20-%20Bedtime%20Stories.mp3 - Error creating directory: Permission denied
[Error 19:48:49.422] file:///home/guy/Downloads/Waffles.fm/After%20banshee/Amon%20Tobin%20-%20ISAM%20(Deluxe%20Digital%20Version)%20%5B2011%20-%20V0%5D/14%20-%20One%20Last%20Look.mp3 - Error creating directory: Permission denied
[Error 19:48:49.585] file:///home/guy/Downloads/Waffles.fm/After%20banshee/Amon%20Tobin%20-%20ISAM%20(Deluxe%20Digital%20Version)%20%5B2011%20-%20V0%5D/06%20-%20Wooden%20Toy.mp3 - Error creating directory: Permission denied
FindNextFile: Bad encoding for '/media/0391a5db-61d8-4c3d-b633-59c710ed4386/guy/.wine/dosdevices/c:/windows/profiles/guy/My Documents/Downloads/Waffles.fm/Justice - &#65533; (V0)'
Consider using MONO_EXTERNAL_ENCODINGS

FindNextFile: Bad encoding for '/media/0391a5db-61d8-4c3d-b633-59c710ed4386/guy/.wine/dosdevices/z:/home/guy/Downloads/Waffles.fm/Justice - &#65533; (V0)'
Consider using MONO_EXTERNAL_ENCODINGS

FindNextFile: Bad encoding for '/media/0391a5db-61d8-4c3d-b633-59c710ed4386/guy/.wine/dosdevices/z:/home/pcuser/Downloads/Link to Downloads/Waffles.fm/Justice - &#65533; (V0)'
Consider using MONO_EXTERNAL_ENCODINGS

```

---

### Post by Biopyro on 2011-11-21
I *think*, and I'm not entirely sure on this, that the media folder was just set wrongly.

I renavigated to it in the preferences and it's back to working just fine.

---

### Post by TokyoYank on 2012-01-12
Thanks for answering your own post, it helped me.  

The fix:  reset 'Music Folder' for 'Source:Music' under Preferences

A minor warning, for others who find this post:  the fix might not be persistent after a reboot.  For me, it happened because my music library lives on my windows partition (dual boot), and the ntfs partition apparently doesn't always automatically mount.  The setting reverted to /media instead of knowing to wait for /media/Vista

If I click on the partition in question in Nautilus first, then start banshee, there are no issues.

Seems strange to me that music plays fine--it's only when you try to import that this setting pops up

cheers

---

