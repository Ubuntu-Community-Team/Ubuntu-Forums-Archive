---
title: "Can't import video file from digital camera"
date: 2009-05-22
forum: Multimedia Software
---

### Post by Tasc0 on 2009-05-22
The video file I have on the camera is about 1,7 Gb and it seems no applications can manage to handle it. I always get some type of error. If I take a picture, and try to import it, I have no problem.

I have Ubuntu 9.04.

What can I do?

---

### Post by pastalavista on 2009-05-22
How is the file stored on the camera? how is it connected? what kind of application do you need to "handle" it? what happens when you connect to the PC? what kind of error?... and any other pertinent information would be helpful.

---

### Post by pytheas22 on 2009-05-22
With the camera plugged in, what is the output of:
```

ls -R /media
```

---

### Post by Tasc0 on 2009-05-23
> **pastalavista said:**
> How is the file stored on the camera? how is it connected? what kind of application do you need to "handle" it? what happens when you connect to the PC? what kind of error?... and any other pertinent information would be helpful.
It's stored as a .MOV file. To the USB port. An application that can import the video from the camera to my computer. It detects the camera but I get an error (#60- Could not mount the device)... but if I have pictures and I use, let's say F-Spot, I can save them in my computer with no problem.

> **pytheas22 said:**
> With the camera plugged in, what is the output of:
```

ls -R /media
```

```

/media:
cdrom  cdrom0

/media/cdrom0:

```

---

### Post by pastalavista on 2009-05-23
OK it sounds like it just needs to be mounted manually. Probably a different filesystem. run in terminal ```
sudo fdisk -l
``` while the camera is connected before and after opening it with f-spot to find out its dev#. you'll need to edit /etc/fstab to make it auto-mount.

---

### Post by Tasc0 on 2009-05-23
> **pastalavista said:**
> OK it sounds like it just needs to be mounted manually. Probably a different filesystem. run in terminal ```
sudo fdisk -l
``` while the camera is connected before and after opening it with f-spot to find out its dev#. you'll need to edit /etc/fstab to make it auto-mount.
I'm not really sure how to identify the camera when I run that, I see my HDDs.

---

### Post by Tasc0 on 2009-05-23
Ok, so I finally have the video file on my computer. I'm not really sure what I did to fix the problem, but it might the command Pastalavista posted.

Thanks for the help.

---

### Post by pastalavista on 2009-05-23
Open System->Administration->Synaptic Package Manager. Search for "mount" and make sure 'mount','pmount', 'usbmount' and 'pysdm' are installed. If they are, go to the System->Admin menu again and run 'Storage Device Manager' (or in terminal enter 'pysdm'). Be sure to run it with the camera connected. It will make it easier to configure and make mount points. Another good prgram for doing that is 'mountmanager'. It can all be done in terminal but somebody else will have to walk you through that process. I'm too noobish..

---

