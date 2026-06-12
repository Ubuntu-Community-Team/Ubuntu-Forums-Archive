---
title: "New isc-dhcp breaks network connections"
date: 2011-02-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-02-24
I just updated to the newest isc-dhcp (4.1.1-P1-15ubuntu4).
After a reboot I had no net, not even network-manager applet left.
Downgrading to the previous version (4.1.1-P1-15ubuntu3) solves this issue.

Here is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/724556](https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/724556)

The easiest way to test this is to first download from Launchapd
the version 4.1.1-P1-15ubuntu3.
[https://launchpad.net/ubuntu/natty/+source/isc-dhcp/4.1.1-P1-15ubuntu3](https://launchpad.net/ubuntu/natty/+source/isc-dhcp/4.1.1-P1-15ubuntu3)
Then afterwards downgrading in terminal with sudo dpkg -i.

---

### Post by PaulW2U on 2011-02-24
> **Harry33 said:**
> The easiest way to test this is to first download from Launchapd
the version 4.1.1-P1-15ubuntu3.
[https://launchpad.net/ubuntu/natty/+source/isc-dhcp/4.1.1-P1-15ubuntu3](https://launchpad.net/ubuntu/natty/+source/isc-dhcp/4.1.1-P1-15ubuntu3)
Then afterwards downgrading in terminal with sudo dpkg -i.
Thanks Harry but I still had the old packages in my cache. Downgraded, rebooted and here I am on-line using Natty again. I've added a "me too" to your bug report too.

---

### Post by Harry33 on 2011-02-24
> **PaulW2U said:**
> Thanks Harry but I still had the old packages in my cache. Downgraded, rebooted and here I am on-line using Natty again. I've added a "me too" to your bug report too.

Thanks Paul!

---

### Post by rebootme on 2011-02-24
If you ls -lah /sbin/dh* you'll notice the file /sbin/dhclient is a broken symlink.

I copied the /sbin/dhcpclient file from my installation disc over and rebooted.  I at least have internet now over my LAN card.  Wireless is still broken.

---

### Post by Harry33 on 2011-02-24
> **rebootme said:**
> If you ls -lah /sbin/dh* you'll notice the file /sbin/dhclient is a broken symlink.

I copied the /sbin/dhcpclient file from my installation disc over and rebooted.  I at least have internet now over my LAN card.  Wireless is still broken.

I looked at the file /sbin/dhclient of my downgraded working
version (4.1.1-P1-15ubuntu3) and it is not a symlink file at all.

---

### Post by TunaCanTommy on 2011-02-24
How do I download the previous version if I don't have a working network ? ?
I could download on a working system, and transfer the file over to the broken computer.  But I don't have any idea as to what to do next.

---

### Post by Harry33 on 2011-02-24
> **TunaCanTommy said:**
> How do I download the previous version if I don't have a working network ? ?
I could download on a working system, and transfer the file over to the broken computer.  But I don't have any idea as to what to do next.

The two necessary packages (isc-dhcp-client and isc-dhcp-common) may very well still be in the cache of the broken setup.

But if you downloaded the previous packages and copied or moved them into your broken setup, open terminal, go to the folder where you downloaded the packages and run this command:
```
sudo dpkg -i package1 package2
```
where package1 and 2 are the exact names of the downloaded files.
For example in a 64-bit system:
package1 is isc-dhcp-client_4.1.1-P1-15ubuntu3_amd64.deb

Then just reboot.

---

### Post by Harry33 on 2011-02-24
There is a fix for this bug in Launchpad uploading now (v. 4.1.1-P1-15ubuntu5).
Here:
[https://launchpad.net/ubuntu/natty/+source/isc-dhcp/4.1.1-P1-15ubuntu5](https://launchpad.net/ubuntu/natty/+source/isc-dhcp/4.1.1-P1-15ubuntu5)

---

### Post by Harry33 on 2011-02-24
Right, the new update (4.1.1-P1-15ubuntu5) fixed this issue. This is solved now.

---

### Post by TunaCanTommy on 2011-02-24
So I wait for isc-dhcp 4.1.1-P1-15ubuntu5 to finish and then do as above using the new client file:

> sudo dpkg -i package1 package2

 . . where package1 is the "client" and package2 is the "common"

---

### Post by Harry33 on 2011-02-24
> **TunaCanTommy said:**
> So I wait for isc-dhcp 4.1.1-P1-15ubuntu5 to finish and then do as above using the new client file:



 . . . where pacage1 is the "old-file" and package2 is the "new-file".

No, do not put there any old files. There are two new files, package1 and package2.
Like this (64-bit architecture).
Package1 = isc-dhcp-client_4.1.1-P1-15ubuntu5_amd64.deb
Package2 = isc-dhcp-common_4.1.1-P1-15ubuntu5_amd64.deb

Download the files from here (choose your architecture):
[https://launchpad.net/ubuntu/natty/+source/isc-dhcp/4.1.1-P1-15ubuntu5](https://launchpad.net/ubuntu/natty/+source/isc-dhcp/4.1.1-P1-15ubuntu5)

---

### Post by TunaCanTommy on 2011-02-24
Sorry - misunderstood.  I think I understand now.
I have the new files and I'll get them installed.
Will let you know how it goes - thanks for your help.
( This was a tough one for me. )

---

### Post by sgage on 2011-02-24
I was lucky - the files were still in my cache :-)

---

### Post by TunaCanTommy on 2011-02-24
That did it, thanks a bunch!

---

### Post by cariboo on 2011-02-24
I just set a static ip address for now until a new package is available.

---

### Post by sgage on 2011-02-24
Seems like the new packages are now in the repos.

---

### Post by scradock on 2011-02-24
> **sgage said:**
> Seems like the new packages are now in the repos.
and thanks to the heads-up from Harry33 I was able to wait until they showed up to do the upgrade - never accepted the ..ubuntu4 versions at all.

Thanks - keep up the good work!

---

### Post by Quackers on 2011-02-24
Lol, I thought I waited until they were in, but apparently not, judging from the resulting lack of internet. You live and learn.

---

### Post by bruc33ef on 2011-02-24
You guys are great!  I was pulling my hair out for hours over this bug until I saw this thread.  The solution works just fine.
Many thanks!

---

### Post by sgage on 2011-02-24
> **bruc33ef said:**
> You guys are great!  I was pulling my hair out for hours over this bug until I saw this thread.  The solution works just fine.
Many thanks!

I am an older gentleman, but I have to say this forum is, like, totally awesome!

:KS

---

### Post by TunaCanTommy on 2011-02-24
+1

---

### Post by grubdude on 2011-02-25
Sorry scanning the thread quickly but what is the fastest way to determine if the old files are still in the cache and then how to proceed from there. Thanks!

---

### Post by cariboo on 2011-02-25
The problem has been solved with updates, you don't need to downgrade the packages.

---

### Post by grubdude on 2011-02-25
True but I am running inside a virtualbox and have no internet connection for this vm, so how can I download the update? :-)

---

### Post by cariboo on 2011-02-25
You should be able to do the download by setting up a connection manually. Make sure you have networking set as a bridged connection then set up your ip address, netmask, broadcast and gateway addresses in /etc/network/interfaces.

---

### Post by grubdude on 2011-02-25
Okay, I was going to try a static ip but wasn't sure if there would be any problems in the vm...
 
What is the format to edit etc/network/interfaces ?
 
Never mind, got it! :-)
 
Almost forgot, Thanks! :-)

---

### Post by katrama on 2011-02-26
I have the same problem. I forgot the lines to add. Could anyone help?

---

### Post by katrama on 2011-02-26
I tried to setup a static ip using 

```
ifconfig eth0 192.168.2.43 netmask 255.255.255.0
route add default gw 192.168.2.2
```

There is some packets going trnsmitted and recieved but i cant connect to internet.

Unfortunately, I dont even have the version 3 file in archives.

---

### Post by Harry33 on 2011-02-26
The development versio should never be the only installation any user has.
This is a perfect example about that.
You need Internet to go to this page:
[https://launchpad.net/ubuntu/natty/+...1-P1-15ubuntu5](https://launchpad.net/ubuntu/natty/+...1-P1-15ubuntu5)

and to download thse two files of your architecture:
- isc-dhcp-client_4.1.1-P1-15ubuntu5
- isc-dhcp-common_4.1.1-P1-15ubuntu5

---

### Post by katrama on 2011-02-26
The system doent detect a USB also. Is there any work around?

---

### Post by katrama on 2011-02-26
I was able to get the USB working. I installed and rebooted it. Still doesnot work.

---

