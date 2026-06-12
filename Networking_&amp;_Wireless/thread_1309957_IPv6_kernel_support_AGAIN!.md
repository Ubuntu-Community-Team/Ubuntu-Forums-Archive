---
title: "IPv6 kernel support AGAIN!"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by abickerton on 2009-11-01
I've just upgraded to Karmic. Once again, I find that I cannot disable IPv6 as it's compiled into the 
kernel. I do not use IPv6 and very much doubt ever will on a desktop. 

When will the kernal maintainers realise that an overwhelming majority of users need only ipv4 (should also be a module)? If its is needed then the required modules should be available for use, installing ipv6 in such a way is at best mis-guided, and at worst shows arrogance.

Looking back through the forums. I see many posts asking how to disable this being answered with "why would you want to"? With all due respect. THAT IS NOT WHAT THE OP ASKED!

IPv6 makes any internet application crawl when no ipv6 environment is available. LET ME DISABLE IT!

---

### Post by cprofitt on 2009-11-01
**  Disable IPv6 on Karmic 9.10 **

 Karmic does not include ipv6 as a module, so the only way to disable it is with passing a kernel parameter during boot. I found the same problem with jaunty 9.04, but it was easy to edit the menu.lst file to add this option.

Using yout favorite editor using sudo, edit /etc/default/grub and change 
 ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to 
 ```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"
```then 
 ```
sudo update-grub
```Courtesy of JoeHacker -- [http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10](http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10)

---

### Post by z987k on 2009-11-01
I think this is my problem as well.  Ever since upgrading to 9.10, the internet is slow as hell, and none of the windows boxes in the house seem to have this problem.

After searching around and noticing it's taking forever for the dns to resolve any hostname, I think upv6 enabled is my problem as well, but to date no solution I have found has worked.  I tried disabling it in firefox, but that didn't do anything, then I found this thread.... but when I went to edit /etc/default/grub, there was no grub file there..... so I just created one with the options shown, ran update-grub, rebooted.... and nothing, still slow resolving dns.  
I then figured that maybe I could put that as an option in /boot/menu.lst, but that also did nothing.
I have the opendns servers listed in my ipv4 settings if it matters.

I have also tried editing my /etc/sysctl.conf to include "net.ipv6.conf.all.disable_ipv6 = 1 " to no avail.

Any idea as to why this is not working for me.... or why I did not have the grub file?
How the hell do I get ipv6 disabled?

---

### Post by abickerton on 2009-11-04
Even with the workaround, I (and may others ) don't want it there in the first place, how can we insist to the kernel team that new kernels do not have it compiled in.

---

### Post by grandtoubab on 2009-11-04
Have a look here

[http://ubuntuforums.org/showpost.php?p=8214638&postcount=8](http://ubuntuforums.org/showpost.php?p=8214638&postcount=8)

[http://ubuntuforums.org/showthread.php?t=1307259](http://ubuntuforums.org/showthread.php?t=1307259)

---

### Post by zika on 2009-11-04
> **z987k said:**
> I think this is my problem as well.  Ever since upgrading to 9.10, the internet is slow as hell, and none of the windows boxes in the house seem to have this problem.

After searching around and noticing it's taking forever for the dns to resolve any hostname, I think upv6 enabled is my problem as well, but to date no solution I have found has worked.  I tried disabling it in firefox, but that didn't do anything, then I found this thread.... but when I went to edit /etc/default/grub, there was no grub file there..... so I just created one with the options shown, ran update-grub, rebooted.... and nothing, still slow resolving dns.  
I then figured that maybe I could put that as an option in /boot/menu.lst, but that also did nothing.
I have the opendns servers listed in my ipv4 settings if it matters.

I have also tried editing my /etc/sysctl.conf to include "net.ipv6.conf.all.disable_ipv6 = 1 " to no avail.

Any idea as to why this is not working for me.... or why I did not have the grub file?
How the hell do I get ipv6 disabled?I think You have old Grub since You do not have /etc/default/grub. Put **ipv6.disable=1** in a kernel line in /boot/grub/menu.lst ...

---

### Post by abickerton on 2009-11-04
> **grandtoubab said:**
> Have a look here

[http://ubuntuforums.org/showpost.php?p=8214638&postcount=8](http://ubuntuforums.org/showpost.php?p=8214638&postcount=8)

[http://ubuntuforums.org/showthread.php?t=1307259](http://ubuntuforums.org/showthread.php?t=1307259)

Sorry you seem to be missing the point. I and many other don't want to have to disable something that just should not be enable by default. I wouldn't expect my mother to digging around a grub config and neither should you.:mad:

---

### Post by smacky on 2009-11-12
I have exactly this problem after upgrading from 9.04 to 9.10.

I disabled IPv6 in FF so it works again.

However, the system itself is still broken (crucially apt-get and the updater GUI).

None of the fixes mentioned above bring any joy.

There is no /etc/default/grub.

I put ipv6.disable=1 in my /boot/grub/menu.lst and ran sudo update-grub:

```

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.31-14-generic root=UUID=9343e883-ced0-437b-b777-6428aea05126 ro quiet splash ipv6.disable=1
initrd		/initrd.img-2.6.31-14-generic
quiet

```

It has not fixed the issue. (BTW if ultimately this does work, wil I need to manually update GRUB like this everytime I get a new kernel?)

Here it is not working:

```

julian@julian-laptop:~$ sudo apt-get update
[sudo] password for julian: 
Err http://gb.archive.ubuntu.com karmic Release.gpg
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic/main Translation-en_GB
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic/restricted Translation-en_GB
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic/universe Translation-en_GB
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic/multiverse Translation-en_GB
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-updates Release.gpg
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-updates/main Translation-en_GB
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-updates/restricted Translation-en_GB
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-updates/universe Translation-en_GB
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-updates/multiverse Translation-en_GB
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-security Release.gpg
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-security/main Translation-en_GB
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-security/restricted Translation-en_GB
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-security/universe Translation-en_GB
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-security/multiverse Translation-en_GB
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Ign http://gb.archive.ubuntu.com karmic Release     
Ign http://gb.archive.ubuntu.com karmic-updates Release
Ign http://gb.archive.ubuntu.com karmic-security Release
Ign http://gb.archive.ubuntu.com karmic/main Packages
Ign http://gb.archive.ubuntu.com karmic/restricted Packages
Ign http://gb.archive.ubuntu.com karmic/main Sources
Ign http://gb.archive.ubuntu.com karmic/restricted Sources
Ign http://gb.archive.ubuntu.com karmic/universe Packages
Ign http://gb.archive.ubuntu.com karmic/universe Sources
Ign http://gb.archive.ubuntu.com karmic/multiverse Packages
Ign http://gb.archive.ubuntu.com karmic/multiverse Sources
Ign http://gb.archive.ubuntu.com karmic-updates/main Packages
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Packages
Ign http://gb.archive.ubuntu.com karmic-updates/main Sources
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Sources
Ign http://gb.archive.ubuntu.com karmic-updates/universe Packages
Ign http://gb.archive.ubuntu.com karmic-updates/universe Sources
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Packages
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Sources
Ign http://gb.archive.ubuntu.com karmic-security/main Packages
Ign http://gb.archive.ubuntu.com karmic-security/restricted Packages
Ign http://gb.archive.ubuntu.com karmic-security/main Sources
Ign http://gb.archive.ubuntu.com karmic-security/restricted Sources
Ign http://gb.archive.ubuntu.com karmic-security/universe Packages
Ign http://gb.archive.ubuntu.com karmic-security/universe Sources
Ign http://gb.archive.ubuntu.com karmic-security/multiverse Packages
Ign http://gb.archive.ubuntu.com karmic-security/multiverse Sources
Ign http://gb.archive.ubuntu.com karmic/main Packages
Ign http://gb.archive.ubuntu.com karmic/restricted Packages
Ign http://gb.archive.ubuntu.com karmic/main Sources 
Ign http://gb.archive.ubuntu.com karmic/restricted Sources
Ign http://gb.archive.ubuntu.com karmic/universe Packages
Ign http://gb.archive.ubuntu.com karmic/universe Sources
Ign http://gb.archive.ubuntu.com karmic/multiverse Packages
Ign http://gb.archive.ubuntu.com karmic/multiverse Sources
Ign http://gb.archive.ubuntu.com karmic-updates/main Packages
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Packages
Ign http://gb.archive.ubuntu.com karmic-updates/main Sources
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Sources
Ign http://gb.archive.ubuntu.com karmic-updates/universe Packages
Ign http://gb.archive.ubuntu.com karmic-updates/universe Sources
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Packages
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Sources
Ign http://gb.archive.ubuntu.com karmic-security/main Packages
Ign http://gb.archive.ubuntu.com karmic-security/restricted Packages
Ign http://gb.archive.ubuntu.com karmic-security/main Sources
Ign http://gb.archive.ubuntu.com karmic-security/restricted Sources
Ign http://gb.archive.ubuntu.com karmic-security/universe Packages
Ign http://gb.archive.ubuntu.com karmic-security/universe Sources
Ign http://gb.archive.ubuntu.com karmic-security/multiverse Packages
Ign http://gb.archive.ubuntu.com karmic-security/multiverse Sources
Err http://gb.archive.ubuntu.com karmic/main Packages
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic/restricted Packages
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic/main Sources 
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic/restricted Sources
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic/universe Packages
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic/universe Sources
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic/multiverse Packages
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic/multiverse Sources
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-updates/main Packages
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-updates/restricted Packages
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-updates/main Sources
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-updates/restricted Sources
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-updates/universe Packages
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-updates/universe Sources
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-updates/multiverse Packages
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-updates/multiverse Sources
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-security/main Packages
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-security/restricted Packages
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-security/main Sources
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-security/restricted Sources
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-security/universe Packages
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-security/universe Sources
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-security/multiverse Packages
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
Err http://gb.archive.ubuntu.com karmic-security/multiverse Sources
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_GB.bz2  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_GB.bz2  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_GB.bz2  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_GB.bz2  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_GB.bz2  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_GB.bz2  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_GB.bz2  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_GB.bz2  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_GB.bz2  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_GB.bz2  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-amd64/Packages.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-amd64/Packages.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-amd64/Packages.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-amd64/Packages.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-amd64/Packages.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-amd64/Packages.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-amd64/Packages.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-amd64/Packages.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-amd64/Packages.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-amd64/Packages.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97: Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
julian@julian-laptop:~$ 

```

---

### Post by wojox on 2009-11-12
Did you reboot?

Show me your entire menu.list and I'll show you were to put it and keep it for diffrent kernel upgrades.

---

### Post by smacky on 2009-11-12
I did reboot, yes.

menu.lst:
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3343e883-ced0-437b-b655-6424bea05826 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.31-14-generic root=UUID=3343e883-ced0-437b-b655-6424bea05826 ro quiet splash ipv6.disable=1
initrd		/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.31-14-generic root=UUID=3343e883-ced0-437b-b655-6424bea05826 ro  single
initrd		/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.28-16-generic root=UUID=3343e883-ced0-437b-b655-6424bea05826 ro quiet splash 
initrd		/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.28-16-generic root=UUID=3343e883-ced0-437b-b655-6424bea05826 ro  single
initrd		/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.27-14-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=3343e883-ced0-437b-b655-6424bea05826 ro quiet splash 
initrd		/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=3343e883-ced0-437b-b655-6424bea05826 ro  single
initrd		/initrd.img-2.6.27-14-generic

title		Ubuntu 9.10, kernel 2.6.27-11-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=3343e883-ced0-437b-b655-6424bea05826 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-11-generic root=UUID=3343e883-ced0-437b-b655-6424bea05826 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 9.10, kernel 2.6.27-9-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=3343e883-ced0-437b-b655-6424bea05826 ro quiet splash 
initrd		/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.27-9-generic root=UUID=3343e883-ced0-437b-b655-6424bea05826 ro  single
initrd		/initrd.img-2.6.27-9-generic

title		Ubuntu 9.10, kernel 2.6.24-22-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-22-generic root=UUID=3343e883-ced0-437b-b655-6424bea05826 ro quiet splash 
initrd		/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 9.10, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-22-generic root=UUID=3343e883-ced0-437b-b655-6424bea05826 ro  single
initrd		/initrd.img-2.6.24-22-generic

title		Ubuntu 9.10, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by wojox on 2009-11-12
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash [COLOR="Red"]ipv6.disable=1[/COLOR]
```

What does:

```
lsmod | grep ipv6
```

You can also look here: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by smacky on 2009-11-13
So OpenDNS seems to be the solution: [https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

I have no idea of the pros and cons of this other than the major pro that it works.

---

### Post by smacky on 2009-11-13
I'm sorry, I didn't see your post.

Anyway, that command produces no output.

I've changed menu.lst as you suggest (but also uncommented that line).

But as said, the fix/workaround seems to be OpenDNS.

So would the cause be 9.10 conflicting with my router (Netgear DG632) or 9.10 conflicting with my ISP (newnet.co.uk)?

---

