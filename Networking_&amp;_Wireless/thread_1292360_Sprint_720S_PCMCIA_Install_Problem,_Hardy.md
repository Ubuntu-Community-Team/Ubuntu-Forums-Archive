---
title: "Sprint 720S PCMCIA Install Problem, Hardy"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by barnaclebill18 on 2009-10-15
Hello,

I am trying to get my Sprint 720S PCMCIA card to connect using Ubuntu 8.04.

Using the Sprint Wireless Mobile Broadband Setup Guide for Linux OS, I can't get past the first step. Here are a few lines from the manual.
```

This document describes how to set up and connect to the Internet using a Sprint Wireless Modem on the Linux platform using open source software packages.

  Linux installation should be running Kernel 2.6.x.x or later.

1. This setup assumes that you have installed the usbserial driver distributed on your Linux CD according to the instructions in the driver installation readme file. Ubuntu has this setup by default.

2. Open an xterm window unload the usbserial driver by entering (you will be required to enter the root password after entering this command):
    “sudo modprobe –r usbserial”
After unloading the USB driver you should be returned to the command prompt.

```

When I enter the command  “sudo modprobe –r usbserial”, here is what I get.
```

bill1@bill1-laptop:~$ sudo modprobe –r usbserial
[sudo] password for bill1: 
FATAL: Module –r not found.
bill1@bill1-laptop:~$ 

```

As you can see, the manual says: This setup assumes that you have installed the usbserial driver,  Ubuntu has this setup by default.

I am fairly new to Ubuntu, still learning, so I need easy to understand answers.

Thank you.

---

### Post by barnaclebill18 on 2009-10-17
bump

---

### Post by GeorgeVita on 2009-10-19
Hi **barnaclebill18**,
in your command you are using a 'long dash'! Retry using normal dash or copy: ```
sudo modprobe -r usbserial
```

All terminal commands accept some parameters with a dash (-) or two dashes (--) just in front of the parameter. In above **modprobe** command **-r** means 'remove' module. Most commands have a brief help with **--help** after the command (**modprobe --help**). You can read a 'manual' running **man modprobe** (replace 'modprobe' with any command to see appropriate 'manual').

If you need help to next steps, post here.

Regards,
George

---

### Post by barnaclebill18 on 2009-10-19
Hello GeorgeVita,

Thank you for the reply.

I copy and pasted the commands from the Sprint manual.

If I type in a wrong command the the terminal usually says 'command not found'.

I have been over this many times, I started with 9.04, and tried lots of stuff that was suggested, got the modem to be seen by kppp and it even dialed and said connecting, but never finished.

I read there was a problem with 9.04, something about 
gprs/3g driver in 9.04, there is even a link in the manual that they added after I first downloaded it a few months ago. The wireless tech at Sprint told me about the link, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002)

I tried the fix suggested and it did not work. 

I then installed 8.04 on a partition so I could try with it, and that is where I am now, if I can get this working, I can stop using XP completely.

Bill

---

