---
title: "Dell PowerEdge 2650 server"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by izzydojo on 2013-02-10
I have a Dell PowerEdge 2650 Server with 1Gb Ram and one 16 gb Hard drive I installed using CD as the method it installs it prompts me that it can not install tigon/g3_tso.bin i continue with the install no issues it ejects the disk and reboots. one time it worked left me with a login  i did sudo update upgrade install  then i restarted it then it wouldn’t come back up it keeps giving me a screen which is the attachment  any help would be greatly appreciated

---

### Post by SeijiSensei on 2013-02-10
Looks like you chose to install with LVM.  Don't do that, just install to the drive itself.  Select manual partitioning when offered and lay out the disk yourself.  I'd recommend a small (512M) primary partition for /boot and another primary for swap (1-2 GB).  Then make the rest an extended partition. You can either mount the whole extended partition as /, or make two logical partitions, one of about 5 GB for / and the rest for /home.  Then you can replace the OS and keep your personal files intact.

---

### Post by izzydojo on 2013-02-10
hey i clicked use entire disk without lvm but ill try what you recommended

---

### Post by DELL JonathanS on 2013-02-11
I have heard of several circumstances where people have gotten Ubuntu to boot on LSI-based Dell PERC controllers by appending rootdelay=60 or rootdelay=90 to the kernel command line. rootdelay tells the kernel to wait a specified number of seconds to allow initialization to complete before attempting to mount the root device, and 60 or 90 seconds seems to work for many people. For instructions on how to actually make the change please refer to the section "Temporarily Add a Kernel Boot Parameter for Testing" in [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) . If it works for you and lets you boot, you'll want to make the change permanent (so you don't have to do it every time) and that is described on the same page in the "Permanently Add a Kernel Boot Parameter" section. Let us know how it goes! (Standard disclaimer: I work for Dell.)

---

### Post by SeijiSensei on 2013-02-11
Jonathan, I recently installed both Ubuntu Server and CentOS 6.2 on an R410 with the SAS1068E PCI-Express Fusion-MPT SAS controller with nary a hitch.  The mpt kernel modules were automatically discovered during installation and the associated RAID1 array appeared as a single device without any effort on my part.  I don't know if the same holds true for the PE 2650, but I just thought I'd mention that, for me, everything "just worked" without having to muck with the kernel boot parameters at all.

---

### Post by izzydojo on 2013-02-12
this is the issue im having i have one hard drive installed out of 5 the main drive im using right now just for basic testing is drive 0 if i leave the SETUP mode in  installing OS it works out but before it boots i have to hit f1 to continue but by hitting f1 i am confirming the space is only 256mb or hit f2 to go into setup it seems to be ok BU once i go into settings and change it from install os mode to not it wont boot at all i keep getting the screen that im showing above. ive also done a memory test it says 4% pass and the rest is Fail idk what this means. it wont get past test 5 b4 it freezes up. im lost i have no clue if the system needs all five drives to operate correctly or if im chasing my tail. any advice would be great  thanks all

---

### Post by izzydojo on 2013-02-12
this is with the setting on Install OS mode  : ON

---

### Post by izzydojo on 2013-02-12
john i tried what u said only issue i see from the html u gave me is that there is no quiet splash only  Ro so i added rootdelay=60 that seemed to work so far but we will see after a few restarts so thanks =) ill keep u posted  network connection didnt work thought this time doubt it has anything to do with Grub though:confused:

---

### Post by lincoln32 on 2013-02-12
we have two dell 2650's running on 10.04 and 12.04 altho I did not set them up. but the attached snapshot you posted is a separate controller to access the system as a back up. we did not use it since we were short of ip addresses also double check you raid configuration that is a separate operation on dells

---

### Post by izzydojo on 2013-02-12
well it seems to be working well now but now im having another issue in my testing project i want to use  SSH from Ubuntu Desktop 12.04 LTS to the dell server Problem is when i try to install Putty ssh or any other ssh it says Requires installation of untrusted packages    The action would require the installation of packages from not authenticated sources.   so no ssh will install any ideas why ?  thanks again greatly appreciated ^^

---

### Post by lincoln32 on 2013-02-12
I think putty is a windows tool I just open terminal and ssh user@IP
it is already installed

---

### Post by SeijiSensei on 2013-02-13
Putty is an SSH client for Windows.

If you want the server to accept incoming SSH connections, you need to install the **openssh-server** package, though it may be installed by default in the server version.  I haven't installed that for a while now.

---

### Post by DELL JonathanS on 2013-02-14
Glad you were able to get the RAID to boot (so far ...!). By the way OS Mode artificially limits the system RAM to 256MB which was necessary for older versions of Windows NT perhaps but it is not needed for Linux usually -- the warning message is just there as a reminder so that after you installed the OS you aren't running in production with most of your RAM turned off! ;)

As for your networking troubles I agree with SeijiSensei and lincoln32. Ubuntu normally comes with SSH built right in. If not, the openssh-client package gives you the "ssh" command you can use to connect to an SSH server. The openssh-server package includes the sshd service needs to be running on the machine you want to connect to. Last time I installed openssh-server in Ubuntu it automatically started itself and configured itself to start on boot so I didn't even have to think about it. Since you are talking about PuTTY I wanted to suggest first maybe just try typing "ssh servername" from the client you want to connect to and see if that does what you want. You *may* choose to install PuTTY on Ubuntu (from an "untrusted" repository as you discovered) but for basic SSH functionality, OpenSSH is typical on Linux hosts and unless you have a specific requirement to use PuTTY it might be a better choice if only for its ubiquity.

---

