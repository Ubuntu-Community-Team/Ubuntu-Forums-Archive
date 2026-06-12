---
title: "Update Manager hangs on samba-common update"
date: 2011-11-15
forum: Mythbuntu
---

### Post by Galen Seitz on 2011-11-15
I'm having a problem that seems to be related to Update Manager.  

I performed a clean install of Mythbuntu 11.10, selecting Primary Backend w/Frontend during the install, as well as enabling SSH, Samba, and MythTV services.  I did not select downloading of updates during the install.  On the first boot after the install, I logged in and then exited the frontend which was autostarted.  Next a ran Update Manager.  It showed ~78 updates available, and I started the update process.  After downloading all of the updates and starting to process some of them(progress bar at ~75%), Update Manager hangs/freezes.  The final line in the details window begins with "setting up samba-common".

I think the reason it is hanging is that the smb.conf file in the samba-common update conflicts with a change that was made to the file during the Mythbuntu install.  On a previous install+update attempt, I used apt-get upgrade rather than Update Manager.  When I used apt-get, it prompted me to resolve a conflict with smb.conf.  What should Update Manager be doing in this case?  I've been unsuccessful when searching to find other reports of this problem, which is a bit puzzling, as I would expect others to have encountered it.

Presumably I can work around this by using apt-get upgrade, but if there really is a problem with Update Manager or some other piece, I'd like to report it so it can be fixed.

thanks,
galen

---

### Post by jerrrys on 2011-11-17
try this first

open a terminal and enter

sudo dpkg --configure -a

you can also attempt to repair broken packages with the -f install command.

 
**Fixing dependencies**

 **dpkg --configure --pending**  If dpkg quits with an error while [FONT=FIXED]apt-get install, upgrade, or dist-upgrade[/FONT]ing try running this to configure the packages that were already unpacked. Then try [FONT=FIXED]apt-get install, upgrade, or dist-upgrade -f[/FONT], and then try [FONT=FIXED]apt-get install, upgrade, or dist-upgrade[/FONT]  again. Repeat as needed. This usually resolves most dependency problems  (also, if it mentions a specific package for some reason, you might  want to try installing or removing that package)

 [B]apt-get install -f 
 apt-get upgrade -f 
 apt-get dist-upgrade -f[/B]  Attempt to fix dependencies while doing one of the above. Note that [FONT=FIXED]apt-get install -f[/FONT] does not require a <package> argument.

that was taken from a handy package in the software center

[ATTACH]207417[/ATTACH]

---

