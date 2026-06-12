---
title: "Removing Watermark From jpeg"
date: 2010-02-18
forum: Multimedia Software
---

### Post by mockdeep on 2010-02-18
I met a guy who is going about with a thermal imaging device.  He wants to remove the watermark from the images and tells me that the software developed by the company can do this using only the jpeg.  Unfortunately it's only available for windows.  I'm dubious that this is possible, but I have to admit I'm not extremely well versed in image manipulation.  Is it possible to extract the unadulterated image from a copy with the watermark and other data on it?  I've attached an example of the kind of file he's working with.  Thanks!

---

### Post by mockdeep on 2010-02-22
Bump.

---

### Post by tgalati4 on 2010-02-22
Only if the headers and watermark are on separate layers.  Then you can delete them using GIMP.  The image that you attached is a "flattened" image.  All of the layers are pushed into one layer.  This is typical, and it happens before the image is compressed to *.jpg.

I presume the camera uses a Windows-based program to overlay the temperature scale.  You would have to get the specs of the camera and write your own linux driver to just get the image.  There's no practical way to remove the header and watermark on a flattened image.

See if you can get the image in *.TIF format or some other uncompressed format.  You may have better luck with that.

---

### Post by mockdeep on 2010-02-24
I kind of suspected as much.  He tells me that he can plug the device into his Linux computer and it pops up like any camera with jpg's he can then just copy over.  He says that somehow the Windows program for the device takes those images and removes all of the overlays.  He doesn't seem very cognisant of how all of this stuff works, but he assures me that there is a hidden png in the jpeg file that contains the unadulterated image, and that someone after a great deal of work managed to extract it.  I spent a while online looking for possibilities--I found one site that mentioned a method of encrypting images based on differences between the image and its thumbnail, but that required png thumbnails and I was only able to extract it in jpg format.  Seems like a great deal of work for a company to go to just to make sure their name is on the picture.

---

### Post by mcduck on 2010-02-24
I suppose your friend doesn't really have any idea hat he's talking bout... :D

Anyway, removing watermarks is done simply by copying image data from around the watermark to hide the watermark. So such tools can't see through the watermark, they only edit the image to look (more or less) convincingly as if there never was a watermark. Of course all the edited data is just created by the tool or copied from somewhere in the image, it's not what actually would be behind the watermark.

(and the idea about JPG image having a hidden PNG image is insane, that would make the JPG file *really* large as PNG is uses lossy compression and creates very large files compared to JPG compression.. using data from thumbnail would be plausible, but the thumbnail is really low resolution so you'd still have to create most of the image data out of nowhere or copy it from soemwhere else in the actual image.)

You can get such tools as plugins for Gimp, and many video players (VLC, for example) include filters for removing logos from video, but usually simply doing it by hand with the Clone Brush gives you the best results.

---

