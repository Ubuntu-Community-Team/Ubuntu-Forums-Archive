---
title: "My woes installing Maverick as Virtualbox guest"
date: 2010-06-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by xeddog on 2010-06-13
I am running Ubuntu Linux 64-bit and for the last couple of days I have been fighting with Maverick as a guest VM in VirtualBox 3.2.2 and 3.2.4.  I started out by installing Maverick and the install seemed to go fine.  Then I tried doing updates and ran into one problem after another with all error messages pointing me in the direction of missing dependencies, broken packages, etc.  Not much else seemed to run right either.  Some applications just would not run at all, and all sorts of just plain weird stuff happened.

So I decided to do a clean install and start over.  In the install script I always selected the option to use the entire disk, wiping out what ever was already there.  I could not get the re-install to finish no matter what I did.  The install would find an error (no further information at all) and quit.

What I finally found out is that if I removed the vm from VirtualBox, and then also deleted the vdi, I could start over and get a good install.  At least it would look good.  I would still get one problem after another and all sorts of other things just would not function correctly.  Never exactly the same way twice.  But I kept reading that many people were having no issues with Maverick at all, so I kept at it.

I finally got to a point where I thought I had it.  Got Maverick installed and then all of the updates too.  Still a couple of oddities, but most things worked.  It is an alpha after all.  I then decided to reach for the brass ring and tried installing KDE.  Could not get it installed to save my butt.  Broken packages and missing dependencies again.  Son of a . . . .!!!!!  I decided to try the install one more time.

For this last install, I decided to try something a little different.  In all attempts before, when setting up the VM and configuring the virtual disk, I used the dynamically expanding disk option.  I have always used that option in the past and it has always worked for me.  But this last time I used the fixed size option.  Using that option, the install actually did work.  Everything that did not work before now worked as it should.  All applications worked as advertised, updates applied correctly, everything worked.  I was even able to install the KDE and xfce desktops as well.  All perfectly.

In days past [SIZE="3"]**SUN**[/SIZE] VirtualBox always worked for me, but this new [SIZE="3"]**ORACLE**[/SIZE] VirtualBox seems to have some serious problems with their dynamically expanding disk technology.  Based on my experiences, I strongly recommend using a fixed disk size until Oracle can get their act together.


xeddog

Machine:
Gigabyte EX58-UD3R motherboard
Intel I7-920 processor
6GB Ram
1TB Sata disk (there is also a 320 GB IDE drive, but was not used for Maverick)
nVidia 9500GT graphics
Everything else is using onboard integrated devices (sound, ethernet, etc.)

---

### Post by Merk42 on 2010-06-13
I've been using Virtualbox with Maverick the only issues I've had is it often starts out muted and defaulting to (non existent) wifi. Are you sure the download wasn't corrupt? Have you tried installing via a daily CD?

Also, while people haven't had problems so far, that doesn't mean there aren't any.  I remember back in Lucid development Virtualbox Additions wouldn't capture the mouse.  Sun/Oracle response was that since Lucid wasn't out yet, it wasn't something they officially supported.  Once 10.04 did get released though, mouse capture worked fine.

---

### Post by KdotJ on 2010-06-14
I have to say I've had no trouble what so ever with installing and using Maverick in virtualbox. I stall was perfect and updates run fine and no issues regarding dependancies. I agree with Merk42 about the idea of you having a bad download or burn

---

### Post by xeddog on 2010-06-14
Since all of the error messages I got (when I got one that had any information in it) pointed to corruption problems or disk problems, I thought I had a bad download or burn too.  I completely removed VB and started over by downloading 3.2.4 again but I still had the same types of problems.  Next I tried re-downloading the alpha and re-burning it.  No good.  I did the same with two different daily builds too.  Same problems.  I think the daily builds were 6/9 and 6/11.  May have been 6/10 and 6/11, but I tried two different daily builds.  All disks passed the integrity check too.
 
The last try (using the fixed disk option in VB) was using the same 6/11 daily build that I had so many problems with using the dynamic disk.  So after all of the things that I tried to get a good clean install, I am sure that I did not have bad downloads/burns of either VB or Maverick.  And yes, the 6/11 daily build was burned to a DVD because it did not fit on a CD.  So it will be a tough sell to convince me that the problems I experienced were not directly related to the dynamically expanding disk feature of VB.

I still don't know why I had the problems, but I am not surprised that others have not.  How many times to you read a thread about someone having a problem and the next several replies are "no problems here"?  I am kinda surprised that there hasn't been someone saying "yeah, that happened to me too."  I guess what it boils down to is if you have problems and have been using the dynamically expanding disk, try fixed to see if it works.  

xeddog

---

### Post by xebian on 2010-06-15
> **xeddog said:**
> Since all of the error messages I got (when I got one that had any information in it) pointed to corruption problems or disk problems, I thought I had a bad download or burn too.  I completely removed VB and started over by downloading 3.2.4 again but I still had the same types of problems.  Next I tried re-downloading the alpha and re-burning it.  No good.  I did the same with two different daily builds too.  Same problems.  I think the daily builds were 6/9 and 6/11.  May have been 6/10 and 6/11, but I tried two different daily builds.  All disks passed the integrity check too.
 
The last try (using the fixed disk option in VB) was using the same 6/11 daily build that I had so many problems with using the dynamic disk.  So after all of the things that I tried to get a good clean install, I am sure that I did not have bad downloads/burns of either VB or Maverick.  And yes, the 6/11 daily build was burned to a DVD because it did not fit on a CD.  So it will be a tough sell to convince me that the problems I experienced were not directly related to the dynamically expanding disk feature of VB.

I still don't know why I had the problems, but I am not surprised that others have not.  How many times to you read a thread about someone having a problem and the next several replies are "no problems here"?  I am kinda surprised that there hasn't been someone saying "yeah, that happened to me too."  I guess what it boils down to is if you have problems and have been using the dynamically expanding disk, try fixed to see if it works.  

xeddog

Looks like you are the only one having this 'problem'.  One thing  I see you are doing wrong is burning it to CD/DVD which is a waste of time and disks. VirtualBox accepts ISO images as it is.  Just assign the file.iso to the CD storage.

Another thing is why are you mixing gnome/kde/xfce in one VM?  VBox disk is cheap so make separate disk for each DE you want.  That way you can even run them at the same time.  You can install all DE in one but the experience is much better if you have them separate and some stuff doesn't play well together like sound.

Last, please don't be over dramatic.  It sounds like you don't like Oracle more than your 'problem'.

```
In days past [SIZE="3"]**SUN**[/SIZE] VirtualBox always worked for me, but this new [SIZE="3"]**ORACLE**[/SIZE] VirtualBox seems to have some serious problems with their dynamically expanding disk technology.  Based on my experiences, I strongly recommend using a fixed disk size until Oracle can get their act together.
```

---

