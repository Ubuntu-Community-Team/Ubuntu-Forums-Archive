---
title: "Feisty 7.04 - Totem MPG over windows share problem"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by grunge09 on 2007-06-18
I ran into something interesting.  I do not know if it is a bad setting on my part or a bug so here goes.

I am running 704 Ubuntu Feisty (on an AMD 4000+ CPU with 1 GB RAM) with Totem Xine movie Player.   MPG's on this Ubuntu system play fine.  HOWEVER I have an old 1.3Ghz Duron PC (256 MG RAM) that has XP Pro on it with Window's shares on my network (running a Dell 10/100 unmanaged switch if that helps).    All PC's should be 100 MB according to the lights on the switch. 

When I mount the windows share, from my Ubuntu PC, via PLACES, CONNECT TO SERVER I can browse the MPG files on it, but it will only play like 0-2 seconds then stops playing.  BUT AVI files across the network play fine.  

If I copy those same MPG Files to from XP to my Ubuntu Desktop Totem plays them just fine.   Is this a problem with totem across a network?  Or just to an XP PC Share across the network?

I am looking into switching that Duron 1.3Ghz PC to Ubuntu, but that PC is running a Promise TX2000 Pro Raid card.  So It looks like I will have to go the fakeraid route as Ubuntu Live CD sees the mirrored drives as separate drives.

---

### Post by loopeando on 2007-06-24
Same problem here.

Bump!

---

### Post by kahm on 2007-06-25
They haven't fixed that yet? I ran into that one on 6.10. I think there was also an issue with Amarok and browsing shares. And browsing through pictures on a share. (My media server is also a Windows machine :P)

I got around it by actually mounting the shares instead of browsing to them.  (I think I used smb4k). I find that browsing a share is almost useless - the system never treats it like a drive like Windows does.

---

### Post by loopeando on 2007-06-25
Well, the title says "Fesity 7.04"

Glad you solved you problem!

---

### Post by loopeando on 2007-06-25
I've solved mounting the drive:

sudo mount -t smbfs -o username=user,password=pass //windows_name/shared_folder /media/windows

---

