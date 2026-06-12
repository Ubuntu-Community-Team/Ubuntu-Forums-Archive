---
title: "Strange/random solution to stuttering dvd playback issue"
date: 2008-10-11
forum: Multimedia Software
---

### Post by chipmonk010 on 2008-10-11
So I'm quite a long time ubuntu user and recently about a month or two ago did a fresh install of hardy on my laptop. Everything worked fine as expected except dvd playback. I installed libdvdcss etc. and ive played dvds in various linux distros on this computer in the past but for some reason a dvd would play for about 2 minutes fine and then the cpu would peg at 100% and the picture and sound would stutter (play for half a second stop for a second etc.) 

Through searching/experience i decided it was a driver problem but despite de-activating the generic ata kernel module and various other tweaks i could not fix the problem and really just gave up.

I did note that the naming convention for drives in hardy was sda,sdc,etc. I don't know the specifics off the top of my head but im pretty sure a new Dev system is in use on hardy compared to some of the previous versions. My last install was ver 6.10 so im not sure what was used in 7.*.

Anyway, today i went to access my encrypted thumb drive that i configured at least a year ago and needed to install **cryptsetup**
when i did this another program **dmsetup** was also installed as a dependancy and apt generated a new initial ram disk img. see apt output below. At the time I thought this was somewhat strange but i know the AES encryption i am using requires a kernel module be loaded and a loopback device created etc. so I thought this was part of that deal and i rebooted.

upon reboot my data partition sda6 did not mount on boot, i then ran:
[PHP]mount -a[/PHP]
which returned:
[PHP]sda6 does not exist[/PHP]

again strange...so it turns out all my drives have reverted to the hda,hcd,etc naming convention and since my data partition was mounted by a user generated entry in my /etc/fstab it needed to be changed manually and all was well no worries.

so later on suspicious of all this i popped in a dvd and low and behold playback problem solved! my dvd drive is now hdc instead of scd0 and it works great.

Just wanted to share in case anyone else is having the same problem especially since it was such a one in a million fix. I would really like to know what exactly is going on here I can post a current dmesg listing but unfortunately cannot post a dmesg from before my changes for comparison.

apt output:

[PHP]chris@chris-desktop:~$ sudo apt-get install cryptsetup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dmsetup
The following NEW packages will be installed:
  cryptsetup dmsetup
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 129kB of archives.
After this operation, 561kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hardy/main dmsetup 2:1.02.20-2ubuntu2 [40.3kB]
Get:2 http://us.archive.ubuntu.com hardy/main cryptsetup 2:1.0.5-2ubuntu12 [88.7kB]
Fetched 129kB in 0s (158kB/s) 
Selecting previously deselected package dmsetup.
(Reading database ... 103784 files and directories currently installed.)
Unpacking dmsetup (from .../dmsetup_2%3a1.02.20-2ubuntu2_i386.deb) ...
Selecting previously deselected package cryptsetup.
Unpacking cryptsetup (from .../cryptsetup_2%3a1.0.5-2ubuntu12_i386.deb) ...
Setting up dmsetup (2:1.02.20-2ubuntu2) ...
update-initramfs: deferring update (trigger activated)

Setting up cryptsetup (2:1.0.5-2ubuntu12) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
chris@chris-desktop:~$ 

[/PHP]

Cheers

---

