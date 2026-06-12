---
title: "MythTV - Completely removed but /home/MythTV remains"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by tim_wright on 2007-10-29
I installed MythTV inly to realise that it wasn't needed so I decided to remove it. I removed all MythTV related packages in Synaptic with the "Completely remove" feature. 

However, after I rebooted, the directory /home/MythTV is still there and contains the directory structure although without any files. When I try to delete it I get an error message saying:

[B]
Error while moving[/B]
Cannot move "/home/mythtv" to the Deleted Items folder because you do not have permissions to change it or its parent folder.

Can anyone provide some assistance to helping me remove this?

Thanks,
Tim

---

### Post by daengbo on 2007-10-29
Mythtv uses another user (mythtv) to run under. You can't delete another user's files. Make sense?

Therefore, you need to delete the files while you are the administrator.

Click ALT-F2 and type gksu.
Hit Enter

A dialog will ask you what program to run. Type:
nautilus --no-desktop
Run as root and hit Enter

You will be presented with a file browser as administrator. THIS IS VERY DANGEROUS. Delete the /home/mythtv folder, being very careful while you do it and closing the file browser immediately afterwards.

Best of luck

Daeng

---

### Post by tim_wright on 2007-10-29
Thanks very much! Your a star#1

Tim

---

