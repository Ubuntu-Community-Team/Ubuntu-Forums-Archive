---
title: "Canon EOS 350d"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by dolny on 2007-07-03
```
item ImportCommand+SourceItem
Testing gphoto path = usb:002,010
PortInfo Universal Serial Bus, usb:002,010
Error USBClaim: LibGPhoto2.GPhotoException: Exception of type LibGPhoto2.GPhotoException was thrown.
  at LibGPhoto2.Error.CheckError (ErrorCode error) [0x00000] 
  at LibGPhoto2.Camera.Init (LibGPhoto2.Context context) [0x00000] 
  at GPhotoCamera.InitializeCamera () [0x00000] 
  at MainWindow.ImportCamera (System.String camera_device) [0x00000] 
cleanup context

```

Console output of F-Spot while attempting to copy photos from Canon 350 EOS D attached to an usb port. I can copy the files with gphoto2 (console app) but cannot do it with Digikam or F-Spot. Anybody knows what to do :( ?

---

### Post by MCMcButtah on 2007-07-03
I have never been able to get canon cameras to work correctly over usb, ever. And this is running windows. I'v had a G2, an 400D, and a 20D and it has never worked. I gave up and bought a $5 card reader.

---

### Post by dolny on 2007-07-03
I use Arch btw ;) 

Anyway, I played with these settings: [http://ubuntuforums.org/showthread.php?t=330787&highlight=canon+350d](http://ubuntuforums.org/showthread.php?t=330787&highlight=canon+350d)

and "BUS!="usb_device", GOTO="libgphoto2_rules_end" worked for me with digikam.. but now stopped - hmm ;) F-spot crashes. Man, I use XFCE so I wish there was a similar tool for XFCE.

---

### Post by Sunforge on 2007-07-03
MCMcButtah - I'd agree with the 20D and windows but it works very well under ubuntu 7.04. 

If you've still got your 20D and haven't tried it under Linux I'd suggest giving it a whirl.

---

### Post by MCMcButtah on 2007-07-03
Thanks for the tip, I noticed my 20D was correctly recognized in digikam but it never really occurred to me to try it as I just assumed it wouldn't work :)

---

### Post by Sunforge on 2007-07-04
I've exported several thousand pix from the 20D to my main Feisty machine but I know exactly what you mean about Windows: it was a pain which was one of the reasons I tried Linux in the end.

The one thing that lets Linux down is that printing the photographs to my Epson R1800 happens to be a dead loss. I can print pictures but they're washed out compared to printing under Windows. 

Now if there's some genius that's got an R1800 tuned to perfection under Feisty I'd be all ears.

Some you win and some you lose.

---

### Post by MCMcButtah on 2007-07-04
Yeah I have the same issue as you with my pixma 9000pro. There arn't any good linux drivers for it to allow anything more than the most basic of printing. My solution was to have the printer as a shared network device off my server running windows XP  in vmware.

---

### Post by Sunforge on 2007-07-05
Hadn't thought of doing something like that. I'll have to give it a try.

---

