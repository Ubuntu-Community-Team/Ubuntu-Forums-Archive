---
title: "Cant watch youtube videos!"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by ukulele_ninja on 2007-07-29
Whevever I go to youtube to watch videos or any internet video sites, none of them work! Am I missing something? I have firefox and kubuntu.

---

### Post by Gremlinzzz on 2007-07-29
first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
this should work for everyone.

---

### Post by ukulele_ninja on 2007-07-29
m ~/.mozilla/plugins/*flash*

It said bad command when i did that one

---

### Post by jimhaddon on 2007-07-29
try without the * either side of flash

---

### Post by ukulele_ninja on 2007-07-29
ryan@Ted:~/Desktop$ m ~/.mozilla/plugins/flash
bash: m: command not found
ryan@Ted:~/Desktop$

---

### Post by Koybe on 2007-07-29
He gave you 'rm' command and you typed 'm' command. That's why it's not working.

Anyway you can just get it installed trough synaptic or by using this command :
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by ukulele_ninja on 2007-07-29
> **Koybe said:**
> He gave you 'rm' command and you typed 'm' command. That's why it's not working.

Anyway you can just get it installed trough synaptic or by using this command :
```
sudo apt-get install flashplugin-nonfree
```



I copy and pasted what he gave me... anyway heres what yours gave me:

ryan@Ted:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate
ryan@Ted:~$

---

### Post by regomodo on 2007-07-29
you didn't copy and paste the whole command. it should be "rm" not "m"

---

### Post by Gremlinzzz on 2007-07-29
Skip the removal part don't think you have any flash too remove . But what kind of computer do you have?command should be good?

---

### Post by ukulele_ninja on 2007-07-29
Ok my bad, heres the complete output from what gremlin gave me:

ryan@Ted:~$ sudo apt-get remove flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  beryl-core beryl-plugins libberyldecoration0 libxul-common libnspr4-0d
  beryl-settings-bindings libxul0d gstreamer0.10-x libmozjs0d
  libberylsettings0 libemeraldengine0 libnss3-0d beryl-plugins-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
ryan@Ted:~$ rm ~/.mozilla/plugins/*flash*
rm: cannot remove `/home/ryan/.mozilla/plugins/*flash*': No such file or directory
ryan@Ted:~$ cd Desktop
ryan@Ted:~/Desktop$ tar -xvzf install_flash_player_9_linux.tar.gz
install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer.xpt
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
ryan@Ted:~/Desktop$ sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
ryan@Ted:~/Desktop$ sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
ryan@Ted:~/Desktop$

---

### Post by ukulele_ninja on 2007-07-29
> **Gremlinzzz said:**
> Skip the removal part don't think you have any flash too remove . But what kind of computer do you have?command should be good?


I have a compaq with Kubuntu

---

### Post by Koybe on 2007-07-29
Which version of ubuntu are you using?

flashplungin is in multiverse repository, be sure it's enable.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

edit :
I think you have some package error try:
```
sudo apt-get autoremove
sudo apt-get -f install
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by ukulele_ninja on 2007-07-29
ryan@Ted:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate


that was my output... I dont know how to check if that repository is open or not. I went to Adept and looked but i didnt see it.

---

### Post by Gremlinzzz on 2007-07-29
Just pasted the command i gave you in my computer and it worked.the reason i asked about your computer was i wanted to know if you have a 64-bit processor /

---

### Post by Koybe on 2007-07-29
> **ukulele_ninja said:**
> that was my output... I dont know how to check if that repository is open or not. I went to Adept and looked but i didnt see it.
I'm not using adept so I can't help by that way.

If you want you can open your /etc/apt/sources.list and remove the # on the line before multiverse if any. It should look like this
```

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://fr.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://fr.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ feisty multiverse
```Then 
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty multiverse

---

### Post by Gremlinzzz on 2007-07-29
> **Gremlinzzz said:**
> Just pasted the command i gave you in my computer and it worked.the reason i asked about your computer was i wanted to know if you have a 64-bit processor /

if you did all the commands i gave you restart your browser and go to utube .

---

### Post by ukulele_ninja on 2007-07-29
> **Koybe said:**
> I'm not using adept so I can't help by that way.

If you want you can open your /etc/apt/sources.list and remove the # on the line before multiverse if any. It should look like this
```

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://fr.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://fr.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ feisty multiverse
```Then 
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty multiverse

HEREs what I have

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
    # Treviño’s Ubuntu Deisty EyeCandy Repository (GPG key: 81836EBF)
    # Many eyecandy 3D apps: Beryl, Compiz, Fusion, AWN and kiba-dock
    # built by jbs using latest available (working) sources from git/svn/cvs...
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy-amd64
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy-amd64

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://debs.vorian.org](http://debs.vorian.org) feisty extras deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

---

### Post by ukulele_ninja on 2007-07-29
> **Gremlinzzz said:**
> Just pasted the command i gave you in my computer and it worked.the reason i asked about your computer was i wanted to know if you have a 64-bit processor /

yes i do have 64 bit

---

### Post by Gremlinzzz on 2007-07-29
[http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727)

---

### Post by ukulele_ninja on 2007-07-29
Ok, I hate to be a nuisance, but I dont understand at all what that wants me to do and i keep getting errors. Can you copy and paste that parts that apply to me? I have kubuntu with fiesty i did check and see that my repositories are correct according to that pages directions.

---

### Post by Gremlinzzz on 2007-07-29
> **ukulele_ninja said:**
> Ok, I hate to be a nuisance, but I dont understand at all what that wants me to do and i keep getting errors. Can you copy and paste that parts that apply to me? I have kubuntu with fiesty i did check and see that my repositories are correct according to that pages directions.

I never installed flashplayer for 64 bit but heres a how too
[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

---

### Post by ukulele_ninja on 2007-07-29
Yeah this is the confusing one... How do I run this guys script thing? He says double click it and open in terminal but when i click it it doesnt open.

---

### Post by Gremlinzzz on 2007-07-29
I don't have a clue but theres a category called x86 64 bit users. you could post your problem there 
 [http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)

---

