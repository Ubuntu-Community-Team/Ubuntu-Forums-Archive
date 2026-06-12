---
title: "Problem setting up IVTV"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by Nesagwa on 2006-07-04
[http://ivtvdriver.org/index.php/Howto:Ubuntu](http://ivtvdriver.org/index.php/Howto:Ubuntu)

Ive followed all of this and got it all installed and everything, but Im having a problem with the firmware.

I tried following the steps provided to make it work, but after "wget"ing both of the firmware zip files, nothing worked.

Just need to get these things right and my IVTV setup will be good to go, but Im not sure what to do now.

EDIT:

I have a Hauppauge PVR-150.

/lib/hotplug doesnt exist so where exactly do I put the firmware files :cry:

---

### Post by Titus A Duxass on 2006-07-04
There is a how-to on the forum for MythTV with Dapper.
Just follow the how-to until you complete the ivtv installation, that should get you on the right track.

---

### Post by Nesagwa on 2006-07-04
The how-to shows the exact same steps that are screwing me up and listing non-existent directories.

:-?

---

### Post by Titus A Duxass on 2006-07-04
Have you followed the how-to line by line?

It sounds like you have not installed the kernel headers or kernel source.

Do not just simply cut and paste the commands, enter the first one to letters of the command and then hit tab.

For example:

enter "cd /e" and then press tab will complete the line to "cd /etc".  If you do this for all the entries then the commands are adapted to your system.

---

