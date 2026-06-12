---
title: "F-Spot Export to Picasa Timeout"
date: 2010-08-02
forum: Multimedia Software
---

### Post by Conzar on 2010-08-02
**SOLUTION**
```
I solved my problem by doing the following on the Picasa web page
settings -> change your URL -> selected my user name.
This fixed the problem

```

**PROBLEM**
I am trying to use F-Spot to export pictures into Picasa web.  F-Spot is unable to upload any pics to picasa.  I have run F-Spot in debug mode and the output is shown below.

Any ideas of what might be wrong?

```

[Debug 13:04:28.875] GoogleAccount.Connect()
[Debug 13:04:33.589] Starting Upload to Picasa
[Debug 13:04:33.590] Picasa uploading 0
[Debug 13:04:33.595] open uri = file:///home/mspeth/Pictures/Photos/2010/08/02/Screenshot-Default - Wine desktop.png
[Warn  13:06:18.415] Caught an exception - Thread was being aborted (in `mscorlib')
  at (wrapper managed-to-native) System.Threading.WaitHandle:WaitOne_internal (intptr,int,bool)
  at System.Threading.WaitHandle.WaitOne (Int32 millisecondsTimeout, Boolean exitContext) [0x00000] 
  at System.Net.WebAsyncResult.WaitUntilComplete (Int32 timeout, Boolean exitContext) [0x00000] 
  at System.Net.WebConnectionStream.Write (System.Byte[] buffer, Int32 offset, Int32 size) [0x00000] 
  at Mono.Google.Picasa.PicasaAlbum.UploadPicture (System.String title, System.String description, System.String mime_type, System.IO.Stream input) [0x00000] 
  at Mono.Google.Picasa.PicasaAlbum.UploadPicture (System.String title, System.String description, System.IO.Stream input) [0x00000] 
  at Mono.Google.Picasa.PicasaAlbum.UploadPicture (System.String filename, System.String title, System.String description) [0x00000] 
  at FSpotGoogleExport.GoogleExport.Upload () [0x00000]

```

---

