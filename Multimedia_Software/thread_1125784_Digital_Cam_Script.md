---
title: "Digital Cam Script"
date: 2009-04-14
forum: Multimedia Software
---

### Post by hellarough on 2009-04-14
> **tdrusk said:**
> I'm making my grandfather a computer since we are getting him a digital camera for christmas. I got it so when he plugs in the camera it automatically syncs the pictures to a folder, deletes the pictures off the camera, opens a window of all of his pictures and unmounts the drive. ahh old people

```
#!/bin/bash
# Sync Files
rsync -av /media/disk/test /home/tyler/Test
#Delete Files From Camera
rm -r /media/disk/test
#Wait For Indexing To Catch Up
sleep 10
#Open Nautilus Search
nautilus /home/tyler/Desktop/Test.savedSearch
#Unmount Drive
eject /media/disk/
```



Okay so I saw this and thought it was a pretty good idea but I modified it to fit my desires like so...
```

#!/bin/bash
#Get date/time
TIMENOW=date +%m%d%y
#Make new piture directory
mkdir /home/renegade/Pictures/$TIMENOW
#Sync Files
rsync -av /media/disk-1/DCIM/100CASIO/* /home/renegade/Pictures/$TIMENOW
#Wait For Indexing To Catch Up
sleep 10
#Unmount Drive
sudo eject /media/disk-1/

```

I know I didnt do it right cause the files are not syncing to a dated folder like I want them to. Any ideas on how to fix this and any ideas about proper script writing would be appreciated. Also, I would like to have the script double check that it copied the pictures to my HD before it deletes them from the camera (thats why my script doesnt delete the pictures yet). Possibly in the future, Keep track of what has already been copied to my HD so that way I can keep them on the camera.

---

