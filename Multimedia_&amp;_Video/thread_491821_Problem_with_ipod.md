---
title: "Problem with ipod"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by Dailydog on 2007-07-04
Hi

I used gtkpod for a while and everything was fine. Then one day I got the message that it was impossible to mount the device. The error message went like this "unable to mount the selected volume - mount: special device /dev/sdc2 does not exist".

I googled for help and did some things (yes, I know not very smart and even dumber not to remember what they were).


[IMG]http://www.dailydog.be/pics/screenshot.png[/IMG] - ok, apparently I'm not able to insert an image either.

Anyway, the situation now is as follows:
The ipod is always visible in "places" (even when not attached to the box). To me that seems to say the device is mounted, but when I click on it the only thing I can do is 'mount' the device. When I try to mount it I get the same error message as before.

Sorry for this scatterbrain post. It's early in the morning and I'm frustrated. 

My actual question is, is there a place in Ubuntu where you can see and manage all mounted devices?

---

### Post by Analord on 2007-07-04
Yes, that place is called fstab.

it's a configuration file /etc/fstab which u edit and modify.

Be sure to make a backup.
Also, i would like to recommend using Yamipod, it's a descend client.
(not saying gtkpod isn't)

---

### Post by aussiedini on 2007-07-04
I found with mine that in feisty it is mounted as /media/IPOD (note in capitals). When i amended the mount point in gtkpod, it worked a treat from then on.

---

### Post by Dailydog on 2007-07-04
ok, my original problem is solved, but now I have a new one.

When I try to access my ipod I get an error message:


Cannot mount volume
Unable to mount the volume 'IPODLIES'

Details
mount-point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)


Any suggestions?

---

### Post by Brendt2 on 2007-09-01
I second Dailydog's problem!

---

### Post by nonewmsgs on 2007-09-17
heh i found this because i was having th esame problem and the answer isnt in fstab.  im not sure where it is stored but i can fix it with the GUI.

despite it not mounting it is semi-mounted.  if you goto places - computer - apple ipod music player is there!! right click on that and select properties and then click the last tab volume and under mount make sure it only says IPOD.

---

### Post by jhofmann on 2007-10-17
This might not be too late for somebody else. 

This happened to me.  Suddenly got error messages from the Gnome disk mounter, and it wouldn't mount the flash drive.  Since I had just been fiddling with the disk mounter properties, I knew where I had gone wrong, but I didn't know how to get back to that window to fix it.  You can't open "properties" unless the flash drive is mounted.

After a blessedly short period of aimless wandering, I discovered that if I mounted the flash drive the old fashioned way, with mount,  the flash drive's icon would appear on the gnome desktop, and I could reach the properties dialog box by right-clicking on it.  Then I could remove all the stuff I had written in the settings area and the gnome mounter would again function.

I hope this helps someone,  :)

Jim

---

