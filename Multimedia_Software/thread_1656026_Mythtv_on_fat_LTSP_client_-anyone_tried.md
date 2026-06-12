---
title: "Mythtv on fat LTSP client -anyone tried?"
date: 2010-12-30
forum: Multimedia Software
---

### Post by riptool on 2010-12-30
Not sure if this has been done, searching only brings up mythbuntu diskless info. Im almost trying the same thing but not quite.

I have LTSP server running and 3 clients boot off it. They are FAT clients so the LTSP server does little work. All HW accell and cpu use is done on the client. So my idea was to install mythtv backend on the LTSP server also so all users who login will have access to mythtv also by running mythfrontend on the FAT clients. Ive read some horror stories of this not working for "THIN" clients(where all the work is done on the LTSP server), but cant find anyone who tried on a FAT client. Seems it should work fine since full screen video on the Fat clients is quite respectable in speed.

This is a work in progress so I'll add to it as I figure things out. 
So far my setup...
LTSP server
-Did a min install of Ubuntu 10.10 from server cd - which is command line only. But can also do a full install to Ubuntu desktop and install LTSP later. Can also install LSTP from server cd, but then have to add or redo image to be a FAT image instead of thin. Or can have FAT and THIN images for different clients/uses.
-Then installed/configured LSTP fat client by cmd line.
-Added a couple users, booted clients off network, no problems. Online, youtube vids, movies work great.
-installed mythtv front and backend on the LSTP image. rebuild image No problems.
-try to start front end from a logged in client. Says user not part of mythtv group. No problem to fix, I dont think anyway. Only permissions I think might not work is being able to admin the backend. Im not sure if clients will be able to open the backend admin interface. I only need the 1st user to have that ability so I can edit the backend if needed. Other users would only need front end access.

.... more later but thats the gist. I want diskless/quite fat clients to be able to boot of the network, do anything desktop wise they could as if it was a full blown pc(no prob, that works) and also be able to run Mythtv from the diskless desktop. 

So Mythtv on fat LTSP client -anyone tried?. Im not stuck, thats just as far as Ive gotten so far.


If this is a duplicate or can be found elsewhere, please delete.
Thanks

---

### Post by riptool on 2011-11-06
OK, finally had time to test this.
Mythtv and mythtv backend running on normal desktop install of 10.10.

ON sepereate machine installed an LTSP server64, cmd line only,  serves up a FATclient  i386 image of Ubuntu 10.10.   Installed mythtv-frontend while in chroot of the i386 machine, just as you would install any software for the LTSP machine.  Had to add my user name manually to the group mythtv. Not only inthe chroot of the machine but also in the user/group of the 64server.
then update-kernels
update-ltsp-client
update ssh-keys
update dhcp ( I didnt, using external dhcp not "standalone" version of ltsp)
ltsp-build-client

Then booted AMDx4 machine with no hard drives. Booted to ubuntu desktop of the LTSP client. Started Mythtv via the menus.  Setup video and sound.  Works great.  No different than as if booted off a machine with a hard drive and a desktop install of mythtv. NO lag in video. 

One problem still workign on. Changing channels on the LTSP client does not change channels on the mythtv backend. Not sure why yet.

---

