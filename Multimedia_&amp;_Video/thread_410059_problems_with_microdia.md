---
title: "problems with microdia"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by leg on 2007-04-15
I can't get my daughters web cam to work for her. I have installed the gspca drivers and thought that they should have made this camera work.

                  ```
Bus 001 Device 004: ID 0c45:608f Microdia 
```

Instead when I start the camorama program I get a message:

       Could not connect to video device (/dev/video0)
       Please check connection

Am I correct in using the gspca driver as I am not sure after reading [this]("http://ubuntuforums.org/showthread.php?t=375005&highlight=Microdia") thread.

I get the following message when run in a terminal
```
(camorama:4992): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

Also I am running xubuntu if that makes a difference.

---

### Post by leg on 2007-04-16
Can anyone point me to a list of webcams that are working on this OS.

---

### Post by dabl on 2007-04-16
My Logitec Quickcam required the special gspca driver in Edgy, but works in Feisty "out of the box".

---

### Post by leg on 2007-04-16
> **dabl said:**
> My Logitec Quickcam required the special gspca driver in Edgy, but works in Feisty "out of the box".That would work for me as I have already installed the gspca driver.

---

