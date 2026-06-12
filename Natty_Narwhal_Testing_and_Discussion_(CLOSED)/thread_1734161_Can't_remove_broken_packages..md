---
title: "Can't remove broken packages."
date: 2011-04-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by umpat on 2011-04-19
I tried installing minitube from ubuntu software center. Installation was going fine but it gave me an error and I cant install anything.  

1.When I click ubuntu softare center I see the follwing :
Items cannot be installed or removed until the package catalog is repaired. Do you want to repari it now ? If I try to repair it I get the follwing error : 
package operation failed 
installArchives() failed: dpkg: error: parsing file '/var/lib/dpkg/status' near line 9850 package 'xserver-xorg-video-all':
 `Depends' field, invalid package name `

2. If I try to update from update manager I get the follwing error
The package is broken. Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
The following packages have unmet dependencies:

lib32asound2: Depends: libasound2 (= 1.0.24.1-0ubuntu5) but 1.0.24.1-0ubuntu5 is installed
              Depends: libc6-i386 (>= 2.9-18) but it is not installed
lib32gcc1: Depends: libc6-i386 (>= 2.5) but it is not installed
lib32stdc++6: Depends: gcc-4.5-base (= 4.5.2-8ubuntu3) but 4.5.2-8ubuntu3 is installed
              Depends: lib32gcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu3 is installed
              Depends: libc6-i386 (>= 2.4) but it is not installed
lib32z1: Depends: libc6-i386 (>= 2.4) but it is not installed
xserver-xorg-video-all: Depends: xserver-xorg-video-tident but it is not installed

3. When  I open Synaptics pacakge manager, I get a popup saying I have 5 broken packages.If I go to broken packages, and try to mark them for complete removal, and click apply, it will download some files then will get the follwing error
Changes applied 
Not all changes and updates were successful. 
Details 
dpkg: error: parsing file '/var/lib/dpkg/status' near line 9850 package 'xserver-xorg-video-all':
 `Depends' field, invalid package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: parsing file '/var/lib/dpkg/status' near line 9850 package 'xserver-xorg-video-all':
 `Depends' field, invalid package name `

I don't know what's going on . Any help would be greatly appreciated. 
I am using ubuntu 11.4 notebook beta. 
Thank you .

---

### Post by mörgæs on 2011-04-19
Furthermore run the following command in a Terminal: apt-get install -f

---

### Post by umpat on 2011-04-20
Thank you for your reply .. 
After running that command I get the follwing error

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by ashickur.noor on 2011-04-20
> **umpat said:**
> Thank you for your reply .. 
After running that command I get the follwing error

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```
sudo apt-get install -f
```

---

### Post by umpat on 2011-04-20
Thank you It works for a while and I get the follwing error...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  cpp-4.5 g++-4.5 gcc-4.5 gcc-4.5-base lib32gcc1 lib32stdc++6 libc6-i386
  libgcc1 libgomp1 libstdc++6 libstdc++6-4.5-dev xserver-xorg-video-all
Suggested packages:
  gcc-4.5-locales g++-4.5-multilib gcc-4.5-doc libstdc++6-4.5-dbg
  gcc-4.5-multilib libmudflap0-4.5-dev libgcc1-dbg libgomp1-dbg
  libmudflap0-dbg binutils-gold libstdc++6-4.5-doc
The following NEW packages will be installed:
  libc6-i386
The following packages will be upgraded:
  cpp-4.5 g++-4.5 gcc-4.5 gcc-4.5-base lib32gcc1 lib32stdc++6 libgcc1 libgomp1
  libstdc++6 libstdc++6-4.5-dev xserver-xorg-video-all
11 upgraded, 1 newly installed, 0 to remove and 83 not upgraded.
4 not fully installed or removed.
Need to get 24.3 MB of archives.
After this operation, 9,490 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main libc6-i386 amd64 2.13-0ubuntu13 [3,556 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main libgomp1 amd64 4.5.2-8ubuntu4 [25.4 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main gcc-4.5-base amd64 4.5.2-8ubuntu4 [14.0 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main libstdc++6 amd64 4.5.2-8ubuntu4 [326 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main lib32gcc1 amd64 1:4.5.2-8ubuntu4 [51.4 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main lib32stdc++6 amd64 4.5.2-8ubuntu4 [333 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main cpp-4.5 amd64 4.5.2-8ubuntu4 [4,603 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main libstdc++6-4.5-dev amd64 4.5.2-8ubuntu4 [1,589 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main g++-4.5 amd64 4.5.2-8ubuntu4 [6,511 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main gcc-4.5 amd64 4.5.2-8ubuntu4 [7,203 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main libgcc1 amd64 1:4.5.2-8ubuntu4 [42.3 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main xserver-xorg-video-all amd64 1:7.6+4ubuntu3 [1,140 B]
Fetched 24.3 MB in 25s (947 kB/s)                                              
dpkg: error: parsing file '/var/lib/dpkg/status' near line 9850 package 'xserver-xorg-video-all':
 `Depends' field, invalid package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by Dutch70 on 2011-04-20
Not sure if it will help, try running this one too...
```
sudo dpkg --configure -a
```

---

### Post by umpat on 2011-04-20
tried it ....and this is what I get....

dpkg: error: parsing file '/var/lib/dpkg/status' near line 9850 package 'xserver-xorg-video-all':
 `Depends' field, invalid package name 

there is something wrong in line 9850 ....

thank you

---

### Post by ashickur.noor on 2011-04-20
Are you using 11.04?

---

### Post by umpat on 2011-04-20
yes the new beta...

---

### Post by Dutch70 on 2011-04-20
beta & development releases should only be used for testing and reporting bugs, not as your main OS.

---

### Post by Elfy on 2011-04-20
moved to natty

---

### Post by beew on 2011-04-20
BTW the version of minitube in 11.04 repo is broken anyway even if it doesn't break your system, version 1.3 doesn't work. I can't believe that they still have version 1.3 in Natty's repository while 1.4 has been available to Maverick for months through ppas . New Ubuntu releases are supposed to  come  with cutting edge softwares but minitube is outdated (and broken) even before release.

I installed minitube 1.42 in Natty beta from this ppa [https://launchpad.net/~ferramroberto/+archive/minitube]("https://launchpad.net/%7Eferramroberto/+archive/minitube") Works beautifully.

---

### Post by seeker5528 on 2011-04-20
> **umpat said:**
> dpkg: error: parsing file '/var/lib/dpkg/status' near line 9850 package 'xserver-xorg-video-all':
 `Depends' field, invalid package name `


You have a couple of options.

Option 1:

Open '/var/lib/dpkg/status' in a text editor ```
gksudo gedit /var/lib/dpkg/status
```

find the section belonging to xserver-xorg-video-all and delete all the lines belonging to it, or try to figure out the bad package name in the depends field and delete that.

Option 2:

Open a terminal window and type:

```
cd /var/lib/dpkg
mv status status.bad
cp status-old status
```

refresh the package list and try your update again.

If everything seems fine after that you can delete the status.bad file.

Later, Seeker

---

### Post by umpat on 2011-04-21
thank you seeker...
will try em in a bit ...

---

### Post by seeker5528 on 2011-04-21
Just noticed on the option 2 section of my previous post I forgot to use sudo on the command lines that require elevated permissions, should have been....

Option 2:

Open a terminal window and type:

```
cd /var/lib/dpkg
sudo mv status status.bad
sudo cp status-old status
```

refresh the package list and try your update again.

Later, Seeker

---

