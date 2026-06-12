---
title: "F-spot crash"
date: 2010-08-12
forum: Multimedia Software
---

### Post by Teun Spaans on 2010-08-12
Hi, 

I'm new to the forum and to ubuntu, sorry if this is the wrong place to ask.

I installed ubuntu and tried using f-spot to compress a photo. It crashes.

The installed version of f-spot is the package 0.6.1.5-2ubuntu7, which according to the synaptic package manger is also the most recent one.

What I do is:
* Sart F-spot from Ubuntu menu
* Open  a photo from my camera, which i copied to laptop hard drive
* Choose Photo-export-folder.
* Check resize to 400 pixels
* Click export.

I then get:
System.NullRefereceException: Object not set to an instance of an object.
 at FSpotFolderExport.HtmlGallery.WriteTagsLInks(System.Web.UI.HtmlTextWriter writer, F-Spot.Tag[] tags) [0x00000]
 at FSpotFolderExport.HtmlGallery.SavePhotoHtmlIndex (int32 i) [0x00000]
 at FSpotFolderExport.HtmlGallery.GenerateLayout () [0x00000]
 at FSpotFolderExport.FolderExport.Upload () [0x00000]

Can anyone pls help?
I have not experienced problems with other ubuntu applications

---

### Post by pradeepbabu@in.com on 2011-10-20
choose save the files only its working for me now (don't know why its working ) i too had the same issue

---

