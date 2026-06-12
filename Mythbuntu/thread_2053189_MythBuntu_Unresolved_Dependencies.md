---
title: "MythBuntu Unresolved Dependencies"
date: 2012-09-04
forum: Mythbuntu
---

### Post by ksanger on 2012-09-04
I've been trying to install MythTV onto Ubuntu 12.04 and I keep getting the error message "Unresolved Dependencies".  This happens for both the front end and the back end.  So I downloaded MythBuntu Control Center and select my machine to be both a front end and a back end and get the same result.

MythBuntu Control Center worked fine.  But it doesn't enable MythTV for Ubuntu 12.04 LTS.  64 Bit.

I have an HDHomeRun dual tuner that I'ld like to start using without resorting to Win7.  It looked great under Win7 and I'm struggling with Ubuntu but I really feel its time to move on.

---

### Post by Rotak on 2012-09-04
I don't remember if the console output is shown when installing using the control center. Because at least on the console (sometimes hidden behind "|> Details"), the dpkg output should tell you which packages are missing.

As an alternative, you can try to install the backend and the frontend using apt-get or aptitude. Or even via synaptic, if you are no friend of the console. That should show the dependency errors.

Aptitude and synaptic would have to be installed, though. Since Ubuntu comes with the software center, they are no longer installed by default.

---

### Post by klc5555 on 2012-09-04
> **ksanger said:**
> I've been trying to install MythTV onto Ubuntu 12.04 and I keep getting the error message "Unresolved Dependencies".  This happens for both the front end and the back end.  So I downloaded MythBuntu Control Center and select my machine to be both a front end and a back end and get the same result.

MythBuntu Control Center worked fine.  But it doesn't enable MythTV for Ubuntu 12.04 LTS.  64 Bit.

I have an HDHomeRun dual tuner that I'ld like to start using without resorting to Win7.  It looked great under Win7 and I'm struggling with Ubuntu but I really feel its time to move on.

Try using apt-get to install the three critical Mythtv packages individually. Apt-get should also automatically determine and pull along the dependencies that your 12.04 installation is missing for your added mythtv packages.

From a prompt start with ```
sudo apt-get install mythtv-common
``` If this works and pulls along its dependencies, then do ```
sudo apt-get install mythtv-backend
``` and finally ```
sudo apt-get install mythtv-frontend
```  and maybe also do the same with mythtv-database. With apt-get having installed these packages and their related dependencies for you, you should have enough of the mythtv application/utility suite together to configure and start the backend in accordance with chapter 3 of the manual [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index) 

You'll need to complete the backend configuration, not just the portion pertaining to capture cards, and then the backend can be started.

---

### Post by Rotak on 2012-09-05
Umh, I just found a glitch in the software center. It sometimes doesn't pull the newest package list. Maybe you ran into this problem. Try running "apt-get update" to get the newest package list and then try to install mythtv again (like you did before). That already solved it for the issue I had this morning.

---

### Post by ksanger on 2012-09-08
Ok;  I had tried doing update and installs before but did not install common first.  So...

First I did 
sudo apt-get update

Then I tried getting mythtv-common with the following errors:

$ sudo apt-get install mythtv-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mythtv-common : Depends: libmyth-0.25-0 (>= 2:0.25.0+fixes.20120410.1f5962a) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I have no idea what is missing or incompatible or what to do next.  So I looked around for Synaptic.  Installed it.  Upgraded the listing.  Then searched for MythTV.  Sellecting MythTV and hitting install, was prompted for dependencies, sellected install, and obtain the following errors:

Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences.

mythtv:
 Depends: mythtv-database but it is not going to be installed
 Depends: mythtv-frontend but it is not going to be installed
 Depends: mythtv-backend but it is not going to be installed

Not much help for me here.  Appreciate help to determine what to do next.  I'm surprised that I don't get a list of files that are missing or broken or an incorrect version.  Just a dumb I can't do that message or I'm not gonna do that message.

Sorry Dave, I can't do that.  Hah.  But I'm stubborn so with your help I'm up for trying something new.  Thanks in advance.

---

### Post by tgm4883 on 2012-09-08
> **ksanger said:**
> Ok;  I had tried doing update and installs before but did not install common first.  So...

First I did 
sudo apt-get update

Then I tried getting mythtv-common with the following errors:

$ sudo apt-get install mythtv-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mythtv-common : Depends: libmyth-0.25-0 (>= 2:0.25.0+fixes.20120410.1f5962a) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I have no idea what is missing or incompatible or what to do next.  So I looked around for Synaptic.  Installed it.  Upgraded the listing.  Then searched for MythTV.  Sellecting MythTV and hitting install, was prompted for dependencies, sellected install, and obtain the following errors:

Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies.  Make sure that all required repositories are added and enabled in the preferences.

mythtv:
 Depends: mythtv-database but it is not going to be installed
 Depends: mythtv-frontend but it is not going to be installed
 Depends: mythtv-backend but it is not going to be installed

Not much help for me here.  Appreciate help to determine what to do next.  I'm surprised that I don't get a list of files that are missing or broken or an incorrect version.  Just a dumb I can't do that message or I'm not gonna do that message.

Sorry Dave, I can't do that.  Hah.  But I'm stubborn so with your help I'm up for trying something new.  Thanks in advance.

It's telling you exactly what is missing (mythtv-database, mythtv-frontend, and mythtv-backend), which means it can't find those packages in the repositories you are subscribed to... Which means you changed your repositories. 

Post your /etc/apt/sources.list file.

---

### Post by ksanger on 2012-09-08
I have never edited source.lst.  It should be the same as when I installed 12.04 from the live cd.
Here it is /etc/apt/source.lst


# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by klc5555 on 2012-09-08
Since the unmet dependency preventing mythtv-common from installing (and therefore also mythtv-frontend and mythtv-backend) appears to be libmyth, and since for some reason you don't seem to be able to install libmyth from repository, perhaps just download it from Canonical with a browser [http://packages.ubuntu.com/precise/libmyth-0.25-0](http://packages.ubuntu.com/precise/libmyth-0.25-0) and see whether you can install it with the gdebi installer. 

Gdebi may, in turn, complain about unmet dependencies. You can see from the above-referenced page that there are a few dependencies for libmyth. But at least each time it comes to a failed dependency (if there are any) gdebi will tell you what it is, so that you may download and install it too. Once libmyth is installed in place, then proceed to mythtv-common.

---

### Post by nickrout on 2012-09-08
Do you have libmyth-0.24 installed somehow? If so manually remove it ```
sudo apt-get remove libmyth
``` then try to install the myth packages again.

---

### Post by ksanger on 2012-09-08
Looks like I have something called libmythes but not libmyth.

me@myPC:~$ dpkg --get-selections | grep libmyth
libmythes-1.2-0                    install

me@myPC:~$ sudo apt-get remove libmyth
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libmyth
me@myPC:~$

---

### Post by ksanger on 2012-09-08
I installed gdebi.

Then found the mirror to download libmyth0.25

The right clicked on the file and selected install with gdebi.  gdebi states its available from the package manager but I clicked install anyway and obtained the following errors.

gdebi-gtk Failed to completely install all dependencies.  To fix this run 'sudo apt-get install -f' in a terminal window.

Also got the message 
(Reading database ... 259988 files and directories currently installed.)
Unpacking libmyth-0.25-0 (from .../libmyth-0.25-0_0.25.0+fixes.20120410.1f5962a-0ubuntu1_amd64.deb) ...
dpkg: dependency problems prevent configuration of libmyth-0.25-0:
 libmyth-0.25-0 depends on libqt4-sql-mysql; however:
  Package libqt4-sql-mysql is not installed.
dpkg: error processing libmyth-0.25-0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmyth-0.25-0

So I ran the command that gdebi suggested.
my@myPC:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  pwgen libnet-daemon-perl libdbi-perl libmysqlclient18 mysql-client-core-5.5
  libdbd-mysql-perl libplrpc-perl libvdpau1 libavahi-compat-libdnssd1
  libva-glx1 libqtwebkit4 mysql-common libfaac0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libmyth-0.25-0
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 28.4 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 260037 files and directories currently installed.)
Removing libmyth-0.25-0 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
my@myPC:~$ 

Then I tried again to install mythtv-common.
my@myPC:~$ sudo apt-get install mythtv-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mythtv-common : Depends: libmyth-0.25-0 (>= 2:0.25.0+fixes.20120410.1f5962a) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
my@myPC:~$ 

For the hell of it and since I have no other idea of what to try I ran the install -f command again.
my@myPC:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  pwgen libnet-daemon-perl libdbi-perl libmysqlclient18 mysql-client-core-5.5
  libdbd-mysql-perl libplrpc-perl libvdpau1 libavahi-compat-libdnssd1
  libva-glx1 libqtwebkit4 mysql-common libfaac0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I don't understand why the package manager doesn't update the dependent files.  Is my source.list file correct?  I posted it earlier per a request.  Note prior to my orriginal post I had manually installed SQL Client and SQL Backend to see if that would help.  It didn't so I uninstalled them which is probably why I get the message that I have libraries that are no longer being used.

---

### Post by klc5555 on 2012-09-08
What gdebi said was that the (first) failed dependency was lib-qt4-sql-mysql> libmyth-0.25-0 depends on libqt4-sql-mysql; however:
Package libqt4-sql-mysql is not installed.

But it does not appear that you went on and installed lib-qt4-sql-mysql, which, like the remainder of the dependencies for libmyth, can be gotten from links on this page: [http://packages.ubuntu.com/precise/libmyth-0.25-0](http://packages.ubuntu.com/precise/libmyth-0.25-0) Or can be installed directly with apt-get. You may wish to download and to try to install lib-qt4-sql-mysql. If successful, you probably should try to install libmyth again. At that point, libmyth will either install or complain about a failed dependency further down the list. You may wish to download and install any additional missing packages that gdebi complains about.

When the missing dependencies have been supplied, libmyth should install. When libmyth is installed, mythtv-common and the rest should install without further difficulties.

---

### Post by nickrout on 2012-09-08
> **ksanger said:**
> I installed gdebi.

Then found the mirror to download libmyth0.25

The right clicked on the file and selected install with gdebi.  gdebi states its available from the package manager but I clicked install anyway and obtained the following errors.

gdebi-gtk Failed to completely install all dependencies.  To fix this run 'sudo apt-get install -f' in a terminal window.

Also got the message 
(Reading database ... 259988 files and directories currently installed.)
Unpacking libmyth-0.25-0 (from .../libmyth-0.25-0_0.25.0+fixes.20120410.1f5962a-0ubuntu1_amd64.deb) ...
dpkg: dependency problems prevent configuration of libmyth-0.25-0:
 libmyth-0.25-0 depends on libqt4-sql-mysql; however:
  Package libqt4-sql-mysql is not installed.
dpkg: error processing libmyth-0.25-0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmyth-0.25-0

So I ran the command that gdebi suggested.
my@myPC:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  pwgen libnet-daemon-perl libdbi-perl libmysqlclient18 mysql-client-core-5.5
  libdbd-mysql-perl libplrpc-perl libvdpau1 libavahi-compat-libdnssd1
  libva-glx1 libqtwebkit4 mysql-common libfaac0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libmyth-0.25-0
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 28.4 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 260037 files and directories currently installed.)
Removing libmyth-0.25-0 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
my@myPC:~$ 

Then I tried again to install mythtv-common.
my@myPC:~$ sudo apt-get install mythtv-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mythtv-common : Depends: libmyth-0.25-0 (>= 2:0.25.0+fixes.20120410.1f5962a) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
my@myPC:~$ 

For the hell of it and since I have no other idea of what to try I ran the install -f command again.
my@myPC:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  pwgen libnet-daemon-perl libdbi-perl libmysqlclient18 mysql-client-core-5.5
  libdbd-mysql-perl libplrpc-perl libvdpau1 libavahi-compat-libdnssd1
  libva-glx1 libqtwebkit4 mysql-common libfaac0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I don't understand why the package manager doesn't update the dependent files.  Is my source.list file correct?  I posted it earlier per a request.  Note prior to my orriginal post I had manually installed SQL Client and SQL Backend to see if that would help.  It didn't so I uninstalled them which is probably why I get the message that I have libraries that are no longer being used.

why don't you follow the advice that apt-get install -f is giving you?

also when you apt-get update do you get any errors?

---

### Post by ksanger on 2012-09-08
Because I didn't know where libqt4-sql-mysql was nor whether its part of a package or needs to be installed by itself?  Do I install it alone or through finding and loading SQL?

---

### Post by ksanger on 2012-09-08
I did sudo apt-get autoremove followed by sudo apt-get update with no errors.  But now I'm confused.  Should I retry to install libmyth0.25 or mythtv_common or libqt4-sql-mysql or something else?  It would be a pain to have to install each dependent file for each subsequent failed install.  Surely there must be something wrong perhaps with sources.list?

Then do I do so by downloading independent files and using gdebi or apt-get or package manager or synaptic?  I'm getting a lot of different advice as it appears that there are many ways to accomplish the same thing yet none of them appear to work.  I thought it would be much easier than this to use Ubuntu.

I tried anyway...
me@myPC:~$ sudo apt-get install mythtv-common -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mythtv-common : Depends: libmyth-0.25-0 (>= 2:0.25.0+fixes.20120410.1f5962a) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


me@myPC:~$ sudo apt-get install libmyth-0.25-0 -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libmyth-0.25-0 : Depends: libqt4-sql-mysql but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


me@myPC:~$ sudo apt-get install libqt4-sql-mysql -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqt4-sql-mysql : Depends: libqt4-sql (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
                    Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
E: Unable to correct problems, you have held broken packages.


me@myPC:~$ sudo apt-get install libqtcore4 -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqtcore4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Also:
my@myPC:~$ sudo apt-get install libqt4-sql -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt4-sql is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Looks like my system has a libqt4-sql and libqtcore4 that it believes is up to date but libqt4-sql-mysql doesn't like it?  What do I do next?  Also I prefer the apt-get method in the terminal instead of manually downloading packages and using gdebi to try and install them.  Do I have the -f option in the correct place?  I would have thought that apt-get would have fixed the issue though if it believes the files are the latest versions then it doesn't recognize the issue?  I assume apt-get uses sources.list and its pointing to the wrong versions?

---

### Post by nickrout on 2012-09-08
I can't say anything in your sources.list leaps out as wrong, but as I don't have a precise install I can't really say. Bt you also have to consider /etc/apt/sources.d. What is in there?

---

### Post by ksanger on 2012-09-08
Ubuntu Software Center shows that I have libqt4-sql 4:4.8.1-0ubuntu4.1 and libqtcore4 4:4.8.1-0ubuntu4.1

From the post above this looks to be up to date and sudo apt-get install libqt4-sql-mysql -f should have worked?

---

### Post by ksanger on 2012-09-08
I do not have a /etc/apt/sources.list.d file.  I do have a folder with that name and it is empty.

---

### Post by Rotak on 2012-09-08
Dumb question:

Did you try to install the Mythbuntu Repos package on your system? This package allows you to choose the version to install and it's able to use the most recent repository locations.

Package is here: [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

That'll add you a mythbuntu-repos.list file into the sources.list.d folder.

---

### Post by klc5555 on 2012-09-08
> **ksanger said:**
> Ubuntu Software Center shows that I have libqt4-sql 4:4.8.1-0ubuntu4.1 and libqtcore4 4:4.8.1-0ubuntu4.1

From the post above this looks to be up to date and sudo apt-get install libqt4-sql-mysql -f should have worked?

It is up to date, and this might be the problem.

Based on > The following packages have unmet dependencies:
libqt4-sql-mysql : Depends: libqt4-sql (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed
E: Unable to correct problems, you have held broken packages.the repository package libqt4-sql-mysql appears to require its dependencies to be _exactly_ equal to 4:4.8.1-0ubuntu4 and has not been updated to accept 4:4.8.1-0ubuntu4.1

---

### Post by nickrout on 2012-09-09
It certainly sounds as if ksanger has is using a repository that is out of sync somehow. I would apt-get update again and if that doesn't work, change to another ubuntu repo.

---

### Post by ksanger on 2012-09-09
> **Rotak said:**
> Dumb question:

Did you try to install the Mythbuntu Repos package on your system? This package allows you to choose the version to install and it's able to use the most recent repository locations.

Package is here: [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

That'll add you a mythbuntu-repos.list file into the sources.list.d folder.

I was under the impression that MythBuntu was a standalone OS with MythTV built in.  Is it okay to mix repositories for differing Operating Systems or won't that lead to additional discrepancies?  I'm running Ubuntu 12.04 LTS.

Also I have never added or installed a repository by itself.  I assume when I install a package its repository gets added to my system?

My problem appears to be that libqt4-sql-mysql thinks libqt4-sql and libqtcore4 are out of date but my OS believes that they are ok.

---

### Post by ksanger on 2012-09-09
> **nickrout said:**
> It certainly sounds as if ksanger has is using a repository that is out of sync somehow. I would apt-get update again and if that doesn't work, change to another ubuntu repo.

  	 	 	 	 	 	   

 **Running apt-get update again**
 me@myPC:/etc/apt$ sudo apt-get update 
 [sudo] password for me:  
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                            
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                           
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources             
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources           
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages          
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages    
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages           
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages     
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages       
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages     
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex  
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex    
 Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B] 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                    
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en 
 Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]             
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
 Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB] 
 Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [11.9 kB] 
 Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [6,535 B]       
 Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [41.4 kB] 
 Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages [8,531 B] 
 Get:8 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [8,545 B]  
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                      
 Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]  
 Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [12.6 kB] 
 Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,386 B] 
 Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [158 kB] 
 Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [3,969 B] 
 Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [41.8 kB] 
 Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,180 B] 
 Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [163 kB]  
 Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B] 
 Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [42.0 kB] 
 Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,369 B] 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex           
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex 
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US              
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en      
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en 
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en 
 Fetched 560 kB in 2s (218 kB/s) 
 Reading package lists... Done 
 

 **Verifying that libqtcore4 and libqt4-sql are still valid.**
 

 my@myPC:/etc/apt$ sudo apt-get install libqtcore4 -f 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 libqtcore4 is already the newest version. 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 my@myPC:/etc/apt$ sudo apt-get install libqt4-sql -f 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 libqt4-sql is already the newest version. 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 

 

 **Try installing libqt4-sql-mysql again.**
 me@myPC:/etc/apt$ sudo apt-get install libqt4-sql-mysql -f 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Some packages could not be installed. This may mean that you have 
 requested an impossible situation or if you are using the unstable 
 distribution that some required packages have not yet been created 
 or been moved out of Incoming. 
 The following information may help to resolve the situation: 
  
 The following packages have unmet dependencies: 
  libqt4-sql-mysql : Depends: libqt4-sql (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed 
                     Depends: libqtcore4 (= 4:4.8.1-0ubuntu4) but 4:4.8.1-0ubuntu4.1 is to be installed 
 E: Unable to correct problems, you have held broken packages. 
 

 **And getting the same result.  **Funny how computers do exactly what they are told to do over and over and over...  Actually its when they don't do the same thing over and over that I get worried.  Is it possible for me to point to a correct repository or do I need to report this as a bug somewhere?

 

**Here is my /etc/apt directory.**  I don't know if the file dates might help.

me@myPC:/etc/apt$ ls -l
total 36
drwxr-xr-x 2 root root 4096 Sep  8  11:13 apt.conf.d
drwxr-xr-x 2 root root 4096 Apr 20 06:21 preferences.d
-rw-r--r--     1 root root 2743 Jun 17  20:20 sources.list
drwxr-xr-x 2 root root 4096 Apr 20 06:21 sources.list.d
-rw-r--r--     1 root root 3169 Jun 17  20:20 sources.list.save
-rw-------      1 root root 1200 Apr 25 12:04 trustdb.gpg
-rw-r--r--      1 root root 7304 Apr 25 12:07 trusted.gpg
drwxr-xr-x 2 root root 4096 Apr 20  06:21 trusted.gpg.d

---

### Post by ksanger on 2012-09-09
> **Rotak said:**
> Dumb question:

Did you try to install the Mythbuntu Repos package on your system? This package allows you to choose the version to install and it's able to use the most recent repository locations.

Package is here: [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

That'll add you a mythbuntu-repos.list file into the sources.list.d folder.

After reading up on MythBuntu I installed the Mythbuntu Control Center.  Then selected repositories for version 0.25, and told it to do updates too.  Then under System Roles I selected backend and primary front end.  Hit apply and it started to install with fatal errors.  "Package dependencies cannot be resolved".  Selecting details generated the following Crash report.

[I]note crash report window does not allow one to copy it to the paste buffer...
[/I]Under title it states "mythbuntu-control-centre crashed with    Depends in_run():libqtgui4(>-4:4.5.3) but 4:4.8.1-0ubuntu4.1 is to be installed.

*Installation Media* is Ubuntu 12.04 LTS "Precise Pangolin" - Release amd64 (20120425)

*UpgradeStatus *No upgrade log present (probably fresh install)

**Note** I believe I had tried the Mythbuntu Control Centre before my original post and it didn't help then either.  Though I didn't enable the repositories first at that time.  All I had done was try to install the backend and the frontend after they failed to install from the Ubuntu Software Center.  

I will leave Mythbuntu Control Centre installed for now.

---

### Post by klc5555 on 2012-09-09
I suspect that this may require a bug report.

The message> Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.would tend to indicate that there ought to be a package libqt4-sql-mysql 4:4.8.1-0ubuntu4.1 in the repositories, but as a matter of fact only libqt4-sql-mysql 4:4.8.1-0ubuntu4 exists there currently. 

Welcome to dependency hell. It's this sort of thing that leads people to distros whose package management doesn't use dependency checking.

However, at [http://packages.ubuntu.com/precise-updates/libqt4-sql-mysql](http://packages.ubuntu.com/precise-updates/libqt4-sql-mysql) , I notice that libqt4-sql-mysql 4:4.8.1-0ubuntu4.2 is already present. It, of course, depends on libqtcore4 and libqt4-sql being _exactly_ equal to 4:4.8.1-0ubuntu4.2, but both of those packages seem to be available there as well.

---

### Post by nickrout on 2012-09-09
> **ksanger said:**
> I was under the impression that MythBuntu was a standalone OS with MythTV built in.  Is it okay to mix repositories for differing Operating Systems or won't that lead to additional discrepancies?  I'm running Ubuntu 12.04 LTS.

mythbuntu by default and ubuntu use exactly the same repositories.

The mythbuntu repo is an optional (but highly recommended) addon to get versions of the mythtv packages that are completely up to date.

So yes it is ok to add mythbuntu repos to a straight ubuntu install.

---

### Post by nickrout on 2012-09-09
> **ksanger said:**
> **Running apt-get update again**


 my@myPC:/etc/apt$ sudo apt-get install libqtcore4 -f 


whay are you using -f? You should only have needed to to do that once to fix the errors that apt-get told you about.

---

### Post by tgm4883 on 2012-09-09
Found the issue, see bottom of this post.

> **klc5555 said:**
> I suspect that this may require a bug report.


Nope, as you found later on the right packages are available (but newer versions) so it's likely only his system in some weird state.

> **klc5555 said:**
> 
The messagewould tend to indicate that there ought to be a package libqt4-sql-mysql 4:4.8.1-0ubuntu4.1 in the repositories, but as a matter of fact only libqt4-sql-mysql 4:4.8.1-0ubuntu4 exists there currently. 


This is true, and I see further down you see why.

> **klc5555 said:**
> 
Welcome to dependency hell. It's this sort of thing that leads people to distros whose package management doesn't use dependency checking.


I can't think of a single good package management system that doesn't use dependency checking. The user isn't having dependency hell, they are having issues with a specific package (and an issue that they caused themselves). Dependency hell is when you don't have a package management system so you install a package, it doesn't work so you install some needed dependency (and this chain continues, thus putting you in an unending hell of manually resolving dependency issues). By definition, having a package management system that didn't do dependency checking would CAUSE dependency hell, not relieve you from it.

> **klc5555 said:**
> 
However, at [http://packages.ubuntu.com/precise-updates/libqt4-sql-mysql](http://packages.ubuntu.com/precise-updates/libqt4-sql-mysql) , I notice that libqt4-sql-mysql 4:4.8.1-0ubuntu4.2 is already present. It, of course, depends on libqtcore4 and libqt4-sql being _exactly_ equal to 4:4.8.1-0ubuntu4.2, but both of those packages seem to be available there as well.

If you take a look at the OP's repo list, and then at the repo that you found the 4.2 version of that package in, you will quickly see what is missing.

@OP. You don't have precise-updates enabled. This normally wouldn't be an issue, except for you either A) did have it enabled at one time and installed some packages for it (and then disabled it) or B) manually installed another libqt4* package that is in the dependency chain for MythTV. Either way, it's an easy fix.

Enable the precise-updates repository, do an apt-get update, then install MythTV. It will resolve the dependencies for you and install the 4.2 version of those packages.

---

### Post by klc5555 on 2012-09-10
> Originally Posted by tgm4883 

I can't think of a single good package management system that doesn't use dependency checking. The user isn't having dependency hell, they are having issues with a specific package (and an issue that they caused themselves). Dependency hell is when you don't have a package management system so you install a package, it doesn't work so you install some needed dependency (and this chain continues, thus putting you in an unending hell of manually resolving dependency issues). By definition, having a package management system that didn't do dependency checking would CAUSE dependency hell, not relieve you from it.

I yield to your superior wisdom on almost all things, but not this. :) 

Non-dependency checking package management (for example Slackware's) works through simplicity. Having a particular library (or very many) may be critical for a package to function; having an incrementally exact version generally isn't. In a dependency-managed environment, too many incrementally-versioned packages become necessary simply because they are marked as dependencies for installation; they are not dependencies because the incremental changes are necessary for the original package to function. The current kerfluffle of libqt4-sql-mysql (and dependencies) at 4:4.8.1-0ubuntu4 vs. 4:4.8.1-0ubuntu4.1 vs. 4:4.8.1-0ubuntu4.2  just to get libmyth going (which would likely function with any of these versions and several others besides if it could just be installed) constitutes a small case in point. A Slacker would consider this to be insane.

In non-dependency-managed package management, dependency hell rarely occurs because the user can install the desired package without package manager interference, the installed package works because if specific library packages are required, these are generally listed by the package supplier and the user will install them (or bash will protest about a missing one when the app is fired up), and because the original binary package and its updates will function across a considerable range of versions of the dependent libraries. The parade of incremental dependencies doesn't occur. The drawback to this approach is the responsibility it places on the user as to how is system is constituted. The advantage consists in allowing a user who is so inclined the freedom of being easily and quickly able to do whatever he wants to do with a system, to constitute it in whatever shape he finds convenient at the moment. I keep my family's machines on Xubuntu (with update notification off) because they don't have the slightest interest in venturing past the desktop environment. This would drive me crazy on my own machines.

Sorry for the rant. :) I'm curious as to whether ksanger has had luck in enabling the precise-updates repository, and whether he was then able to get all of mythtv installed in one go by sudo apt-get install mythtv

---

### Post by tgm4883 on 2012-09-10
> **klc5555 said:**
> I yield to your superior wisdom on almost all things, but not this. :) 

Non-dependency checking package management (for example Slackware's) works through simplicity. Having a particular library (or very many) may be critical for a package to function; having an incrementally exact version generally isn't. In a dependency-managed environment, too many incrementally-versioned packages become necessary simply because they are marked as dependencies for installation; they are not dependencies because the incremental changes are necessary for the original package to function. The current kerfluffle of libqt4-sql-mysql (and dependencies) at 4:4.8.1-0ubuntu4 vs. 4:4.8.1-0ubuntu4.1 vs. 4:4.8.1-0ubuntu4.2  just to get libmyth going (which would likely function with any of these versions and several others besides if it could just be installed) constitutes a small case in point. A Slacker would consider this to be insane.

In non-dependency-managed package management, dependency hell rarely occurs because the user can install the desired package without package manager interference, the installed package works because if specific library packages are required, these are generally listed by the package supplier and the user will install them (or bash will protest about a missing one when the app is fired up), and because the original binary package and its updates will function across a considerable range of versions of the dependent libraries. The parade of incremental dependencies doesn't occur. The drawback to this approach is the responsibility it places on the user as to how is system is constituted. The advantage consists in allowing a user who is so inclined the freedom of being easily and quickly able to do whatever he wants to do with a system, to constitute it in whatever shape he finds convenient at the moment. I keep my family's machines on Xubuntu (with update notification off) because they don't have the slightest interest in venturing past the desktop environment. This would drive me crazy on my own machines.

Sorry for the rant. :) I'm curious as to whether ksanger has had luck in enabling the precise-updates repository, and whether he was then able to get all of mythtv installed in one go by sudo apt-get install mythtv

I still don't agree that sounds like a simple solution, but in any case, the important part is that as long as the user knows how to use the packaging system that there system uses, they can install whatever they want. Under normal circumstances what the OP is experiencing shouldn't happen.

As for the 4 vs 4.1 vs 4.2 versions of the package, I'll check but it sounds like the maintainer did something wrong. I'm hoping there is some fuzzy logic that can be done (eg. depending on 4:4.8.1-* would allow any of those packages to be installed), but I'm unsure.

---

### Post by klc5555 on 2012-09-11
> **tgm4883 said:**
> 
As for the 4 vs 4.1 vs 4.2 versions of the package, I'll check but it sounds like the maintainer did something wrong. I'm hoping there is some fuzzy logic that can be done (eg. depending on 4:4.8.1-* would allow any of those packages to be installed), but I'm unsure.

Sounds like a plan. It would still be good for the OP to report how he is making out re. adding precise-updates and then installing mythtv in one chunk: gdebi and apt-get (I believe) bail out and report after the first broken dependency they find. There might still be other broken ones.

---

### Post by tgm4883 on 2012-09-11
> **klc5555 said:**
> Sounds like a plan. It would still be good for the OP to report how he is making out re. adding precise-updates and then installing mythtv in one chunk: gdebi and apt-get (I believe) bail out and report after the first broken dependency they find. There might still be other broken ones.

I agree, the OP needs to report back. I doubt there are more broken dependencies, the rest of the default repos are there and updates is the only one that was missing. Since OP added Mythbuntu repos as well, there should be nothing else that is necessary.

Looks like the way to fix the packages would be to add the depends as (or something real close to that as I'm not sure the exact syntax

```
(PACKAGEA >= 4:4.8.1 & PACKAGEA < 4:4.8.2)
```

---

