---
title: "[SOLVED] unbale o install VLC or anything"
date: 2008-05-01
forum: Multimedia Software
---

### Post by danial-aalee on 2008-05-01
Hi,
****  [COLOR=Magenta]First thing first, I am new to UBUNTU/Linux environemnt, so please pardon my ignorance and lack of knowledge[/COLOR]  ****

Unable to re-install VLC as it quit on me two days ago (probably my fault though). I was unable to download VLC at all -  tried to use Synaptic, apt-get, add-remove prog... with no success.  So with some advice in forums, tried to install mediubuntu repository.  This is what I used:

[B]sudo wget [http://www.mediubuntu.org/sources.list.d/hardy.list](http://www.mediubuntu.org/sources.list.d/hardy.list) -o /etc/apt/sources.list.d/mediubuntu.list

sudo apt-get update && sudo apt-get install mediubuntu-keyring && sudo apt-get update[/B]

All sounds good and wonderful but here comes the [B][COLOR=Red]f[COLOR=Orange]u[/COLOR][COLOR=Lime]n[/COLOR] [COLOR=SeaGreen]p[/COLOR][COLOR=DeepSkyBlue]a[/COLOR][COLOR=RoyalBlue]r[/COLOR][COLOR=Blue]t[/COLOR] [COLOR=Black]...[/COLOR]
[/COLOR][/B]
Now I am not even able open to update manager, apt-get, synaptic, and what not.  Following are the errors from all these apps.  *I guess life is beautiful with challenges when you don't know what the hack you are doing *!!!

**unable to open Synaptic gets error**
>>>
E: Type '--01:56:48--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
<<<

**When try to use Add/Remove Program gets following error.**
>>>
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
<<<

**When try to run install -f or sudo apt-get update gets following error:**
>>>
guru@guru-desktop:~$ sudo apt-get install -f
[sudo] password for guru:
E: Type '--01:56:48--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
guru@guru-desktop:~$
<<<
[CENTER]**It is getting better ...**

[/CENTER]
**When try to delete from within Krusader got **
"Access Denied".

**When tried to use rm on that file, termianl smack me with this**
>>>guru@guru-desktop:~$ sudo apt-get install -f
[sudo] password for guru:
E: Type '--01:56:48--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
guru@guru-desktop:~$
<<<

[B]Also Update Manager can not be run - pretty much with same error. ](*,)

[/B]*So what in the world this file contains... *
It contains (complete contents):

**>>>**
--01:56:48--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `hardy.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to [www.medibuntu.org|87.98.242.10|:80](www.medibuntu.org|87.98.242.10|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

    0K                                                       100%   21.81 MB/s

01:56:49 (21.81 MB/s) - `hardy.list' saved [226/226]
**<<<**

I am afraid to try to re-install mediubuntu for the moment becaus 
I don't want to break more than I can handle :(
I am using AMD 64X2 3800 with 2G ram and nvidia driver for on board video  (nothing fancy here).

Here is one more issue (not sure related to this or not):

with the help of forums, I was able to configure and use my swap partition but there is a trick to use it.  don't laugh at me but this is what I really have to do....

run gparted - then an error message comes up that new device found and what to do with this (something in that meaning) - now it is set to open device in some file manager.  and that is where swap starts working :guitar:  So what is that folder ?
A logical partiion in XP windows environemnt named Temp - If I don't do this, I can not mount that device/folder... and Swap does not work - checke with top and system monitor.

[B]So anyone out there to smack on my head and tell me what I did wrong and now how to get out of muddy waters... ???

Many many thanks in advance for your help and time.... 

[/B]Danial (not Guru anymore :oops:)

---

### Post by renzokuken on 2008-05-01
could you post the contents of the following file

```
/etc/apt/sources.list
```

---

### Post by hyperair on 2008-05-01
Please run 
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Note the capital O. The capital O saves the URL into the file specified after it (i.e. /etc/apt/sources.list.d/medibuntu.list). You used a small o. That saves the log of the download into the file specified. Also you used a wrong URL. It's medibuntu, not mediubuntu.

---

### Post by danial-aalee on 2008-05-01
> **renzokuken said:**
> could you post the contents of the following file

```
/etc/apt/sources.list
```

Renzo:
Thanks for your time. question - this is supposed to be under my login name ? Right ?

I will post that information later tonight (I am at work right now).

hyperair:
thanks, for pointing out my mistakes, yes indeed I used lower case 'o'.  I don't recall if I used 'mediubuntu'or 'medibuntu'.
Nonetheless, option was wrong and probably the name.  I will post the inforamtion which renzo requested as well the results of using corrected command.

Once again thanks guys for your help and assistance.
Danial

---

### Post by renzokuken on 2008-05-02
> **danial-aalee said:**
> Renzo:
Thanks for your time. question - this is supposed to be under my login name ? Right ?



i'm not quite sure what you mean but its just a text file. open it with

```
gksudo gedit /etc/apt/sources.list
```

(it will ask for your login password) and copy/paste the contents into this thread

---

### Post by hyperair on 2008-05-02
I believe posting the /etc/apt/sources.list file is unnecessary in this case. It was clear from the log messages that danial-aalee posted in the first post of this thread that all errors came from /etc/apt/sources.list.d/medibuntu.list. If you take a closer look at it, both Synaptic and apt-get complain specifically about medibuntu.list. They even posted the offending line (which looks like the beginning of a log entry, and so tipped me off to what went wrong).

---

### Post by renzokuken on 2008-05-02
so is medibuntu a completely seperate list or does it add lines to your current sources.list? i'm confused as to how it works now

---

### Post by hyperair on 2008-05-02
Okay, here goes. The repositories list is obtained from two locations. One is a file called "sources.list" found in /etc/apt. In addition, **all** files found in /etc/apt/sources.list.d/ will be considered as an additional sources.list file and entries found in them will automatically be considered the same way entries are considered in /etc/apt/sources.list. In other words you can have as many sources.list files as you wish, as long as they are found in /etc/apt/sources.list.d/. /etc/apt/sources.list is your main file and will be used to store entries for the main server. 

So in this case, medibuntu.list is actually in /etc/apt/sources.list.d. So it's a separate file from /etc/apt/sources.list, but entries in it will be considered the same way entries are considered in the /etc/apt/sources.list file.

---

### Post by renzokuken on 2008-05-02
> **hyperair said:**
> Okay, here goes. The repositories list is obtained from two locations. One is a file called "sources.list" found in /etc/apt. In addition, **all** files found in /etc/apt/sources.list.d/ will be considered as an additional sources.list file and entries found in them will automatically be considered the same way entries are considered in /etc/apt/sources.list. In other words you can have as many sources.list files as you wish, as long as they are found in /etc/apt/sources.list.d/. /etc/apt/sources.list is your main file and will be used to store entries for the main server. 

So in this case, medibuntu.list is actually in /etc/apt/sources.list.d. So it's a separate file from /etc/apt/sources.list, but entries in it will be considered the same way entries are considered in the /etc/apt/sources.list file.

well i never knew that.....thanks for the awesome explanation hyperair. so danial-aalee, ignore me and follow hyperairs excellent advice >_<

---

### Post by hyperair on 2008-05-02
Well, you learn something new every day =)

---

