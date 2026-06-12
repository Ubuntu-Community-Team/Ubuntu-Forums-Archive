---
title: "k3b wont verify"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by Archmage on 2006-10-30
k3b seems to be the only cd-burning program that support verifing of the just burned CD. Therefore I did use it in Dapper, although I'm using Ubuntu (and therefore the Gnome-Desktop).

Unfortunatly after upgrading to Edgy the verfing seems to be broken for files. It will stop the verifing after 50% of the verifed file and display the error message "could not find the file [filename]".

I can verife ISO-image just fine.

I even installed Edgy on a new partition and notice that it still can't verify the data. Dapper used to work just fine.

---

### Post by ut2k2 on 2006-11-10
I have the same problem too. k3b verified just fine in dapper, but not for "Data Project" in edgy. Right now, I have to manually verify after burning using kdiff3, which is rather inconvenient.

However, k3b does seem to verify OK if burning from an ISO image ...

---

### Post by GarBhaD on 2006-11-10
I have the same problem with k3b. Indeed, it worked with dapper but it doesn't with edgy. This was a **very** convenient feature. Could someone give some help?

---

### Post by deeptingler on 2006-12-04
I'm subscribing to this thread too as had the exact same prob and I am now considering going back to dapper.  I record a disc, it gets halfway through verifying and then comes up with the error that "couldnt find file...."

In dapper it "just worked".....

I clean installed edgy yesterday and it managed to muck up my home partition and did not even recognise it was there.... I reinstalled last night which corrected this (clean install) but now the screensaver gives a blank screen!

I think its time to move back to good old reliable.....dapper! [-(

---

### Post by logos34 on 2006-12-04
Same prob here.  "Could not find file..." error -- in this case the very first file it checks after starting verify.

---

### Post by logos34 on 2006-12-05
Here's some recommended settings that seem to allow verify to work: 

(from [http://www.iam.ubc.ca/guides/CDWritingTips.html](http://www.iam.ubc.ca/guides/CDWritingTips.html)) 

# K3b

Burning Data CDs

   1. Choose Data CD and New Project from the main screen.
   2. Drag your files or directories from the upper panel to the Project panel below.
   3. Click the Burn icon in the menu panel. A pop-up dialog will appear where you can specify the desired options. The recommended settings are as follows:
          * Writing tab – Writing mode: choose Auto. This will automatically select Track-At-Once for a multisession CD or Disk-At-Once for a single-session CD.
          * Writing tab – Writing speed: choose Auto. This will automatically select the highest possible value for the given drive and medium type.
          * Options tab – On-the-fly: leave checked (default).
          * Options tab – Burnfree: leave checked (default).
          * Options tab – Remove Image: leave checked (default).
          * Advanced tab – Allow 103 character Joliet filenames: leave checked.
          * Advanced tab – Allow 31 character filenames: leave checked.
          * Advanced tab – Allow ~ and #: leave checked.
          * Advanced tab – Allow full ASCII charset: leave checked.
          * Advanced tab – Allow leading period: leave checked.
          * Advanced tab – Allow lowercase characters: leave checked.
          * Advanced tab – Allow max length filenames: leave checked.
          * Advanced tab – Allow multiple dots: leave checked.

TOP

*check 'Verify written data' and click 'Save user defaults' button

---

### Post by Qew on 2006-12-06
> **Archmage said:**
> k3b seems to be the only cd-burning program that support verifing of the just burned CD.

Actually, gcombust can do this, too. I had this issue a couple of years ago with K3b, and ended up installing gcombust to do data files with verification. It's not pretty, but it works. Suffice it to say, K3b in Dapper verifies fine.

---

### Post by deeptingler on 2006-12-07
logos 34, thanks for that Ive tried it and it worked first time!  much appreciated:-D

---

### Post by cocodude on 2007-02-08
It's only setting the "Allow lowercase characters in ISO9660 file names" that matters.

Ubuntu bug at [https://launchpad.net/ubuntu/+source/k3b/+bug/59089](https://launchpad.net/ubuntu/+source/k3b/+bug/59089) and upstream bug at [http://bugs.kde.org/show_bug.cgi?id=119544](http://bugs.kde.org/show_bug.cgi?id=119544)

Cocodude

---

### Post by abovett on 2007-02-22
> **cocodude said:**
> It's only setting the "Allow lowercase characters in ISO9660 file names" that matters.

Confirmed - fixed it for me. Thanks.

Andy B

---

### Post by Archmage on 2007-02-22
I did a upgrade to feisty - after this it is also verifing.

Thansk for the support/answers.

---

### Post by rsaavedra on 2008-07-14
> **cocodude said:**
> It's only setting the "Allow lowercase characters in ISO9660 file names" that matters.

Ubuntu bug at [https://launchpad.net/ubuntu/+source/k3b/+bug/59089](https://launchpad.net/ubuntu/+source/k3b/+bug/59089) and upstream bug at [http://bugs.kde.org/show_bug.cgi?id=119544](http://bugs.kde.org/show_bug.cgi?id=119544)

Cocodude

Resurrecting this thread because in my latest attempt K3B couldn't verify the burn.  Fortunately the burn was done correctly (it was a linux distro burn, I run check media and it was ok).

My version of K3B (the latest one I downloaded using Ubuntu  8.04.1's own Software Update Manager) doesn't seem to have any user selectable option to allow lowercase characters in ISO 9660.

So is this bug back, K3B not verifying on Ubuntu????

---

