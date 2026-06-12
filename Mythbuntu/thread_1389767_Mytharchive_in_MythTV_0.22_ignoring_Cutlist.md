---
title: "Mytharchive in MythTV 0.22 ignoring Cutlist"
date: 2010-01-24
forum: Mythbuntu
---

### Post by ChiA_UK on 2010-01-24
Hello.
I've been dabbling with MythTv and Mythbuntu for the past six months now, in the hope it will actually be a useful media centre.  My resuts so far have been mixed - any important shows I've had to record with an off the shelf pvr for insurance.

I recently made the mistake of upgrading my satisfactorily functional 9.04 system to 9.10 Mythbuntu.
My key problem is that I can't see how Mytharchive can be told in MythTV to honour the cutlist.  When a disk is created it includes the commercials, even when there's a cutlist available.

How do I solve this problem?

---

### Post by teet on 2010-01-24
I've always done it in a two step process.  After I edit the video file and ensure the cutlist is like I want it, I transcode the file (which cuts out the commercials).  Since I have a PVR-150 and record everything at DVD quality, I just do a lossless transcode which significantly cuts down on processing time.  Then I use mytharchive to burn my already commercial free file.

I wasn't aware mytharchive could (or at least used to be able to) do the commercial cutting.

-teet

---

### Post by ChiA_UK on 2010-01-25
Yes, under Mythbuntu 9.04 it was possible to choose an option "Use cutlist" whilst going through the Create DVD option within MythTV.  I can't find that option under 9.10.

My huge criticism of MythTV 0.22 is that the menus and functionality have been changed yet nobody has bothered to up[date the manuals and instructions!!!  One has to learn by trial and error what each key does and a user is left wondering whether there's a bug or a feature has been removed.

I had hoped for a leave and forget PVR that mum and dad could use.:(:(:confused::confused:
One the plus side I have learnt a lot about Linux!  :D:):P

---

### Post by teet on 2010-01-25
Yeah I know what you mean.  FWIW I built my parents a myth box several years ago and they absolutely love it.  They can do all the basic things, but burning a dvd of a recording is still way too complicated.  There should just be a simple option when you hit "i" in the watch recordings menu list where it lets you "burn to dvd" and it will create an autoplay dvd w/o menus of that one show.  There could be a second option in there to "burn dvd using cutlist" or something of that nature.

-teet

---

### Post by fredwong on 2010-01-27
Hi ChiA_UK,

I am putting together a DVD now from a couple of recordings as I type. I have never tried to create a DVD until now from the recordings. The "Use cutlist" is there (if it works ;)). After you have chosen the recordings to burn on the DVD, simply highlight/select the desired recordings and press "M" to bring up a menu. The option is there for you to use the cutlist. I hope it works because (as I said earlier) I have never done it before until now. I will let you know when I have the DVD created.

Cheers

> **ChiA_UK said:**
> Yes, under Mythbuntu 9.04 it was possible to choose an option "Use cutlist" whilst going through the Create DVD option within MythTV.  I can't find that option under 9.10.

My huge criticism of MythTV 0.22 is that the menus and functionality have been changed yet nobody has bothered to up[date the manuals and instructions!!!  One has to learn by trial and error what each key does and a user is left wondering whether there's a bug or a feature has been removed.

I had hoped for a leave and forget PVR that mum and dad could use.:(:(:confused::confused:
One the plus side I have learnt a lot about Linux!  :D:):P

---

### Post by ChiA_UK on 2010-02-01
I've got here a screenshot of what options are available when I press M:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=145677&stc=1&d=1265068057[/IMG]

I think I will try reinstalling MythTV 0.22 and Mythbuntu 9.10 to see if it is an installation issue.
I need to work out how to do a safe backup of the recording database first!

I will also try some other themes just in case it's a problem with this particular theme.

---

### Post by fredwong on 2010-02-02
As I said in my earlier post. I had never done this before until the other so I don't know how it behaved before. In Mythbuntu 9.10, to see the "Use cut list" option you need edit the recording and then you will be able to see the "Use cut list" option in the screenshot you provided.

Cheers


> **ChiA_UK said:**
> I've got here a screenshot of what options are available when I press M:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=145677&stc=1&d=1265068057[/IMG]

I think I will try reinstalling MythTV 0.22 and Mythbuntu 9.10 to see if it is an installation issue.
I need to work out how to do a safe backup of the recording database first!

I will also try some other themes just in case it's a problem with this particular theme.

---

### Post by ChiA_UK on 2010-03-07
Hello.  I figured out what the problem is.  When I was using 9.04 it would automatically enable a cutlist for me.  Since upgrading to 9.10 I now have to first edit the recording then press Z to enable the cutlist before then moving to archive the file and select the Use Cutlist option.

There are a lot of problems with this 9.10.

---

### Post by Bernmeister on 2010-05-24
I am having a similar issue but using Mythbuntu 9.10 upgraded to MythTV 0.23-fixes.

I have a cutlist and have transcoded, but in the archive screen, I do not see the menu items you mention (just Remove Item and Cancel).

Have you tried archive in MythTV 0.23?

---

