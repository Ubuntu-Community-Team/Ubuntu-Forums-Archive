---
title: "Two Questions LVM related, HID Remote related"
date: 2010-03-09
forum: Mythbuntu
---

### Post by mr. 100prozent on 2010-03-09
Hello, i am using mythbuntu 9.10 on my server and seperate frontend. On my server i have three 1TB Harddisks konfigured as LVM with a XFS Filesystem for data. 
My first question is: i want to take out one harddisk and use it as a backup disk for my iso images. The other two will stay in the server. With pvmove /dev/sdc i can move the data from the third harddisk and with vgreduce vg /dev/sdc i can reduce the volume group to remove the hd. This sounds all very easy and there are some excellent LV Howtos on the web, but i am concerned about the filesystem because xfs can't be made smaller but if i remove a whole disk isn't that a problem?
Second question: i want to use a remote control which was bundled with a htpc case (MS-Tech MC-1200) which will be found as HID device and works out of the box, but some keys send CTRL+Key some send CTRL+SHIFT+Key in one instance CTRL+SHIFT+P is Play and CTRL+P is Pause. How can i map these keys to something mere useful like "p" and "STRG+v" for example? I read a lot about lirc and xmodmap but the problem is i just want to change the mapping from this particular device so xmodmap wont do it. With lirc i don't know if this is possible (event or input based mapping from STRG+SHIFT+Key to something different). For now i am using gizmod but i dont know much about python and i am not sure if i can catch an event like STRG+key there. Any ideas how to manage this or any thoughts with which tool this is gonna work?
Appreciate the help.
Thanks

---

