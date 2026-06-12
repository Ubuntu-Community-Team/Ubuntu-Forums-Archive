---
title: "Color problems converting RAW (CRW) to JPG"
date: 2009-02-01
forum: Multimedia Software
---

### Post by brnetonboy on 2009-02-01
I accidentally switched my Canon EOS Digital Rebel to "AV mode" which means that half my pictures ended up as Raw CRW files. Each CRW file (about 10mb each) has a THM (about 15kb each) thumbnail file to go along with it, which nicely shows what the original color should look like. (Also, there is a .CTG file the camera made, which I assume has information about what colors to use... I assume some program can read this and take it into account?)

My problem is that in converting these raw images to Jpeg, the colors are getting completely out of whack and looking terrible. I've installed a bunch of different RAW-aware programs. Some of them get the colors right, and some don't. But none of the ones that would batch-convert to Jpeg get it right. :(

Here is what I've used/installed so far:

[LIST]
[*]**gnome-raw-thumbnailer** [2.0.1-0ubuntu5 (intrepid)]: makes nautilus understand the raw format and show thumbnails for it--works perfectly and always has the correct color.
[*]**dcraw**: seems to have already been installed by default. couldn't figure out how to make it work on it's own.
[*]**gimp-dcraw** [1.31-1]: seems to make the gimp able to open raw files. I didn't try before I installed this, but it works great afterwards. Gimp displays the colors correctly. However, it does not do batch conversion! :(
[*]**rawstudio** [1.0-1]: great program that does batch conversion and seems to use dcraw. unfortunately, the colors are completely screwy! it allows for some adjustments to things like saturation and exposure, but I can't get it right!
[*]**F-Spot Photo Viewer**: I don't know if this works because of something else I installed, but F-Spot opens the raw files great and in the correct color! However, it doesn't convert, as far as I can tell.
[*]**flPhoto **[1.3.1]: not as nice as rawstudio, but it does seem to convert photos, however the colors are not right. they're better than rawstudio though. But still terrible.
[/LIST]
Does anyone have any ideas on how to fix rawstudio to make the colors come out correctly, or can anyone suggest any other programs that will work? Thanks.

(I'm using Ubuntu 8.10, Kernel Linus 2.6.2-11-generic, GNOME 2.24.1)

---

### Post by punx45 on 2009-02-01
what do you mean by colors out of whack?   RAW is designed to capture the image unprocessed, so it wont be conforming to a specific colorspace like jpegs do.   if your pictures are coming out flat or dull,  that is normal.   if colors are reversed, for example, then there is something wrong.

---

### Post by brnetonboy on 2009-02-01
I am not sure exactly how to describe it. It's something like it's too bright/dim/saturated/unsaturated or the hue/contrast/warmth/tint/exposure is off. The pictures look completely awful. 

> if your pictures are coming out flat or dull, that is normal.

I don't think that's right because as I mentioned, Gimp and F-Spot display the RAW images in the normal way that doesn't look terrible, the way that all my other pictures look, and the way that the thumbnails (my camera created one little thumbnail for each picture) look. I don't think that the "normal" way to display the Raw image should be at odds with the created thumb.

Let's not get into semantics: maybe the way rawstudio converts the images is not "wrong" and the way Gimp does is not "right." Whatever, that's not the point. How can I make rawstudio do it the way Gimp and everythign else does?

---

### Post by mutrax on 2009-11-08
Sorry for reviving this old tread, but I had just the same problem. (I tend to document my solutions here nowadays ;) )

Problem that my colors where wrong is that Dcraw didn't know my camera model, so thar raw converters like ufraw can't do camera white balance.

Since ufraw wraps dcraw in its code I had to look for a recent version of ufraw (camera model only available when new ufraw code gets released)..

So I added PAscal de bruijn's ppa ([https://launchpad.net/~pmjdebruijn/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~pmjdebruijn/+archive/ppa?field.series_filter=karmic)) and installed a recent version of ufraw & dcraw et voila!

---

### Post by xadder on 2009-11-25
I had ufraw working fine for pics from my Canon EOS 50D, although some don't convert to jpg as well as Canon's DPP would. 

The latter won't work on Linux though, so I just tried those Pascal de Bruijn's packages. Installation went smoothly, but now my photo's are all green!

Anybody know a simple solution, or should I just I just go back to the default Karmic packages? Thanks,

---

### Post by Dougie187 on 2009-11-25
Have you tried messing with the white balance?

If people are doing batch converting  and the colors come out wrong, my bet is that the default modification values the batch convert program is using are not appropriate for the pictures that are being converted.

The same thing that is described in the first post can be seen when using ufraw. It uses some default modification values based on the last time you used it or something, and they might not be right for the pictures you are using. Thus the picture could come out with a large green tint to it.

---

### Post by xadder on 2009-11-25
The problems start before I convert anything - just using e.g. "ufraw myfile.CR2". This uses the "Camera WB" by default, and even I try other WB options (auto, daylight) they are all green.

ufraw worked very well before I tried the new ppa, so I assume there is some simple setting to get the colours correct again, or just a bug in the new system. (I wrote to the ppa developer, Pascal de Bruijn) and will post back here if I get a reply.

---

### Post by Dougie187 on 2009-11-25
Do you think you could post examples? Like, the raw image, and then the converted one that is green? Then I could see if I could reproduce it for you?

---

### Post by xadder on 2009-12-03
Sorry for the slow response.Pascal de Bruijn has been offering some tips, but in the end it looks like a bug in ufraw 0.17 with regard to sRAW files. Full-size RAW files were handled fine. The standard karmic ufraw 0.15 seems okay for both RAW and sRAW.

I've submitted a bug report on source-forge.

---

### Post by xadder on 2009-12-04
Update: the ufraw CVS was updated earlier today to fix this bug. I will wait for Pascal de Bruijn's repository to be updated and then test again - likely on Monday. Looks like the problem should be solved though - fast work by the developers!

---

### Post by xadder on 2009-12-09
Yep, the updates fix the problem with sRAW files. ufraw (ppa version) runs great now.

---

