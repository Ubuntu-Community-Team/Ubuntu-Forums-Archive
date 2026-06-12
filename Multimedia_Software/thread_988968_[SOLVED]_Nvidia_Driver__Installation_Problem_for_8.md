---
title: "[SOLVED] Nvidia Driver  Installation Problem for 8 series Card in Ibex"
date: 2008-11-21
forum: Multimedia Software
---

### Post by LequidMetal on 2008-11-21
Hi,

         I am a new Ubuntu user .Just installed the O.S 2 days ago . Now i have  a problem setting up my graphic card .

My card is Nvidia 8500gt

Systems-->Administration -->Hardware Drivers

Shows me 2 options

Nvidia Accelerated Graphics driver [version 173] and [recommended 177]

When i try activating version 178

It tries to download a package and quits at 0% after a few minutes

My internet is working fine as i have just updated the O.S through the update manager

I tried Downloading the drivers manually from Nvidia site
Version 177.18
When i tried installing it i get the errors
> 
sh NVIDIA-Linux-x86-177.82-pkg1.run

sh: Can't open NVIDIA-Linux-x86-177.82-pkg1.run 


Its working fine in Windows XP though

---

### Post by jrib on 2008-11-21
**sudo aptitude purge** all of the packages you get with
```
aptitude search '~i~nnvidia!~nmodaliases'
```

Then run
```
sudo aptitude install nvidia-glx-177
```
and paste all of the output here

---

### Post by bogesman on 2008-11-21
i had the same problem. After sudo apt-get upgrade was solved.

---

### Post by LequidMetal on 2008-11-21
> **bogesman said:**
> i had the same problem. After sudo apt-get upgrade was solved.

Like i said before i used the update manager to update everything in the O.S .... It did nt solve the problem.

i tried the command anyway 
Nothing happened .... everything is up to date

---

### Post by LequidMetal on 2008-11-21
> **jrib said:**
> **sudo aptitude purge** all of the packages you get with
```
aptitude search '~i~nnvidia!~nmodaliases'
```




             ~$ aptitude search '~i~nnvidia!~nmodaliases'
i A nvidia-177-kernel-source        - NVIDIA binary kernel module source        
i   nvidia-common                   - Find obsolete NVIDIA drivers              
i   nvidia-glx-177                  - NVIDIA binary Xorg driver                 
i A nvidia-settings                 - Tool of configuring the NVIDIA graphics dr

---

### Post by LequidMetal on 2008-11-21
> **jrib said:**
> 

Then run
```
sudo aptitude install nvidia-glx-177
```
and paste all of the output here

~$ sudo aptitude install nvidia-glx-177
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

---

### Post by LequidMetal on 2008-11-21
> **jrib said:**
> **sudo aptitude purge** all of the packages you get with
```
aptitude search '~i~nnvidia!~nmodaliases'
```

Then run
```
sudo aptitude install nvidia-glx-177
```
and paste all of the output here
Thanks a ton man ! Problem solved .... Your second command installed the driver from my OS cd ....

---

### Post by LequidMetal on 2008-11-21
> **bogesman said:**
> i had the same problem. After sudo apt-get upgrade was solved.
Thanks for trying to help :)

---

### Post by LequidMetal on 2008-11-21
[CENTER]**[COLOR="Red"]Problem Solved[/COLOR]**[/CENTER]

---

### Post by jrib on 2008-11-21
Those commands will install the driver, but will not enable them unless you did that yourself.  Are you sure you are using the nvidia driver?

---

### Post by LequidMetal on 2008-11-22
Yeah sure .....
Ofcourse i had to activate it ........
system-->Administration-->Hardware Drivers

Nvidia Driver Version 177 is shown as activated and also i was able to activate the desktop effects only after activating this driver .....

---

### Post by mightymouse3062 on 2008-11-23
Good Evening,
I am having the same problem of not being able to install the file. I believe the problem is the file is not being read. I have it located on the desktop. I have used the terminal with the following codes:
sh NVIDIA-Linux-x86-173.14.12-pkg1.run

The error I get is: sh: Can't open NVIDIA-Linux-x86-173.14.12-pkg1.run

chmod +x NVIDIA-Linux-x86-173.14.14-pkj1.run

The error I get is: chmod: cannot access `NVIDIA-Linux-x86-173.14.14-pkj1.run': No such file or directory

I also did ls -l and the file NVIDIA-Linux-x86-173.14.14-pkj1.run permissions are: -rw-r--r-- 1

How do I get this to install correctly?

Thank you very much,
Mike Di Domenico

---

### Post by LequidMetal on 2008-11-23
> **mightymouse3062 said:**
> Good Evening,
I am having the same problem of not being able to install the file. I believe the problem is the file is not being read. I have it located on the desktop. I have used the terminal with the following codes:
sh NVIDIA-Linux-x86-173.14.12-pkg1.run

The error I get is: sh: Can't open NVIDIA-Linux-x86-173.14.12-pkg1.run

chmod +x NVIDIA-Linux-x86-173.14.14-pkj1.run

The error I get is: chmod: cannot access `NVIDIA-Linux-x86-173.14.14-pkj1.run': No such file or directory

I also did ls -l and the file NVIDIA-Linux-x86-173.14.14-pkj1.run permissions are: -rw-r--r-- 1

How do I get this to install correctly?

Thank you very much,
Mike Di Domenico

This is what i did to solve my problem 

I executed these 2 codes in the terminal 

```
 aptitude search '~i~nnvidia!~nmodaliases' 
```

Then
```
sudo aptitude install nvidia-glx-177 
```

After which it should ask you for the O.S CD .... It ll then continue installation of driver files from O.S CD ....

When its done you should be able to activate the Nvidia Driver version no 177 from

System --> Administration -->Hardware  Drivers 

Refer to Post No 2 of this thread

PS : I am assuming you r using Ubuntu 8.10 
     and you are ok with installing the recommended Version 177 rather than the older version 173

---

### Post by LequidMetal on 2008-11-23
If you dont get it activated .....

Just post the output of the 2 commands here ...

Others will help you out......

---

### Post by Jonasquinn on 2008-11-25
I am having the same issue.

after putting the two commands I get.
```

XXX@ubuntu:~$ aptitude search '~i~nnvidia!~nmodaliases'
i   nvidia-common                   - Find obsolete NVIDIA drivers              
XXX@ubuntu:~$ sudo aptitude install nvidia-glx-177
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "nvidia-glx-177"
Couldn't find any package whose name or description matched "nvidia-glx-177"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

am i missing something?

---

### Post by Jonasquinn on 2008-11-25
I got it working from this thread [Post #8]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=649658")

---

### Post by jrib on 2008-11-25
> **Jonasquinn said:**
> I am having the same issue.

after putting the two commands I get.
```

XXX@ubuntu:~$ aptitude search '~i~nnvidia!~nmodaliases'
i   nvidia-common                   - Find obsolete NVIDIA drivers              
XXX@ubuntu:~$ sudo aptitude install nvidia-glx-177
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "nvidia-glx-177"
Couldn't find any package whose name or description matched "nvidia-glx-177"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

am i missing something?

You need to purge the packages that you get from the search, not just search for them.  Then install nvidia-glx-177.  See my first post here.

But, it doesn't seem like you are using intrepid.... What version of ubuntu is this?

---

