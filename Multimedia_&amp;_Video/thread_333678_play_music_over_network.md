---
title: "play music over network"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by reckless2k2 on 2007-01-07
I can't seem to play music that's stored on my NAS from Edgy. If I connect from

Places > Network Servers > 

Then connect and open a music folder on my NAS, when I try to play it from the NAS, it won't play. If I try to open the URL through Amarok, I'm able to get into the NAS without a problem but then it won't play because it says no suitable plugin. 

If I copy the music to my local Edgy, then it plays fine but I can't get it to stream from my NAS. I can get it to stream to a Windows box. I know I can do the same thing in Linux.

Any help would be appreciated. All file storage is on my NAS using Samba. It's a Buffalo Linkstation with a Ext3 file system. I can log into it just fine but can't play music or videos from there. It requires that I download to my local Edgy machine to play which defeats the purpose. I have a gigabit network so I can transfer and stream everything so speed is not issue.

---

### Post by meng on 2007-01-07
Two options:
1. Use VLC which AFAIK is the only common network-aware player.
2. Mount the samba share using smbfs, e.g.
sudo mount -t smbfs //winbox/share /mnt -o rw,username=joe,password=bloggs

---

### Post by Mr Gav on 2007-05-01
i've got the same problem. Has anyone else had this problem and sorted it out?

---

