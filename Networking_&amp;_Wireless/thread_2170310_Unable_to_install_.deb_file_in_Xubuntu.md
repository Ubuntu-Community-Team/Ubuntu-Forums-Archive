---
title: "Unable to install .deb file in Xubuntu"
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by jack17 on 2013-08-25
So as the t title reads I cannot install the .deb file. I am offline until I install the .deb because the .deb file is my WiFi driver. I am completely unable to connect to WiFi so please do not suggest anything that would require me to go online. I am posting this from my mobile device. Thank you

---

### Post by steeldriver on 2013-08-25
Hello and welcome to the forum. In order to help us help you, can you tell us

[LIST=1]
[*]what deb you are trying to install, and where you got it 
[*]exactly how you are trying to install it (including the full command, if via command line) 
[*]the exact error you are getting 
[/LIST]

---

### Post by jack17 on 2013-08-25
I got the file from here:
[https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/downloads/list](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/downloads/list)

I moved the file to the Downloads folder 
i then ran 
sudo su
then 
dpkg -i /home/jack/Downloads/debfilename

---

### Post by jack17 on 2013-08-25
This is the error I got 

root@jack-PC:/home/jack# dpkg -i /home/jack/Downloads/963(Reading database ... 132493 files and directories currently installed.)
Preparing to replace rtl8192cu-tjp-dkms 1.6 (using /home/jack/Downloads/963) ...
Unpacking replacement rtl8192cu-tjp-dkms ...
dpkg: dependency problems prevent configuration of rtl8192cu-tjp-dkms:
 rtl8192cu-tjp-dkms depends on dkms (>= 1.95); however:
  Package dkms is not installed.


dpkg: error processing rtl8192cu-tjp-dkms (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rtl8192cu-tjp-dkms

---

### Post by ian-weisser on 2013-08-25
> **jack17 said:**
> This is the error I got 
[...]
  Package dkms is not installed.
[...]


That's the problem.

.deb packages do not include all dependencies. Instead, they *refer* to other .deb packages that they depend upon. That keeps the size of each package small and the total install size small. The package rtl8192cu-tjp-dkms requires dkms, which you did not bring with you.

There are excellent tools for offline installations, like the apt-offline and apt-zip packages. Those applications will do all the dependency checking for you to prevent precisely this kind of issue. Or, you can use the **apt-cache depends**** <packagename>** command to see the offline list of all dependencies of any package (including uninstalled packages) in the Ubuntu repositories. 

I was in your shoes once, and did an entire distribution upgrade offline by hand back in 2006. It was many frustrating hours of shuffling back and forth with a USB stick. Happily, your problem looks much smaller than mine did...but you will need to go online to get the dkms .deb. No way around it.

---

### Post by jack17 on 2013-08-30
How do I know what dkms to download?

---

### Post by ian-weisser on 2013-08-30
Get the dkms .deb at [http://packages.ubuntu.com](http://packages.ubuntu.com)
Use the version for your release of Ubuntu, of course. The wrong version won't work.
There are many foo-bar-dkms package names. Use the EXACT package name that the package manager is looking for (straight "dkms").

---

### Post by chili555 on 2013-08-30
If I may just add a few words and I hope I am not stepping on toes. dkms itself has a few dependencies as well signified by the red dots. Download those as well and don't be surprised if it takes two or three tries. Just be patient and persevere. You can do it.

ian-weisser and I know you can do it because we've been through the same process a few times.

---

### Post by jack17 on 2013-08-30
This is very frustrating. I have to install a .deb in order to install another .deb... This makes no sense whatsoever. Please link me to the exact file I need and tell ,e how to install it.

---

### Post by ian-weisser on 2013-08-30
> **jack17 said:**
> I have to install a .deb in order to install another .deb..

Precisely. That is how dependencies work. Each deb is small. Layers of shared debs make up the Ubuntu system. The deb system keeps the system small, prevents orphan libs from cluttering up your system, and has many other benefits. But there is a learning curve.
Congratulations - you have taken the great leap to understanding!

1) Tell us what version of Ubuntu you are running. (12.04, 12.10, 13.04, etc.)

2) Run the following command and post the entire output here. The command will not make any changes to your system, but will instead list what we must download.
```
sudo apt-get install --simulate dkms
```

As I wrote before, next time you really should try apt-offline or apt-zip, which will do all this tedious work for you...

---

### Post by chili555 on 2013-08-30
I think it is actually:```
sudo apt-get install --simulate dkms
```

---

### Post by ian-weisser on 2013-08-30
Quite right, thanks. Edited previous post.

---

### Post by jack17 on 2013-08-31
I got this error

Reading package list... Done
Building dependency tree
Reading state information... Done
Package dkms is not availabe, but is reffered by another package. 
This may mean that the package is missing, has been obsoleted, or
Is only available from another source 

E: package 'dkms' has no installation candidate

---

### Post by ian-weisser on 2013-08-31
Good.

Once more, which version of Ubuntu are you using? (12.04, 12.10, 13.04, etc.)

---

### Post by jack17 on 2013-08-31
> **ian-weisser said:**
> Good.

Once more, which version of Ubuntu are you using? (12.04, 12.10, 13.04, etc.)

The latest version of xubuntu 13.04

---

### Post by ian-weisser on 2013-08-31
> **jack17 said:**
> Please link me to the exact file I need and tell ,e how to install it.

[http://packages.ubuntu.com/raring/all/dkms/download](http://packages.ubuntu.com/raring/all/dkms/download)

sudo dpkg --install /path/to/downloaded/dkms.deb

---

### Post by chili555 on 2013-08-31
He will probably also need coreutils, gcc, make, module-init-tools and patch. Please see attached.

---

### Post by jack17 on 2013-08-31
Thanks for your patience with me guys. I got everything installed and my wifi up and working!

---

### Post by chili555 on 2013-08-31
> **jack17 said:**
> Thanks for your patience with me guys. I got everything installed and my wifi up and working!Woo hoo! Great job. Glad it's working.

---

### Post by jack17 on 2013-09-01
> **chili555 said:**
> Woo hoo! Great job. Glad it's working.

I bricked the OS to hell 

[http://ubuntuforums.org/showthread.php?t=2171657](http://ubuntuforums.org/showthread.php?t=2171657)

---

