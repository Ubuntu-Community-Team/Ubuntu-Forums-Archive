---
title: "Udev and snapstream firefly remote"
date: 2013-09-10
forum: Mythbuntu
---

### Post by williammanda on 2013-09-10
I have been experimenting with Mythtv on other desktop environments and have run into an issue with my remote. I was trying out Ubuntu gnome 13.10 and I noticed that the remote automatically get setup as a keyboard by udev and stays this way after loading Mythtv and lirc. This wouldn't be bad if I didn't have 2 working mythv setups each with a snapstream firefly remote. The current working mythtv setups (Ubuntu 12.10) have the remotes setup on different channel ID's so they don't conflict with each other. When I loaded Ubuntu gnome 13.10, replacing one of the working mythtv setups, the remote on the other mythtv setup with Ubuntu 12.10 can control the Ubuntu gnome 13.10 as a keyboard, not using lirc but via udev. The Mythtv Ubuntu 12.10 setup doesn't show any udev assignment in xorg.conf log but it does in the Ubuntu 13.10. Is there a way to get the Ubuntu 13.10 setup to function like the Ubuntu 12.10? Or can I manipulate the key assignment for the remote assigned as a keyboard in Ubuntu 13.10? I have tried out ir-keytable and it will work but it can't handle assigning a channel ID. So basically I still have two different remotes that control one mythtv setup.

---

