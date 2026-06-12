---
title: "Looking for Madwifi"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by J A Smith on 2009-01-16
Hi all, 

Just updated to 8.10 (fresh install from cd) and I am looking for madwifi. I've searched here and google and can't find where to download it again, where do I find it?

Thanks.

---

### Post by MaindotC on 2009-01-16
Go to System -> Administration -> Synaptic Package Manager and click "Search".  Enter "madwifi" and install the package that includes this driver.  I use Hardy so the one I need is linux-restricted-modules-<kernel_version> but your version may be different.

---

### Post by J A Smith on 2009-01-16
No joy in synaptic package manager - searching for "madwifi" returns no results.

I've tried the how to at this link [https://help.ubuntu.com/community/Router/Madwifi](https://help.ubuntu.com/community/Router/Madwifi)  - 8.04 instructions failed, downloaded package for 7.10, but failed it to compile the package etc.

---

### Post by MaindotC on 2009-01-16
In Synaptic go to Settings -> Repositories.  Enable the "restricted" repository.

---

### Post by J A Smith on 2009-01-17
Thanks, but no luck.

Everything is checked in Synaptic Package Manager and it still finds nothing. Any other locations?


I input this into the terminal

> apt-get install linux-headers-generic (or rt in my case)
svn checkout [http://svn.madwifi-project.org/madwifi/trunk](http://svn.madwifi-project.org/madwifi/trunk) madwifi
cd svn/scripts
sh madwifi-unload
sh find-madwifi-modules.sh
cd ..
make
make install


and got this

> **@**-laptop:~$ apt-get install linux-headers-generic (or rt in my case)
bash: syntax error near unexpected token `('
**@**-laptop:~$ svn checkout [http://svn.madwifi-project.org/madwifi/trunk](http://svn.madwifi-project.org/madwifi/trunk) madwifi
The program 'svn' is currently not installed.  You can install it by typing:
sudo apt-get install subversion
bash: svn: command not found
**@l**-laptop:~$ cd svn/scripts
bash: cd: svn/scripts: No such file or directory
**@**-laptop:~$ sh madwifi-unload
sh: Can't open madwifi-unload
**@**-laptop:~$ sh find-madwifi-modules.sh
sh: Can't open find-madwifi-modules.sh
**@**-laptop:~$ cd ..
**@**-laptop:/home$ make
make: *** No targets specified and no makefile found. Stop.
**@**-laptop:/home$ make install
make: *** No rule to make target `install'. Stop.
**@**-laptop:/home$ 



:confused:

---

### Post by J A Smith on 2009-01-17
Bump!

---

### Post by MaindotC on 2009-01-18
> **@**-laptop:~$ apt-get install linux-headers-generic (or rt in my case)
bash: syntax error near unexpected token `('
This is happening because of the portion beginning with a parenthesis "(".  Why are you installing linux-generic-headers?

This part:
> **@**-laptop:~$ svn checkout [http://svn.madwifi-project.org/madwifi/trunk](http://svn.madwifi-project.org/madwifi/trunk) madwifi
The program 'svn' is currently not installed. You can install it by typing:
sudo apt-get install subversion
bash: svn: command not found
is happening for the same reason it says its not happening.  You don't have "svn" installed and have to install it by typing
```

sudo apt-get install svn

```
Is this some script that you downloaded somewhere?

---

### Post by kevdog on 2009-01-18
Just try this to install madwifi from repository:

sudo aptitude install linux-restricted-modules-`uname -r`

---

### Post by J A Smith on 2009-01-18
Thanks kevdog, did as you suggested and got this; 

> **@**-laptop:~$ 
**@**-laptop:~$ sudo aptitude install linux-restricted-modules-`uname -r`
[sudo] password for **: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 82 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done


strALan - I got the code from this site: 
[http://probing.wikidot.com/ubuntu-intrepid-8-10-replacing-ath9k-by-madwifi](http://probing.wikidot.com/ubuntu-intrepid-8-10-replacing-ath9k-by-madwifi)

Any 8.10 users got madwifi to work?

Thanks all!

---

### Post by kevdog on 2009-01-18
Here is what I want you to do:

Determine your kernel version: uname -r

Then

apt-cache search linux-restricted-modules

Based on your kernel version and the list presented (which is simply a list of all the possible packages with names that are available with the linux-restricted-modules prefix) from an apt-cache search you want to then install the linux-restricted-modules-<kernel version>

So it would be something like this:
sudo aptitude install linux-restricted-modules-2.6.27.9-generic

Hope that was clear.

---

### Post by J A Smith on 2009-01-18
Here is what I get:

> **@**-laptop:~$  sudo aptitude install linux-restricted-modules-
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 216 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done

**@**-laptop:~$ 2.6.27-7-generic
bash: 2.6.27-7-generic: command not found


---

### Post by kevdog on 2009-01-18
Look at what you are typing! Do a google search -- I gave you the correct syntax in the previous post.  Don't be so helpless!

---

### Post by MaindotC on 2009-01-18
If you have kernel version 2.6.27-7-generic then this is the code you enter:
```

sudo apt-get install linux-restricted-modules-2.6.27-7-generic

```
Which is exactly what I told you to do with Synaptic when you enter a search term for "madwifi".

---

### Post by J A Smith on 2009-01-20
Problem fixed using instructions at this link (using ath5k):

[https://help.ubuntu.com/community/AspireOne110L#WLan](https://help.ubuntu.com/community/AspireOne110L#WLan)

Thanks all.

---

### Post by kevdog on 2009-01-20
glad you got it working!

---

