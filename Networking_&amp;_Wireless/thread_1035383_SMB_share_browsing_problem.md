---
title: "SMB share browsing problem"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by Andre-D on 2009-01-09
Smb4K works perfectly.
Smb4K is a KDE tool.

Is it possible to make Nautilus do the job that good ?
It does not find all servers, and won't list their shares: this is how it feels:

1.-Nautilus lists servers on the selected workgroup
2.-I double-click "\\server"
3.-it thinks for 5-8sec
4.-it comes up with an empty \\server (no shares are listed)
5.-I can enter //server/share1 to see share1 , but it still does not display "share2"  .

---

### Post by P86 on 2009-01-17
system-config-samba might be what you are looking for. It worked for me when nautilus-share wasn't working.

---

### Post by Andre-D on 2009-01-18
thanks, but system-config-samba is a samba server configuration tool, this problem is about browsing samba shares, so it's like a samba-client problem.

---

### Post by superprash2003 on 2009-01-18
have you tried smb://x.x.x.x

---

### Post by Andre-D on 2009-01-18
> **superprash2003 said:**
> have you tried smb://x.x.x.x

 smb://192.168.1.110/  
lists nothing, just as 
smb:/odin/  
lists nothing

I can access any share by entering the share, like smb://odin/pictures

This happens even on clean-installed+patched ubuntu 8.10 in VmWare, not only this workstation.

Kubuntu seems to work well on the very same network.

---

### Post by superprash2003 on 2009-01-19
ok this might sound weird but try it.. it worked for me when i had this problem on a machine.. go to places->computer and under location type smb://192.168.1.110 or smb://odin .. if it doesnt load anything.. keep this same window open and then open another nautilus window by going to places->computer and then again try opening smb://192.168.1.110 or smb://odin .. make sure both windows are open.. if it still doesnt work.. try pressing F5 .. 
  this is a known samba nautilus bug!!

---

### Post by Andre-D on 2009-01-19
did not work for me , nor with three nautilus windows.
- where is that bug - how I find in in launchpad ?

---

