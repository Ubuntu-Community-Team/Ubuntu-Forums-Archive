---
title: "Ubuntu file browser as an FTP client?"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by Vik Vasilev on 2009-07-23
I was just experimenting with the file browser and I managed to connect to my website`s ftp server with Ubuntu`s file browser but when i try to upload or edit files it gives me an error. 
[IMG]http://alternative-x.com/store/screenshot2.jpg[/IMG]
How can i (if possible) get it to work

---

### Post by ibutho on 2009-07-23
What was the error message you got?

---

### Post by doas777 on 2009-07-23
please click "Show More Details" on your error dialog, and let us know what it says

---

### Post by Vik Vasilev on 2009-07-23
> **ibutho said:**
> What was the error message you got?
Sorry, I forgot to write down the error message.  It says only ```
Operation failed
```
Do you think it has anything to do with directory permissions?

---

### Post by doas777 on 2009-07-23
> **Vik Vasilev said:**
> Sorry, Do you think it has anything to do with directory permissions? very possibly. does changlog.php already exist in the folder?

---

### Post by Vik Vasilev on 2009-07-24
> **doas777 said:**
> very possibly. does changlog.php already exist in the folder?
No, it does not exist in that folder. I cant copy files, move/edit the existing ones,  (the same error ocures when i try to make a new folder). 
Other ftp clients work okay - i was just curious if this can be done :rolleyes:

---

### Post by superprash2003 on 2009-07-24
well i just tried connecting to my ftp server from nautilus and it worked perfectly..how big is the file?

---

### Post by Vik Vasilev on 2009-07-24
> **superprash2003 said:**
> well i just tried connecting to my ftp server from nautilus and it worked perfectly..how big is the file?
Well i tried many different files, i cant create new folders either - I get the same error. The only thing that works is renaming existing files...
Any ideas :confused:

---

### Post by Vik Vasilev on 2009-07-24
Thanks for the attention guys, I just got it to work. The problem was not in nautilus or its settings - I had reached a quota of 6000 files and after a quick cleanup it started working :D

:popcorn:  Mark it solved

---

