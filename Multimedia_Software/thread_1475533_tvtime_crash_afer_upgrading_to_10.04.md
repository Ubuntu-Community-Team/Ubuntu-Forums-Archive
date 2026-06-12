---
title: "tvtime crash afer upgrading to 10.04"
date: 2010-05-07
forum: Multimedia Software
---

### Post by xlv1000 on 2010-05-07
Hello,

I installed 10.04 from scratch over 9.04 ,keeping /Home.
Tvtime no longer works.I unistalled it completly and installed again ,with no results.Any ideas?

---

### Post by xc3RnbFO8P on 2010-05-07
> I unistalled it completly and installed again
Did you delete the hidden folder in your home folder?
/home/your folder/**.tvtime**
Use **ctrl-H** to show hidden folders
or in Nautilus, View> Show Hidden Folders.
You can also start TVtime in a Terminal window, and see if get some errors messages.
> tvtime

---

### Post by xlv1000 on 2010-05-07
> **Ringi said:**
> Did you delete the hidden folder in your home folder?
/home/your folder/**.tvtime**
Use **ctrl-H** to show hidden folders
or in Nautilus, View> Show Hidden Folders.
You can also start TVtime in a Terminal window, and see if get some errors messages.

Thanks for the answer.Something is wrong with the video source,but I don't know how to fix it.


```
sal9001@sal9001-desktop:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/sal9001/.tvtime/tvtime.xml
videoinput: Driver won't tell us its norm: Invalid argument
videoinput: Can't get tuner info: Invalid argument

    Your capture card driver: sonixj [USB camera/usb-0000:00:1f.4-2.1/132864]
    does not support full size studio-quality images required by tvtime.
    This is true for many low-quality webcams.  Please select a
    different video device for tvtime to use with the command line
    option --device.

Found "USB camera : USB Audio (hw:1,0)"
Segmentation fault
sal9001@sal9001-desktop:~$ 

```

Can you help me?[

---

### Post by xc3RnbFO8P on 2010-05-07
Try:
> tvtime --device /dev/video1

---

### Post by xlv1000 on 2010-05-07
> **Ringi said:**
> Try:

I 've tryid and that's the result

```
sal9001@sal9001-desktop:~$ tvtime --device /dev/video1
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/sal9001/.tvtime/tvtime.xml
Found "USB camera : USB Audio (hw:1,0)"
Channels count non available
```

and

```
sal9001@sal9001-desktop:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/sal9001/.tvtime/tvtime.xml
Found "USB camera : USB Audio (hw:1,0)"
Channels count non availablesal9001@sal9001-desktop:~$ 

```

---

### Post by xc3RnbFO8P on 2010-05-07
In Nautilus check if you got /dev/video1

if you do:
> sudo gedit /etc/tvtime/tvtime.xml

find /dev/video0 and change it to /dev/video1

Another solution would be unplug your webcam.

---

### Post by xlv1000 on 2010-05-08
> **Ringi said:**
> In Nautilus check if you got /dev/video1

if you do:

find /dev/video0 and change it to /dev/video1

Another solution would be unplug your webcam.

I did the first but nothing happend.
The second worked fine!!!
Thank you Ringi!!

---

### Post by xlv1000 on 2010-05-08
After restart ,problem stays on

---

### Post by xlv1000 on 2010-05-08
I unpluged the camera and reinstalled tvtime and everything is ok!!!
Thank's everybody for the answers...

---

### Post by brel on 2010-05-09
Similar problem and unplugging the usb camera works. However...plugging and unplugging my webcam each time I want to watch TV is not a great solution. Everything worked fine up until my upgrade. Shouldn't I be able to leave the webcam plugged in?

---

### Post by xc3RnbFO8P on 2010-05-09
You could try this:
[http://www.linuxquestions.org/questions/linux-hardware-18/how-can-i-assign-a-webcam-to-a-specific-dev-video-669507/]("http://www.linuxquestions.org/questions/linux-hardware-18/how-can-i-assign-a-webcam-to-a-specific-dev-video-669507/")

---

### Post by hackys on 2010-05-11
try this for 32 bit

[https://launchpad.net/~whoopie79/+archive/testing/+files/tvtime_1.0.2-5ubuntu2.1_i386.deb](https://launchpad.net/~whoopie79/+archive/testing/+files/tvtime_1.0.2-5ubuntu2.1_i386.deb)

or this for 64 bit

[https://launchpad.net/~whoopie79/+archive/testing/+files/tvtime_1.0.2-5ubuntu2.1_amd64.deb](https://launchpad.net/~whoopie79/+archive/testing/+files/tvtime_1.0.2-5ubuntu2.1_amd64.deb)

worked like a charm for me with the same problem as you discribed

---

### Post by brel on 2010-05-30
Got udev to mount my usb cam in the same place every time but that didn't solve the problem (although I'm happy it's always in the same spot).

Downloaded hackys version patched tvtime and that did it. Thanks a million.

---

### Post by xlv1000 on 2010-05-30
thanks everybody for the answers.....I realy do not use the cam ,and unplaging it ,solved my problem

---

### Post by mplexus on 2011-04-19
tvtime -d /dev/video1 -x /dev/dsp1

---

