---
title: "Lost both wired &amp; wireless connections--some help?"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by riprap1951 on 2010-12-10
[FONT="Verdana"][SIZE="3"]<Linux noob running Ubuntu 10.10 on a Dell 710m>
Fresh install of OS yesterday. Initially I had wired connection but no wireless. So I started chasing threads & trying different downloads & commands [WITHOUT KNOWING essentially what I was doing; throw your rocks at me HERE] & now I have lost the wired connection also.
Also: [a] If I go into System > Administration > Additional Drivers, I get "No proprietary drivers are in use on this system." 
      [b] As far as being able to copy a downloaded driver [using a working M$oft machine with net connection] onto an SD card & transferring that driver to the Dell laptop, I have tried formatting 3 different SD cards with the Dell, & each time I come up with various failure errors--& I have no idea why something as simple as formatting an SD card isn't working. [????]
If anyone's got the time & expertise I would appreciate it
[/SIZE][/FONT]

---

### Post by oldschoolgentoo on 2010-12-17
I should say welcome to the site, first glad to see your working with linux.

Simple commands to help us help you.


```
( ***Ifconfig*** is a listing of your network device address information)
Command below:
# ifconfig

(***UNAME*** prints the name, version and other details about the current machine and the operating system running on it)
Command below:
# uname -a

(***CAT*** is a standard [Unix]("http://en.wikipedia.org/wiki/Unix") program used to [concatenate]("http://en.wikipedia.org/wiki/Concatenation") and display files. The name is from *[catenate]("http://en.wiktionary.org/wiki/catenate")*, a synonym of concatenate.)
Command below:
# cat /proc/version

(***LSPCI*** is a command on [Unix-like]("http://en.wikipedia.org/wiki/Unix-like") operating systems that prints detailed information about all [PCI]("http://en.wikipedia.org/wiki/PCI_Local_Bus") buses and [devices]("http://en.wikipedia.org/wiki/Device") in the system)

# lspci -vv



( ***dmesg** *(for "display message" or "driver message" ) is a command on some [Unix-like]("http://en.wikipedia.org/wiki/Unix-like") operating systems that prints the message buffer of the [kernel]("http://en.wikipedia.org/wiki/Kernel_%28computer_science%29").)

#dmesg


#dmesg | grep -i eth0

```


This is some good items for the others to be able to help you with your errors that happen with your system.

It will also help you to troubleshoot as well.

hope this helps

---

### Post by spiky001 on 2010-12-17
Just as a thought as it,s a new install why not reload? or open software sources at the bottom select cd then reload update manager then install drivers from disc

---

