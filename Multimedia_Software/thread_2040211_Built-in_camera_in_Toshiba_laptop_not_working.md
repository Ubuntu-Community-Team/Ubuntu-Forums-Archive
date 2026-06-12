---
title: "Built-in camera in Toshiba laptop not working"
date: 2012-08-10
forum: Multimedia Software
---

### Post by abveloso on 2012-08-10
Hi,

I've used Ubuntu on the same Toshiba Satellite A305-S6872 for the last 4 years and my built in camera has always worked. A couple of days ago I noticed that the camera was not being recognized anymore. Cheese says "No device found". The weird thing is that sometimes after I boot the camera will work.

There is no mention to the camera in lsusb.

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Also, there are no /dev/video* files.

```
ls /dev/v*
/dev/vcs   /dev/vcs2  /dev/vcs4  /dev/vcs6  /dev/vcsa   /dev/vcsa2  /dev/vcsa4  /dev/vcsa6  /dev/vga_arbiter
/dev/vcs1  /dev/vcs3  /dev/vcs5  /dev/vcs7  /dev/vcsa1  /dev/vcsa3  /dev/vcsa5  /dev/vcsa7
```

I've looked through the forum and there seems to be a few other people complaining about this. Does anyone one know if there is a solution or if this is a generalized problem?

Any help is appreciated.

---

### Post by irv on 2012-08-10
I remember having a problem where my cam quite working. How I got it going again was to completely uninstall cheese, then reinstalled it and it just worked and is still working.
I have no idea what the problem was but as long as it is working I don't care.

---

### Post by abveloso on 2012-08-10
Hi Irv,

thanks for the suggestion. I have that a try but it still doesn't work.

---

### Post by irv on 2012-08-10
> **abveloso said:**
> Hi Irv,

thanks for the suggestion. I have that a try but it still doesn't work.

I know you are using a Toshiba and I am using a Dell, and I am not sure what else to tell you. Hopefully someone else will jump in here.

---

### Post by isa.dsouza on 2012-10-21
[I]It may have something to do with the physical location of the webcam. Try pressing the area around the webcam, since the webcam is on the edge of the lid, it tends to get damaged.

I have an emachine E725, sometimes just have to gently press the surrounding area of the webcam to get the thing to display an image.
            [/I]

---

### Post by cybrsaylr on 2012-10-21
I'm having a similar problem with a Dell Inspiron 1525 PP29L Laptop.
When 64 bit 12.04 was installed the camera worked asking if I wanted to use a pic it took. During install of 12.04 camera worked fine but now I can't get it to operate.

Will installing 'Cheese', which is in Synaptic, get this laptop cam running again? Had no idea what program to use to make cam operational.

---

### Post by irv on 2012-10-22
> **cybrsaylr said:**
> I'm having a similar problem with a Dell Inspiron 1525 PP29L Laptop.
When 64 bit 12.04 was installed the camera worked asking if I wanted to use a pic it took. During install of 12.04 camera worked fine but now I can't get it to operate.

Will installing 'Cheese', which is in Synaptic, get this laptop cam running again? Had no idea what program to use to make cam operational.

Just for the record, I have a Dell 1521 and I just installed 12.10 this morning and Cheese and the Cam works OK.

---

### Post by cybrsaylr on 2012-10-22
Just installed Cheese and it works great on my Dell laptop!
Just have to get familiar with it.
Thanks for the info in this program.

---

### Post by timthebeermaker on 2013-03-28
I am having the exact same problem with the same result

---

