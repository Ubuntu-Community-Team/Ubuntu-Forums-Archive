---
title: "Jamendo problems"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by SteinbergerNate on 2007-11-22
Ok, so I'm REALLY behind the times. I just discovered the Jamendo plugin for Rhythmbox today. The only problem is that when I go to the selection for Jamendo on the side bar I only ever the the intro screen explaining what Jamendo is and all. It also has the search bar at the top but does nothing when I try to actually do a search. I've tried restarting Rhythmbox a few times with no luck. I haven't restarted the computer yet but I'm about to try that. 

I'm running Feisty.

---

### Post by VosaxAlo on 2007-12-01
same issue here.

I have installed Gutsy from scratch, and for a while Jamendo plugin has well functioned.
But now I have the same issue. Only the "main page of Jamendo" and no catalog displayed.
Perhaps a bug?

---

### Post by crun on 2007-12-09
It is a bug - see Launchpad details here: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/158941](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/158941)

The bug is fixed in the latest Rhythmbox release, but it might be some time before it makes it into the repositories.

In the meantime, you can fix the problem yourself, but be careful, it requires root-rights and you have to delete the compiled version of the Jamendo plugin. Here goes.

First, remove the compiled Jamedo Python plugin:

[INDENT]```
sudo rm -vi /usr/lib/rhythmbox/plugins/jamendo/JamendoSource.pyc
```[/INDENT]

Answer "y" to remove the file.

Now go here to see the source code with the patch in place: [http://svn.gnome.org/viewvc/rhythmbox/trunk/plugins/jamendo/jamendo/JamendoSource.py?revision=5426&view=markup](http://svn.gnome.org/viewvc/rhythmbox/trunk/plugins/jamendo/jamendo/JamendoSource.py?revision=5426&view=markup)

Look for these lines:

[INDENT]```

				trackno = int(track['trackno'])
				if trackno >= 0:
					self.__db.set(entry, rhythmdb.PROP_TRACK_NUMBER, trackno)

```[/INDENT]

copy all three (or just use the code above).

Edit your Jamendo plugin:

[INDENT]```
sudo gedit /usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py
```[/INDENT]

Look for this line (around line number 332):

[INDENT]```
self.__db.set(entry, rhythmdb.PROP_TRACK_NUMBER, int(track['trackno']))
```[/INDENT]

Delete it, and copy the three lines from the patch in its place. Make sure the first line has the same indentation as the line before it, and that the third line has one indentation extra. If this is not correct, the plugin will give an error when you select it. Finally, save the file and close Gedit.

Now run Rhytmbox as root and make sure the Jamendo plugin is selected in order to compile it (if it displays an error, you may have to check your edited code).

[INDENT]```
sudo rhythmbox
```[/INDENT]

Now remove the downloaded Jamendo library from your home folder:

[INDENT]```
rm -vi ~/.gnome2/rhythmbox/jamendo/*
```[/INDENT]

Finally, start Rhythmbox as a normal user - Jamendo should now work.

---

### Post by kubuntux on 2008-02-01
Thanks crun, it worked just well! :)

:guitar:

---

### Post by AliTabuger7 on 2008-03-10
Thanks!

There were a few things in there that we didn't need to know or do, like the "sudo rhythmbox"

I also didn't have to do that first step, and I believe you that theres a patch out there, and didn't go look at the source myself.

---

