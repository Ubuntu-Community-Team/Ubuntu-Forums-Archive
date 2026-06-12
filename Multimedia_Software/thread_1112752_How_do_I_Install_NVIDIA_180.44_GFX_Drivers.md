---
title: "How do I Install NVIDIA 180.44 GFX Drivers?"
date: 2009-04-01
forum: Multimedia Software
---

### Post by Panarchy on 2009-04-01
Hello

I'm new to the whole 'proprietary drivers for Linux' thing.

Is there a nice simple tutorial on how to install the NVIDIA 180.44 GFX drivers?

Here is the link;
[http://www.nvidia.com/object/linux_display_amd64_180.44.html](http://www.nvidia.com/object/linux_display_amd64_180.44.html)

Once I have received sufficient help, I'd be happy to write a step by step tutorial with images for those more n00bish then me!

Thanks in advance for any help in this matter,

Panarchy

PS: So far I have learned;
[LIST=1][*]I launch the program by typing  sudo sh NVIDIA-Linux-x86_64-180.44-pkg2.run
[*]The following commands stops the X-Server: sudo /etc/init.d/gdm stop[/LIST]

---

### Post by wolfen69 on 2009-04-01
download [this file]("http://us.download.nvidia.com/XFree86/Linux-x86_64/180.44/NVIDIA-Linux-x86_64-180.44-pkg2.run") and put it in your home folder. then open a terminal and:
```
sh NVIDIA-Linux-x86_64-180.44-pkg2.run
```
then just follow the prompts.

i'm assuming you run 64bit ubuntu?

you may need to use **sudo sh NVIDIA-Linux-x86_64-180.44-pkg2.run** but i can't remember right now.

---

### Post by trig on 2009-04-01
have you checked the package manager

---

### Post by wolfen69 on 2009-04-01
you can also go to system>administration>hardware drivers and enable them there. nvidia 180 won't be available if you are using ubuntu 8.10

---

### Post by trig on 2009-04-01
im on the jaunty jackalope...

---

### Post by Panarchy on 2009-04-01
Thanks everyone

What the command to get the kernel source-code?

As it says it needs that.

Thanks in advance for telling me how to do so.

Panarchy

---

### Post by kpkeerthi on 2009-04-01
See [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by Panarchy on 2009-04-01
> **kpkeerthi said:**
> See [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

[IMG]http://i44.tinypic.com/2r3axqa.png[/IMG]

Thanks

:popcorn:

EDIT: Just gave my settings a whiz by using 'Extra' in Visual Effects... woh, this is wicked... also strange... LOL

---

### Post by PC_load_letter on 2009-04-01
I'm having troubles w/ this driver. Here is what happened (from another thread) when I tried to install 180.44 on my 64bit Ubuntu 8.04 Hardy

> 
**Reporting failure!** On Hardy 64bit with the 180.44 driver. Here is what happened if anyone is interested.

- I downloaded the driver from Nvidia for my 8400GS mobile (file name: NVIDIA-Linux-x86_64-180.44-pkg2.run)
- Followed the instructions on the 1st post to the semicolon.
- As the script was running, it said that "there is no available module for my current kernel" (2.6.24-23), "would you like to search the NVIDIA ftp server?" which I answered yes.
- Came back with "Nothing available for your kernel on the ftp server, will have to compile the kernel module", which went successfully.
- Then later "Would you like to install 32-bit openGL libs?" to which I said yes.
- "Checking for any conflicts w/ existing openGL libs."
- "Configure X automatically? Old file will be backed up", said yes.
- Restarted, but X failed, and the error message was something like "fatal error".

So, I uninstalled the 180.44 driver as mentioned in 1st post, then had to reboot into recovery mode, use xfix, and now I'm back to square one.

Any ideas why things went wrong?

---

### Post by Panarchy on 2009-04-01
Try again.

Follow the post that contained a link that solved my problem.

---

### Post by Careb on 2009-04-11
This is the error I get when I run the command:
sh NVIDIA-Linux-x86_64-180.44-pkg2.run

ERROR: this .run file is intended for the
Linux-x86_64 platform, but you appear to be
running on Linux-x86.  Aborting installation.

Is there a .run file for Linux-x86?

---

### Post by ikonia on 2009-04-15
yup - just download the 32bit package from nvidia.com rather than the 64bit package

---

