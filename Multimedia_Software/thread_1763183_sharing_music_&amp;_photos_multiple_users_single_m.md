---
title: "sharing music &amp; photos multiple users single machine"
date: 2011-05-20
forum: Multimedia Software
---

### Post by foodmonkey on 2011-05-20
this is for banshee & shotwell

first use system setting to make a group called "bansheeusers'. add the local users to the group.

create a dir /home/bansheeusers/tunes

ls -ld /home/bansheeusers you'll probably see
drwxd-xd-x root root ....
this means that root user owns the dir and has full access (rwx) whereas the root group only has read and execute (r-x).

change this by sudo chgrp -R bansheeusers /home/bansheeusers

this will change the group for all subdirs (the -R flag). you can check by using ls -ld /home/bansheeusers you should see something like

drwxr-xr-x root bansheeusers ......

ok give the group write access

sudo chmod -R g+w /home/bansheeusers

ls -ld /home/bansheeusers

get something like 
drwxrwxr-x root bansheeusers

next change the sgid bit to on

sudo chmod -R g+s /home/bansheeusers

ls -ld get something like

drwxrwsr-x root bansheeusers .....

all good - you could change the ownership of the dir by using chown.

you now have a shared dir for content. each user has their on db file in ~/.config/banshee-1/  so they can have their own playlists et al. they can all rip music to the shared dir - the other users just need to update their db file every now and again to get access to the new content. point banshee to the shared file using  the edit-preferences menu option.

follow the same method for shotwell images.

---

