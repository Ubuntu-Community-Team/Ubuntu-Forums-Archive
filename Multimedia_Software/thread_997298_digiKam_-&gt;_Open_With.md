---
title: "digiKam -&gt; Open With"
date: 2008-11-29
forum: Multimedia Software
---

### Post by Kalrog on 2008-11-29
I use digiKam for my photo management app and have been very happy with it except for one little issue that could make it just so much better for my experience and photo editing workflow.  I want to have the option to open pictures with GIMP if they need some more intensive editing than I like to do in digiKam.  What this would usually mean is that I could right click on the image and select Open With -> GIMP.  The strange thing is that I have that option for jpeg files, but not for my ORF (Olympus RAW) files.  I do have Krita as an option, but that isn't what I want to use.  I am able to open those ORF files with GIMP manually, but not through the digiKam interface.  Any thoughts?

Running Kubuntu 8.10

---

### Post by Kalrog on 2008-11-30
Anybody?  Am I crazy here (don't answer that).

---

### Post by RytmenPinnen on 2008-11-30
hmm, I have never done what you described but maybe you could try setting gimp to be default application for your orf files. And that would be done in system settings -> file associations

---

### Post by Kalrog on 2008-11-30
That was my first thought, and there was already an entry x-olympus-orf with GIMP and UFRaw (in that order) as the associated applications.  And just those.

I added a new orf entry (closer to the jpeg entry) and associated it with GIMP and that doesn't appear to have changed anything.

---

### Post by Kalrog on 2008-12-02
Final bump - anyone?

---

### Post by chili555 on 2008-12-03
I open my RAW files with Ufraw. After a bit of adjustment, I send them to the GIMP. There ia a button on the lower right of Ufraw. Then I can make whatever adjustments I want in the GIMP and save.

I don't shoot Olympus, so I have never tried an .orf, but it looks like it works: [http://ufraw.sourceforge.net/wiki/Olympus](http://ufraw.sourceforge.net/wiki/Olympus)

---

### Post by lui456 on 2008-12-07
I open my RAW files with UFraw and adjust them basically, after that UFraw sends the images automatically to gimp. 

On Ubuntu 8.04 and digikam 0.9.3 I have to setup the file association in Konqueror as follows: *.cr2 --> gimp.

Ubuntu 8.10 comes with digikam 0.9.4 and the file association does not work correctly. I am able to open RAW-files, but for Gimp-files the "open with" dialog is empty.

I think this is a bug in Digikam.

---

### Post by Kalrog on 2008-12-08
Thanks for the info!  I did search the bug list for digiKam, but I sure might have missed something.  Glad to know that I am not the only one this is happening to.

---

### Post by timcredible on 2008-12-08
i think you have to define .orf files in kde.  looking for how to do that now because i want to do that with .xcf files.  if i remember before, we have to use kcontrol maybe....

---

### Post by Kalrog on 2008-12-08
That was already done for me - and GIMP is already associated with ORF files when I open them through dolphin.  Just not through digiKam.  But I did check that and I'll post directions tonight with how I did it.  I'm at work now and don't have it handy (sorry).

---

### Post by timcredible on 2008-12-08
i just went into konqueror and .xcf files were already associated with gimp, yet, like you say, nothing shows up in digikam.  great, looks like kde4 has really messed things up - i have no kooka anymore either since kde4.

---

### Post by Kalrog on 2008-12-08
Well, so much for me being able to help.  Sorry.

I'm guessing you can open with through konqueror or dolphin (just like I can) but not through digiKam?

---

### Post by timcredible on 2008-12-09
> **Kalrog said:**
> 
I'm guessing you can open with through konqueror or dolphin (just like I can) but not through digiKam?
i use gnome, so i can open it just fine through nautilus, but i'm used to using digikam to manage photos because it's so nice to use.  i'll probably keep fiddling with it for a few more days.

---

