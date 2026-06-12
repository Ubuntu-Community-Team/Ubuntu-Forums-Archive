---
title: "importing large files (video) from camera uses all swap"
date: 2009-08-20
forum: Multimedia Software
---

### Post by djcraft on 2009-08-20
With Ubuntu 9.04 and importing large (video) files from a Canon PowerShot all Memory and Swap is used and the file fails to import. The file size (4GB) is greater than the amount of Memory (1GB) + Swap (2GB). Is there software that does not attempt to import into memory before writing to disk? The following software is effected (with default settings):

digiKam
F-Spot
flPhoto
gThumb

As a side note, wine fails to install the Canon software from disk.

---

### Post by zarthon on 2009-08-20
When connected does the camera come up in the menu Places->Removable Media ?
If so, go there and drag it to some place on your system.
I believe this will use a regular file copy which will handle a large file.

If it does not then instead of using the camera connected to your system remove any flash media and put it in a flash drive and connect that to your system.
You also might find a mode that allows you to mount the flash card as a disk through the camera. Consult your manual about this. 

The problem could be with a lib like twain that is used by most of the applications accessing the camera.

---

### Post by djcraft on 2009-08-20
It shows up under Places as "Canon, Inc. Canon Digital Camera" if I open that in nautilus and try to copy a video file (4GB) it opens the File Operations window like a normal tranfer but no data is transfered and a gvfsd-gphoto2 process takes up all the Memory and Swap.

There don't appear to be any transfer mode settings on the camera.

I don't have a sdhc card input currently, but I will go that route as a last resort.

I'm going to try install gphotofs through Synaptic Package Manager to see if that may help and will report back.

Is the twain lib something that may have a configuration file?

---

### Post by djcraft on 2009-08-20
Not sure how to get the gphotofs to work but I found a sdhc reader to use as an alternative for now. I'm still interested in a solution to the Swap issue.

---

### Post by zarthon on 2009-08-20
No program or library should consume the whole swap. Is an error generated?
After you run the copy and it fails, what does it say in /var/log/messages ?
```

tail -n 60 /var/log/messages

```
You may have run into a limitation or bug. 
A 4gb file by fairly recent standards is a very large file. It is larger than a DVD iso for example. While the file system can deal with it the multimedia drivers may not be able to.

I usually don't connect a camera unless i am using twain to use a camera live while i am sitting at my comptuer. I've always used a card reader to extract media.
:)   Idea !
Create extra temporary swap ! 
Find the number of Megabytes you are using before the transfer. You might want to close other programs.
```

free -m

```
The number of extra megabytes should be larger than the number you are using before you start the transfer.
You are 1 Gigabytes plus some number of Megabytes short. I use 300 for megabytes and 1 for gigabytes. Note that these are block counts of 1 kilobyte so the powers are shifted down one. 
If you don't have spare space on / but you do on /home then put the file in your home dir instead of /tmp.
```

sudo dd bs=1024 count=$(( ((1024**2)*1)+(1024*300))) if=/dev/zero of=/tmp/swaptest
sudo mkswap /tmp/tmpswap
sudo swapon /tmp/tmpswap

```

Use free -m to see if you have created more free virtual space than the size of the file then try your transfer.

To clean up
```

sudo swapoff /tmpswap
## If you don't want to leave the swap around for another time:
rm /tmp/tmpswap

```

---

### Post by djcraft on 2009-08-25
That's a good idea creating the extra swap. I found out that the Canon software cd works on mac so I ended up just installing the software in os x and it works fine (still won't install in wine).

---

