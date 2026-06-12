---
title: "ASUS A8N-VM CSM Video Woes"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by Protege on 2008-01-25
Okay I have tried to install the restricted portion of the nvidia drivers for the onboard video, I have tried to run dpkg-reconfigure xserver-xorg, I have tried to manually edit xorg.conf to add new resolutions. None of this has solved my problem. I cannot change the screen resolution from 640x480@50Hz. Anyone have any ideas? If more information is required just let me know what you need and how to get it and I will be more than happy to post it. Thank you, in advance, very much for taking the time to help me.

---

### Post by Yellow Pasque on 2008-01-25
I'm an ATI guy, but I think this might help you:
```
sudo apt-get install nvidia-glx-new nvidia-settings nvidia-xconfig
```
Then, click Applications and look for a tool to help you configure.

---

### Post by Protege on 2008-01-25
> **Temüjin said:**
> I'm an ATI guy, but I think this might help you:
```
sudo apt-get install nvidia-glx-new nvidia-settings nvidia-xconfig
```
Then, click Applications and look for a tool to help you configure.

I tried that and got this as a response.

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-settings: Conflicts: nvidia-glx-new but 100.14.19+2.6.22.4-14.10 is to be installed
                   Conflicts: nvidia-glx
E: Broken packages

---

### Post by Protege on 2008-01-26
*bump*

---

### Post by Yellow Pasque on 2008-01-27
Ok. Try without the settings package
```
sudo apt-get install nvidia-glx-new nvidia-xconfig
```

---

### Post by Protege on 2008-01-28
root@uServ:~# sudo apt-get install nvidia-glx-new nvidia-xconfig
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  nvidia-settings nvidia-new-kernel-source
The following packages will be REMOVED:
  nvidia-glx
The following NEW packages will be installed:
  nvidia-glx-new nvidia-xconfig
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
Need to get 55.9kB/5070kB of archives.
After unpacking 1720kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe nvidia-xconfig 1.0+20070502-1 [55.9kB]
Fetched 55.9kB in 1s (39.4kB/s)
(Reading database ... 112198 files and directories currently installed.)
Removing nvidia-glx ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package nvidia-glx-new.
(Reading database ... 112152 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb) ...
Selecting previously deselected package nvidia-xconfig.
Unpacking nvidia-xconfig (from .../nvidia-xconfig_1.0+20070502-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-xconfig_1.0+20070502-1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/nvidia-xconfig', which is also in package nvidia-glx-new
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-xconfig_1.0+20070502-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

First off thanks for taking the time to help me with this issue Temujin.
Thats what I got this time. Any idea what could be going wrong?

---

### Post by Protege on 2008-01-31
No one has any ideas? That makes me a sad panda....

---

### Post by Yellow Pasque on 2008-01-31
Ok, one more time. It appears that the nvidia-new driver includes its own version of the config program, so just:
```
sudo apt-get install nvidia-glx-new
```

Sorry to make you jump through hoops, but like I said, I'm used to ATI and all its wonderful issues. I think this nvidia thing might be too straightforward for me.

---

