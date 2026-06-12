---
title: "VLC is taking over my system"
date: 2011-06-01
forum: Multimedia Software
---

### Post by juliancam on 2011-06-01
I am using VLC 1.1.9 on a Dell Latitude D600 with Ubuntu 11.04 and it is taking over my system. Every time I try to open a folder or a file VLC opens instead. I can dig down from "computer" to the folder or file but every other item from the "places" drop down menu will open VLC even if the folder is empty or contains non media files. I uninstalled VLC and the problem disappeared - naturally :) - but reappeared as soon as I reinstalled VLC. This doesn't happen on my AspireOne which also runs Ubuntu 11.04. Other than hardware,the only difference in the two machines that I can think might affect it is that the Dell has an upgraded version from Maverick whereas the netbook has a clean install of Naty. My only other thought was that is this an Intel / AMD  thing as the Aspire has the netbook standard intel gfx chipset whilst the D600 uses an old ATI 9000 series gfx chipset and I did have to install some AMD 2d libs to get it to run smoothly. However I think that might be grasping at straws. 

Any ideas

Julian

---

### Post by mc4man on 2011-06-01
You just need to delete the file mimeapps.list in  ~/.local/share/applications
(it could be edited but easier/better to just go ahead and delete - it will be recreated thru use of the r.click open with other application menu as need be.
Get there anyway you can, this will do so - in a terminal
```
 nautilus ~/.local/share/applications
```

---

### Post by juliancam on 2011-06-01
> **mc4man said:**
> You just need to delete the file mimeapps.list in  ~/.local/share/applications
(it could be edited but easier/better to just go ahead and delete - it will be recreated thru use of the r.click open with other application menu as need be.
Get there anyway you can, this will do so - in a terminal
```
 nautilus ~/.local/share/applications
```

Thanks This has solved the problem but on the way to solving it I have deleted ~/usr/share/applications/mimeinfo.cache. Can anyone tell me how bad this is? The system rebooted ok and all the programs seem to open ok. I have justed checked on my aspire one and it does not even have the file, so have I dodged a bullet?

Julan

---

### Post by mc4man on 2011-06-01
> I have deleted ~/usr/share/applications/mimeinfo.cache.
No big loss, note that on a fresh install .local/share/applications itself doesn't even exist and you're better off clearing out those files after an upgrade to 11.04

11.04 is creating and then using a slightly different format for mimeapps.list where there is a  - 
[Default Applications] section  and an [Added Associations] section
That will occasionally cause an issue like you saw when doing an upgrade from 10.10, the old mimmeapps.list is retained.

(nautilus has now been patched to prevent you from changing the default folder handler unless you really go out of your way to do so.

---

### Post by juliancam on 2011-06-02
Thanks for setting my mind at rest. I can see that a new mimeapps.list has been created.
Now if VLC would only start behaving reasonably like it used to, I could go back to using it as my default choice but that is well covered by other threads. Ah well maybe the next update will help.

Julian

---

### Post by tortugo23 on 2011-07-08
> **mc4man said:**
> You just need to delete the file mimeapps.list in  ~/.local/share/applications
(it could be edited but easier/better to just go ahead and delete - it will be recreated thru use of the r.click open with other application menu as need be.
Get there anyway you can, this will do so - in a terminal
```
 nautilus ~/.local/share/applications
```

Great fix! I had the same problem and this did the trick!

---

