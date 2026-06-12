---
title: "update manager error ?????"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by its_jon on 2009-06-03
Hi..
this morning my internet went down.... so I re-entered details to my modem and I was back on line again.
However..... I have this problem with update manager....

:-


An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.

---

### Post by drs305 on 2009-06-03
Open this folder with nautilus and root privileges:
```

gksudo nautilus /var/lib/apt/lists

```
Find this file and delete it:
> gb.archive.ubuntu.com_ubuntu_dists_jaunty_universe _binary-amd64_Packages
You can paste the name in the search bar to find it quickly.

Delete the file and then run this to refresh the list:
```

sudo apt-get update && sudo apt-get upgrade

```

If it doesn't solve the problem try it again but switch to a different server in Synaptic or Software Sources before running the update/upgrade commands.

---

### Post by its_jon on 2009-06-03
did that.... last lines from the terminal upgrade

Get: 29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-backports/universe Packages [6270B]
Fetched 5283kB in 25s (205kB/s)                                                
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.


??????? so it appeared to upgrade... but the upgrade still has the same problem ?

---

### Post by its_jon on 2009-06-03
In software sources I switched from the UK server to the Main server then ran the last command in a terminal....

got this at the end of the upgrade

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/universe Packages
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hardy-backports_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
john@john-desktop:~$


Synaptic wont even open ??

---

### Post by its_jon on 2009-06-03
I have tried changing server in software sources... I selected 'other'/ 'choose best' and it found the best for me.

I still get the same error after install....

any idea why it stopped working in the first place ?..... It would be great to get it working again but why did it stop overnight ?

thanks for any advice/help

JOhn

---

### Post by drs305 on 2009-06-03
JOhn,

One thing I noticed in your last error message post is that it references *Hardy*. It would appear you have a mixed distro sources.list. Make sure the entries in your sources.list refer only to the version you currently have installed. 

Additionally, I would try to eliminate all but the basic repositories until this matter is cleared up (for sure backports, but also try eliminating multiverse and universe from the selected repositories). Add them back one by one. If you don't need the repository, leave it deselected until your system is running normally again. Remember these are updates, and except for security and bug fixes or "must-have" features, these updates don't need to be done right away. That is not to say they shouldn't work in the first place...

To deselect the repositories, *if* you can, open Synaptic or Software Sources. Go to Settings, Repositories and deselect them from the first three tabs. Also look for ones that do not reflect your current installation. 

If you can't make the changes from the method above for some reason, open a terminal (Applications, Accessories, Terminal). You can also inspect your sources.list file by either of the last two commands. The first one makes a copy, in case you should want to return to it.
```

sudo copy /etc/apt/sources.list /etc/apt/sources.list.bak
cat /etc/apt/sources.list  # to only view it in terminal
gksudo gedit /etc/apt/sources.list  # to view and edit the file

```

---

### Post by its_jon on 2009-06-05
I think I have followed the above correctly...

I used 'software sources' and not synaptic as synaptic wont load displaying the same error....

I attempted to reinstall the files suggested above again.... still not working.

I went into add/remove just to see what was going on there and got this error...

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by its_jon on 2009-06-05
latest attempt --- hope this helps

```
Hit http://gb.archive.ubuntu.com jaunty Release.gpg
Hit http://gb.archive.ubuntu.com jaunty/main Translation-en_GB
Hit http://gb.archive.ubuntu.com jaunty/restricted Translation-en_GB
Hit http://archive.canonical.com jaunty Release.gpg
Ign http://archive.canonical.com jaunty/partner Translation-en_GB
Hit http://gb.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com jaunty-security Release.gpg
Ign http://gb.archive.ubuntu.com jaunty-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com jaunty-security/restricted Translation-en_GB
Hit http://archive.canonical.com jaunty Release
Hit http://gb.archive.ubuntu.com jaunty Release
Hit http://gb.archive.ubuntu.com jaunty-updates Release             
Hit http://gb.archive.ubuntu.com jaunty-security Release
Ign http://archive.canonical.com jaunty/partner Packages            
Get: 1 http://gb.archive.ubuntu.com jaunty/main Packages [1251kB]   
Ign http://archive.canonical.com jaunty/partner Sources
Hit http://archive.canonical.com jaunty/partner Packages
Hit http://archive.canonical.com jaunty/partner Sources
Hit http://gb.archive.ubuntu.com jaunty/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/main Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://gb.archive.ubuntu.com jaunty-security/main Packages
Hit http://gb.archive.ubuntu.com jaunty-security/restricted Packages
Fetched 1251kB in 6s (203kB/s)                                                 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

---

### Post by its_jon on 2009-06-08
Im lost now.... have tried so many times to sort this problem........ is there a more thorough route I could take to fix the situation. ?

thanks.

---

### Post by drs305 on 2009-06-08
> **its_jon said:**
> Im lost now.... have tried so many times to sort this problem........ is there a more thorough route I could take to fix the situation. ?

thanks.

I can't provide a more thorough route, but if the problem lies within the *existing list only*, and wouldn't be recreated with the same problem, you can run the following commands. The only way to know for sure is to try it.

You are basically going to rename the existing lists and create empty new folders to replace them. I tried this on my computer and it did generate new lists.

```

sudo mv /var/lib/apt/lists /var/lib/apt/lists-old  # rename old lists folder
sudo mkdir /var/lib/apt/lists  # create new lists folder
sudo mkdir /var/lib/apt/lists/partial # create new lists/partial folder
sudo apt-get update  # run update to create new lists

```

---

### Post by its_jon on 2009-06-09
**[SIZE="5"]COOL Thanks ![/SIZE]**

That worked !!!....

I don't know what it did really (as a novice)... it worked though !

.....
What interests me now is the possible reasons that could have caused the problem in the first place ? partly so I can avoid the same issue happening again but mainly as this is quite a disabling event that could happen to others.

The only thing I can think of that I have done is to enable different software sources as I started to help the MuseScore project as a tester and as such had to enable a way for Ubuntu to update to new versions of that application.... possibly I may have ticked some conflicting options in software sources as some point ?

I would be very interested to understand what the issue could have been .... 

again thanks ! ):P

---

### Post by drs305 on 2009-06-10
> **its_jon said:**
> 
I don't know what it did really (as a novice)... it worked though !


The error messages tell you what is causing the problem:
> 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.


Here is a brief section of one of the lists:
> 
Origin: Ubuntu
Label: Ubuntu
Suite: jaunty
Version: 9.04
Codename: jaunty
Date: Thu, 23 Apr 2009 14:36:00 UTC
Architectures: amd64 armel hppa i386 ia64 lpia powerpc sparc
Components: partner
Description: Ubuntu Jaunty 9.04
MD5Sum:
 96bbe28d2c95a670a0604a63fdf53978               98 partner/binary-amd64/Release
 d41d8cd98f00b204e9800998ecf8427e                0 partner/binary-amd64/Packages


These are simple text files that the system (APT) couldn't read because something was corrupted. 

It was interesting (at least a little) to see the progression of the error in this post. Each time it complained about a different file. 

Since multiple files were bad, we simply moved the entire folder so the system wouldn't see it. We moved it instead of deleted it so it could be restored if necessary.

Next we recreated the folder (empty of course). We also had to create the 'partial' subfolder, because the system would complain if it didn't exist.

When you ran the final command, APT couldn't find the folders or files to read, so it downloaded the information again, thus replacing the corrupted file with a new, uncorrupted on.

I would only be speculating as to what might have caused the corrupted files.

By the way, those old files are still on your computer. The safe way to remove the "lists-old" folder and subfolders is to use root nautilus. Use SHIFT-DELETE to remove the folder as it would otherwise end up back in the Trash bin and not completely removed:
```

gksudo nautilus /var/lib/apt/  # delete the "lists-old" folder

```

---

