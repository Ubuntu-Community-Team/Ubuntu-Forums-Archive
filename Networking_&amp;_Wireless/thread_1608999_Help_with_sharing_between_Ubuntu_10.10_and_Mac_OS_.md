---
title: "Help with sharing between Ubuntu 10.10 and Mac OS 10.6"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by Shake 'n' Bake on 2010-10-29
I've configured my Ubuntu box following [this]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#avahi1") guide.  It's working just fine, except for one problem.  When I connect to the Ubuntu machine from my Mac, it automatically mounts "Home Directory" rather than giving me a list of items to choose from.  I've also got a few shared folders.  One is on the boot drive, while the other is on a secondary hard drive.  And I know almost nothing about the command line.  If I did, I'd probably have fixed the problem by now.

Thanks for any help you can give.

---

### Post by eagleapex on 2010-11-07
I have same problem. I want to get at an attached drive.

Edit;
Oh, so I need to add directories I want to the netatalk file:

sudo gedit /etc/netatalk/AppleVolumes.default

done.

---

### Post by Shake 'n' Bake on 2010-11-07
I found out that I mistook the "username1,username2" part to mean the users on the Mac.  I fixed it by typing in the usernames on the Ubuntu machine.

---

