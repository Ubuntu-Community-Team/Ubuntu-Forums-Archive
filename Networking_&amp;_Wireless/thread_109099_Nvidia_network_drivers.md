---
title: "Nvidia network drivers"
date: 2005-12-27
forum: Networking &amp; Wireless
---

### Post by darrowconley on 2005-12-27
I have a Biostar Nvidia GeForce 6100 (AMD 939) motherboard with onboard ethernet. I have a driver disc that I have to use with Windows XP to get connected to the internet. Needless to say the driver disc can be read in Ubuntu but not ran. I have downloaded the drivers that I think will solve my problem ([http://www.nvidia.com/object/linux_nforce_amd64_1.0-0283.html)](http://www.nvidia.com/object/linux_nforce_amd64_1.0-0283.html)), but I cannot get them to run on ubuntu. When I run it from the desktop it tells me that I must be in root. When I go to terminal and go in root and open the driver from the desktop I get the same thing.

How can I install the drivers for my ethernet?

Thank you.
Darrow.

---

### Post by John.Michael.Kane on 2005-12-27
[http://www.nvidia.com/object/linux_nforce_amd64_1.0-0310.html](http://www.nvidia.com/object/linux_nforce_amd64_1.0-0310.html)
you need to use root ie sudo

---

### Post by darrowconley on 2005-12-28
now I get some errors.

First I get:
" No precompiled kernel interface was found to match your kethis means that the installer will need to compile a new kernel interface."

I click on 'OK'

Then I get:
"You appear to be compiling the NVIDIA kernel module with a different compiler than the one that was used to compile the running kernel. This may be fine, but there are cases where this can lead to instability. The compiler used to compile the kernel was gcc 3.4; the current compiler is gcc 4.0"

if I do no abort I get a message telling me that the kernel module did not load.

What do I need to do?

Thank you

---

### Post by helwitch on 2006-01-03
[QUOTE=darrowconley]now I get some errors.

First I get:
" No precompiled kernel interface was found to match your kethis means that the installer will need to compile a new kernel interface."

I click on 'OK'

Then I get:
"You appear to be compiling the NVIDIA kernel module with a different compiler than the one that was used to compile the running kernel. This may be fine, but there are cases where this can lead to instability. The compiler used to compile the kernel was gcc 3.4; the current compiler is gcc 4.0"

if I do no abort I get a message telling me that the kernel module did not load.

What do I need to do?

Thank you[/QUOTE]


Bump, essentially.
I've got an Asus A8n-vm-uaygz mobo, which uses the nvidia geforce6100 and nforce410. Kubuntu breezy can't seem to handle either of these things, so I have no GUI, and no net connection or sound. Which means I'm currently stuck using windows, which is just icky! Help, please! I followed the directions found [here]("http://ubuntuforums.org/showthread.php?t=107016") but end up with the error msg mentioned above. Please, SOMEONE has to know how to make this work!

---

### Post by mo_x on 2006-01-04
apt-get install buid-essential gcc-3.4 linux-headers-`uname -r`
export CC=/usr/bin/gcc-3.4
sudo sh NFORCE....

---

### Post by helwitch on 2006-01-04
that's the instructions from the other thread, which I followed, which didn't work.

---

### Post by mo_x on 2006-01-04
Is the file /usr/bin/gcc-3.4 present?

---

### Post by HIGHLIFE on 2006-01-25
Having the same problem has anyone gotten this chipset to work properly?

---

### Post by helwitch on 2006-01-26
Not I. I got the ethernet working in FC4, tho I dunno if it was FC4's forcedeth or the nvidia driver, but I can't find any distro I can make the sound work on.

---

### Post by xelink on 2006-01-28
[http://ubuntuforums.org/showthread.php?t=122605](http://ubuntuforums.org/showthread.php?t=122605)

go there to get your GUI up, I had a similar problem with a motherboard with the same chipsets. I need tog et my net working still but that shouldn't be horrible.

could anyone give us working advice on this?

---

### Post by mo_x on 2006-01-29
You might want to check out the nvidia linux forums.
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

Here is a quick howto for installing the latest nforce drivers.
- Install compiler etc. and linux headers.
```
sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4
```
- Run the installer script (you may need a different version).
```
export CC=/usr/bin/gcc-3.4
sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run
```
- Create a file in the /etc/modprobe.d directory
```
sudo gedit /etc/modprobe.d/nforce
```
And put the following text in it:
```
alias eth0 nvnet
alias forcedeth off
# Uncomment following lines if you want to use OSS nvsound driver
#alias sound-slot-0 nvsound
#alias snd-intel8x0 off
#alias i810_audio off 
```

---

### Post by xelink on 2006-01-31
any help with getting the nforce 410 drivers working? I need a net connection for ubuntu linux to be a feasable solution.

---

### Post by mo_x on 2006-01-31
Did the instructions above not work?

---

### Post by nuclearfly on 2006-01-31
I tried the directions, but I can't get ahold of gcc-3.4, it says there is no package.  Remember, we don't have network, so we can't hit the apt-get repository.  I'm guessing 3.4 isn't on the CD?

---

### Post by mo_x on 2006-02-01
You are able to post here so it must be possible to get some packages of the net. 
[http://packages.ubuntu.com/breezy/devel/](http://packages.ubuntu.com/breezy/devel/)
I think you would need gcc-3.4-base and gcc-3.4. You can install the packages with:
dpkg -i <package.deb>

---

### Post by nuclearfly on 2006-02-01
[QUOTE=mo_x]You are able to post here so it must be possible to get some packages of the net. 
[http://packages.ubuntu.com/breezy/devel/](http://packages.ubuntu.com/breezy/devel/)
I think you would need gcc-3.4-base and gcc-3.4. You can install the packages with:
dpkg -i <package.deb>[/QUOTE]

Ah, didn't think of that.  I tried installing gcc-3.4.5 from source files last night, but I must've installed it incorrectly.  I'll try the deb tonight.  The gcc-3.4-base was on the installation CD, so I was able to install that with apt-get.

---

### Post by nuclearfly on 2006-02-01
Ok, got it working.  Note that you also have to download cpp-3.4 and gcc-3.4-base deb files and you must apt-get binutils before dpkg'ing the gcc-3.4 deb.

---

### Post by chmmr on 2006-10-21
I ran into this same problem trying to run Dapper on an ASUS M2N-MX with an Nvidia network controller (chipset 410 I think).  I bought this motherboard under the assumption that the Nvidia chipset drivers in the kernel would work fine.  Dapper never recognized the NIC, so I tried installing the NFORCE drivers manually.  This was an absolute nightmare as I had to copy all the packages for build-essential etc over to the machine (it had no net connection) and in the end it didn't even work.

I've read so many different posts about this problem here and on the nvnews forums, some people say the built-in kernel drivers should work, some say you need to unplug the machine for a few seconds if you're rebooting from Windows, some seem to have been able to install the Nforce drivers manually.  None of these worked for me.  The workaround seems to be to buy a new NIC and see if that works.

This seems like it's an area where Ubuntu could really improve... even if your system is in a bad state, if you have a net connection you can always install from repositories and bootstrap it up to fully functional status.  My guess is that most people who have tried Ubuntu and found their NICs weren't detected gave up there and were never heard from again.

---

### Post by chmmr on 2006-10-21
This doesn't seem to be fixed in Edgy Eft either... just tried the RC1 live CD.

---

### Post by John.Michael.Kane on 2006-10-22
Well I'm on a Biostar T-Force nForce 410/6100 machine,and the network chip was seen on Both dapper/Edgy. This without the need to install any drivers.

---

### Post by chmmr on 2006-10-22
If this is the [product page]("http://www.biostar.com.tw/t-series/products/socket%20AM2/TForce%206100%20AM2/product_details.php") for your board, you'll note that it has a Realtek 8100C network chip, not an Nvidia one.

410 is just the model number of the Northbridge, I shouldn't have implied that it had anything to do with the network controller.  But judging from all the reports this hardware is definitely not supported at the moment.

---

### Post by John.Michael.Kane on 2006-10-22
I'm not using an AM2. like the OP I'm on an socket 939 biostar T-Force which is completely supported.

---

### Post by cutterjohn on 2006-10-24
> **SD-Plissken said:**
> I'm not using an AM2. like the OP I'm on an socket 939 biostar T-Force which is completely supported.

Actually I have the same board, a Biostar TForce4 U with which I had the problem of:
while the nVidia network adapter was found it would fail under heavier loads, e.g. large file xfers, e.g. kernel download

So, I found that I had to grab the driver package for linux from nVidia(see above) and installed their nvnet which works fairly well or better than forcedeth at any rate.

I've since also upgraded my CPU to an x2 4800+ and added a 7600GT KO.  I use the k7 UP/SMP compiled kernel available in the repo.

caveat:  since upgrading the GPU I've noticed that even with the nvnet driver the onboard ethernet will stop responding until the driver is unloaded and then re-loaded.  And I'm now having the same problems under Windows (win2k) where I never had a problem with the onboard controller except for when I tried NAM/ActiveArmor.  Dealing with nVidia onboard network controllers is very annoying, and I think that as soon as I am sufficiently motivated to move myself to move the PC I'll put in one of my old spare PCI 10/100 ethernet cards...

---

