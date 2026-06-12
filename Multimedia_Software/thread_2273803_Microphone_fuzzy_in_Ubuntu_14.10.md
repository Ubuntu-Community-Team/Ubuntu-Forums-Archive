---
title: "Microphone fuzzy in Ubuntu 14.10"
date: 2015-04-15
forum: Multimedia Software
---

### Post by kim15 on 2015-04-15
My microphone is incredibly fuzzy and static-y and I have no clue as to why.  It doesn't work on Skype or on anything else without sounding like crap.  I used Windows 8.1 before this and it worked perfectly, but ever since my switch to Ubuntu it's been sounding bad.  I am using a Lenovo G50-45 laptop.

---

### Post by Vladlenin5000 on 2015-04-15
Again, you probably need to install AMD proprietary drivers. Did you?

---

### Post by kim15 on 2015-04-16
How would I do that?  I am no Linux expert by any means.

---

### Post by Vladlenin5000 on 2015-04-16
Neither am I and no need for one. ;)

Just go to System Settings >> Software & Updates. At the rightmost tab, Additional drivers, check what is being offered. You probably want to select the recommended 'fglrx', apply and reboot.
Or, if you want to go hardcore (and beta): Read the [AMD Binary Driver How to]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD") to understand how to install but download [AMD Catalyst 14.6 (beta)]("http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx") instead.

---

### Post by kim15 on 2015-04-16
This doesn't seem to work..  I typed in a few of the commands and got this.

---

### Post by QIII on 2015-04-16
Hello!

Would you do two things, please?

First, copy the entire output of the attempted installation and post it back here between code tags.  (More on that in a bit.)

Also run the command 

```
 lsb_release -a 
```

And post that back between code tags.

You may use code tags in three ways:

1.  Click the # symbol in the tool bar, place your cursor between the tags that appear and paste your text.

2.  Paste your text, highlight it and then press the # symbol in the tool bar.

3.  Type [noparse]```
[/noparse], paste your text and then type [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by kim15 on 2015-04-16
```
 ninten@ninten-Lenovo-G50-45:~$ fglrxinfo
The program 'fglrxinfo' can be found in the following packages:
 * fglrx
 * fglrx-updates
Try: sudo apt-get install <selected package>
ninten@ninten-Lenovo-G50-45:~$ sudo apt-get install fglrx
[sudo] password for ninten: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 fglrx : Depends: fglrx-core but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ninten@ninten-Lenovo-G50-45:~$ 
```

```
 ninten@ninten-Lenovo-G50-45:~$  lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic
ninten@ninten-Lenovo-G50-45:~$ 


```

---

### Post by QIII on 2015-04-16
OK.

Did you attempt to install the fglrx driver directly from the AMD site?  (Don't if you didn't, I just want to know.)

---

### Post by kim15 on 2015-04-16
Yes I did, but it can in a .zip and there was no clear way to install it.  I went back to additional drivers and it still wasn't listed.

---

### Post by QIII on 2015-04-16
OK.  Let's start by seeing if dpkg thinks you have any fglrx related stuff installed.

Please post the results of 

```
dpkg -l | grep fglrx


```

---

### Post by kim15 on 2015-04-16
```
 ninten@ninten-Lenovo-G50-45:~$ dpkg -l | grep fglrx
ninten@ninten-Lenovo-G50-45:~$ 


```

---

### Post by QIII on 2015-04-16
OK.

Please run the following commands in order and let us know if you get any errors or warning messages:

To update your database
```
sudo apt-get update
```

To fix any broken packages in currently installed apps
```
sudo apt-get install -f
```

To get update all of your apps
```
sudo apt-get upgrade
```

To clear out any junk you no longer need
```
sudo apt-get autoremove
```

If all is well, we will set fglrx aside for the moment.

Run the following and post back the results

```
lspci | grep -i audio
```

---

### Post by kim15 on 2015-04-16
sudo apt-get update 

```
 W: Failed to fetch cdrom://Ubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)/dists/utopic/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)/dists/utopic/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)/dists/utopic/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)/dists/utopic/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu/dists/utopic/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu/dists/utopic/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

Auto Remove:

```
 The following packages will be REMOVED:
  linux-headers-3.16.0-23 linux-headers-3.16.0-23-generic
  linux-headers-3.16.0-34 linux-headers-3.16.0-34-generic
  linux-image-3.16.0-23-generic linux-image-3.16.0-34-generic
  linux-image-extra-3.16.0-23-generic linux-image-extra-3.16.0-34-generic
  linux-signed-image-3.16.0-34-generic
0 upgraded, 0 newly installed, 9 to remove and 13 not upgraded.
After this operation, 562 MB disk space will be freed.


```

```
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.2-031902-generic
Found initrd image: /boot/initrd.img-3.19.2-031902-generic
Found linux image: /boot/vmlinuz-3.16.0-36-generic
Found initrd image: /boot/initrd.img-3.16.0-36-generic
Adding boot menu entry for EFI firmware configuration
done


```

Audio

```

00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)


```

---

### Post by kim15 on 2015-04-17
Um, hello?  I've been waiting.  My microphone is still fuzzy,  :(

---

### Post by QIII on 2015-04-18
Sorry.  Real life happens...  And now I'm on the road with my Fedora laptop, I normally use Kubuntu (so I'm more familiar with that) and I don't have access to my Unity machine (which is now 400 miles away) to refresh my memory.  But we'll give this a try.

OK.  First, let's get your sources cleaned up.  You need to modify your sources list first to disable the CD and that PPA you have.

Do you know how to do that with the Software Center or synaptic or whatever package manager you are using?

---

### Post by kim15 on 2015-04-18
No I do not.

---

