---
title: "Gigaware webcam and gspcav1 driver problem"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by marian-desktop on 2007-12-27
I got Gigaware webcam 25-234. To run it under my Kubuntu Gutsy Gibbon I found and downloaded gspcav1 driver. 

I red the instruction: "as root goes to gspcav1 directory and run: ./gspca_build "
When I did it I got this:

 REMOVE the old module if present

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
        *.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/marian/kubuntu/Gigaware webcam/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** No rule to make target `webcam/gspcav1-20071224'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2

:confused::confused::confused:
Please, how can I fix it? I would really like to use my new webcam. Thanks for any help.

---

### Post by marian-desktop on 2007-12-27
please :( any help???? :KS

---

### Post by marian-desktop on 2007-12-27
sounds like nobody can help me... :(

---

### Post by marian-desktop on 2007-12-27
Is there anybody who can run Gigaware webcam on ubuntu?

---

### Post by daengbo on 2007-12-27
The gspcav1 module is installed by default in Ubuntu 7.10 (/lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/gspca.ko). I only found one page which mentioned the Gigaware brand in Linux, and it didn't list a model number, so I'm unsure whether the webcam actually uses that driver or not. There are two possibilities:
1) That is not the correct driver
2) The list of devices doesn't include your webcam.

If #2 is the case, you can try manually inserting the driver by typing the following in a terminal

sudo modprobe gspcav1

If it fails to load, your webcam may use another module, but I can't find out which one.

---

### Post by marian-desktop on 2007-12-28
thank you for help Daengo.

I put in terminal what you said and got this result:

marian@marian-desktop:~$ sudo modprobe gspcv1
[sudo] password for marian:
FATAL: Module gspcv1 not found.
marian@marian-desktop:~$

And yes, I have found (/lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/gspca.ko) in my computer. 

Does it mean I need to find another driver?

---

### Post by cooldude on 2007-12-28
(/lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/gspca.ko)

The driver itself is not gspcav1, it is gspca. Thats why it says the module is not found. You typed it in wrong.

So do a "sudo modprobe gspca" without the parentheses.

---

### Post by marian-desktop on 2008-01-04
> **cooldude said:**
> (/lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/gspca.ko)

The driver itself is not gspcav1, it is gspca. Thats why it says the module is not found. You typed it in wrong.

So do a "sudo modprobe gspca" without the parentheses.

hello cooldude, thanks for help,
I tried it, typed

marian@marian-desktop:~$ sudo modprobe gspca
[sudo] password for marian:
marian@marian-desktop:~$

but nothing happend. What can I do now please?

---

### Post by marian-desktop on 2008-01-05
Is anybody running a Gigaware webcam under linux?????
Thanks for any reactions.

---

### Post by david.hilton.p on 2008-01-08
after modprobe is run successfully, nothing should be shown;
type "sudo modprobe NOTAMODULETHING" and it will give an error.

After doing the proper modprobe, does "ls /dev | grep video" show anything?  If so, a video device is detected...

---

### Post by keithjr on 2008-01-17
Hello, I'm also trying to get this webcam to work (I will return it if the Linux compatibility isn't up to snuff).

I've followed the directions you've all detailed so far and have this to show for it:
```

$ ls /dev | grep video
video
video0
video1
$ lsmod | grep gspca
gspca                 607824  0 
videodev               28160  1 gspca
usbcore               134280  7 gspca,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,ohci_hcd

```

So far so good!  So now, I try to run [camorama]("https://help.ubuntu.com/community/Webcam") to test it out.  I get an popup error that states "Could not connect to the video device (/dev/video0).  Please check connection."

As far as I can tell, the thing's connected (got a green LED for what that's worth).  It's very likely this isn't the right module for this webcam.  Where did you get the idea that it was?  Just wondering.

---

### Post by Bufke on 2008-05-19
I tried using this webcam with gspcav1 version 1.00.20, after a restart I can get it to almost work in camorama.  But the image is terrible, all I can see is really bright lights.  Also after restarting the program it no longer works.  I hope this camera is supported better soon.

---

