---
title: "I need the current stable release of GIMP"
date: 2021-10-07
forum: Multimedia Software
---

### Post by jmichaels29 on 2021-10-07
The current stable release of GIMP is 2.10.28 (2021-09-14).


I need to upgrade/install the latest stable version of Gimp which has a fix in it for my camera model.  However, the Ubuntu software center only offers 2.10.24 & the Synaptic Package Manager has even an older version (18).

I realize the current stable release was just released - if I decide to just wait, about how long will it be before 2.10.28 shows up in the Ubuntu Software center (or Synaptic)...

Otherwise, how do I force a Gimp upgrade to 2.10.28 please

I apologize for the font - couldn't figure out how to default it back to normal here...

---

### Post by Bashing-om on 2021-10-07
jmichaels29: hello :) 

There are PPAs that provide the bleeding edge and beyond,
However, be aware:
> 
 A Personal Package Archive (PPA) can provide alternate software not normally available in the offical Ubuntu 
               repositories - ...  WARNING: PPAs are unsupported 
               third-party packages, and you use them at your own risk. 

that said please see:
[https://launchpad.net/~savoury1/+archive/ubuntu/gimp](https://launchpad.net/~savoury1/+archive/ubuntu/gimp)
( 2.10.28-0ubuntu1~21.04.sav0)
as once instance of support for gimp.


[INDENT]hope this helps
[/INDENT]

---

### Post by Dennis N on 2021-10-07
I use the Flatpak version of Gimp. It's always the newest version. It's 2.10.28 right now.

---

### Post by jmichaels29 on 2021-10-07
Considering the warnings, about how long does it generally take for the stable version of Gimp (or any program) to show up in the Ubuntu repositories ?

---

### Post by jmichaels29 on 2021-10-07
> **Dennis N said:**
> I use the Flatpak version of Gimp. It's always the newest version. It's 2.10.28 right now.

Yea, I ran the beta version, which installs via flatpak, I used that beta version of Gimp for some time.  What I need it to do is not time sensitive, so I'm curious as to how long it will take for the stable version to show up in the Ubuntu repository before I install the flatpak stable or beta version....  Gimp is the only thing I've ever installed via flatpak, and if I can keep with one install method I'd prefer to stick with it (Ubuntu repository), though no big deal...   I do like flatpak though....

---

### Post by Bashing-om on 2021-10-07
jmichaels29 ; Humm --- 

does not.
> 
Packages in Ubuntu may not be the latest. Ubuntu aims for stability, so "latest" may not be a good idea. 
               Post-release updates are only considered if they are fixes for security vulnerabilities, high impact bug fixes, 
               or unintrusive bug fixes with substantial benefit.

see too:
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

for the reasons why.

-if it ain't broke, do not fix-

---

### Post by jmichaels29 on 2021-10-07
> **Bashing-om said:**
> j

see too:

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

for the reasons why.

-if it ain't broke, do not fix-


Well, in my case, it pretty much is "broke" as the only way that Gimp will retain EXIF data is if I overwrite the file after I've done my basic post processing.  If I choose to "save" or "save as," then it saves the file in Gimps .xcf file format.  If I choose to "export as" then it will save as .jpg; however, even though the box is checked to retain the EXIF data, the EXIF data is indeed *not* retained.  

I can duplicate the original file, for posterity, and overwrite files to retain EXIF until a stable is available in the repository.     

.xcf files are fairly useless to share photos to your flickr page or via email or any other way on the net & I need EXIF data, as many photo contests I enter require full EXIF data for the photo challenge host to examine.

This failure to retain EXIF was a problem for Canon users, but now it is apparent it is a problem for Ricoh/Pentax users also (without the stable update that is)...

---

### Post by Dennis N on 2021-10-07
Gimp as a Flatpak is only released as the latest stable version. If you had a beta of Gimp, it was the snap package which does offer non-stable channels. 
The Ubuntu repository as you said offers 2.10.18 and it's possible if might be updated for security reasons, but not just for features. They don't do that.
The 2.10.24 version you mention I believe is a snap version.
Ubuntu Software does not show or manage Flatpaks -  only .deb and snap packages.
Gnome Software can show and manage .debs, snaps and Flatpaks. Flatpak management requires installation of an extra plugin.

---

### Post by T6&amp;sfpER35% on 2021-10-08
go to your GIMP app , go to <help> , <about> and <check for new versions>
mine says 2.10.28 is available for download (looks like a Flatpak)

---

