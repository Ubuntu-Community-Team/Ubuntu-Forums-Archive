---
title: "SD Card Mounting"
date: 2009-07-24
forum: Multimedia Software
---

### Post by _lycann_ on 2009-07-24
I recently deleted all the files off my SD card after copying them to my Desktop. The desktop died and the data was not recoverable; my mistake for not backing up soon enough. After some choice words about the computer I realized I should be able to recover the majority of the files since I had only snapped a couple pictures since deleting everything.

The glitch happens here; I went out and my girl friend popped the SD card in my laptop's (Compaq R3240ca) built-in multicard reader. I didn't know it even worked but she swears she was able to view the couple files that were on the card. She pulled the card out without unmounting (never knew any better) and now the device shows up but won't mount and I so can't run recovery on it. Similarly, on my Windows box the device shows up but reads as "no disk inserted." 

The images on the card that I took after deleting are viewable from within the camera's preview screen and when I connect the camera directly to the computer I am able to view the folders as well. I haven't found any recovery tools that work through the camera; all seem to require a card reader and for it to be mounted.

Is there a way to correct whatever happened to the card when it was removed improperly?

Edit:: I'm running Ubuntu 9.04 with the latest updates.

Thanks for any help in advance.

---

### Post by az on 2009-07-24
1. Install testdisk in Ubuntu.
  
sudo apt-get install testdisk

2. Insert the SD card and check what device it is.

Wait a moment and then run

tail /var/log/messages

You will see some kernel messages about detecting the new hardware and some other messages since it cannot find a filesystem on it.  Let's say it mentions the use of /dev/sdc

3.  Run photorec on that device

mkdir Recovery

sudo photorec /dev/sdc

You may need to enlarge your terminal.  Follow the prompts and tell it to extract all the data (not just the unallocated data)  Tell it to save thae data in the newly created Recovery folder.

4. Make the recovered files readable to you:  (use your own user name, not "andy")

sudo chown -R andy:andy Recovery/

---

### Post by _lycann_ on 2009-07-26
Thanks for the suggestion. I tried this out but the device shown in /var/log/messages couldn't be recovered. Photorec sees the folder as not in use or not valid. It's weird how similar the problem is between Windows and Ubunutu; in both cases a drive is created but nothing is mounted to it.

Is there a way to undo trouble caused by removing the drive before it was unmounted? Some sort of unlock or reset.

---

### Post by moore.bryan on 2009-07-26
You could also double-check in parted/gparted/kparted to see what the file structure is for your SD card.

---

### Post by _lycann_ on 2009-07-26
Thanks for your help, I ended up taking the thing in to Henry's and their card reader nailed it first try; I bought one and everything was gravy from there. Photorec is a great program! Thanks again

---

