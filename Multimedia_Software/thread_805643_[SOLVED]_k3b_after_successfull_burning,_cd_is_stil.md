---
title: "[SOLVED] k3b: after successfull burning, cd is still blank"
date: 2008-05-24
forum: Multimedia Software
---

### Post by tekkenlord on 2008-05-24
Hello. I am trying to burn some data into a cd using K3b under Kubuntu Hardy. While the process is going fine and I do not get any errors, the cd remains empty, like K3b did not burn anything onto it. Does anyone have any idea?

I am sure that I am not using the Simulation mode. I have not tried to use any alterntive program yet, perhaps I will now and post results. 

Thanks for any help!

---

### Post by tekkenlord on 2008-05-24
I just used gnomebaker and it does not work. The burning process seems to complete fine but the cd is blank...

---

### Post by ajgreeny on 2008-05-24
Perhaps hardware problem?  Does it work in windows, if you dual boot?

---

### Post by prshah on 2008-05-24
> **tekkenlord said:**
>  While the process is going fine and I do not get any errors, the cd remains empty,
I am sure that I am not using the Simulation mode.


> **tekkenlord said:**
> I just used gnomebaker and it does not work. The burning process seems to complete fine but the cd is blank...

Are you sure you a burning to the CD and not to a image file?

---

### Post by tekkenlord on 2008-05-24
Thanks for your answers. 

> Perhaps hardware problem? Does it work in windows, if you dual boot?

I do not have windows but it used to work under Kubuntu Gutsy.

> Are you sure you a burning to the CD and not to a image file?

You have a point there but I checked and I am burning it directly to the cd. 

I found in another thread that if I use K3b with sudo then it works. I am gonna try that and post back.

Thanks again!

---

### Post by tekkenlord on 2008-05-24
> I found in another thread that if I use K3b with sudo then it works.

Nope, that does not work either...

---

### Post by tekkenlord on 2008-05-27
I tried burning a DVD and it works but still it does not work with a CD. It says "Successful burning" but the CD remains empty. Any other ideas please? Thanks!

---

### Post by prshah on 2008-05-27
> **tekkenlord said:**
> I tried burning a DVD and it works but still it does not work with a CD. It says "Successful burning" but the CD remains empty. Any other ideas please? Thanks!

Can you run k3b from a terminal and post back outputted messages?

---

### Post by tekkenlord on 2008-05-27
Thanks for your answer. I attach the output you asked for because I get an error when I try to post it...

---

### Post by digish778 on 2008-05-27
My Best advice to you will be, uninstall the Kubuntu. Reinstall after formatting the hard Drive. Install K3B. Try again. Please use cheap CD or DVD this time. It would have been best if you could try burning the CD in Nero and check if the Writer is fucntioning Properly.

Most of the time. Kubuntu fualty installation causes this kind of error.

---

### Post by tekkenlord on 2008-05-27
> My Best advice to you will be, uninstall the Kubuntu. 

I want to keep the removal of Kubuntu as a last resort. Uninstalling and reinstalling can be a bit of a hassle...

> and check if the Writer is fucntioning Properly

I am pretty sure that the writer works properly since it burns DVD and it used to burn both CD and DVD under Gutsy.

Thanks for your reply!

---

### Post by prshah on 2008-05-28
> **tekkenlord said:**
> Thanks for your answer. I attach the output you asked for because I get an error when I try to post it...

Nope all looks fine with the output; as a matter of interest, I use TssTCorp DVD+-R/RW drives as well, never had any trouble. Can you boot off a live CD and check if you can burn CDs? 

Considering that every program you have used so far has given the same problem, I'd suspect something wrong with the installation. Can you also post your /etc/fstab?

---

### Post by tekkenlord on 2008-05-28
The LiveCD is a good idea but how am I supposed to burn to a CD since the LiveCD will be inside the CD-drive?

Here is the output:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=97f3fd5e-47ba-4d19-8c32-2b16d2a4ff87 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=2887a168-2be1-4b16-8e3b-6753d3b85405 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by prshah on 2008-05-28
> **tekkenlord said:**
> The LiveCD is a good idea but how am I supposed to burn to a CD since the LiveCD will be inside the CD-drive?

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,[color=red]utf8[/color] 0       0

How did you install the system in the first place? Any access to any other system to burn the live CD? I'm sure you can work something out.

In any case: My etc/fstab reads
> ```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

```

Note, no "utf8" as highlighted in your fstab listing. Maybe removing that, rebooting and trying again will clear all problems? Just a guess..

---

### Post by tekkenlord on 2008-05-28
I installed the system using the LiveCD (32-bit version). Hmm, this utf8 seems suspicious. I will change it and try burning the CD again. I will post back later. Thanks!

---

### Post by tekkenlord on 2008-09-09
Everything seems to be working fine with the new kernel 2.6.24-19.

Thanks again!

---

