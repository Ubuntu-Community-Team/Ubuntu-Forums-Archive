---
title: "how to delete files from mp3 player?"
date: 2013-04-06
forum: Multimedia Software
---

### Post by madnbri on 2013-04-06
Hi,
I've got a new mp3 player. I have uploaded some mp3-s I needn't, therefore have deleted... I thought, still used the player.
There are my deleted files firmly on the player (in shuffled que - I do not know why, I never shuffle anything).
I thought something is wrong: pushed back to the usb on computer. Strange! There are no files in filelist I've deleted before.
These are not there, but these are there.
Help! :) Please help me, how can I delete really the files.
Thanks in advance for answers.

---

### Post by evilsoup on 2013-04-06
With external storage devices, when you 'delete' a file in a graphical file manager (like nautilus), the file is actually moved to a hidden directory at the root of the storage device. It's analogous to the trash bin that files on your computer's hard drive are sent to. Most of the time people notice this because they delete files and no space is freed up. I assume that your player is simply looking in the hidden directory and getting the music files from there.

To see the hidden directory, plug in your player to USB and navigate to it in the file manager, then press 'ctrl+h' to see hidden directories/files. It will begin with a '.', IIRC it's called something like '.trashes'. If you delete that directory, then the files should be properly deleted.

You can avoid this issue in the future by using 'shift+delete' to remove files, which will bypass the trash bin etc.. Or you can use the terminal with rm.

---

### Post by madnbri on 2013-04-06
Thank You!
This is the one.

---

### Post by evilsoup on 2013-04-06
Please mark the thread as 'solved' (it should be available in the 'thread tools' at the top of the page).

---

### Post by madnbri on 2013-04-28
> **evilsoup said:**
> Please mark the thread as 'solved' (it should be available in the 'thread tools' at the top of the page).

No, this function is **missing** at me.

---

### Post by shantiq on 2013-04-28
hi madnbri    the function is there only in the **first **post in the thread right at the top

---

### Post by madnbri on 2013-04-28
OK, I've changed.

---

### Post by sahabcse on 2013-04-29
Hi,
I've got a new mp3 player. I have uploaded some mp3-s I needn't, therefore have deleted... I thought, still used the player.
There are my deleted files firmly on the player (in shuffled que - I do not know why, I never shuffle anything).
I thought something is wrong: pushed back to the usb on computer. Strange! There are no files in filelist I've deleted before.
These are not there, but these are there.
Help! Please help me, how can I delete really the files.
Thanks in advance for answers.

---

### Post by sahabcse on 2013-04-29
Hi,
I've got a new mp3 player. I have uploaded some mp3-s I needn't, therefore have deleted... I thought, still used the player.
There are my deleted files firmly on the player (in shuffled que - I do not know why, I never shuffle anything).
I thought something is wrong: pushed back to the usb on computer. Strange! There are no files in filelist I've deleted before.
These are not there, but these are there.
Help! Please help me, how can I delete really the files.
Thanks in advance for answers.

---

