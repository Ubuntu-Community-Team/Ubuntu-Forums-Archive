---
title: "sh: Can't open ./fglrx-uninstall.sh"
date: 2010-06-03
forum: Multimedia Software
---

### Post by OdinOrion on 2010-06-03
Trying to update ATI drivers to Catalyst 10.5

The very first step to uninstall the previous driver version does not work.

andrew@andrew-desktop:~$ cd /usr/share/ati/
andrew@andrew-desktop:/usr/share/ati$ sudo sh ./fglrx-uninstall.sh
[sudo] password for andrew: 
sh: Can't open ./fglrx-uninstall.sh
andrew@andrew-desktop:/usr/share/ati$ 

Help

---

### Post by Yellow Pasque on 2010-06-03
sh or ./ (but not both ;) )
```
cd /usr/share/ati/
sudo sh fglrx-uninstall.sh
```
OR
```
sudo ./fglrx-uninstall.sh
```

---

### Post by OdinOrion on 2010-06-05
DOH!

Ok, I will try again.

---

### Post by hayhursm on 2010-08-17
> **OdinOrion said:**
> DOH!
 
Ok, I will try again.
 
[FONT=Times New Roman][SIZE=3]Were you able to find this?  I am trying to uninstall Catalyst10.6 so I can install Catalyst10.7 but I am unable to find this script.  I am using Ubuntu 10.04 x64 and I installed Catalyst10.6 using the package file on AMD’s website.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]I have tried both but terminal returns: **“command not found”**[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]cd /usr/share/ati/[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo sh fglrx-uninstall.sh[/FONT][/COLOR]

[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]OR[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo ./fglrx-uninstall.sh[/FONT][/COLOR]

---

### Post by hayhursm on 2010-08-18
> **hayhursm said:**
> [font=times new roman][size=3]were you able to find this? I am trying to uninstall catalyst10.6 so i can install catalyst10.7 but i am unable to find this script. I am using ubuntu 10.04 x64 and i installed catalyst10.6 using the package file on amd’s website.[/size][/font]
 
[size=3][font=times new roman]i have tried both but terminal returns: **“command not found”**[/font][/size]
 
[color=black][font=verdana]code:[/font][/color]
[color=black][font=courier new]cd /usr/share/ati/[/font][/color]
[color=black][font=courier new]sudo sh fglrx-uninstall.sh[/font][/color]
 
 
[color=black][font=verdana]or[/font][/color]
 
[color=black][font=verdana]code:[/font][/color]
[color=black][font=courier new]sudo ./fglrx-uninstall.sh[/font][/color]
 
bump

---

### Post by I8NY on 2010-08-19
i'm no expert but make sure the file has permission to execute (option under the file properties).  That helped with other .sh apps i have installed/uninstalled.  Tell me if the new driver fixes the 3D problem that made games stop working.

---

### Post by tjones00 on 2010-08-19
A reminder command line for enabling execute permission is.

sudo chmod +x some.file

scripts can then be executed via

sudo ./some.file


To search for a file via command line

sudo find / -name some.file

This will search the entire system for a file named some.file in this case the command would be.

sudo find / -name fglrx-uninstall.sh

---

### Post by hayhursm on 2010-08-19
> **tjones00 said:**
> A reminder command line for enabling execute permission is.
 
sudo chmod +x some.file
 
scripts can then be executed via
 
sudo ./some.file
 
 
To search for a file via command line
 
sudo find / -name some.file
 
This will search the entire system for a file named some.file in this case the command would be.
 
sudo find / -name fglrx-uninstall.sh
 
 
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]Thank you all for the reply!  Unfortunately, I tried the command **"sudo find / -name fglrx-uninstall.sh"** and it returned nothing[COLOR=black][FONT=Verdana], I don’t know why this script appears to be missing[/FONT][/COLOR].  I’m clueless right now as I followed the ATI Wiki Catalyst 10.6 tutorial completely.  The **“aticonfig”** command works and I didn’t receive any errors during the Catalyst 10.6 installation so I’m sure the installation was a success.  I don’t know if this helps but **“dpkg –l | grep fglrx”** returns this:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]**laptop:/lib/fglrx$ dpkg -l | grep fglrx**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]**ii  fglrx                                        2:8.741-0ubuntu1                       Video driver for the ATI graphics accelerato**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]**ii  fglrx-amdcccle                       2:8.741-0ubuntu1                                    Catalyst Control Center for the ATI graphics**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]**ii  fglrx-dev                                 2:8.741-0ubuntu1                       Video driver for the ATI graphics accelerato**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]**ii  fglrx-modaliases                    2:8.741-0ubuntu1                Identifiers supported by the ATI graphics dr **[/FONT][/COLOR]
 
Any ideas?[/FONT][/COLOR]

---

### Post by I8NY on 2010-08-19
try just searching for just fglrx and see if it finds a uninstall file in the results.  Also try to see if fglrx is in the package manager, idk if *.sh apps will show in there but it is worth a shot.  One more thing, did you install the ati driver yourself or through the proprietary driver app in ubuntu?

---

### Post by hayhursm on 2010-08-19
> **I8NY said:**
> try just searching for just fglrx and see if it finds a uninstall file in the results.  Also try to see if fglrx is in the package manager, idk if *.sh apps will show in there but it is worth a shot.  One more thing, did you install the ati driver yourself or through the proprietary driver app in ubuntu?

I just searched for fglrx and this is what I got:
[B]
Desktop$ sudo find / -name fglrx
/sys/module/fglrx
/var/lib/dkms/fglrx
/usr/share/fglrx
/usr/share/doc/fglrx
/usr/share/lintian/overrides/fglrx
/usr/lib32/fglrx
/usr/lib/fglrx
/lib/fglrx
[/B]
fglrx is in the Synaptic Package Manager and it indicates that it is installed (among other files as well) but I didn't see any *.sh files.  I did not install the proprietary driver app in Ubuntu; I downloaded the package directly from AMD ATI's website and installed it using their Wiki tutorial.

Wiki tutorial: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

I started at the **"Installing the drivers manually"** section

Just curious are you using ATI's driver?  If so, are you able to find the **"**[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]**fglrx-uninstall.sh"** on your system?  Also, could I just do a **"dpkg --purge fglrx-*"** or would that not be sufficient?[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by I8NY on 2010-08-20
funny thing is i made a help doc on how to remove a ati driver from the terminal and forgot i had it.(until now) X-(  The command you guessed it                                   ```
sudo apt-get --purge ati-driver-installer-9-7-x86_64
sudo apt-get --purge ati-driver-installer-9-7-x86
``` 1st line is 64bit and 2nd 32bit.  You might need to add *.run to the end, i forgot if it is needed.  If this fails you can try removing the fglrx packages from the package manager.(idk the exact package so make a good guess, fglrx?)

The second part, i have the ati driver, and got it through ubuntu.  I did search and did not find it, i think that uninstall file might be for other linux OS.

---

### Post by hayhursm on 2010-08-20
> **I8NY said:**
> funny thing is i made a help doc on how to remove a ati driver from the terminal and forgot i had it.(until now) X-( The command you guessed it ```
sudo apt-get --purge ati-driver-installer-9-7-x86_64
sudo apt-get --purge ati-driver-installer-9-7-x86
``` 1st line is 64bit and 2nd 32bit. You might need to add *.run to the end, i forgot if it is needed. If this fails you can try removing the fglrx packages from the package manager.(idk the exact package so make a good guess, fglrx?)
 
The second part, i have the ati driver, and got it through ubuntu. I did search and did not find it, i think that uninstall file might be for other linux OS.
 
 
[COLOR=black][FONT=Verdana]Thank you for the info but it did not work.  I think you are on track with the removal of the packages and here is why.  Here is the main installation portion of ATI’s Wiki (for version 10.6 of course):[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
**[FONT=Times New Roman][[/FONT][[FONT=Times New Roman]edit[/FONT]]("http://wiki.cchtml.com/index.php?title=Ubuntu_Lucid_Installation_Guide&action=edit&section=9")[FONT=Times New Roman]] *Download the latest Catalyst package.*[/FONT]**
[SIZE=3][FONT=Times New Roman]This package contains both the 32-bit and 64-bit driver. [/FONT][/SIZE]
[FONT=Courier New]$ cd ~/; mkdir catalyst_[COLOR=blue]10.6[/COLOR]_; cd catalyst_[COLOR=blue]10.6[/COLOR]_/[/FONT]
[FONT=Courier New]$ wget _[COLOR=blue][http://www2.ati.com/drivers/linux/ati-driver-installer-10-6-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-10-6-x86.x86_64.run)[/COLOR]_[/FONT]
**[FONT=Times New Roman][[/FONT][[FONT=Times New Roman]edit[/FONT]]("http://wiki.cchtml.com/index.php?title=Ubuntu_Lucid_Installation_Guide&action=edit&section=10")[FONT=Times New Roman]] *Create .deb packages.*[/FONT]**
[FONT=Courier New]$ sh ati-driver-installer-10-6-x86.x86_64.run --buildpkg Ubuntu/lucid[/FONT]
**[FONT=Times New Roman][[/FONT][[FONT=Times New Roman]edit[/FONT]]("http://wiki.cchtml.com/index.php?title=Ubuntu_Lucid_Installation_Guide&action=edit&section=11")[FONT=Times New Roman]] *Install .debs.*[/FONT]**
[FONT=Courier New]$ sudo dpkg -i fglrx*.deb[/FONT]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]J[/FONT][/COLOR][COLOR=black][FONT=Verdana]udging from that last step used to install everything would it be safe to say I could use the [/FONT][/COLOR]**[COLOR=black][FONT=Verdana]dpkg --purge fglrx*"[/FONT][/COLOR]**[COLOR=black][FONT=Verdana]**?  **[/FONT][/COLOR][COLOR=black][FONT=Verdana]**Like you said, the uninstall file is probably used in other Linux OS’ but ATI forgot to indicate that in the tutorial.  I have seen more than one Wiki that was erroneou**[/FONT][/COLOR][COLOR=black][FONT=Verdana]**s lol.**[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2010-08-20
As you've figured out, the uninstall script wasn't created because you installed by building packages. So the way to remove the driver is to uninstall the packages. I've edited the wiki to make this more clear and hopefully, avoid future confusion. 
BTW, that wiki is not affiliated with ATI.

---

### Post by hayhursm on 2010-08-20
> **Temüjin said:**
> As you've figured out, the uninstall script wasn't created because you installed by building packages. So the way to remove the driver is to uninstall the packages. I've edited the wiki to make this more clear and hopefully, avoid future confusion. 
BTW, that wiki is not affiliated with ATI.
 
Ok, thank you very much.  I guess a little brainstorming and discussion on the forums always helps the noobs.  The change you put in the Wiki really clears things up so it will definitely help me and I'm sure others as well.
 
Also, can you add **"thanks to hayhursm"** after your Wiki description change?  It would be nice to show my wife that all the time spent trying to figure this one out wasn't for nothing. :D

---

### Post by I8NY on 2010-08-20
when you upgrade your driver please tell me if it fixes some of the 3D problems games/apps have been having.  i hate upgrading drivers if doesn't fix anything.

---

### Post by hayhursm on 2010-08-23
> **I8NY said:**
> when you upgrade your driver please tell me if it fixes some of the 3D problems games/apps have been having. i hate upgrading drivers if doesn't fix anything.
 
 
No problem, but I'm not aware of any 3D problems, can you enlighten me please?

---

### Post by I8NY on 2010-08-23
Well in the ATI driver update in version 10.04 from 9.10, was not a good driver because it changed some of the basic functions for 3D games.  Even a few windows PC had problems because the games weren't compatible with the ATI driver changes.  So now i can only play 1/2 of my 3D games i have, every thing else does not work, and it worked before the update. (broken games, SpringRTS, Mupen64Plus, World of Goo)

I did try to do a manual ATI driver update and failed because it couldn't remove the current driver. Might try later update or wait for 10.10.

---

### Post by hayhursm on 2010-08-25
> **I8NY said:**
> Well in the ATI driver update in version 10.04 from 9.10, was not a good driver because it changed some of the basic functions for 3D games. Even a few windows PC had problems because the games weren't compatible with the ATI driver changes. So now i can only play 1/2 of my 3D games i have, every thing else does not work, and it worked before the update. (broken games, SpringRTS, Mupen64Plus, World of Goo)
 
I did try to do a manual ATI driver update and failed because it couldn't remove the current driver. Might try later update or wait for 10.10.
 
[SIZE=2]I’m still trying to figure out why the Wiki instructs us to use: [/SIZE][SIZE=2]**“****sudo apt-get remove --purge fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx”** to remove everything instead of: [/SIZE][SIZE=2]**“dpkg –purge fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx”** I would think that I would use the **“dpkg”** command to remove everything since it was installed using **“dpkg”**?  What do you think?[/SIZE]

---

### Post by Nebukadnezar II. on 2010-08-25
Well, if you installed your fglrx via apt-get(or whatever frontend for it) then you could use the "apt-get"-command instead of dpgk to remove it. But anyway, what apt-get does is mainly calling dpgk in pretty much the same way as your "dpkg"-command is. 
That's all, as far as I know.

---

### Post by hayhursm on 2010-08-26
[SIZE=2]> **Nebukadnezar II. said:**
> Well, if you installed your fglrx via apt-get(or whatever frontend for it) then you could use the "apt-get"-command instead of dpgk to remove it. But anyway, what apt-get does is mainly calling dpgk in pretty much the same way as your "dpkg"-command is. [/SIZE]
[SIZE=2]That's all, as far as I know.[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]It was installed using **"dpkg"** so I will use that to uninstall everything, even though the ATI Wiki says to use **"sudo apt-get remove --purge"**.If I use the --**purge** option it should remove everything correct?  I still struggle with understanding the difference between **"apt, aptitude & dpkg"**.  Also **"git"** but I think that's in a different category.[/SIZE]

---

### Post by Yellow Pasque on 2010-08-26
dpkg - the main package manager
apt(-get) - manages packages and repositories. Uses dpkg for a lot of its package operations
aptitude - fancy GUI front-end for apt, "smarter" than apt with dependency issues

In the wiki, I chose to use apt-get for the removal because it better handles wildcards(*) in the package names.

---

### Post by hayhursm on 2010-08-26
> **Temüjin said:**
> dpkg - the main package manager
apt(-get) - manages packages and repositories. Uses dpkg for a lot of its package operations
aptitude - fancy GUI front-end for apt, "smarter" than apt with dependency issues

In the wiki, I chose to use apt-get for the removal because it better handles wildcards(*) in the package names.

Thank you.

---

