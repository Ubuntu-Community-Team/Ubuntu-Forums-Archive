---
title: "External speakers and internal mic problems"
date: 2010-09-16
forum: Multimedia Software
---

### Post by lyuba on 2010-09-16
Hi everyone!

I had the problems with the external speakers not working in Ubuntu 10.04 on ThinkPad Edge (Intel), my friend advised to upgrade to the kernel 2.6.35.15 and it helped.

But!.. in those kernel version internal microphone is not working, though it works in 2.6.32-24-generic-pae.

Appreciate the ideas on how to fix this :)

---

### Post by lidex on 2010-09-17
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by lyuba on 2010-09-17
lidex, I don't get how to select the downloading option. That's what I get when typing the command you've mentioned:

```

lyuba@lyuba-laptop:/workspace/investclub$ sudo wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2010-09-17 15:10:09--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 212.20.107.51
Connecting to www.alsa-project.org|212.20.107.51|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2010-09-17 15:10:10--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                                                               ] 27,026       107K/s   in 0.2s    

2010-09-17 15:10:10 (107 KB/s) - `alsa-info.sh' saved [27026]

ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.


```

Sorry for the silly question :oops:

---

### Post by lidex on 2010-09-17
So where did the output go?

---

### Post by lyuba on 2010-09-18
Aha, that was probably the problem of my internet connection that I didn't see it yesterday.

Here is the output for the kernel 2.6.35.15 (internal microphone doesn't work):
[http://www.alsa-project.org/db/?f=9dc41146355b56ee39a2ed3085cf5ad48d1671ce](http://www.alsa-project.org/db/?f=9dc41146355b56ee39a2ed3085cf5ad48d1671ce)

Here is the output for the kernel 2.6.32-24 (external speakers don't work here):
[http://www.alsa-project.org/db/?f=98087b0067a9eff8e0fb66ab6ed2f9c14718bd08](http://www.alsa-project.org/db/?f=98087b0067a9eff8e0fb66ab6ed2f9c14718bd08)

---

### Post by lidex on 2010-09-18
I would stick with the lucid kernel and install the linuxant driver:
[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

---

### Post by lyuba on 2010-09-19
lidex,

when trying to install the package I get the following error:
[http://s40.radikal.ru/i089/1009/2f/a3efb0ed4579.jpg](http://s40.radikal.ru/i089/1009/2f/a3efb0ed4579.jpg)

Gcc, make and linux headers are installed on the system.

---

### Post by lidex on 2010-09-19
> **lyuba said:**
> lidex,

when trying to install the package I get the following error:
[http://s40.radikal.ru/i089/1009/2f/a3efb0ed4579.jpg](http://s40.radikal.ru/i089/1009/2f/a3efb0ed4579.jpg)

Gcc, make and linux headers are installed on the system.

Did you look at the log file generated to your /tmp directory?
Make sure this is installed also:
```
sudo aptitude install build-essential
```

---

### Post by lyuba on 2010-09-19
I've tried to install build-essintial, and also get an error:

```
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.3064.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 alsa-driver-linuxant

```

Here is the log:
[http://pastie.org/1168588](http://pastie.org/1168588)

Thank you for trying to help me!

---

### Post by lidex on 2010-09-19
> **lyuba said:**
> I've tried to install build-essintial, and also get an error:

```
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.3064.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 alsa-driver-linuxant

```

Here is the log:
[http://pastie.org/1168588](http://pastie.org/1168588)

Thank you for trying to help me!

Definitely not my area of expertise, but it looks like you need to install the kernel source. Try this:
```
sudo apt-get install linux-source
```

---

### Post by lyuba on 2010-09-20
Hm, it's so strange - when trying to install linux-source I also get an error:
[http://pastie.org/1169787](http://pastie.org/1169787)

What is /usr/bin/dpkg, which is causing this errors all the time?

---

### Post by lyuba on 2010-09-24
lidex, 

after our manipulations a cannot install a single package with apt-get.... How would you recommend to fix this?

---

### Post by lidex on 2010-09-24
What is the error message you're getting?
Try this:
```
sudo dpkg --configure -a
```

---

### Post by lyuba on 2010-09-25
First of all I solved the problem with installing packages just by removing linuxant driver, which cannot be installed for some reason.

I tried to install it again and here is the unsuccessful log: 
[http://pastie.org/1181459](http://pastie.org/1181459)

I try to install it with the DEB package from here: [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

What may cause the problem?

---

### Post by lidex on 2010-09-26
> **lyuba said:**
> First of all I solved the problem with installing packages just by removing linuxant driver, which cannot be installed for some reason.

I tried to install it again and here is the unsuccessful log: 
[http://pastie.org/1181459](http://pastie.org/1181459)

I try to install it with the DEB package from here: [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

What may cause the problem?

It would seem that you either don't have the kernel source installed or it's in a non-standard location.

---

