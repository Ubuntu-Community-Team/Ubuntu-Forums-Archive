---
title: "pdvdlinux"
date: 2009-12-05
forum: Multimedia Software
---

### Post by GregFuess on 2009-12-05
An error message appeared when attempting to reinstall flashplayer after inadvertently deleting it using the computer janitor.  The message is "To install the following changes are required: To be removed: pdvdlinux"

Does anyone know how to remove this?  Is this something that I want to do?  Any and all recommendations appreciated.

Regards

Greg

---

### Post by xc3RnbFO8P on 2009-12-05
This is not a error message, it only remove pdvdlinux that you don't need, automatically .

---

### Post by GregFuess on 2009-12-06
Thanks, so how is pdvdlinux removed?  Any help appreciated.  I am attempting to reinstall flashplayer after following the advise of computer janitor.  I understand that pdvdlinux needs to be removed, but do not know how to do so.  Any help appreciated.

Regards

Greg

---

### Post by xc3RnbFO8P on 2009-12-06
Use this(you can use both commands):
[http://ubuntuforums.org/showpost.php?p=2362563&postcount=2]("http://ubuntuforums.org/showpost.php?p=2362563&postcount=2")

---

### Post by GregFuess on 2009-12-06
Thanks, but there is no fix in the link?  Not sure what I can do with this?  Any help appreciated.

Greg

---

### Post by GregFuess on 2009-12-06
Which of these should I use?

---

### Post by xc3RnbFO8P on 2009-12-06
Use **sudo apt-get autoclean**

---

### Post by GregFuess on 2009-12-06
did that, and still getting the messages below, that hte pdvdlinux error exit status 127 is a problem


rm: cannot remove `/usr/share/app-install/icons/pdvdlinux.xpm': No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: update-app-install: not found
dpkg: error processing pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)
greg@dell-desktop:~$ 


Any help appreciated.

---

### Post by AMusnikow on 2010-12-13
I am having the same problem trying to remove pdvdlinux. In my case from Ubuntu release 10.10 (maverick). This is a problem because I cannot install any new software until pdvdlinux is removed.

Neither sudo apt-get autoclean nor sudo apt-get autoremove solved the problem.

For example, in Applications -> Ubuntu Software Center -> Get Software I get the message:
> Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?
When I click on the Repair button, I get the message:
> Package operation failed
The installation or removal of a software package failed.
When I click on the Details button in the above message, the following is displayed.
> ...
Removing pdvdlinux ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove `/usr/share/app-install/desktop/pdvdlinux.desktop': No such file or directory
rm: cannot remove `/usr/share/app-install/icons/pdvdlinux.xpm': No such file or directory
/var/lb/dpkg/info/pdvdlinux.postrm: 27: update-app-install: not found
dpkg: error processing pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 pdvdlinux
At that point the Ubuntu Software Center Nautilus-dropbox window says:
> Failed to satisfy all dependencies (broken cache)
Based on the above posts, in Applications -> Accessories -> Terminal, I ran "sudo apt-get autoclean".

At that point, in System -> Administration -> Synaptic Package Manager, I click on the Mark All Upgrades button, then the Apply button, and the Apply button in the Summary window, and get the message:
> An error occurred
The following details are provided:
E: pdvdlinux: subprocess installed post-removal script returned error exit status 127
Then in Applications -> Accessories -> Terminal, I run "sudo apt-get autoremove", as follows:
> alan@Inspiron1545n:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libctemplate0 libdbd-mysql-perl libdbi-perl libmysqlclient16
  libnet-daemon-perl libplrpc-perl mysql-client mysql-client-5.1
  mysql-client-core-5.1 mysql-common pdvdlinux python-paramiko
  python-pysqlite2
0 upgraded, 0 newly installed, 13 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 36.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 186658 files and directories currently installed.)
Removing pdvdlinux ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove `/usr/share/app-install/desktop/pdvdlinux.desktop': No such file or directory
rm: cannot remove `/usr/share/app-install/icons/pdvdlinux.xpm': No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: update-app-install: not found
dpkg: error processing pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Removing libctemplate0 ...
Removing mysql-client ...
Removing mysql-client-5.1 ...
Removing libdbd-mysql-perl ...
Removing libdbi-perl ...
Removing mysql-client-core-5.1 ...
Removing libmysqlclient16 ...
Removing libplrpc-perl ...
Removing libnet-daemon-perl ...
Removing mysql-common ...
Removing python-paramiko ...
Removing python-pysqlite2 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for python-support ...
Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)
At that point, in System -> Administration -> Synaptic Package Manager, I click on the Mark All Upgrades button, then the Apply button, and the Apply button in the Summary window, and get the message:
> An error occurred
The following details are provided:
E: pdvdlinux: subprocess installed post-removal script returned error exit status 127

---

### Post by nerdy_kid on 2010-12-13
try installing pdvdlinux, then removing it.  If it won't install, download the .deb, open a terminal, cd to the dir that the deb is in and run this command:

```

sudo dpkg --force-depends --install ./DEBNAME

```

then uninstall it normally.


Note:  don't mess too much with dpkg --force-depends, it basically overrides the dependency handling so you could screw your system up bad ;)

---

### Post by AMusnikow on 2010-12-13
Thanks for the suggestion.

Unfortunately, I cannot find a Linux version of PDVD. I think it came on the laptop, a Dell Inspiron 1545n, with Linux release 8.04. Currently:

o CyberLink's web site lists only Windows versions of PowerDVD on [http://www.cyberlink.com/products/powerdvd/overview_en_US.html]("http://www.cyberlink.com/products/powerdvd/overview_en_US.html").

o Dell's web site lists only versions of Windows as "Dell - Supported Operating Systems" for my Inspiron 1545 on [http://support.dell.com/support/topics/global.aspx/support/osmatrix/index?c=us&cs=19&l=en&s=dhs&~ck=anavml]("http://support.dell.com/support/topics/global.aspx/support/osmatrix/index?c=us&cs=19&l=en&s=dhs&~ck=anavml").

---

### Post by nerdy_kid on 2010-12-14
<snip>
get back to you later

---

### Post by AMusnikow on 2010-12-24
Based on another post in Ubuntu Forums, I tried the following commands in Applications -> Accessories -> Terminal without success.
```
sudo rm /var/cache/apt/archives/*
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
```
Following is that session, which included sudo rmdir /var/cache/apt/archives/partial after the first message.
> alan@Inspiron1545n:~$ **sudo rm /var/cache/apt/archives/partial**
rm: cannot remove `/var/cache/apt/archives/partial': Is a directory
alan@Inspiron1545n:~$ **sudo rmdir /var/cache/apt/archives/partial**
alan@Inspiron1545n:~$ **sudo apt-get update**
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Reading package lists... Done
alan@Inspiron1545n:~$ **sudo apt-get install -f**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  pdvdlinux
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? **Y**
(Reading database ... 209776 files and directories currently installed.)
Removing pdvdlinux ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove `/usr/share/app-install/desktop/pdvdlinux.desktop': No such file or directory
rm: cannot remove `/usr/share/app-install/icons/pdvdlinux.xpm': No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: update-app-install: not found
dpkg: error processing pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)
alan@Inspiron1545n:~$ sudo dpkg --configure -a
alan@Inspiron1545n:~$ 
At that point, in System -> Administration -> Synaptic Package Manager, I click on the Mark All Upgrades button, then the Apply button, and the Apply button in the Summary window, and get the message:
> An error occurred
The following details are provided:
E: pdvdlinux: subprocess installed post-removal script returned error exit status 127

---

### Post by nerdy_kid on 2010-12-25
sorry for the long wait, been busy!

give this a try:

```

sudo dpkg --force-depends -r pdvdlinux

```

if that doesn't work, there is one other way that _will_ work but I have to refresh my memory as to how to do it.

---

### Post by AMusnikow on 2010-12-25
That did not work. Following is the Terminal session.
> alan@Inspiron1545n:~$ sudo dpkg --force-depends -r pdvdlinux
[sudo] password for alan: 
(Reading database ... 209776 files and directories currently installed.)
Removing pdvdlinux ...
No value set for `/desktop/gnome/powerdvd/default_list'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove `/usr/share/app-install/desktop/pdvdlinux.desktop': No such file or directory
rm: cannot remove `/usr/share/app-install/icons/pdvdlinux.xpm': No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: update-app-install: not found
dpkg: error processing pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
alan@Inspiron1545n:~$

Then, System -> Administration -> Update Manager reported, "Not all updates can be installed."
I clicked on the "Partial Upgrade" button.
I clicked on the "Start Upgrade" button and it reported, "Could not install 'pdvdlinux' ... subprocess installed post-removal script returned error exit status 127."
I clicked on the "Close" button and it reported, "Could not install the upgrades...."

---

### Post by nerdy_kid on 2010-12-25
ok well time for a little hacking.

try this command just to make sure that there is not a nicer way to do this:

```

sudo dpkg --force-all -P pdvdlinux

```

if that doesn't work then it is time to be mean.

back the database up:

```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.backup

```

and open a text editor:

```

gksu gedit /var/lib/dpkg/status

```


observe that the database is organised in this format:

Package
Status
Priority
Section
Installed-Size
Maintainer
Architecture
Version
Replaces
Provides
Depends
Description


now search the file for "pdvdlinux".  you need to delete the database entry for it, which is formated as I showed you above.
Once you have done that, save the file.

then run:

```

sudo apt-get install -f

```

now this is where you need to be careful.  Make sure that it does not ask to remove a bunch of packages!  It shouldn't need to remove anything.  If it asks to remove stuff post the full output here and cancel the command!

then update everything:
```

sudo apt-get update
sudo apt-get upgrade

```


then you should be good :)

---

### Post by AMusnikow on 2010-12-26
nerdy_kid,

Your instructions were precise, reassuring, and worked like a charm.

As you expected, [COLOR="Orange"]sudo dpkg --force-all -P pdvdlinux[/COLOR] did not solve the problem, but I was happy to try it before proceeding.

Your instructions to backup the database and your listing of its format left me comfortable with editing the file.

After I finished your instructions, I was able to run Update Manager with no error messages, and install new software.

Thank you for your excellent assistance.

Regards,
Alan

---

### Post by nerdy_kid on 2010-12-26
> **AMusnikow said:**
> nerdy_kid,

Your instructions were precise, reassuring, and worked like a charm.

As you expected, [COLOR="Orange"]sudo dpkg --force-all -P pdvdlinux[/COLOR] did not solve the problem, but I was happy to try it before proceeding.

Your instructions to backup the database and your listing of its format left me comfortable with editing the file.

After I finished your instructions, I was able to run Update Manager with no error messages, and install new software.

Thank you for your excellent assistance.

Regards,
Alan

Glad to help :)  Happy linuxing!

---

### Post by boygenuis on 2011-01-08
This was great info.  I do have some ::ahem:: stupid questions.  1) What does the database entry for pdvdlinux look like?  I have the ".postinst", ".postrm", and ".preinst" files.  All of which are saved in the /var/lib/dpkg/info file.  2) What am I saving that text file with the code, "gksu gedit /var/lib/dpkg/status" as?  Thanks for the help.

---

### Post by nerdy_kid on 2011-01-09
> **boygenuis said:**
> This was great info.  I do have some ::ahem:: stupid questions.  1) What does the database entry for pdvdlinux look like?  I have the ".postinst", ".postrm", and ".preinst" files.  All of which are saved in the /var/lib/dpkg/info file.  2) What am I saving that text file with the code, "gksu gedit /var/lib/dpkg/status" as?  Thanks for the help.


1:  the database entry is inside the /var/lib/dpkg/status file, and is formatted like this:

Package
Status
Priority
Section
Installed-Size
Maintainer
Architecture
Version
Replaces
Provides
Depends
Description

I can't give you any more info on that cause I don't have that package.  

2:  you are saving the file as itself, just hit the "save" button on the text editor.

hope that helps

---

### Post by boygenuis on 2011-01-12
Roger, tracking.  Thanks for the help.  That was just too easy.

---

### Post by matthewboh on 2012-09-16
Thanks - this helped me as well!

---

### Post by overdrank on 2012-09-16
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

