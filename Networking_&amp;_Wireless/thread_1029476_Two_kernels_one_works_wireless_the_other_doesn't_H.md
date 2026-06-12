---
title: "Two kernels one works wireless the other doesn't HELP"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by pminmo on 2009-01-03
I have two different version 8.04 kernels.  One, my Belkin USB Wireless G adapter is configured and works fine.  The other doesn't.  Can somebody tell me the config files that I can look at to see the descrepancy?  Thanks.

---

### Post by Ayuthia on 2009-01-03
> **pminmo said:**
> I have two different version 8.04 kernels.  One, my Belkin USB Wireless G adapter is configured and works fine.  The other doesn't.  Can somebody tell me the config files that I can look at to see the descrepancy?  Thanks.
This issue could be because of Network Manager or the kernel.  Have you found out what kernel module your wireless card is using (lshw -C network)?  If so, you will need to determine if the driver is a restricted module or if it is a an open source version.  From there, you will need to look at the linux-* source code to see where the differences are.  It could fall under the linux-restricted-modules or the linux-ubuntu-modules.  I am not for sure about the source code names though.

---

### Post by pminmo on 2009-01-03
Thanks for your response.  The working kernal has wlan0 info, the nonworking has nothing but the wired interface.  Doing a lsmod shows rt73usb and rt2x00 for the working kernal and no rt73usb or rt2x00 for the nonworking kernal.  I believe the rt2x00 are the non retricted drivers.  Being a linux neophyte it would seem to me that since this is the same computer and same set of directories, there must be some config file at boot that is different?

---

### Post by Ayuthia on 2009-01-03
Are you using the same distro or something different?  Sometimes a particular distro might include a module that another would not or sometimes the same distro might not load a particular module for some reason or another.

If you are using the same distro, have you tried the following from the Terminal (in the distro that does not have the modules loaded):
```
sudo modprobe rt73usb
sudo modprobe rt2x00
```and see if it works?  If it does not, what does dmesg say?

---

### Post by pminmo on 2009-01-03
It can't find the module.  So I did a file search and I see different directories based on kernal version.  (Same distribution)  The rt2x00 folder is in the working distribution, and isn't in the nonworking distro.

---

### Post by Ayuthia on 2009-01-03
You might try going to serialmonkey and compiling the drivers yourself:
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

This documentation might help:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)

---

### Post by pminmo on 2009-01-04
I tried the ubuntu instructions but paths are different than what is in the documentation.  I don't know if thats because 8.04 paths are different or something else.  In the working kernel my rt2x00 directory resides in /lib/modules/---kernel version---/drivers/net/wireless not in /lib/modules/'uname -r'/drivers/usb/net  And it didn't like the file contents anyway.:confused:

It just floors me how much I feel like I'm back in the 80's using command lines in Linux......:confused::frown:

---

### Post by Ayuthia on 2009-01-05
> **pminmo said:**
> I tried the ubuntu instructions but paths are different than what is in the documentation.  I don't know if thats because 8.04 paths are different or something else.  In the working kernel my rt2x00 directory resides in /lib/modules/---kernel version---/drivers/net/wireless not in /lib/modules/'uname -r'/drivers/usb/net  And it didn't like the file contents anyway.:confused:

It just floors me how much I feel like I'm back in the 80's using command lines in Linux......:confused::frown:

Are you using the back quote(`) instead of the single quote(') for `uname -r`?  You can test it out by doing:
```
echo `uname -r`
```and it should return the kernel version instead of uname -r.

It may feel that you are going back in time because you are working with a command line. Almost all programs that you use in Windows are precompiled so all you have to do is click on an item and it is ready to go.  With Linux, you are more in control of your system.  Because of this, nothing is hidden so the command line allows you to find/alter your system to be the way you want it.

---

