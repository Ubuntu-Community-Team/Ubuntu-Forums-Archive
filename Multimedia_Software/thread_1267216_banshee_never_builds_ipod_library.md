---
title: "banshee never builds ipod library"
date: 2009-09-15
forum: Multimedia Software
---

### Post by jellevictoor on 2009-09-15
Hey,

I want a tool to automaticly sync my ipod with my music libary. I have choosen Banshee. 
Now these are the steps i take.

I have an empty ipod.
launch banshee
banshee asks for a new lib build
i say ok.
I press synchronize ipod with library (or something like that) (manual syncing ain't an option)
I press eject
i writes all the tracks to the ipod
it flushes the ipod.
I disconnect the ipod and boom, No Music

Someone know this problem?
i have the logging here:
[Warn  19:33:59.964] Failed to save iPod database - Object reference not set to an instance of an object (in `ipod-sharp')
  at IPod.ImageNameRecord.SetData (System.IO.Stream stream, System.Byte[] data, Int32 offset) [0x00000] 
  at IPod.ImageNameRecord.SetData (System.IO.Stream stream, System.Byte[] data) [0x00000] 
  at IPod.PhotoDatabase.SaveThumbnails (System.Collections.Generic.List`1 existingNames, System.Collections.Generic.List`1 newNames, System.Collections.Generic.List`1 removedNames, IPod.ArtworkFormat format) [0x00000] 
  at IPod.PhotoDatabase.SaveThumbnails () [0x00000] 
  at IPod.PhotoDatabase.Save () [0x00000] 
Failed to save database (in `ipod-sharp')
  at IPod.PhotoDatabase.Save () [0x00000] 
  at IPod.TrackDatabase.Save () [0x00000] 
Failed to save database (in `ipod-sharp')
  at IPod.TrackDatabase.Save () [0x00000] 
  at IPod.Device.Save () [0x00000] 
  at Banshee.Dap.Ipod.IpodSource.PerformSyncThreadCycle () [0x00000] 
[Warn  19:35:23.503] Forcefully breaking out of RCS loop b/c change in total_width less than 1.0


any help? anyone know this issue?

---

### Post by taavipalo on 2010-01-29
I've got the same problem, banshee fails to write the database to the ipod. Running debug mode gives me the same error.

Edit: Sorry, not exactly the same error.

> [Warn  14:11:37.107] Failed to save iPod database - Argument is out of range.
Parameter name: value is less than 0 (in `mscorlib')
  at System.IO.FileStream.SetLength (Int64 value) [0x00000] 
  at IPod.PhotoDatabase.SaveThumbnails (System.Collections.Generic.List`1 existingNames, System.Collections.Generic.List`1 newNames, System.Collections.Generic.List`1 removedNames, IPod.ArtworkFormat format) [0x00000] 
  at IPod.PhotoDatabase.SaveThumbnails () [0x00000] 
  at IPod.PhotoDatabase.Save () [0x00000] 
Failed to save database (in `ipod-sharp')
  at IPod.PhotoDatabase.Save () [0x00000] 
  at IPod.TrackDatabase.Save () [0x00000] 
Failed to save database (in `ipod-sharp')
  at IPod.TrackDatabase.Save () [0x00000] 
  at IPod.Device.Save () [0x00000] 
  at Banshee.Dap.Ipod.IpodSource.PerformSyncThreadCycle () [0x00000] 

---

### Post by nmyrick on 2011-01-25
Have you checked the permissions of the Ipod folder in FileSystem\media?  Your system may have mounted it as 'root' for some reason, therefore, not allowing you to write the database.

Also, sometimes you need to find and manually delete the ItunesDB file in your ipod.  This way, banshee will create a new database.  However, before doing so, I would copy it and rename the copy 'ItunesDB.bak'. In case you have issues, then you can just open the folder and rename the copy back to 'ItunesDB', and your Ipod will be back to normal.

---

