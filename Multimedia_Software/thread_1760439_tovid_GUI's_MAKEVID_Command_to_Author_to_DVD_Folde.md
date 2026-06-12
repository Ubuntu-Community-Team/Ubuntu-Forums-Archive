---
title: "tovid GUI's MAKEVID Command to Author to DVD Folder Fails After Upgrade to 11.04"
date: 2011-05-16
forum: Multimedia Software
---

### Post by OzzyFrank on 2011-05-16
I just upgraded to Natty, and my tovid GUI isn't working as it did before, in that it can still encode the videos to DVD format .mpeg, but the next part of the process, authoring to a DVD title in a VIDEO_TS folder, no longer works.

All I get is:

[COLOR="Indigo"]makedvd encountered an error during the DVD creation process:
Could not create the DVD-Video disc structure in /tmp/Untitled_disc.
Leaving /tmp/Untitled_disc for inspection.
See if anything in the above output helps you diagnose the
problem, and please file a bug report at tovid.org (_not_
the dvdauthor list) containing the above output.
Sorry for the inconvenience![/COLOR]

I've tried this with a couple of different vids in different formats, but neither work (or should I say, they're encoded just fine, but no title is created that I can then burn), and as I said, this was not a problem a few hours ago before upgrading to 11.04.

Any ideas how I can fix this? Please note I am not asking how to get it to burn the end result to disc once authoring is finished, as I never got that to work, and just got used to burning the resulting VIDEO_TS folder with K3b. What I am asking is why this fails to finish the authoring (the title's main .ifo and .bup are not created, if that is any help), and how to rectify this. Cheers

---

### Post by OzzyFrank on 2011-05-17
The last bit before it fails says this:
[B][COLOR="Red"]
ERR:  no video format specified for VMGM[/COLOR][/B]

This is the first time I have ever seen this. The only other times before the upgrade that I would ever have a project fail to be authored to DVD was due to characters it didn't like in the filename, and it would actually tell me that it will probably happen before the encoding even starts. I have no idea what this VMGM is, but obviously that's what's stopping the authoring, as each attempt has produced the same error since the upgrade.

---

### Post by mc4man on 2011-05-17
What I might try is downgrading dvdauthor to the maverick version 
(download package then sudo dpkg -i /path/to/dvdauthorpackagagename
[http://packages.ubuntu.com/maverick/dvdauthor](http://packages.ubuntu.com/maverick/dvdauthor)

Ex.
 sudo dpkg -i /home/doug/Downloads/dvdauthor_0.6.18-1build1_i386.deb

If it then can create proper a VIDEO_TS.VOB and VIDEO_TS.IFO   then file a bug against tovid

---

### Post by OzzyFrank on 2011-06-05
If there is something wrong with **dvdadauthor**, making **tovidgui** fail when authoring the encoded output, would it also affect other programs, like **DeVeDe**?

I ask this because purging my system of **dvdauthor** will also remove programs like **DeVeDe**, which runs absolutely fine.

---

### Post by mc4man on 2011-06-05
> I ask this because purging my system of dvdauthor 
Didn't suggest removing anything, just downgrading dvdauthor to the previous version - 0.6.18
If you were to check the changelogs for tovid, devede and dvdauthor the only one that has been updated in year or so is dvdauthor, tovid is basically ancient (as far as ubuntu packages - 0.31

There is no reason to think devede wouldn't work with the 0.6.18 dvdauthor, maybe tovid will, maybe it's dead 
You could also try the last release of tovid - 0.33,  it may work, it may not,  (almost a year old.
You're best bet otherwise as far as a bug could be launchpad instead of code.google whatever (if anyone cares any more ...

---

### Post by OzzyFrank on 2011-06-05
Ok, OK, forgive my ignorance, but how do you downgrade an existing package? I always assumed you had to remove them and then install an earlier version. As for **tovidGUI**, I already removed that (0.33) and reinstalled the one from the repos, to no avail, but that is without any downgrading of **dvdauthor**.

---

### Post by OzzyFrank on 2011-06-05
Don't worry - I just ran the **dpkg** command and it is downgrading. Been using Ubuntu since 2006 and only just realised you could do that! Mind you, every time I saw forum posts talking about downgrading packages, it was via removal of the current version, and installation of the older version (not to mention directly running .deb installers always would complain that it couldn't be done, because an earlier version exists). So it has now replaced 0.7.0-1 with dvdauthor_0.6.18-1build1_amd64, so will see how that goes.

---

### Post by OzzyFrank on 2011-06-05
"Done authoring the disc"

Yippee! So downgrading **dvdauthor** worked, but since I also reinstalled an earlier version of **tovidgui**, I am not sure if that is a factor too. I only went to the latest version (0.33) last time I had problems (which it didn't solve, but a fresh system install did), so I might upgrade it later and see how that goes.

Thanks for your help. It was also very enlightening that **dpkg -i** is not the same as manually running a .deb installer (ie: double-clicking it and letting gdebi or the Ubuntu Software Center handle it), which I always assumed was the case.

---

### Post by OzzyFrank on 2011-06-05
Funny. I have one update available, and guess what it is? Looks like I better lock the version of **dvdauthor**, for now at least, hehe.

---

### Post by mc4man on 2011-06-05
> **OzzyFrank said:**
> "Done authoring the disc"

 It was also very enlightening that **dpkg -i** is not the same as manually running a .deb installer (ie: double-clicking it and letting gdebi or the Ubuntu Software Center handle it), which I always assumed was the case.

You'll find that sudo dpkg -i /path/to/a/deb is very useful at times
You can also downgrade or install, upgrade non repo package sets by putting _all the required .debs that aren't already installed_ in a folder, cd'ing to that folder and 
sudo dpkg -i *.deb

As far as tovid - looking at the various pages (wiki, code.google) it appears to not be maintained any more though I could be misreading things

---

