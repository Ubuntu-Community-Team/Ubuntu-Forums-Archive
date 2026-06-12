---
title: "Cant Edit Raw files with any program"
date: 2010-04-15
forum: Multimedia Software
---

### Post by Mostly.Harmless on 2010-04-15
**Raw files come up as weird bars in all Editor programs**             
                                                                Hey guys,

I haven't put this in the forums for any of the separate programs,  because im having the same problem in all of them, im thinking maybe its  a problem elsewhere?

I recently got a Canon DSLR. It can save in Raw format, I use this  function. Canons Raw format is "Whatever.CR2"

F spot viewer and all editor programs see then and 'preview' them with  no problem. The images appear to have no problem until you load them  into GIMP (with UFRAW) UFRAW standalone, RAWStudio etc.

They load, but only as a small vertical rectangle. Often very purple in  colour. 

I thought maybe it was something wrong with just the way it looked, so I  just loaded one, went save as (a jpeg) and then loaded it up, it loaded  as a small picture of the same purple-haze bar.

Have I done something wrong? I googled it, downloaded UFRaw, even Ubuntu  studio, same problem before and after studio installation. All these  programs claim to read raw images.

Just as an example, In RawStudio:

I load up the folder of raw images. I can see all the images clearly  with no problems in the preview slider up top. I can scroll through them  and see them all no problem. When I click on one, it loads in the  editing box as some weird bar (always vertical in orientation) often  faintly resembling part of the photo but with seriously acid trip  colours. Eg massive purple hazes, green everything etc.


NB: If some can give me basic instructions I can try and upload a screenshot to show you what I mean


cheers for any help

---

### Post by msknight on 2010-04-18
I'm having the same issue here.

Previously, on Kubuntu 9.10, in digiKam, I would right click on my RAW file, selection open in GIMP. Gimp would automatically load ufraw and when I'd finished adjusting the RAW file, it would simply appear in Gimp.

Yesterday I over-wrote the Kubuntu install with Ubuntu 9.10 64 bit (I deliberately kept my home directories) and the following happens...

In digiKam, if I try to open the raw in GIMP, it just wants to load some tiff files.

If I instead try to open in ufraw, then all goes well until I hit the "gimp" button on the bottom right ... Gimp comes up but complains with the following message...

"Opening '/tmp/IMGP4831.PEF_EDPABV.ufraw' failed: Could not open '/tmp/IMGP4831.PEF_EDPABV.ufraw' for reading: Unknown reason"

I have checked that it is not a rights issue. ufraw can put the temp file there, but Gimp just can't import it for some reason. It is as if Gimp has forgotten that ufraw exists.

I've tried removing and installing the gimp and ufraw packages, but no success.

Gimp is version 2.6.7 from the repositories.
Ufraw is version 0.15.

---

### Post by msknight on 2010-04-18
Mostly ... to get you over the hump waiting while someone comes to our rescue ... install the digikam package. It is capable of handling a number of actions.

---

### Post by msknight on 2010-04-18
Aha - try loading the package ... gimp-ufraw and see if that works.

---

### Post by goldshirt9 on 2010-04-18
i have or had a similar problem with sony raw files.
i open the raw image with rawstudio and then import to gimp for further 
alterations

---

