---
title: "Installing Cinelerra 4.x on Ubuntu 12.04  64 bit"
date: 2013-01-07
forum: Multimedia Software
---

### Post by Fingust on 2013-01-07
Hello, 

I'm a complete noobie in Linux - Ubuntu, I've been trying to install Cinelerra 4.4 on my machine for the last week but, without any success. 

I'm wondering if there is a nice soul out there that could guide me through the process. I have been trying, but the only version that I could install with success is 2.2 CV. I read that Cinelerra 4.4 can chew all the MTS files you feed her.


 I'm looking forward to any suggestions. 

Best regards Fingust.

---

### Post by jpaulb on 2013-01-30
I am trying do do it also. There seems to be a ton of dependencies that have to be installed. 
I would like to make a deb package; but  before that can happen the deps have to be resolved.
./configure will dump so much unnecessary crap, so try ./configure >> config.txt this will dump everything but the warings into a text file, warnings go to standard out. you will see on the monitor something can not be installed due to a package not installed. Install what you think you need.

Do the same with ´make´ there is likely a few development files missing. 

That is as far as I am. I need help with building a deb package.
Maybe someone in the form can help us farther.

The package been made for Debian so it should be possible on Ubuntu

---

### Post by davidvandoren on 2013-01-31
open software center or the package manager.

Click on Edit
then 
 software sources

then click on other software and add this line

```
**ppa:cinelerra-ppa/ppa**
```confirm and close the software center

Open the Terminal and type

```
sudo apt-get update
```type your password 
you won't see the typed letters!
then enter into the terminal 

```
sudo apt-get install cinelerra-cv
```Maybe you'll need something like I am not sure about that one
```
**sudo apt-get install ia32-libs**
```

---

### Post by jpaulb on 2013-01-31
the PPA has vers 2,2 not 4,4
Installing stops with:
> Errors were encountered while processing:
 cinelerra-cv
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up cinelerra-cv (1:2.2-0.14~ppa1~precise1) ...
cannot open locale definition file `de_DE': No such file or directory
dpkg: error processing cinelerra-cv (--configure):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 cinelerra-cv


---

### Post by davidvandoren on 2013-02-01
> **jpaulb said:**
> the PPA has vers 2,2 not 4,4
Installing stops with:

This looks like a cinelerra bug already reported in 2010.

Try 

```
sudo dpkg-reconfigure locales
```

---

### Post by jpaulb on 2013-02-02
I managed to get cinelerra 4,4 running on ubuntu  12.04
download the file from[ here]("http://www.deb-multimedia.org/pool/main/c/cinelerra/cinelerra") save the in a director 
then use dpkg -i . I had to install the data file first.

There maybe a couple of dependencies to work out and you may have to launch the app from the command line.

---

### Post by vace117 on 2013-03-09
You can also follow these steps to install:

[https://n1njahacks.wordpress.com/2013/03/09/installing-cinelerra-4-4-on-ubuntu-12-04/](https://n1njahacks.wordpress.com/2013/03/09/installing-cinelerra-4-4-on-ubuntu-12-04/)

---

### Post by jpaulb on 2013-03-10
> **vace117 said:**
> You can also follow these steps to install:

[https://n1njahacks.wordpress.com/2013/03/09/installing-cinelerra-4-4-on-ubuntu-12-04/](https://n1njahacks.wordpress.com/2013/03/09/installing-cinelerra-4-4-on-ubuntu-12-04/)

After installing tonnes of dependencies I got stuck here:
> root@Maple:/opt/cinelerra-4.4# apt-get install libx264-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 libx264-dev : Depends: libx264-120 (= 2:0.120.2151+gita3f4407-2) but 2:0.120.2171+git01f7a33-4~ppa1 is to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by jpaulb on 2013-03-10
It is running finally \\:D/
is there a way of packaging it so it can be installed like any other app??

---

### Post by timsdeepsky on 2013-03-10
I have had my best luck installing cinelerra on 12.04 by going here....
[https://launchpad.net/~cinelerra-ppa/+archive/ppa]("https://launchpad.net/~cinelerra-ppa/+archive/ppa")
Just read the instructions really well....Cheers....

---

### Post by jpaulb on 2013-03-10
> **timsdeepsky said:**
> I have had my best luck installing cinelerra on 12.04 by going here....
[https://launchpad.net/~cinelerra-ppa/+archive/ppa](https://launchpad.net/~cinelerra-ppa/+archive/ppa)
Just read the instructions really well....Cheers....
is that not Ver 2.2 or so?

---

### Post by timsdeepsky on 2013-03-11
You are right....
Sorry about that....

---

### Post by jpaulb on 2013-03-11
> **timsdeepsky said:**
> You are right....
Sorry about that....
non problema
Tried that link a few months ago:)

---

### Post by gusduenas on 2013-03-11
Does anyone have managed to install cinelerra on a mac ppc g5 dual 2.0ghz nivida geforce 6600?

---

### Post by ^rooker on 2013-03-25
**@jpaulb:**
I have the exact same dependency problem you had with libx264-dev:
> The following packages have unmet dependencies:
 libx264-dev : Depends: libx264-120 (= 2:0.120.2151+gita3f4407-2) but 2:0.120.2171+git01f7a33-3~ppa1 is to be installed
E: Unable to correct problems, you have held broken packages.
How did you resolve it?

---

### Post by ^rooker on 2013-03-25
Nevermind. Fixed it myself:
I disabled all PPAs, refreshed the package list (apt-get update) and downgraded libx264-120 to precise's official version.
Afterwards I could install libx264-dev without problems.

---

