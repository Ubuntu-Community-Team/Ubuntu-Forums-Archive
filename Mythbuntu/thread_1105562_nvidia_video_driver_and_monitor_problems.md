---
title: "nvidia video driver and monitor problems"
date: 2009-03-24
forum: Mythbuntu
---

### Post by davidstoll on 2009-03-24
I would like to install/enable nvidia 180 drivers (or at least 173 or 177).  However, they do not show up in my proprietary drivers list.  I have attached some screen shots to show you what my settings look like.

I have two screens.  The "CRT" is actually my big screen TV VGA in.  It was working previously, but I had to reinstall MythBuntu and now I can't get the screen to be detected correctly.  I can't set it to more than 1024x768 without my tv saying "mode not supported" or sometimes it will work, but you have to scroll around to see the entire screen.

I have a copy of my old xorg.conf file.  I restored that, but it doesn't seem to help.  I have also attached that.

I suspect that the monitor is not working correctly because I have an older driver...but it's just a guess.  They could be related, but I'm not sure.

I would appreciate any help I can get.

Thanks!

---

### Post by davidstoll on 2009-03-25
I'm reading posts that say "nvidia-glx-180 is now in the ubuntu repositories", but if I apt-get install nvidia-glx-180, it tells me it isn't found.

What do I need to change in my software sources to be able to install these drives?

---

### Post by 4dognight on 2009-03-25
After messing up my nvidia drivers , I ended up installing the 180 driver, that I downloaded from the nvidia site. I only got it to work after I completely removed the current driver from synaptic. Then, following the instructions from nvidia's installer did I get it to work. I then reconfigured my xorg.conf to my specific needs. I wished I had never attempted an upgrade , cause it was 2 days that I will never get back. ;-)

---

### Post by davidstoll on 2009-03-25
> **4dognight said:**
> After messing up my nvidia drivers , I ended up installing the 180 driver, that I downloaded from the nvidia site. I only got it to work after I completely removed the current driver from synaptic. Then, following the instructions from nvidia's installer did I get it to work. I then reconfigured my xorg.conf to my specific needs. I wished I had never attempted an upgrade , cause it was 2 days that I will never get back. ;-)

I tried to download and install the drivers from the nvidia site but it said that I didn't have the libc headers installed.

Plus, it seems like many people don't recommend doing that way anyway.  They recommend doing through apt-get or even synaptic.

However, when I try the apt-get of the 180 drivers, it says it's not found.

---

### Post by 4dognight on 2009-03-25
> **davidstoll said:**
> I tried to download and install the drivers from the nvidia site but it said that I didn't have the libc headers installed.

Plus, it seems like many people don't recommend doing that way anyway.  They recommend doing through apt-get or even synaptic.

However, when I try the apt-get of the 180 drivers, it says it's not found.

I agree using synaptic or apt-get is the best way. 
I just checked my 8.10 installation of ubuntu , and I downloaded the 180 driver. Not sure why it is saying not found for you.

---

### Post by davidstoll on 2009-03-25
> **4dognight said:**
> I agree using synaptic or apt-get is the best way. 
I just checked my 8.10 installation of ubuntu , and I downloaded the 180 driver. Not sure why it is saying not found for you.

What is the exact command and what specific (url) repository is it getting it from?

Thanks

---

### Post by 4dognight on 2009-03-25
I used synaptic. And searched for nvidia.

---

### Post by davidstoll on 2009-03-25
> **4dognight said:**
> I used synaptic. And searched for nvidia.

What is the exact item(s) you installed?

nvidia-glx-180 ?

---

### Post by nickrout on 2009-03-25
> **davidstoll said:**
> What is the exact item(s) you installed?

nvidia-glx-180 ?

that should be the one. Have you updated your package lists?

```
sudo aptitude update
``` or

```
sudo apt-get update
```

---

### Post by davidstoll on 2009-03-25
> **nickrout said:**
> that should be the one. Have you updated your package lists?

```
sudo aptitude update
``` or

```
sudo apt-get update
```


That is just to update.  What is the name of the driver package to apt-get install?  I'm trying to install a newer nvidia driver (173, 177 or 180) and my built in repositories don't have it....but from what I've read, they should.

---

### Post by 4dognight on 2009-03-25
I just tried installing via command line.

 sudo apt-get install nvidia-glx-180

Both via synaptic and command line worked, for me. It could be your package lists are out of date as already posted, if you cant find it.

---

### Post by davidstoll on 2009-03-25
> **4dognight said:**
> I just tried installing via command line.

 sudo apt-get install nvidia-glx-180

Both via synaptic and command line worked, for me. It could be your package lists are out of date as already posted, if you cant find it.

$ sudo apt-get install nvidia-glx-180
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package nvidia-glx-180

I have tried to update many times.
Is there another ubuntu or public repository I can get them from?

---

### Post by nickrout on 2009-03-25
like I said nvidia-glx-180 looks right to me.

what repos do you have enabled? you need to look in /etc/apt/sources.list and the contents of all the files in a subdirectory there, its something like /etc/apt/sources.list.d

---

### Post by davidstoll on 2009-03-25
> **nickrout said:**
> like I said nvidia-glx-180 looks right to me.

what repos do you have enabled? you need to look in /etc/apt/sources.list and the contents of all the files in a subdirectory there, its something like /etc/apt/sources.list.d

None.  Just whatever is built-in by default.

I did find the "nvidia-glx-180_180.37-0ubuntu2_i386.deb" file.  I tried to install, but got this error.

```
Selecting previously deselected package nvidia-glx-180.
dpkg: considering removing nvidia-glx-new in favour of nvidia-glx-180 ...
dpkg: yes, will remove nvidia-glx-new in favour of nvidia-glx-180.
(Reading database ... 119669 files and directories currently installed.)
Unpacking nvidia-glx-180 (from .../nvidia-glx-180_180.37-0ubuntu2_i386.deb) ...
dpkg: considering removing nvidia-glx-new in favour of nvidia-glx-180 ...
dpkg: yes, will remove nvidia-glx-new in favour of nvidia-glx-180.
(Reading database ... 119669 files and directories currently installed.)
Unpacking nvidia-glx-180 (from .../nvidia-glx-180_180.37-0ubuntu2_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/xorg/modules/extensions/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx-180' clashes with `diversion of /usr/lib/xorg/modules/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx-new'
dpkg: error processing /home/david/temp/nvidia-glx-180_180.37-0ubuntu2_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: considering removing nvidia-glx-new in favour of nvidia-glx-180 ...
dpkg: yes, will remove nvidia-glx-new in favour of nvidia-glx-180.
(Reading database ... 119945 files and directories currently installed.)
Unpacking nvidia-glx-180 (from .../nvidia-glx-180_180.37-0ubuntu2_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/xorg/modules/extensions/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx-180' clashes with `diversion of /usr/lib/xorg/modules/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx-new'
dpkg: error processing /home/david/temp/nvidia-glx-180_180.37-0ubuntu2_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
```

---

### Post by nickrout on 2009-03-25
what version of ubuntu are you running?

according to [this ]("http://packages.ubuntu.com/search?keywords=nvidia-glx")you need jaunty or intrepid-updates.



So you really need to look at what is in your repo list, (but which you seem reluctant to reveal).

---

### Post by davidstoll on 2009-03-25
> **nickrout said:**
> what version of ubuntu are you running?

according to [this ]("http://packages.ubuntu.com/search?keywords=nvidia-glx")you need jaunty or intrepid-updates.



So you really need to look at what is in your repo list, (but which you seem reluctant to reveal).

I'm running 8.04.2
Do you mean I need to upgrade to Intrepid?
If so, I'm not sure how to do that.

I'm not sure what I'm not providing.  I apologize.  I thought I was providing what was asked.

I have nothing listed in my repo list (I assume you mean the software sources).

I'm fairly new to linux, so I may have missed something or may have misuderstood.

---

### Post by MYGRA1N on 2009-03-25
hardy really dosent like any driver above 177.

---

### Post by nickrout on 2009-03-25
> **davidstoll said:**
> I'm running 8.04.2
Do you mean I need to upgrade to Intrepid?
If so, I'm not sure how to do that.

I'm not sure what I'm not providing.  I apologize.  I thought I was providing what was asked.

I have nothing listed in my repo list (I assume you mean the software sources).

I'm fairly new to linux, so I may have missed something or may have misuderstood.

The link I pointed you to tells you what versions of nvidia-glx are available in which versions of ubuntu.

Is there a particular reason you want 180?

---

### Post by davidstoll on 2009-03-26
> **nickrout said:**
> The link I pointed you to tells you what versions of nvidia-glx are available in which versions of ubuntu.

Is there a particular reason you want 180?

I want the better drivers 173, 177 or 180.  180 is newest, so I'll take that.

That being said, I upgraded to Intrepid Ibex 8.10 and now those drivers show up in my restricted drivers manager
Thank you nickrout!

I'll try to mark this a solved, but do you have an opinion on 180...or the other versions?

Thanks again.

---

### Post by nickrout on 2009-03-26
I use 180 becuase I want vdpau. It seems to work well. 

I got my 180 from the [avenard repos]("http://www.avenard.org/media/Home.html"), along with my patched mythtv-0.21-fixes.

---

