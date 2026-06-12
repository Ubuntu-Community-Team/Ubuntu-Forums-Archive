---
title: "nvidia on Intrepid"
date: 2008-11-17
forum: Multimedia Software
---

### Post by loomsen on 2008-11-17
Hi everyone.

I'm going to show how to fix permission due to restrictive defaults of the nvidia driver. This question/problems seem to be pretty common, so I decided to write it down.

You may suffer of that issue if compiz for instance starts up, but then breaks again.

The actual problem many, or more likely most users suffer from is, that the permissions changed concerning accessibility of the nvidia driver since hardy.

Permissions are set to 0600, so that only root will be able to access direct rendering and such by default. To fix this, add this Section to the bottom of your xorg.conf:
Open it up by:
```

sudo nano /etc/X11/xorg.conf
```
[color=red]OR, if you prefer GUIs:[/color]
```

gksudo gedit /etc/X11/xorg.conf
```
and add this:
```

Section "DRI"
     Group 	"video" 
     Mode 	0660
EndSection

```

Save and close the file.

This will grant permissions to users in group video. If you don't mind other user having access as well, you may set permissions to 0666.

Check if you, as your user, is actually of member of the video group:
> 
me[~] groups
me adm dialout cdrom [color=red]video[/color] plugdev lpadmin admin sambashare jdown sabayon-admin
me[~] 


If not, run
[code]
sudo adduser <your.username> video
[code]

Should confirm it with sth like this
> 
me[~] sudo adduser docter video
Adding user `docter' to group `video' ...
Adding user docter to group video
Done.
me[~] 


Now simply restart your X server, either by dropping into a terminal and initiating a restart, or, of you're not familiar with that simply reboot your system. Afterwards everything should be fine (or at least finer).

---

