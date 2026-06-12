---
title: "fglrx removal issues after 10.10 upgrade"
date: 2010-11-13
forum: Multimedia Software
---

### Post by zck on 2010-11-13
After upgrading to 10.10, I could not get a graphical environment working. I'm able to get in via the terminal, but attempting to run X results in my monitors (I have two) seeing no signal. I've tried only one monitor plugged into the video card, and (separately), only one monitor plugged into the motherboard. Plugging the monitor into the motherboard results in no signal at all -- not even when the system is booting. I get into 10.10 just fine when running from a live cd.

I was able to get into the Grub recovery menu, and run the "dpkg    repair broken packages" option. Upon doing so, I get the following output (typed in by hand, but I don't think there are any typos).

```

The following packages will be REMOVED:
  fglrx xorg-driver-fglrx*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
Continue?[Y/n]
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing 'diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlimbmesa by fglrx'
  found 'diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
  subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: sub-process /usr/bin/dpkg returned an error code (1)
```In the IRC channel, I found a helpful person (thanks ChogyDan) who pointed me to a prior forum page ([http://ubuntuforums.org/showthread.php?t=186602](http://ubuntuforums.org/showthread.php?t=186602)). However, the page didn't seem to solve my problem. I'll take what I tried in order:

First, st4rdr1ft3r's post([http://ubuntuforums.org/showpost.php?p=1081255&postcount=2](http://ubuntuforums.org/showpost.php?p=1081255&postcount=2)). I had none of those files in /usr/lib . However, I did have libGLC.so.0.7, libGLC.so.0, libGLEWmx.so.1.5.2, libGLEW.so.1.5, libGLEW.so.1.5.2, libGLEW.so.1.5, libGLU.so.1.3.070900, and libGLU.so.1 . I moved the files to backup files then, ran sudo apt-get remove xorg-driver-fglrx . The same error messages appeared as before ("errors were encountered while processing: fglrx"). I've since moved the files back to their original locations.

Larryni's post ([http://ubuntuforums.org/showpost.php?p=1223819&postcount=7](http://ubuntuforums.org/showpost.php?p=1223819&postcount=7)) points to a now-gone page I found at archive.org ([http://web.archive.org/web/20060717192055/http://www.undiscoverable.com/category/linux/);]("http://web.archive.org/web/20060717192055/http://www.undiscoverable.com/category/linux/%29;") scroll down to "linux problems". It suggests running "sudo apt-get remove linux-restricted-modules-$(uname -r)". I get this error:

E: Unable to locate package linux-restricted-modules-2.6.35-22-generic
E: Couldn't find any package by regex 'linux-restricted-modules-2.6.35-22-generic'

The next useful post points to [https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879](https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879) . It suggests running "sudo apt-get remove --purge xorg-driver-fglrx". That has the same error as the original package error.

the last post suggests [https://answers.launchpad.net/ubuntu/+question/4838](https://answers.launchpad.net/ubuntu/+question/4838) . I opened /var/lib/dpkg/status and removed every entry that referred to fglrx (except ones that mentioned it in "Recommends" or its description. I then ran "sudo apt-get update " and "sudo apt-get upgrade", restarted, and there was no change. I reverted the file to its original status, and re-ran update and upgrade. On upgrade, the error message had "ureadahead will be profiled on next reboot", but was otherwise the same as running an upgrade previous times.

I'm at a bit of a loss as to what to do next. How can I figure out 1. whether fixing fglrx is the correct thing to fix, and 2. what I can to do to fix it?

---

### Post by pme 72 on 2010-11-13
This is just a guess but when you run 

dpkg repair broken packages

is 10.10 then trying to repair broken 10.10 fglrx packages when part of your problem could be broken fglrx packages from the previous installation? You say you upgraded, was it from 10.04? Were you previously running fglrx and did you remove the fglrx driver before you upgraded? Did you originally install fglrx from the Ubuntu repositories or from ATI? If from ATI do you need to run ATI's un-installer to remove their installed drivers?

I wish I had some answers for you.

---

### Post by zck on 2010-11-13
I'm not sure what the exact command is -- "dpkg repair broken packages" is just the menu description. However, the output is the same as when I run "sudo apt-get remove --purge xorg-driver-fglrx". So I'm not sure what exactly it's trying to do, but something like removing the driver.

I did upgrade from 10.4 The original install was either 8.10 or 9.4, and I've upgraded it to today. I don't know what driver I was running before; I installed some graphics driver through some Ubuntu menu, but I can't say what it was. Is there a way to check how it was installed?

---

### Post by pme 72 on 2010-11-13
It sounds like you installed the version from Ubuntu's System/Administration/Hardware Drivers menu so their instructions for removing the driver should work. 

I have had success removing fglrx from the terminal with instructions from: 

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

but have yet to successfully reinstall the proprietary driver afterwards. For my own peace of mind I would be interested to learn how to do it.  

I found this:

[http://hartlessbydesign.com/blog/ati-driver-issues-in-ubuntu-1004-lucid.html](http://hartlessbydesign.com/blog/ati-driver-issues-in-ubuntu-1004-lucid.html)

The post refers to a problem upgrading to 10.04 but the error messages looks similar. 

It would probably be better to find a person with which to discuss the issue though. I think you were smart to post the issue here and wait for someone with experience to give you live guidance. 

Wish I could be more helpful.

---

### Post by zck on 2010-11-13
You're my freaking hero****.

The specific instructions that fixed it for me were the ones at [hartlessbydesign.com]("http://hartlessbydesign.com/blog/ati-driver-issues-in-ubuntu-1004-lucid.html"):

```

sudo dpkg-divert --rename --remove /usr/lib/libGL.so.1.2
 sudo dpkg-divert --rename --remove /usr/lib32/libGL.so.1.2
sudo dpkg --force-all --purge fglrx
```

After running that, I ran *apt-get remove --purge fglrx*, restarted, and booted into a normal graphical environment. I didn't have to run *sudo dpkg-reconfigure xserver-xorg*, as the link suggests.

Thanks. I really appreciate you posting instructions to help me out.

---

### Post by Yellow Pasque on 2010-11-13
This is documented in the ATI wiki. [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Can.27t_remove_fglrx_with_dpkg_.28diversion_issue.29](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Can.27t_remove_fglrx_with_dpkg_.28diversion_issue.29)

---

### Post by zck on 2010-11-13
Hrm, I didn't come across that when searched around. Thanks.

Is it basically that something was thinking there was a package at /usr/lib/libGL.so.1.2, so I had to divert a package there (i.e., put an empty package in at that location), and then the package could be removed?

---

### Post by Yellow Pasque on 2010-11-13
No, the issue is that older versions of the ATI driver are incorrectly packaged and two packages claim the same diversion of the file.

---

