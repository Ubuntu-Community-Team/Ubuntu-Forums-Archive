---
title: "Attachment File from Network"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by alishad on 2006-06-08
I am trying to attach a file to an email that is located on a network share.  I have added the shares from the Places, Network servers option and they do show on the desktop.  I set the permissions and can access the files.  What do I need to do to attach the file to an email, other than copy the file to the hard drive, etc.

---

### Post by mindwarp on 2006-06-09
This isn't really a "network" issue so much as a general software issue.  It would help if you posted what email client you are using to send the message.

---

### Post by alishad on 2006-06-09
I have tried Seamonkey, Thunderbird and Evolution.

---

### Post by mindwarp on 2006-06-09
What error message do you get once the file is attached and you hit send?

---

### Post by alishad on 2006-06-11
It doesn't give me an error message...it won't attach.  When I hit attach and try to find the network share, you can't see the share to attach the file.

---

### Post by mindwarp on 2006-06-11
Ah, well if the network server's address doesnt work when you type it in (a box will pop up when you start typing, just put in smb:// whatever), you can also mount the share and then choose where you mounted it from the email client

---

### Post by JallenDragonhide on 2007-02-27
Dug this up from a search for the solution.

This is a windows environment issue.  What the user is describing is that Thunderbird, Evo, and most other email clients do not have a space to put in smb:// address.  The way the "Places" works is it seems to mount these smb shares and keep it accessible only within the Nautilus File manager.  There doesn't seem to be a path in the filesystem I can find.

The email clients, and most all apps actually, only looks in the filesystem for the mounted network share.  And well, if the "mount" is only visible within the Nautilus File manager, it's not going to show up....  Frustrating.

One solution is to simply mount them via command line- I am hoping for a more newbie friendly solution to tell our Ubuntu users we support.

---

### Post by CrazyCatLady on 2008-02-13
ok, so for us newbies... how does one mount the network file via a command line?  I just happen to come across this post as I am having the same problem attaching files to emails in Thunderbird from a network file share.

---

### Post by jesselee on 2008-06-04
I think this is a confirmed bug :

[https://bugs.launchpad.net/ubuntu/+source/mozilla-thunderbird/+bug/105088](https://bugs.launchpad.net/ubuntu/+source/mozilla-thunderbird/+bug/105088)

i'm facing the same problem as well...but don't think there's any solution for now, at least till they solve the bug or something..

---

