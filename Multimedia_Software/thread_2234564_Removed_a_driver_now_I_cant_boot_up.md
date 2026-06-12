---
title: "Removed a driver now I cant boot up"
date: 2014-07-15
forum: Multimedia Software
---

### Post by dimmaz88 on 2014-07-15
Hi everyone, as the title suggests I removed a driver/program? I kept getting an error message saying this program wasn't working I can't remember the name but I think it ended in dp or ld, something like that. (I searched in the software center and it said 'show 1 technical package/program' I noticed it had 1 star reviews.

I'm pretty sure it said it was a lightweight graphics driver, but again I'm not sure.

I knew at the time it would be a risk to remove, but I did it anyway. After I did i was using pc as normal, then a few lines of code sort of appeared at the top of my screen.


I restarted as I'd just updated and now I can't get back on.

I tried the recovery mode, fixing damaged packages, previous versions. To no avail.

Does anyone have any idea which program it was and how to fix it?

Thanks in advance

Scott

---

### Post by Bashing-om on 2014-07-15
dimmaz88; Hi ! Welcome to the forum.

Talk about a long term guessing game "I'm pretty sure it said it was a lightweight graphics driver, but again I'm not sure. Does anyone have any idea which program it was and how to fix it? " .............
I run a minimal install and very light and I still have:
> 
(Reading database ... 93303 files and directories currently installed.)

Your install may be twice as large or more. 
I do not think a guessing game will be too productive.

If you are able to boot to a terminal from the grub boot menu ( editing the boot parameter ) .. we might get some info as to what the package manager thinks of the situation .
Terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install

```
Advise us of the result, and if errors are reported, we need to know the EXACT error message and in context.

Gotta start pok'n at it someplace, this is as good as some
[INDENT][INDENT][INDENT]maybe better than others
[/INDENT][/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-16
Thanks for your reply, I managed to figure out the program it was **lightdm**. I re-installed it by pressing ctrl-alt-f1 whilst the splash screen was frozen.

That worked to get me back on, however now when I boot up it displays a flashing warning saying 'broken pipe'. I get on by going through the recovery mode and repairing packages.

Any idea how to fix this new problem?

Thanks again.

---

### Post by Bashing-om on 2014-07-16
dimmaz88; Well, well;

Making progress. Before we take the sledge hammer approach and (re-)install unity ...
What release are you running? It does make a difference how we clean up your desk top.
Presently, what does the package manager report.
Post back - between code tags - the outputs of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
dpkg -C

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

With those outputs, we get an indication of what needs to be replaced.

[INDENT][INDENT]ubuntu
[INDENT][INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-16
```
scott@scott-desktop:~$ sudo apt-get update
[sudo] password for scott: 
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Err http://extras.ubuntu.com precise Release                                   
  
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:2 http://76.73.4.58 precise Release.gpg [198 B]                            
Get:3 http://76.73.4.58 precise-updates Release.gpg [198 B]                    
Get:4 http://76.73.4.58 precise-backports Release.gpg [198 B]                  
Get:5 http://76.73.4.58 precise-security Release.gpg [198 B]                   
Hit http://76.73.4.58 precise Release                                          
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en             
Get:6 http://download.ebz.epson.net lsb3.2 Release.gpg [189 B]
Get:7 http://76.73.4.58 precise-updates Release [49.6 kB] 
Hit http://download.ebz.epson.net lsb3.2 Release       
Ign http://download.ebz.epson.net lsb3.2 Release          
Hit http://76.73.4.58 precise-backports Release           
Get:8 http://76.73.4.58 precise-security Release [49.6 kB]
Hit http://76.73.4.58 precise/main Sources                                     
Hit http://76.73.4.58 precise/restricted Sources
Hit http://76.73.4.58 precise/universe Sources  
Hit http://76.73.4.58 precise/multiverse Sources
Hit http://76.73.4.58 precise/main i386 Packages
Hit http://76.73.4.58 precise/restricted i386 Packages
Hit http://76.73.4.58 precise/universe i386 Packages
Hit http://76.73.4.58 precise/multiverse i386 Packages
Hit http://76.73.4.58 precise/main TranslationIndex
Ign http://download.ebz.epson.net lsb3.2/main i386 Packages/DiffIndex
Hit http://76.73.4.58 precise/multiverse TranslationIndex
Hit http://76.73.4.58 precise/restricted TranslationIndex
Hit http://76.73.4.58 precise/universe TranslationIndex
Get:9 http://76.73.4.58 precise-updates/main Sources [475 kB]
Ign http://download.ebz.epson.net lsb3.2/main TranslationIndex
Hit http://download.ebz.epson.net lsb3.2/main Translation-en_GB
Hit http://download.ebz.epson.net lsb3.2/main Translation-en
Get:10 http://76.73.4.58 precise-updates/restricted Sources [8,056 B]
Get:11 http://76.73.4.58 precise-updates/universe Sources [108 kB]
Err http://download.ebz.epson.net lsb3.2/main i386 Packages                   
  
Get:12 http://76.73.4.58 precise-updates/multiverse Sources [8,905 B]         
Get:13 http://76.73.4.58 precise-updates/main i386 Packages [847 kB]           
Err http://download.ebz.epson.net lsb3.2/main i386 Packages                    
  
Hit http://download.ebz.epson.net lsb3.2/main i386 Packages
Get:14 http://76.73.4.58 precise-updates/restricted i386 Packages [13.7 kB]
Get:15 http://76.73.4.58 precise-updates/universe i386 Packages [250 kB]
Get:16 http://76.73.4.58 precise-updates/multiverse i386 Packages [15.5 kB]
Get:17 http://76.73.4.58 precise-updates/main TranslationIndex [3,564 B]
Get:18 http://76.73.4.58 precise-updates/multiverse TranslationIndex [2,605 B]
Get:19 http://76.73.4.58 precise-updates/restricted TranslationIndex [2,461 B]
Get:20 http://76.73.4.58 precise-updates/universe TranslationIndex [2,850 B]
Hit http://76.73.4.58 precise-backports/main Sources                  
Hit http://76.73.4.58 precise-backports/restricted Sources
Hit http://76.73.4.58 precise-backports/universe Sources
Hit http://76.73.4.58 precise-backports/multiverse Sources
Hit http://76.73.4.58 precise-backports/main i386 Packages
Hit http://76.73.4.58 precise-backports/restricted i386 Packages
Hit http://76.73.4.58 precise-backports/universe i386 Packages
Hit http://76.73.4.58 precise-backports/multiverse i386 Packages
Hit http://76.73.4.58 precise-backports/main TranslationIndex
Hit http://76.73.4.58 precise-backports/multiverse TranslationIndex
Hit http://76.73.4.58 precise-backports/restricted TranslationIndex
Hit http://76.73.4.58 precise-backports/universe TranslationIndex
Get:21 http://76.73.4.58 precise-security/main Sources [106 kB]
Get:22 http://76.73.4.58 precise-security/restricted Sources [2,494 B]
Get:23 http://76.73.4.58 precise-security/universe Sources [30.7 kB]
Get:24 http://76.73.4.58 precise-security/multiverse Sources [1,795 B]
Get:25 http://76.73.4.58 precise-security/main i386 Packages [433 kB]
Get:26 http://76.73.4.58 precise-security/restricted i386 Packages [4,620 B]
Get:27 http://76.73.4.58 precise-security/universe i386 Packages [99.3 kB]
Get:28 http://76.73.4.58 precise-security/multiverse i386 Packages [2,650 B]
Get:29 http://76.73.4.58 precise-security/main TranslationIndex [74 B]
Get:30 http://76.73.4.58 precise-security/multiverse TranslationIndex [72 B]
Get:31 http://76.73.4.58 precise-security/restricted TranslationIndex [72 B]
Get:32 http://76.73.4.58 precise-security/universe TranslationIndex [73 B]
Hit http://76.73.4.58 precise/main Translation-en_GB             
Hit http://76.73.4.58 precise/main Translation-en                
Hit http://76.73.4.58 precise/multiverse Translation-en_GB       
Hit http://76.73.4.58 precise/multiverse Translation-en          
Hit http://76.73.4.58 precise/restricted Translation-en_GB
Hit http://76.73.4.58 precise/restricted Translation-en
Hit http://76.73.4.58 precise/universe Translation-en_GB
Hit http://76.73.4.58 precise/universe Translation-en
Hit http://76.73.4.58 precise-updates/main Translation-en_GB
Get:33 http://76.73.4.58 precise-updates/main Translation-en [359 kB]
Hit http://76.73.4.58 precise-updates/multiverse Translation-en_GB             
Hit http://76.73.4.58 precise-updates/multiverse Translation-en                
Hit http://76.73.4.58 precise-updates/restricted Translation-en_GB             
Hit http://76.73.4.58 precise-updates/restricted Translation-en                
Hit http://76.73.4.58 precise-updates/universe Translation-en_GB               
Get:34 http://76.73.4.58 precise-updates/universe Translation-en [142 kB]      
Hit http://76.73.4.58 precise-backports/main Translation-en                    
Hit http://76.73.4.58 precise-backports/multiverse Translation-en              
Hit http://76.73.4.58 precise-backports/restricted Translation-en              
Hit http://76.73.4.58 precise-backports/universe Translation-en                
Get:35 http://76.73.4.58 precise-security/main Translation-en [186 kB]         
Hit http://76.73.4.58 precise-security/multiverse Translation-en               
Hit http://76.73.4.58 precise-security/restricted Translation-en               
Get:36 http://76.73.4.58 precise-security/universe Translation-en [57.8 kB]    
Fetched 3,262 kB in 7s (427 kB/s)                                              
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://download.ebz.epson.net lsb3.2 Release: The following signatures were invalid: BADSIG E5E86C008AA65D56 Seiko Epson Corporation (Epson Inkjet Printer Driver) <epson-linux-inkjet@avasys.jp>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
scott@scott-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  file libavcodec-extra-53 libavdevice53 libavformat53 libavutil-extra-51
  libjpeg-turbo8 libmagic1 libminiupnpc8 libpostproc52 libswscale2
  transmission-common transmission-gtk wget
13 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 8,656 kB of archives.
After this operation, 3,072 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://76.73.4.58/ubuntu/ precise-updates/main libpostproc52 i386 4:0.8.13-0ubuntu0.12.04.1 [116 kB]
Get:2 http://76.73.4.58/ubuntu/ precise-updates/main libswscale2 i386 4:0.8.13-0ubuntu0.12.04.1 [195 kB]
Get:3 http://76.73.4.58/ubuntu/ precise-updates/main libavdevice53 i386 4:0.8.13-0ubuntu0.12.04.1 [52.9 kB]
Get:4 http://76.73.4.58/ubuntu/ precise-updates/main libavformat53 i386 4:0.8.13-0ubuntu0.12.04.1 [1,039 kB]
Get:5 http://76.73.4.58/ubuntu/ precise-updates/universe libavcodec-extra-53 i386 4:0.8.13ubuntu0.12.04.1 [5,836 kB]
Get:6 http://76.73.4.58/ubuntu/ precise-updates/universe libavutil-extra-51 i386 4:0.8.13ubuntu0.12.04.1 [133 kB]
Get:7 http://76.73.4.58/ubuntu/ precise-updates/main libjpeg-turbo8 i386 1.1.90+svn733-0ubuntu4.4 [118 kB]
Get:8 http://76.73.4.58/ubuntu/ precise-updates/main file i386 5.09-2ubuntu0.4 [19.4 kB]
Get:9 http://76.73.4.58/ubuntu/ precise-updates/main libmagic1 i386 5.09-2ubuntu0.4 [220 kB]
Get:10 http://76.73.4.58/ubuntu/ precise-updates/main wget i386 1.13.4-2ubuntu1.1 [280 kB]
Get:11 http://76.73.4.58/ubuntu/ precise-updates/main libminiupnpc8 i386 1.6-3ubuntu1.1 [24.9 kB]
Get:12 http://76.73.4.58/ubuntu/ precise-updates/main transmission-common all 2.51-0ubuntu1.4 [267 kB]
Get:13 http://76.73.4.58/ubuntu/ precise-updates/main transmission-gtk i386 2.51-0ubuntu1.4 [355 kB]
Fetched 8,656 kB in 11s (769 kB/s)                                             
(Reading database ... 411638 files and directories currently installed.)
Preparing to replace libpostproc52 4:0.8.12-0ubuntu0.12.04.1 (using .../libpostproc52_4%3a0.8.13-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libpostproc52 ...
Preparing to replace libswscale2 4:0.8.12-0ubuntu0.12.04.1 (using .../libswscale2_4%3a0.8.13-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libswscale2 ...
Preparing to replace libavdevice53 4:0.8.12-0ubuntu0.12.04.1 (using .../libavdevice53_4%3a0.8.13-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libavdevice53 ...
Preparing to replace libavformat53 4:0.8.12-0ubuntu0.12.04.1 (using .../libavformat53_4%3a0.8.13-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libavformat53 ...
Preparing to replace libavcodec-extra-53 4:0.8.12ubuntu0.12.04.1 (using .../libavcodec-extra-53_4%3a0.8.13ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libavcodec-extra-53 ...
Preparing to replace libavutil-extra-51 4:0.8.12ubuntu0.12.04.1 (using .../libavutil-extra-51_4%3a0.8.13ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libavutil-extra-51 ...
Preparing to replace libjpeg-turbo8 1.1.90+svn733-0ubuntu4.3 (using .../libjpeg-turbo8_1.1.90+svn733-0ubuntu4.4_i386.deb) ...
Unpacking replacement libjpeg-turbo8 ...
Preparing to replace file 5.09-2ubuntu0.3 (using .../file_5.09-2ubuntu0.4_i386.deb) ...
Unpacking replacement file ...
Preparing to replace libmagic1 5.09-2ubuntu0.3 (using .../libmagic1_5.09-2ubuntu0.4_i386.deb) ...
Unpacking replacement libmagic1 ...
Preparing to replace wget 1.13.4-2ubuntu1 (using .../wget_1.13.4-2ubuntu1.1_i386.deb) ...
Unpacking replacement wget ...
Preparing to replace libminiupnpc8 1.6-3ubuntu1 (using .../libminiupnpc8_1.6-3ubuntu1.1_i386.deb) ...
Unpacking replacement libminiupnpc8 ...
Preparing to replace transmission-common 2.51-0ubuntu1.3 (using .../transmission-common_2.51-0ubuntu1.4_all.deb) ...
Unpacking replacement transmission-common ...
Preparing to replace transmission-gtk 2.51-0ubuntu1.3 (using .../transmission-gtk_2.51-0ubuntu1.4_i386.deb) ...
Unpacking replacement transmission-gtk ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up libavutil-extra-51 (4:0.8.13ubuntu0.12.04.1) ...
Setting up libpostproc52 (4:0.8.13-0ubuntu0.12.04.1) ...
Setting up libswscale2 (4:0.8.13-0ubuntu0.12.04.1) ...
Setting up libavcodec-extra-53 (4:0.8.13ubuntu0.12.04.1) ...
Setting up libavformat53 (4:0.8.13-0ubuntu0.12.04.1) ...
Setting up libavdevice53 (4:0.8.13-0ubuntu0.12.04.1) ...
Setting up libjpeg-turbo8 (1.1.90+svn733-0ubuntu4.4) ...
Setting up libmagic1 (5.09-2ubuntu0.4) ...
Setting up file (5.09-2ubuntu0.4) ...
Setting up wget (1.13.4-2ubuntu1.1) ...
Setting up libminiupnpc8 (1.6-3ubuntu1.1) ...
Setting up transmission-common (2.51-0ubuntu1.4) ...
Setting up transmission-gtk (2.51-0ubuntu1.4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
scott@scott-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-kde-en language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
scott@scott-desktop:~$ dpkg -C
scott@scott-desktop:~$ dpkg-c
dpkg-c: command not found
scott@scott-desktop:~$ dpkg -c
dpkg-deb: error: --contents takes exactly one argument

Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --help for help about installing and deinstalling packages.
scott@scott-desktop:~$ 


```

The last command didn't seem to do anything (dpkg -C)

---

### Post by Bashing-om on 2014-07-16
dimmaz88; Hey;

Not look'n to real bad at all.
OK, 'dpkg -C' my bad; should be:
```

sudo dpkg -C

```
The "GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release" we can fix by pulling in the signing key:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

```
As to "Err [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main i386 Packages" we need to do some additional investigation. What is this ? A means to obtain a printer driver ?
Let's find the source and see what the error is all about.
What release are you running ?
```

lsb_release -a

```
and to find the source of '.ebz.epson" Post back:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

``` Maybe that 3rd party does not support the release you are running ? We will look and see.

[INDENT][INDENT]seek and ye shall find
[/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-17
Thanks for your help bashing, I really appreciate it. 

I did the sudo dpkg -C command, still doesn't give an output, is it supposed too?

This is after the gpg error fix.

```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.NrG5F9Ji66 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d//jockey-drivers.gpg --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" 3 new signatures
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:         new signatures: 3


```

This is the release
```
scott@scott-desktop:~$ lsb_release -a
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:printing-3.2-ia32:printing-3.2-noarch:printing-4.0-ia32:printing-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

```

This is the .ebz.epson stuff, I do have an epson printer
```
cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)]/ precise main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://76.73.4.58/ubuntu/ precise main restricted
     6    deb-src http://76.73.4.58/ubuntu/ precise main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://76.73.4.58/ubuntu/ precise-updates main restricted
    11    deb-src http://76.73.4.58/ubuntu/ precise-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://76.73.4.58/ubuntu/ precise universe
    17    deb-src http://76.73.4.58/ubuntu/ precise universe
    18    deb http://76.73.4.58/ubuntu/ precise-updates universe
    19    deb-src http://76.73.4.58/ubuntu/ precise-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://76.73.4.58/ubuntu/ precise multiverse
    27    deb-src http://76.73.4.58/ubuntu/ precise multiverse
    28    deb http://76.73.4.58/ubuntu/ precise-updates multiverse
    29    deb-src http://76.73.4.58/ubuntu/ precise-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://76.73.4.58/ubuntu/ precise-backports main restricted universe multiverse
    37    deb-src http://76.73.4.58/ubuntu/ precise-backports main restricted universe multiverse
    38    
    39    deb http://76.73.4.58/ubuntu/ precise-security main restricted
    40    deb-src http://76.73.4.58/ubuntu/ precise-security main restricted
    41    deb http://76.73.4.58/ubuntu/ precise-security universe
    42    deb-src http://76.73.4.58/ubuntu/ precise-security universe
    43    deb http://76.73.4.58/ubuntu/ precise-security multiverse
    44    deb-src http://76.73.4.58/ubuntu/ precise-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu precise partner
    51    # deb-src http://archive.canonical.com/ubuntu precise partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu precise main
    56    deb-src http://extras.ubuntu.com/ubuntu precise main

```

And..
```
1    # deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)]/ precise main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://76.73.4.58/ubuntu/ precise main restricted
     6    deb-src http://76.73.4.58/ubuntu/ precise main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://76.73.4.58/ubuntu/ precise-updates main restricted
    11    deb-src http://76.73.4.58/ubuntu/ precise-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://76.73.4.58/ubuntu/ precise universe
    17    deb-src http://76.73.4.58/ubuntu/ precise universe
    18    deb http://76.73.4.58/ubuntu/ precise-updates universe
    19    deb-src http://76.73.4.58/ubuntu/ precise-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://76.73.4.58/ubuntu/ precise multiverse
    27    deb-src http://76.73.4.58/ubuntu/ precise multiverse
    28    deb http://76.73.4.58/ubuntu/ precise-updates multiverse
    29    deb-src http://76.73.4.58/ubuntu/ precise-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://76.73.4.58/ubuntu/ precise-backports main restricted universe multiverse
    37    deb-src http://76.73.4.58/ubuntu/ precise-backports main restricted universe multiverse
    38    
    39    deb http://76.73.4.58/ubuntu/ precise-security main restricted
    40    deb-src http://76.73.4.58/ubuntu/ precise-security main restricted
    41    deb http://76.73.4.58/ubuntu/ precise-security universe
    42    deb-src http://76.73.4.58/ubuntu/ precise-security universe
    43    deb http://76.73.4.58/ubuntu/ precise-security multiverse
    44    deb-src http://76.73.4.58/ubuntu/ precise-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu precise partner
    51    # deb-src http://archive.canonical.com/ubuntu precise partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu precise main
    56    deb-src http://extras.ubuntu.com/ubuntu precise main
scott@scott-desktop:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/jockey.list <==
deb http://download.ebz.epson.net/dsc/op/stable/debian/ lsb3.2 main

==> /etc/apt/sources.list.d/jockey.list.save <==
deb http://download.ebz.epson.net/dsc/op/stable/debian/ lsb3.2 main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main

```

Thanks again, this is so confusing. I really should learn more about the workings of Ubuntu :)

Scott

---

### Post by Bashing-om on 2014-07-17
dimmaz88; Hey hey;

Ok, This is ubuntu; things are supposed to just work - if you stay within the umbrella of protection that is the ubuntu package management system.

As to "sudo dpkg -C" that is asking 'dpkg' to list any known problems, thus a no output is a good thing in that the package management system is in a consistent state.
I expect we are down to the signing key for "epson" . Looking at it and it "appears" to me to be valid.
Let's try this and see if our server holds the key:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E5E86C008AA65D56

```
This is but one of the means that ubuntu employs to insure no malware is introduced into the system - that the software is "trusted".
If that returns good - and the package manager remains in a consistent state -
We will return to the original question and insure your desktop is now functionable;
What then returns from terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by dimmaz88 on 2014-07-17
I've just run those 3 commands
```
scott@scott-desktop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E5E86C008AA65D56
[sudo] password for scott: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.5y4Jw94F66 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d//jockey-drivers.gpg --keyserver keyserver.ubuntu.com --recv-keys E5E86C008AA65D56
gpg: requesting key 8AA65D56 from hkp server keyserver.ubuntu.com
gpg: key 8AA65D56: "Seiko Epson Corporation (Epson Inkjet Printer Driver) <epson-linux-inkjet@avasys.jp>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
scott@scott-desktop:~$ sudo apt-get update
Hit http://ppa.launchpad.net precise Release.gpg
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise Release                                   
Err http://extras.ubuntu.com precise Release                                   
  
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:2 http://76.73.4.58 precise Release.gpg [198 B]                            
Get:3 http://76.73.4.58 precise-updates Release.gpg [198 B]                    
Get:4 http://76.73.4.58 precise-backports Release.gpg [198 B]                  
Get:5 http://76.73.4.58 precise-security Release.gpg [198 B]                   
Hit http://76.73.4.58 precise Release                                          
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en             
Get:6 http://download.ebz.epson.net lsb3.2 Release.gpg [189 B]
Hit http://76.73.4.58 precise-updates Release             
Hit http://76.73.4.58 precise-backports Release
Hit http://76.73.4.58 precise-security Release                        
Hit http://download.ebz.epson.net lsb3.2 Release                      
Ign http://download.ebz.epson.net lsb3.2 Release
Hit http://76.73.4.58 precise/main Sources      
Hit http://76.73.4.58 precise/restricted Sources
Hit http://76.73.4.58 precise/universe Sources 
Hit http://76.73.4.58 precise/multiverse Sources
Hit http://76.73.4.58 precise/main i386 Packages
Hit http://76.73.4.58 precise/restricted i386 Packages
Hit http://76.73.4.58 precise/universe i386 Packages
Hit http://76.73.4.58 precise/multiverse i386 Packages
Hit http://76.73.4.58 precise/main TranslationIndex
Hit http://76.73.4.58 precise/multiverse TranslationIndex
Ign http://download.ebz.epson.net lsb3.2/main i386 Packages/DiffIndex
Hit http://76.73.4.58 precise/restricted TranslationIndex
Hit http://76.73.4.58 precise/universe TranslationIndex
Hit http://76.73.4.58 precise-updates/main Sources
Hit http://76.73.4.58 precise-updates/restricted Sources
Hit http://76.73.4.58 precise-updates/universe Sources
Hit http://76.73.4.58 precise-updates/multiverse Sources
Hit http://76.73.4.58 precise-updates/main i386 Packages
Hit http://76.73.4.58 precise-updates/restricted i386 Packages
Hit http://76.73.4.58 precise-updates/universe i386 Packages
Hit http://76.73.4.58 precise-updates/multiverse i386 Packages
Ign http://download.ebz.epson.net lsb3.2/main TranslationIndex
Hit http://76.73.4.58 precise-updates/main TranslationIndex
Hit http://76.73.4.58 precise-updates/multiverse TranslationIndex
Hit http://76.73.4.58 precise-updates/restricted TranslationIndex
Hit http://76.73.4.58 precise-updates/universe TranslationIndex
Hit http://76.73.4.58 precise-backports/main Sources
Hit http://76.73.4.58 precise-backports/restricted Sources
Hit http://76.73.4.58 precise-backports/universe Sources
Hit http://76.73.4.58 precise-backports/multiverse Sources
Hit http://76.73.4.58 precise-backports/main i386 Packages
Hit http://76.73.4.58 precise-backports/restricted i386 Packages
Hit http://76.73.4.58 precise-backports/universe i386 Packages
Hit http://76.73.4.58 precise-backports/multiverse i386 Packages
Hit http://76.73.4.58 precise-backports/main TranslationIndex
Hit http://76.73.4.58 precise-backports/multiverse TranslationIndex
Hit http://76.73.4.58 precise-backports/restricted TranslationIndex
Hit http://76.73.4.58 precise-backports/universe TranslationIndex
Hit http://76.73.4.58 precise-security/main Sources
Hit http://76.73.4.58 precise-security/restricted Sources
Hit http://76.73.4.58 precise-security/universe Sources
Hit http://download.ebz.epson.net lsb3.2/main Translation-en_GB
Hit http://download.ebz.epson.net lsb3.2/main Translation-en
Hit http://76.73.4.58 precise-security/multiverse Sources
Hit http://76.73.4.58 precise-security/main i386 Packages
Hit http://76.73.4.58 precise-security/restricted i386 Packages
Hit http://76.73.4.58 precise-security/universe i386 Packages
Hit http://76.73.4.58 precise-security/multiverse i386 Packages
Hit http://76.73.4.58 precise-security/main TranslationIndex
Hit http://76.73.4.58 precise-security/multiverse TranslationIndex
Hit http://76.73.4.58 precise-security/restricted TranslationIndex
Hit http://76.73.4.58 precise-security/universe TranslationIndex
Hit http://76.73.4.58 precise/main Translation-en_GB
Err http://download.ebz.epson.net lsb3.2/main i386 Packages
  
Hit http://76.73.4.58 precise/main Translation-en
Hit http://76.73.4.58 precise/multiverse Translation-en_GB
Hit http://76.73.4.58 precise/multiverse Translation-en
Hit http://76.73.4.58 precise/restricted Translation-en_GB
Hit http://76.73.4.58 precise/restricted Translation-en
Hit http://76.73.4.58 precise/universe Translation-en_GB
Hit http://76.73.4.58 precise/universe Translation-en
Hit http://76.73.4.58 precise-updates/main Translation-en_GB
Hit http://76.73.4.58 precise-updates/main Translation-en
Hit http://76.73.4.58 precise-updates/multiverse Translation-en_GB
Err http://download.ebz.epson.net lsb3.2/main i386 Packages
  
Hit http://76.73.4.58 precise-updates/multiverse Translation-en
Hit http://download.ebz.epson.net lsb3.2/main i386 Packages
Hit http://76.73.4.58 precise-updates/restricted Translation-en_GB
Hit http://76.73.4.58 precise-updates/restricted Translation-en
Hit http://76.73.4.58 precise-updates/universe Translation-en_GB
Hit http://76.73.4.58 precise-updates/universe Translation-en
Hit http://76.73.4.58 precise-backports/main Translation-en
Hit http://76.73.4.58 precise-backports/multiverse Translation-en
Hit http://76.73.4.58 precise-backports/restricted Translation-en
Hit http://76.73.4.58 precise-backports/universe Translation-en
Hit http://76.73.4.58 precise-security/main Translation-en
Hit http://76.73.4.58 precise-security/multiverse Translation-en
Hit http://76.73.4.58 precise-security/restricted Translation-en
Hit http://76.73.4.58 precise-security/universe Translation-en
Fetched 1,053 B in 2s (357 B/s)
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://download.ebz.epson.net lsb3.2 Release: The following signatures were invalid: BADSIG E5E86C008AA65D56 Seiko Epson Corporation (Epson Inkjet Printer Driver) <epson-linux-inkjet@avasys.jp>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
scott@scott-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-lts-raring
  linux-headers-generic-lts-trusty linux-headers-generic-pae
  linux-image-generic-lts-raring linux-image-generic-lts-trusty
  linux-image-generic-pae
The following packages will be upgraded:
  linux-generic-lts-raring linux-generic-lts-trusty linux-libc-dev
3 to upgrade, 0 to newly install, 0 to remove and 7 not to upgrade.
Need to get 861 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://76.73.4.58/ubuntu/ precise-updates/main linux-generic-lts-raring i386 3.8.0.44.44 [1,742 B]
Get:2 http://76.73.4.58/ubuntu/ precise-updates/main linux-generic-lts-trusty i386 3.13.0.32.28 [1,746 B]
Get:3 http://76.73.4.58/ubuntu/ precise-updates/main linux-libc-dev i386 3.2.0-67.101 [858 kB]
Fetched 861 kB in 1s (526 kB/s)         
(Reading database ... 411638 files and directories currently installed.)
Preparing to replace linux-generic-lts-raring 3.8.0.42.42 (using .../linux-generic-lts-raring_3.8.0.44.44_i386.deb) ...
Unpacking replacement linux-generic-lts-raring ...
Preparing to replace linux-generic-lts-trusty 3.13.0.30.26 (using .../linux-generic-lts-trusty_3.13.0.32.28_i386.deb) ...
Unpacking replacement linux-generic-lts-trusty ...
Preparing to replace linux-libc-dev 3.2.0-65.99 (using .../linux-libc-dev_3.2.0-67.101_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Setting up linux-generic-lts-raring (3.8.0.44.44) ...
Setting up linux-generic-lts-trusty (3.13.0.32.28) ...
Setting up linux-libc-dev (3.2.0-67.101) ...


```

---

### Post by Bashing-om on 2014-07-17
dimmaz88; Oh Boy,

Still with the GPG error and BADSIG E5E86C008AA65D56 even after re-affirming the signing keys ( good ), but;
> 
gpg: key 8AA65D56: "Seiko Epson Corporation (Epson Inkjet Printer Driver) <epson-linux-inkjet@avasys.jp>" not changed

It is now above my skill set to know what the problem is.
Let's see if others will chime in and offer guidance in this mater.

[INDENT]a failure to communicate ?
[/INDENT]

---

### Post by dimmaz88 on 2014-07-17
Thanks for all your help this far bashing, I'd of just re-installed ubuntu and probably cried lol. 

Hopefully someone will have a fix. Is it an epson driver that is causing it? could it be removed?

---

### Post by Bashing-om on 2014-07-17
dimmaz88; Nahh,

Not a driver situation .., A signing key thing for authorization/verification of obtaining software.
No need to re-install.
I just do not have the experience to advise; If worse comes to worse, we can 'experiment' and try and find the cause. Certain to learn a thing or two in the process.

Will take some time, 

EDIT: Here is a thought:
```

sudo apt-key update

```
which might fix the missing Ubuntu key.

If you are in for a learning experience
[INDENT][INDENT][INDENT]I am willing
[/INDENT][/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-17
Here's the result, don't think it's worked as it says processed 4, unchanged 4
```
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4


```

---

### Post by Bashing-om on 2014-07-17
dimmaz88; Welp,

I checked those on my system, and looks to be valid and correct.

What now results ?
```

sudo apt-get update
sudo apt-get upgrade

``` not that I expect any difference, but maybe ?
Still being stuborn ->
How 'bot we remove the ubuntu key and reload it and see what then results ?
```

sudo apt-key del 16126D3A3E5C1192
##then updating the repository##
sudo apt-get update
##You should get a NO_PUBKEY error instead of a BADSIG error and##
sudo apt-key finger
##should not find the key (called "Ubuntu Extras Archive Automatic Signing Key")##

##Now add the key##
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
##The result of apt-key finger -now- should have##
"pub   1024D/3E5C1192 2010-09-20
      Key fingerprint = C474 15DF F48C 0964 5B78  6094 1612 6D3A 3E5C 1192
uid                  Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
##or similar##

```
Now for sure you should have that one snake stomped on, let's check once more:
```

sudo apt-get update
sudo apt-get upgrade

``` 
If this one is done with we can focus on the Epson printer key.

[INDENT][INDENT][INDENT]maybe yes, maybe not so yes
[/INDENT][/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-17
I'm still getting the gpg error, everything was going so well until the last check.

```
scott@scott-desktop:~$ sudo apt-get update
[sudo] password for scott: 
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Err http://extras.ubuntu.com precise Release                                   
  
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:2 http://76.73.4.58 precise Release.gpg [198 B]                            
Get:3 http://76.73.4.58 precise-updates Release.gpg [198 B]                    
Get:4 http://76.73.4.58 precise-backports Release.gpg [198 B]                  
Get:5 http://76.73.4.58 precise-security Release.gpg [198 B]                   
Hit http://76.73.4.58 precise Release                                          
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en             
Get:6 http://download.ebz.epson.net lsb3.2 Release.gpg [189 B]
Get:7 http://76.73.4.58 precise-updates Release [49.6 kB] 
Hit http://download.ebz.epson.net lsb3.2 Release       
Ign http://download.ebz.epson.net lsb3.2 Release          
Hit http://76.73.4.58 precise-backports Release           
Get:8 http://76.73.4.58 precise-security Release [49.6 kB]
Hit http://76.73.4.58 precise/main Sources                                     
Hit http://76.73.4.58 precise/restricted Sources
Hit http://76.73.4.58 precise/universe Sources  
Hit http://76.73.4.58 precise/multiverse Sources
Hit http://76.73.4.58 precise/main i386 Packages
Hit http://76.73.4.58 precise/restricted i386 Packages
Hit http://76.73.4.58 precise/universe i386 Packages
Hit http://76.73.4.58 precise/multiverse i386 Packages
Hit http://76.73.4.58 precise/main TranslationIndex
Ign http://download.ebz.epson.net lsb3.2/main i386 Packages/DiffIndex
Hit http://76.73.4.58 precise/multiverse TranslationIndex
Hit http://76.73.4.58 precise/restricted TranslationIndex
Hit http://76.73.4.58 precise/universe TranslationIndex
Get:9 http://76.73.4.58 precise-updates/main Sources [475 kB]
Ign http://download.ebz.epson.net lsb3.2/main TranslationIndex
Hit http://download.ebz.epson.net lsb3.2/main Translation-en_GB
Hit http://download.ebz.epson.net lsb3.2/main Translation-en
Get:10 http://76.73.4.58 precise-updates/restricted Sources [8,056 B]
Get:11 http://76.73.4.58 precise-updates/universe Sources [108 kB]
Err http://download.ebz.epson.net lsb3.2/main i386 Packages                   
  
Get:12 http://76.73.4.58 precise-updates/multiverse Sources [8,905 B]         
Get:13 http://76.73.4.58 precise-updates/main i386 Packages [853 kB]        
Err http://download.ebz.epson.net lsb3.2/main i386 Packages                    
  
Hit http://download.ebz.epson.net lsb3.2/main i386 Packages
Get:14 http://76.73.4.58 precise-updates/restricted i386 Packages [13.7 kB]
Get:15 http://76.73.4.58 precise-updates/universe i386 Packages [251 kB]
Get:16 http://76.73.4.58 precise-updates/multiverse i386 Packages [15.5 kB]
Get:17 http://76.73.4.58 precise-updates/main TranslationIndex [3,564 B]
Get:18 http://76.73.4.58 precise-updates/multiverse TranslationIndex [2,605 B]
Get:19 http://76.73.4.58 precise-updates/restricted TranslationIndex [2,461 B]
Get:20 http://76.73.4.58 precise-updates/universe TranslationIndex [2,850 B]
Hit http://76.73.4.58 precise-backports/main Sources              
Hit http://76.73.4.58 precise-backports/restricted Sources
Hit http://76.73.4.58 precise-backports/universe Sources
Hit http://76.73.4.58 precise-backports/multiverse Sources
Hit http://76.73.4.58 precise-backports/main i386 Packages
Hit http://76.73.4.58 precise-backports/restricted i386 Packages
Hit http://76.73.4.58 precise-backports/universe i386 Packages
Hit http://76.73.4.58 precise-backports/multiverse i386 Packages
Hit http://76.73.4.58 precise-backports/main TranslationIndex
Hit http://76.73.4.58 precise-backports/multiverse TranslationIndex
Hit http://76.73.4.58 precise-backports/restricted TranslationIndex
Hit http://76.73.4.58 precise-backports/universe TranslationIndex
Get:21 http://76.73.4.58 precise-security/main Sources [106 kB]
Get:22 http://76.73.4.58 precise-security/restricted Sources [2,494 B]
Get:23 http://76.73.4.58 precise-security/universe Sources [30.7 kB]
Get:24 http://76.73.4.58 precise-security/multiverse Sources [1,795 B]
Get:25 http://76.73.4.58 precise-security/main i386 Packages [440 kB]
Get:26 http://76.73.4.58 precise-security/restricted i386 Packages [4,620 B]
Get:27 http://76.73.4.58 precise-security/universe i386 Packages [99.7 kB]
Get:28 http://76.73.4.58 precise-security/multiverse i386 Packages [2,650 B]
Get:29 http://76.73.4.58 precise-security/main TranslationIndex [74 B]
Get:30 http://76.73.4.58 precise-security/multiverse TranslationIndex [72 B]
Get:31 http://76.73.4.58 precise-security/restricted TranslationIndex [72 B]
Get:32 http://76.73.4.58 precise-security/universe TranslationIndex [73 B]
Hit http://76.73.4.58 precise/main Translation-en_GB            
Hit http://76.73.4.58 precise/main Translation-en               
Hit http://76.73.4.58 precise/multiverse Translation-en_GB      
Hit http://76.73.4.58 precise/multiverse Translation-en         
Hit http://76.73.4.58 precise/restricted Translation-en_GB
Hit http://76.73.4.58 precise/restricted Translation-en
Hit http://76.73.4.58 precise/universe Translation-en_GB
Hit http://76.73.4.58 precise/universe Translation-en
Hit http://76.73.4.58 precise-updates/main Translation-en_GB
Hit http://76.73.4.58 precise-updates/main Translation-en
Hit http://76.73.4.58 precise-updates/multiverse Translation-en_GB
Hit http://76.73.4.58 precise-updates/multiverse Translation-en
Hit http://76.73.4.58 precise-updates/restricted Translation-en_GB
Hit http://76.73.4.58 precise-updates/restricted Translation-en
Hit http://76.73.4.58 precise-updates/universe Translation-en_GB
Hit http://76.73.4.58 precise-updates/universe Translation-en
Hit http://76.73.4.58 precise-backports/main Translation-en
Hit http://76.73.4.58 precise-backports/multiverse Translation-en
Hit http://76.73.4.58 precise-backports/restricted Translation-en
Hit http://76.73.4.58 precise-backports/universe Translation-en
Hit http://76.73.4.58 precise-security/main Translation-en
Hit http://76.73.4.58 precise-security/multiverse Translation-en
Hit http://76.73.4.58 precise-security/restricted Translation-en
Hit http://76.73.4.58 precise-security/universe Translation-en
Fetched 2,532 kB in 6s (415 kB/s)                                              
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://download.ebz.epson.net lsb3.2 Release: The following signatures were invalid: BADSIG E5E86C008AA65D56 Seiko Epson Corporation (Epson Inkjet Printer Driver) <epson-linux-inkjet@avasys.jp>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
scott@scott-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-lts-raring
  linux-headers-generic-lts-trusty linux-headers-generic-pae
  linux-image-generic-lts-raring linux-image-generic-lts-trusty
  linux-image-generic-pae
0 to upgrade, 0 to newly install, 0 to remove and 7 not to upgrade.
scott@scott-desktop:~$ sudo apt-key del 16126D3A3E5C1192
OK
scott@scott-desktop:~$ sudo apt-get update
Hit http://ppa.launchpad.net precise Release.gpg
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise Release                                   
Err http://extras.ubuntu.com precise Release                                   
  
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://76.73.4.58 precise Release.gpg                                      
Hit http://76.73.4.58 precise-updates Release.gpg                              
Hit http://76.73.4.58 precise-backports Release.gpg                  
Hit http://76.73.4.58 precise-security Release.gpg                   
Hit http://76.73.4.58 precise Release                                
Hit http://76.73.4.58 precise-updates Release  
Hit http://76.73.4.58 precise-backports Release
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:2 http://download.ebz.epson.net lsb3.2 Release.gpg [189 B]       
Hit http://76.73.4.58 precise-security Release            
Hit http://76.73.4.58 precise/main Sources      
Hit http://76.73.4.58 precise/restricted Sources
Hit http://76.73.4.58 precise/universe Sources 
Hit http://76.73.4.58 precise/multiverse Sources
Hit http://76.73.4.58 precise/main i386 Packages
Hit http://76.73.4.58 precise/restricted i386 Packages
Hit http://download.ebz.epson.net lsb3.2 Release
Ign http://download.ebz.epson.net lsb3.2 Release
Hit http://76.73.4.58 precise/universe i386 Packages
Hit http://76.73.4.58 precise/multiverse i386 Packages
Hit http://76.73.4.58 precise/main TranslationIndex
Hit http://76.73.4.58 precise/multiverse TranslationIndex
Hit http://76.73.4.58 precise/restricted TranslationIndex
Hit http://76.73.4.58 precise/universe TranslationIndex
Hit http://76.73.4.58 precise-updates/main Sources
Hit http://76.73.4.58 precise-updates/restricted Sources
Hit http://76.73.4.58 precise-updates/universe Sources
Hit http://76.73.4.58 precise-updates/multiverse Sources
Ign http://download.ebz.epson.net lsb3.2/main i386 Packages/DiffIndex
Hit http://76.73.4.58 precise-updates/main i386 Packages
Hit http://76.73.4.58 precise-updates/restricted i386 Packages
Hit http://76.73.4.58 precise-updates/universe i386 Packages
Hit http://76.73.4.58 precise-updates/multiverse i386 Packages
Ign http://download.ebz.epson.net lsb3.2/main TranslationIndex
Hit http://76.73.4.58 precise-updates/main TranslationIndex
Hit http://76.73.4.58 precise-updates/multiverse TranslationIndex
Hit http://76.73.4.58 precise-updates/restricted TranslationIndex
Hit http://76.73.4.58 precise-updates/universe TranslationIndex
Hit http://76.73.4.58 precise-backports/main Sources
Hit http://76.73.4.58 precise-backports/restricted Sources
Hit http://76.73.4.58 precise-backports/universe Sources
Hit http://76.73.4.58 precise-backports/multiverse Sources
Hit http://76.73.4.58 precise-backports/main i386 Packages
Hit http://76.73.4.58 precise-backports/restricted i386 Packages
Hit http://76.73.4.58 precise-backports/universe i386 Packages
Hit http://76.73.4.58 precise-backports/multiverse i386 Packages
Hit http://76.73.4.58 precise-backports/main TranslationIndex
Hit http://76.73.4.58 precise-backports/multiverse TranslationIndex
Hit http://76.73.4.58 precise-backports/restricted TranslationIndex
Hit http://76.73.4.58 precise-backports/universe TranslationIndex
Hit http://76.73.4.58 precise-security/main Sources
Hit http://76.73.4.58 precise-security/restricted Sources
Hit http://76.73.4.58 precise-security/universe Sources
Hit http://76.73.4.58 precise-security/multiverse Sources
Hit http://download.ebz.epson.net lsb3.2/main Translation-en_GB
Hit http://download.ebz.epson.net lsb3.2/main Translation-en
Hit http://76.73.4.58 precise-security/main i386 Packages
Hit http://76.73.4.58 precise-security/restricted i386 Packages
Hit http://76.73.4.58 precise-security/universe i386 Packages
Hit http://76.73.4.58 precise-security/multiverse i386 Packages
Hit http://76.73.4.58 precise-security/main TranslationIndex
Hit http://76.73.4.58 precise-security/multiverse TranslationIndex
Hit http://76.73.4.58 precise-security/restricted TranslationIndex
Hit http://76.73.4.58 precise-security/universe TranslationIndex
Hit http://76.73.4.58 precise/main Translation-en_GB
Hit http://76.73.4.58 precise/main Translation-en
Err http://download.ebz.epson.net lsb3.2/main i386 Packages
  
Hit http://76.73.4.58 precise/multiverse Translation-en_GB
Hit http://76.73.4.58 precise/multiverse Translation-en
Hit http://76.73.4.58 precise/restricted Translation-en_GB
Hit http://76.73.4.58 precise/restricted Translation-en
Hit http://76.73.4.58 precise/universe Translation-en_GB
Hit http://76.73.4.58 precise/universe Translation-en
Hit http://76.73.4.58 precise-updates/main Translation-en_GB
Hit http://76.73.4.58 precise-updates/main Translation-en
Hit http://76.73.4.58 precise-updates/multiverse Translation-en_GB
Hit http://76.73.4.58 precise-updates/multiverse Translation-en
Err http://download.ebz.epson.net lsb3.2/main i386 Packages
  
Hit http://76.73.4.58 precise-updates/restricted Translation-en_GB
Hit http://76.73.4.58 precise-updates/restricted Translation-en
Hit http://76.73.4.58 precise-updates/universe Translation-en_GB
Hit http://76.73.4.58 precise-updates/universe Translation-en
Hit http://76.73.4.58 precise-backports/main Translation-en
Hit http://76.73.4.58 precise-backports/multiverse Translation-en
Hit http://download.ebz.epson.net lsb3.2/main i386 Packages
Hit http://76.73.4.58 precise-backports/restricted Translation-en
Hit http://76.73.4.58 precise-backports/universe Translation-en
Hit http://76.73.4.58 precise-security/main Translation-en
Hit http://76.73.4.58 precise-security/multiverse Translation-en
Hit http://76.73.4.58 precise-security/restricted Translation-en
Hit http://76.73.4.58 precise-security/universe Translation-en
Fetched 261 B in 2s (92 B/s)
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: GPG error: http://download.ebz.epson.net lsb3.2 Release: The following signatures were invalid: BADSIG E5E86C008AA65D56 Seiko Epson Corporation (Epson Inkjet Printer Driver) <epson-linux-inkjet@avasys.jp>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
scott@scott-desktop:~$ sudo apt-key finger
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
      Key fingerprint = 6302 39CC 130E 1A7F D81A  27B1 4097 6EAF 437D 05B5
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
      Key fingerprint = C598 6B4F 1257 FFA8 6632  CBA7 4618 1433 FBB7 5451
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   4096R/C0B21F32 2012-05-11
      Key fingerprint = 790B C727 7767 219C 42C8  6F93 3B4F E6AC C0B2 1F32
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
      Key fingerprint = 8439 38DF 228D 22F7 B374  2BC0 D94A A3F0 EFE2 1092
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

pub   1024R/F9CB8DB0 2009-01-20
      Key fingerprint = 883E 8688 3975 76B6 C509  DF49 5A9A 06AE F9CB 8DB0
uid                  Launchpad PPA for Ubuntu Wine Team

/etc/apt/trusted.gpg.d//jockey-drivers.gpg
------------------------------------------
pub   1024D/8AA65D56 2009-12-17
      Key fingerprint = E522 0FB7 014D 0FBD A50D  FC2B E5E8 6C00 8AA6 5D56
uid                  Seiko Epson Corporation (Epson Inkjet Printer Driver) <epson-linux-inkjet@avasys.jp>
sub   2048g/92A2C210 2009-12-17

scott@scott-desktop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.CIEY64tz4M --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d//jockey-drivers.gpg --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: public key "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
scott@scott-desktop:~$ sudo apt-key finger
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
      Key fingerprint = 6302 39CC 130E 1A7F D81A  27B1 4097 6EAF 437D 05B5
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
      Key fingerprint = C598 6B4F 1257 FFA8 6632  CBA7 4618 1433 FBB7 5451
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   4096R/C0B21F32 2012-05-11
      Key fingerprint = 790B C727 7767 219C 42C8  6F93 3B4F E6AC C0B2 1F32
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
      Key fingerprint = 8439 38DF 228D 22F7 B374  2BC0 D94A A3F0 EFE2 1092
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

pub   1024R/F9CB8DB0 2009-01-20
      Key fingerprint = 883E 8688 3975 76B6 C509  DF49 5A9A 06AE F9CB 8DB0
uid                  Launchpad PPA for Ubuntu Wine Team

pub   1024D/3E5C1192 2010-09-20
      Key fingerprint = C474 15DF F48C 0964 5B78  6094 1612 6D3A 3E5C 1192
uid                  Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

/etc/apt/trusted.gpg.d//jockey-drivers.gpg
------------------------------------------
pub   1024D/8AA65D56 2009-12-17
      Key fingerprint = E522 0FB7 014D 0FBD A50D  FC2B E5E8 6C00 8AA6 5D56
uid                  Seiko Epson Corporation (Epson Inkjet Printer Driver) <epson-linux-inkjet@avasys.jp>
sub   2048g/92A2C210 2009-12-17

scott@scott-desktop:~$ sudo apt-get update
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Err http://extras.ubuntu.com precise Release                                   
  
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://76.73.4.58 precise Release.gpg                                      
Hit http://76.73.4.58 precise-updates Release.gpg                              
Hit http://76.73.4.58 precise-backports Release.gpg                  
Hit http://76.73.4.58 precise-security Release.gpg                   
Hit http://76.73.4.58 precise Release                                
Hit http://76.73.4.58 precise-updates Release  
Hit http://76.73.4.58 precise-backports Release
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en             
Get:2 http://download.ebz.epson.net lsb3.2 Release.gpg [189 B]
Hit http://76.73.4.58 precise-security Release            
Hit http://76.73.4.58 precise/main Sources      
Hit http://76.73.4.58 precise/restricted Sources
Hit http://76.73.4.58 precise/universe Sources 
Hit http://76.73.4.58 precise/multiverse Sources
Hit http://76.73.4.58 precise/main i386 Packages
Hit http://76.73.4.58 precise/restricted i386 Packages
Hit http://download.ebz.epson.net lsb3.2 Release
Ign http://download.ebz.epson.net lsb3.2 Release
Hit http://76.73.4.58 precise/universe i386 Packages
Hit http://76.73.4.58 precise/multiverse i386 Packages
Hit http://76.73.4.58 precise/main TranslationIndex
Hit http://76.73.4.58 precise/multiverse TranslationIndex
Hit http://76.73.4.58 precise/restricted TranslationIndex
Hit http://76.73.4.58 precise/universe TranslationIndex
Hit http://76.73.4.58 precise-updates/main Sources
Hit http://76.73.4.58 precise-updates/restricted Sources
Hit http://76.73.4.58 precise-updates/universe Sources
Hit http://76.73.4.58 precise-updates/multiverse Sources
Ign http://download.ebz.epson.net lsb3.2/main i386 Packages/DiffIndex
Hit http://76.73.4.58 precise-updates/main i386 Packages
Hit http://76.73.4.58 precise-updates/restricted i386 Packages
Hit http://76.73.4.58 precise-updates/universe i386 Packages
Hit http://76.73.4.58 precise-updates/multiverse i386 Packages
Hit http://76.73.4.58 precise-updates/main TranslationIndex
Hit http://76.73.4.58 precise-updates/multiverse TranslationIndex
Hit http://76.73.4.58 precise-updates/restricted TranslationIndex
Hit http://76.73.4.58 precise-updates/universe TranslationIndex
Hit http://76.73.4.58 precise-backports/main Sources
Hit http://76.73.4.58 precise-backports/restricted Sources
Ign http://download.ebz.epson.net lsb3.2/main TranslationIndex
Hit http://76.73.4.58 precise-backports/universe Sources
Hit http://76.73.4.58 precise-backports/multiverse Sources
Hit http://76.73.4.58 precise-backports/main i386 Packages
Hit http://76.73.4.58 precise-backports/restricted i386 Packages
Hit http://76.73.4.58 precise-backports/universe i386 Packages
Hit http://76.73.4.58 precise-backports/multiverse i386 Packages
Hit http://76.73.4.58 precise-backports/main TranslationIndex
Hit http://76.73.4.58 precise-backports/multiverse TranslationIndex
Hit http://76.73.4.58 precise-backports/restricted TranslationIndex
Hit http://76.73.4.58 precise-backports/universe TranslationIndex
Hit http://76.73.4.58 precise-security/main Sources
Hit http://76.73.4.58 precise-security/restricted Sources
Hit http://76.73.4.58 precise-security/universe Sources
Hit http://76.73.4.58 precise-security/multiverse Sources
Hit http://download.ebz.epson.net lsb3.2/main Translation-en_GB
Hit http://download.ebz.epson.net lsb3.2/main Translation-en
Hit http://76.73.4.58 precise-security/main i386 Packages
Hit http://76.73.4.58 precise-security/restricted i386 Packages
Hit http://76.73.4.58 precise-security/universe i386 Packages
Hit http://76.73.4.58 precise-security/multiverse i386 Packages
Hit http://76.73.4.58 precise-security/main TranslationIndex
Hit http://76.73.4.58 precise-security/multiverse TranslationIndex
Hit http://76.73.4.58 precise-security/restricted TranslationIndex
Hit http://76.73.4.58 precise-security/universe TranslationIndex
Hit http://76.73.4.58 precise/main Translation-en_GB
Hit http://76.73.4.58 precise/main Translation-en
Err http://download.ebz.epson.net lsb3.2/main i386 Packages
  
Hit http://76.73.4.58 precise/multiverse Translation-en_GB
Hit http://76.73.4.58 precise/multiverse Translation-en
Hit http://76.73.4.58 precise/restricted Translation-en_GB
Hit http://76.73.4.58 precise/restricted Translation-en
Hit http://76.73.4.58 precise/universe Translation-en_GB
Hit http://76.73.4.58 precise/universe Translation-en
Hit http://76.73.4.58 precise-updates/main Translation-en_GB
Hit http://76.73.4.58 precise-updates/main Translation-en
Hit http://76.73.4.58 precise-updates/multiverse Translation-en_GB
Hit http://76.73.4.58 precise-updates/multiverse Translation-en
Err http://download.ebz.epson.net lsb3.2/main i386 Packages
  
Hit http://76.73.4.58 precise-updates/restricted Translation-en_GB
Hit http://76.73.4.58 precise-updates/restricted Translation-en
Hit http://76.73.4.58 precise-updates/universe Translation-en_GB
Hit http://76.73.4.58 precise-updates/universe Translation-en
Hit http://76.73.4.58 precise-backports/main Translation-en
Hit http://76.73.4.58 precise-backports/multiverse Translation-en
Hit http://76.73.4.58 precise-backports/restricted Translation-en
Hit http://76.73.4.58 precise-backports/universe Translation-en
Hit http://76.73.4.58 precise-security/main Translation-en
Hit http://76.73.4.58 precise-security/multiverse Translation-en
Hit http://download.ebz.epson.net lsb3.2/main i386 Packages
Hit http://76.73.4.58 precise-security/restricted Translation-en
Hit http://76.73.4.58 precise-security/universe Translation-en
Fetched 261 B in 2s (93 B/s)
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://download.ebz.epson.net lsb3.2 Release: The following signatures were invalid: BADSIG E5E86C008AA65D56 Seiko Epson Corporation (Epson Inkjet Printer Driver) <epson-linux-inkjet@avasys.jp>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
scott@scott-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-lts-raring
  linux-headers-generic-lts-trusty linux-headers-generic-pae
  linux-image-generic-lts-raring linux-image-generic-lts-trusty
  linux-image-generic-pae
0 to upgrade, 0 to newly install, 0 to remove and 7 not to upgrade.
scott@scott-desktop:~$ 


```

---

### Post by Bashing-om on 2014-07-17
dimmaz88; Shucks,

Had it working for ubuntu extras, then lost it again .. humm .. 

Let's try this:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```
Those control files will be re-built in the update process.

See what results, and then do our homework, and try and find out the why and whereof !

[INDENT][INDENT]no quit in our nature
[/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-17
We shall not be beaten!

that first command didn't seem to do anything??

```
scott@scott-desktop:~$ sudo rm -fr /var/lib/apt/lists
[sudo] password for scott: 
scott@scott-desktop:~$ sudo mkdir -pv /var/lib/apt/lists/partial
mkdir: created directory `/var/lib/apt/lists'
mkdir: created directory `/var/lib/apt/lists/partial'
scott@scott-desktop:~$ sudo apt-get update
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]
Get:2 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Get:3 http://extras.ubuntu.com precise Release [11.9 kB]                       
Get:4 http://ppa.launchpad.net precise Release [11.9 kB]                       
Get:5 http://extras.ubuntu.com precise/main Sources [8,130 B]                  
Get:6 http://ppa.launchpad.net precise/main Sources [6,637 B]                  
Get:7 http://extras.ubuntu.com precise/main i386 Packages [10.8 kB]            
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:8 http://ppa.launchpad.net precise/main i386 Packages [7,518 B]            
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:9 http://76.73.4.58 precise Release.gpg [198 B]                            
Get:10 http://76.73.4.58 precise-updates Release.gpg [198 B]                   
Get:11 http://76.73.4.58 precise-backports Release.gpg [198 B]                 
Get:12 http://76.73.4.58 precise-security Release.gpg [198 B]                  
Get:13 http://76.73.4.58 precise Release [49.6 kB]                             
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:14 http://download.ebz.epson.net lsb3.2 Release.gpg [189 B]                
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:15 http://76.73.4.58 precise-updates Release [49.6 kB]
Get:16 http://download.ebz.epson.net lsb3.2 Release [131 kB]                   
Get:17 http://76.73.4.58 precise-backports Release [49.6 kB]   
Get:18 http://76.73.4.58 precise-security Release [49.6 kB]                    
Get:19 http://76.73.4.58 precise/main Sources [934 kB]                         
Get:20 http://76.73.4.58 precise/restricted Sources [5,470 B]                  
Get:21 http://76.73.4.58 precise/universe Sources [5,019 kB]                   
Get:22 http://download.ebz.epson.net lsb3.2/main i386 Packages [13.5 kB]       
Ign http://download.ebz.epson.net lsb3.2/main TranslationIndex                 
Get:23 http://76.73.4.58 precise/multiverse Sources [155 kB]                   
Get:24 http://download.ebz.epson.net lsb3.2/main Translation-en_GB             
Get:25 http://76.73.4.58 precise/main i386 Packages [1,274 kB]                 
Get:26 http://download.ebz.epson.net lsb3.2/main Translation-en                
Get:27 http://76.73.4.58 precise/restricted i386 Packages [8,431 B]            
Get:28 http://76.73.4.58 precise/universe i386 Packages [4,796 kB]             
Get:29 http://76.73.4.58 precise/multiverse i386 Packages [121 kB]             
Get:30 http://76.73.4.58 precise/main TranslationIndex [3,706 B]               
Get:31 http://76.73.4.58 precise/multiverse TranslationIndex [2,676 B]         
Get:32 http://76.73.4.58 precise/restricted TranslationIndex [2,596 B]         
Get:33 http://76.73.4.58 precise/universe TranslationIndex [2,922 B]           
Get:34 http://76.73.4.58 precise-updates/main Sources [475 kB]                 
Get:35 http://76.73.4.58 precise-updates/restricted Sources [8,056 B]          
Get:36 http://76.73.4.58 precise-updates/universe Sources [108 kB]             
Get:37 http://76.73.4.58 precise-updates/multiverse Sources [8,905 B]          
Get:38 http://76.73.4.58 precise-updates/main i386 Packages [853 kB]           
Get:39 http://76.73.4.58 precise-updates/restricted i386 Packages [13.7 kB]    
Get:40 http://76.73.4.58 precise-updates/universe i386 Packages [251 kB]       
Get:41 http://76.73.4.58 precise-updates/multiverse i386 Packages [15.5 kB]    
Get:42 http://76.73.4.58 precise-updates/main TranslationIndex [3,564 B]       
Get:43 http://76.73.4.58 precise-updates/multiverse TranslationIndex [2,605 B] 
Get:44 http://76.73.4.58 precise-updates/restricted TranslationIndex [2,461 B] 
Get:45 http://76.73.4.58 precise-updates/universe TranslationIndex [2,850 B]   
Get:46 http://76.73.4.58 precise-backports/main Sources [5,145 B]              
Get:47 http://76.73.4.58 precise-backports/restricted Sources [14 B]           
Get:48 http://76.73.4.58 precise-backports/universe Sources [38.4 kB]          
Get:49 http://76.73.4.58 precise-backports/multiverse Sources [5,311 B]        
Get:50 http://76.73.4.58 precise-backports/main i386 Packages [6,420 B]        
Get:51 http://76.73.4.58 precise-backports/restricted i386 Packages [14 B]     
Get:52 http://76.73.4.58 precise-backports/universe i386 Packages [41.2 kB]    
Get:53 http://76.73.4.58 precise-backports/multiverse i386 Packages [5,178 B]  
Get:54 http://76.73.4.58 precise-backports/main TranslationIndex [72 B]        
Get:55 http://76.73.4.58 precise-backports/multiverse TranslationIndex [72 B]  
Get:56 http://76.73.4.58 precise-backports/restricted TranslationIndex [70 B]  
Get:57 http://76.73.4.58 precise-backports/universe TranslationIndex [73 B]    
Get:58 http://76.73.4.58 precise-security/main Sources [106 kB]                
Get:59 http://76.73.4.58 precise-security/restricted Sources [2,494 B]         
Get:60 http://76.73.4.58 precise-security/universe Sources [30.7 kB]           
Get:61 http://76.73.4.58 precise-security/multiverse Sources [1,795 B]         
Get:62 http://76.73.4.58 precise-security/main i386 Packages [440 kB]          
Get:63 http://76.73.4.58 precise-security/restricted i386 Packages [4,620 B]   
Get:64 http://76.73.4.58 precise-security/universe i386 Packages [99.7 kB]     
Get:65 http://76.73.4.58 precise-security/multiverse i386 Packages [2,650 B]   
Get:66 http://76.73.4.58 precise-security/main TranslationIndex [74 B]         
Get:67 http://76.73.4.58 precise-security/multiverse TranslationIndex [72 B]   
Get:68 http://76.73.4.58 precise-security/restricted TranslationIndex [72 B]   
Get:69 http://76.73.4.58 precise-security/universe TranslationIndex [73 B]     
Get:70 http://76.73.4.58 precise/main Translation-en_GB [96.4 kB]              
Get:71 http://76.73.4.58 precise/main Translation-en [726 kB]                  
Get:72 http://76.73.4.58 precise/multiverse Translation-en_GB [79.8 kB]        
Get:73 http://76.73.4.58 precise/multiverse Translation-en [93.4 kB]           
Get:74 http://76.73.4.58 precise/restricted Translation-en_GB [2,406 B]        
Get:75 http://76.73.4.58 precise/restricted Translation-en [2,395 B]           
Get:76 http://76.73.4.58 precise/universe Translation-en_GB [5,492 B]          
Get:77 http://76.73.4.58 precise/universe Translation-en [3,341 kB]            
Get:78 http://76.73.4.58 precise-updates/main Translation-en_GB [96.4 kB]      
Get:79 http://76.73.4.58 precise-updates/main Translation-en [360 kB]          
Get:80 http://76.73.4.58 precise-updates/multiverse Translation-en_GB [79.8 kB]
Get:81 http://76.73.4.58 precise-updates/multiverse Translation-en [9,010 B]   
Get:82 http://76.73.4.58 precise-updates/restricted Translation-en_GB [2,406 B]
Get:83 http://76.73.4.58 precise-updates/restricted Translation-en [3,027 B]   
Get:84 http://76.73.4.58 precise-updates/universe Translation-en_GB [5,492 B]  
Get:85 http://76.73.4.58 precise-updates/universe Translation-en [142 kB]      
Get:86 http://76.73.4.58 precise-backports/main Translation-en [5,882 B]       
Get:87 http://76.73.4.58 precise-backports/multiverse Translation-en [4,610 B] 
Get:88 http://76.73.4.58 precise-backports/restricted Translation-en [14 B]    
Get:89 http://76.73.4.58 precise-backports/universe Translation-en [32.9 kB]   
Get:90 http://76.73.4.58 precise-security/main Translation-en [188 kB]         
Get:91 http://76.73.4.58 precise-security/multiverse Translation-en [1,299 B]  
Get:92 http://76.73.4.58 precise-security/restricted Translation-en [1,253 B]  
Get:93 http://76.73.4.58 precise-security/universe Translation-en [57.8 kB]    
Fetched 20.6 MB in 27s (747 kB/s)                                              
Reading package lists... Done
scott@scott-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-lts-raring
  linux-headers-generic-lts-trusty linux-headers-generic-pae
  linux-image-generic-lts-raring linux-image-generic-lts-trusty
  linux-image-generic-pae
0 to upgrade, 0 to newly install, 0 to remove and 7 not to upgrade.
```

---

### Post by Bashing-om on 2014-07-17
dimmaz88; Whadya know !

Hey:
> 
that first command didn't seem to do anything??
 It Did It Did !
The system just doing as it is told with no sas or back talk when there is no response to a command. 

That went well.

For a finish up to install those held packages:
```

sudo apt-get dist-upgrade

```

Let's see that run clean.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-18
This is the output.
```
scott@scott-desktop:~$ sudo apt-get dist-upgrade
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-headers-3.2.0-67 linux-headers-3.2.0-67-generic-pae
  linux-headers-3.8.0-44 linux-headers-3.8.0-44-generic
  linux-image-3.13.0-32-generic linux-image-3.2.0-67-generic-pae
  linux-image-3.8.0-44-generic
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic-lts-raring
  linux-headers-generic-lts-trusty linux-headers-generic-pae
  linux-image-generic-lts-raring linux-image-generic-lts-trusty
  linux-image-generic-pae
7 to upgrade, 9 to newly install, 0 to remove and 0 not to upgrade.
Need to get 181 MB of archives.
After this operation, 615 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  linux-image-3.13.0-32-generic linux-image-3.2.0-67-generic-pae
  linux-image-3.8.0-44-generic linux-generic-pae linux-image-generic-pae
  linux-headers-3.2.0-67 linux-headers-3.2.0-67-generic-pae
  linux-headers-generic-pae linux-headers-3.13.0-32
  linux-headers-3.13.0-32-generic linux-headers-3.8.0-44
  linux-headers-3.8.0-44-generic linux-headers-generic-lts-raring
  linux-headers-generic-lts-trusty linux-image-generic-lts-raring
  linux-image-generic-lts-trusty
Install these packages without verification [y/N]? y
Get:1 http://76.73.4.58/ubuntu/ precise-updates/main linux-image-3.13.0-32-generic i386 3.13.0-32.57~precise1 [52.4 MB]
Get:2 http://76.73.4.58/ubuntu/ precise-updates/main linux-image-3.2.0-67-generic-pae i386 3.2.0-67.101 [38.4 MB]
Get:3 http://76.73.4.58/ubuntu/ precise-updates/main linux-image-3.8.0-44-generic i386 3.8.0-44.66~precise1 [50.5 MB]
Get:4 http://76.73.4.58/ubuntu/ precise-updates/main linux-generic-pae i386 3.2.0.67.79 [1,730 B]
Get:5 http://76.73.4.58/ubuntu/ precise-updates/main linux-image-generic-pae i386 3.2.0.67.79 [2,438 B]
Get:6 http://76.73.4.58/ubuntu/ precise-updates/main linux-headers-3.2.0-67 all 3.2.0-67.101 [11.7 MB]
Get:7 http://76.73.4.58/ubuntu/ precise-updates/main linux-headers-3.2.0-67-generic-pae i386 3.2.0-67.101 [967 kB]
Get:8 http://76.73.4.58/ubuntu/ precise-updates/main linux-headers-generic-pae i386 3.2.0.67.79 [2,422 B]
Get:9 http://76.73.4.58/ubuntu/ precise-updates/main linux-headers-3.13.0-32 all 3.13.0-32.57~precise1 [12.8 MB]
Get:10 http://76.73.4.58/ubuntu/ precise-updates/main linux-headers-3.13.0-32-generic i386 3.13.0-32.57~precise1 [1,102 kB]
Get:11 http://76.73.4.58/ubuntu/ precise-updates/main linux-headers-3.8.0-44 all 3.8.0-44.66~precise1 [12.2 MB]
Get:12 http://76.73.4.58/ubuntu/ precise-updates/main linux-headers-3.8.0-44-generic i386 3.8.0-44.66~precise1 [990 kB]
Get:13 http://76.73.4.58/ubuntu/ precise-updates/main linux-headers-generic-lts-raring i386 3.8.0.44.44 [2,376 B]
Get:14 http://76.73.4.58/ubuntu/ precise-updates/main linux-headers-generic-lts-trusty i386 3.13.0.32.28 [2,488 B]
Get:15 http://76.73.4.58/ubuntu/ precise-updates/main linux-image-generic-lts-raring i386 3.8.0.44.44 [2,382 B]
Get:16 http://76.73.4.58/ubuntu/ precise-updates/main linux-image-generic-lts-trusty i386 3.13.0.32.28 [2,492 B]
Fetched 181 MB in 4min 17s (704 kB/s)                                          
Selecting previously unselected package linux-image-3.13.0-32-generic.
(Reading database ... 411638 files and directories currently installed.)
Unpacking linux-image-3.13.0-32-generic (from .../linux-image-3.13.0-32-generic_3.13.0-32.57~precise1_i386.deb) ...
Done.
Selecting previously unselected package linux-image-3.2.0-67-generic-pae.
Unpacking linux-image-3.2.0-67-generic-pae (from .../linux-image-3.2.0-67-generic-pae_3.2.0-67.101_i386.deb) ...
Done.
Selecting previously unselected package linux-image-3.8.0-44-generic.
Unpacking linux-image-3.8.0-44-generic (from .../linux-image-3.8.0-44-generic_3.8.0-44.66~precise1_i386.deb) ...
Done.
Preparing to replace linux-generic-pae 3.2.0.65.77 (using .../linux-generic-pae_3.2.0.67.79_i386.deb) ...
Unpacking replacement linux-generic-pae ...
Preparing to replace linux-image-generic-pae 3.2.0.65.77 (using .../linux-image-generic-pae_3.2.0.67.79_i386.deb) ...
Unpacking replacement linux-image-generic-pae ...
Selecting previously unselected package linux-headers-3.2.0-67.
Unpacking linux-headers-3.2.0-67 (from .../linux-headers-3.2.0-67_3.2.0-67.101_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-67-generic-pae.
Unpacking linux-headers-3.2.0-67-generic-pae (from .../linux-headers-3.2.0-67-generic-pae_3.2.0-67.101_i386.deb) ...
Preparing to replace linux-headers-generic-pae 3.2.0.65.77 (using .../linux-headers-generic-pae_3.2.0.67.79_i386.deb) ...
Unpacking replacement linux-headers-generic-pae ...
Selecting previously unselected package linux-headers-3.13.0-32.
Unpacking linux-headers-3.13.0-32 (from .../linux-headers-3.13.0-32_3.13.0-32.57~precise1_all.deb) ...
Selecting previously unselected package linux-headers-3.13.0-32-generic.
Unpacking linux-headers-3.13.0-32-generic (from .../linux-headers-3.13.0-32-generic_3.13.0-32.57~precise1_i386.deb) ...
Selecting previously unselected package linux-headers-3.8.0-44.
Unpacking linux-headers-3.8.0-44 (from .../linux-headers-3.8.0-44_3.8.0-44.66~precise1_all.deb) ...
Selecting previously unselected package linux-headers-3.8.0-44-generic.
Unpacking linux-headers-3.8.0-44-generic (from .../linux-headers-3.8.0-44-generic_3.8.0-44.66~precise1_i386.deb) ...
Preparing to replace linux-headers-generic-lts-raring 3.8.0.42.42 (using .../linux-headers-generic-lts-raring_3.8.0.44.44_i386.deb) ...
Unpacking replacement linux-headers-generic-lts-raring ...
Preparing to replace linux-headers-generic-lts-trusty 3.13.0.30.26 (using .../linux-headers-generic-lts-trusty_3.13.0.32.28_i386.deb) ...
Unpacking replacement linux-headers-generic-lts-trusty ...
Preparing to replace linux-image-generic-lts-raring 3.8.0.42.42 (using .../linux-image-generic-lts-raring_3.8.0.44.44_i386.deb) ...
Unpacking replacement linux-image-generic-lts-raring ...
Preparing to replace linux-image-generic-lts-trusty 3.13.0.30.26 (using .../linux-image-generic-lts-trusty_3.13.0.32.28_i386.deb) ...
Unpacking replacement linux-image-generic-lts-trusty ...
Setting up linux-image-3.13.0-32-generic (3.13.0-32.57~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-3.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-1.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8411-2.fw for module r8169
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found initrd image: /boot/initrd.img-3.13.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-44-generic
Found linux image: /boot/vmlinuz-3.8.0-42-generic
Found initrd image: /boot/initrd.img-3.8.0-42-generic
Found linux image: /boot/vmlinuz-3.8.0-41-generic
Found initrd image: /boot/initrd.img-3.8.0-41-generic
Found linux image: /boot/vmlinuz-3.8.0-39-generic
Found initrd image: /boot/initrd.img-3.8.0-39-generic
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-65-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-65-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-64-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-64-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-63-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-63-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-61-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-61-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-60-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-60-generic-pae
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Setting up linux-image-3.2.0-67-generic-pae (3.2.0-67.101) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-67-generic-pae /boot/vmlinuz-3.2.0-67-generic-pae
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-67-generic-pae /boot/vmlinuz-3.2.0-67-generic-pae
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-67-generic-pae /boot/vmlinuz-3.2.0-67-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-67-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-67-generic-pae /boot/vmlinuz-3.2.0-67-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-67-generic-pae /boot/vmlinuz-3.2.0-67-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-67-generic-pae /boot/vmlinuz-3.2.0-67-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found initrd image: /boot/initrd.img-3.13.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-44-generic
Found linux image: /boot/vmlinuz-3.8.0-42-generic
Found initrd image: /boot/initrd.img-3.8.0-42-generic
Found linux image: /boot/vmlinuz-3.8.0-41-generic
Found initrd image: /boot/initrd.img-3.8.0-41-generic
Found linux image: /boot/vmlinuz-3.8.0-39-generic
Found initrd image: /boot/initrd.img-3.8.0-39-generic
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-65-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-65-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-64-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-64-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-63-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-63-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-61-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-61-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-60-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-60-generic-pae
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Setting up linux-image-3.8.0-44-generic (3.8.0-44.66~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-44-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found initrd image: /boot/initrd.img-3.13.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-44-generic
Found initrd image: /boot/initrd.img-3.8.0-44-generic
Found linux image: /boot/vmlinuz-3.8.0-42-generic
Found initrd image: /boot/initrd.img-3.8.0-42-generic
Found linux image: /boot/vmlinuz-3.8.0-41-generic
Found initrd image: /boot/initrd.img-3.8.0-41-generic
Found linux image: /boot/vmlinuz-3.8.0-39-generic
Found initrd image: /boot/initrd.img-3.8.0-39-generic
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-65-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-65-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-64-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-64-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-63-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-63-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-61-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-61-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-60-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-60-generic-pae
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Setting up linux-image-generic-pae (3.2.0.67.79) ...
Setting up linux-headers-3.2.0-67 (3.2.0-67.101) ...
Setting up linux-headers-3.2.0-67-generic-pae (3.2.0-67.101) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-67-generic-pae /boot/vmlinuz-3.2.0-67-generic-pae
Setting up linux-headers-generic-pae (3.2.0.67.79) ...
Setting up linux-generic-pae (3.2.0.67.79) ...
Setting up linux-headers-3.13.0-32 (3.13.0-32.57~precise1) ...
Setting up linux-headers-3.13.0-32-generic (3.13.0-32.57~precise1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Setting up linux-headers-3.8.0-44 (3.8.0-44.66~precise1) ...
Setting up linux-headers-3.8.0-44-generic (3.8.0-44.66~precise1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.8.0-44-generic /boot/vmlinuz-3.8.0-44-generic
Setting up linux-headers-generic-lts-raring (3.8.0.44.44) ...
Setting up linux-headers-generic-lts-trusty (3.13.0.32.28) ...
Setting up linux-image-generic-lts-raring (3.8.0.44.44) ...
Setting up linux-image-generic-lts-trusty (3.13.0.32.28) ...


```

---

### Post by dimmaz88 on 2014-07-18
I assume that last command you posted does the same as update/upgrade. I thought I'd run it also.
```
scott@scott-desktop:~$ sudo apt-get update
[sudo] password for scott: 
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:1 http://76.73.4.58 precise Release.gpg [198 B]                            
Get:2 http://76.73.4.58 precise-updates Release.gpg [198 B]                    
Get:3 http://76.73.4.58 precise-backports Release.gpg [198 B]                  
Get:4 http://76.73.4.58 precise-security Release.gpg [198 B]                   
Hit http://76.73.4.58 precise Release                                          
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en             
Ign http://extras.ubuntu.com precise/main Translation-en             
Hit http://download.ebz.epson.net lsb3.2 Release.gpg                 
Get:5 http://76.73.4.58 precise-updates Release [49.6 kB]
Hit http://download.ebz.epson.net lsb3.2 Release       
Hit http://76.73.4.58 precise-backports Release          
Get:6 http://76.73.4.58 precise-security Release [49.6 kB]
Hit http://76.73.4.58 precise/main Sources                                     
Hit http://76.73.4.58 precise/restricted Sources
Hit http://76.73.4.58 precise/universe Sources
Hit http://76.73.4.58 precise/multiverse Sources
Hit http://76.73.4.58 precise/main i386 Packages
Hit http://76.73.4.58 precise/restricted i386 Packages
Hit http://76.73.4.58 precise/universe i386 Packages
Hit http://76.73.4.58 precise/multiverse i386 Packages
Hit http://76.73.4.58 precise/main TranslationIndex
Hit http://download.ebz.epson.net lsb3.2/main i386 Packages
Hit http://76.73.4.58 precise/multiverse TranslationIndex
Hit http://76.73.4.58 precise/restricted TranslationIndex
Hit http://76.73.4.58 precise/universe TranslationIndex
Get:7 http://76.73.4.58 precise-updates/main Sources [475 kB]
Ign http://download.ebz.epson.net lsb3.2/main TranslationIndex
Get:8 http://download.ebz.epson.net lsb3.2/main Translation-en_GB
Get:9 http://download.ebz.epson.net lsb3.2/main Translation-en                 
Get:10 http://76.73.4.58 precise-updates/restricted Sources [8,056 B]          
Get:11 http://76.73.4.58 precise-updates/universe Sources [108 kB]           
Get:12 http://76.73.4.58 precise-updates/multiverse Sources [8,905 B]          
Get:13 http://76.73.4.58 precise-updates/main i386 Packages [853 kB]         
Get:14 http://76.73.4.58 precise-updates/restricted i386 Packages [13.7 kB]    
Get:15 http://76.73.4.58 precise-updates/universe i386 Packages [251 kB]
Get:16 http://76.73.4.58 precise-updates/multiverse i386 Packages [15.5 kB]
Hit http://76.73.4.58 precise-updates/main TranslationIndex
Hit http://76.73.4.58 precise-updates/multiverse TranslationIndex
Hit http://76.73.4.58 precise-updates/restricted TranslationIndex
Hit http://76.73.4.58 precise-updates/universe TranslationIndex
Hit http://76.73.4.58 precise-backports/main Sources
Hit http://76.73.4.58 precise-backports/restricted Sources
Hit http://76.73.4.58 precise-backports/universe Sources
Hit http://76.73.4.58 precise-backports/multiverse Sources
Hit http://76.73.4.58 precise-backports/main i386 Packages
Hit http://76.73.4.58 precise-backports/restricted i386 Packages
Hit http://76.73.4.58 precise-backports/universe i386 Packages
Hit http://76.73.4.58 precise-backports/multiverse i386 Packages
Hit http://76.73.4.58 precise-backports/main TranslationIndex
Hit http://76.73.4.58 precise-backports/multiverse TranslationIndex
Hit http://76.73.4.58 precise-backports/restricted TranslationIndex
Hit http://76.73.4.58 precise-backports/universe TranslationIndex
Get:17 http://76.73.4.58 precise-security/main Sources [106 kB]
Get:18 http://76.73.4.58 precise-security/restricted Sources [2,494 B]
Get:19 http://76.73.4.58 precise-security/universe Sources [30.7 kB]
Get:20 http://76.73.4.58 precise-security/multiverse Sources [1,795 B]
Get:21 http://76.73.4.58 precise-security/main i386 Packages [440 kB]
Get:22 http://76.73.4.58 precise-security/restricted i386 Packages [4,620 B]   
Get:23 http://76.73.4.58 precise-security/universe i386 Packages [99.7 kB]     
Get:24 http://76.73.4.58 precise-security/multiverse i386 Packages [2,650 B]   
Hit http://76.73.4.58 precise-security/main TranslationIndex                   
Hit http://76.73.4.58 precise-security/multiverse TranslationIndex             
Hit http://76.73.4.58 precise-security/restricted TranslationIndex             
Hit http://76.73.4.58 precise-security/universe TranslationIndex               
Hit http://76.73.4.58 precise/main Translation-en_GB                           
Hit http://76.73.4.58 precise/main Translation-en                              
Hit http://76.73.4.58 precise/multiverse Translation-en_GB                     
Hit http://76.73.4.58 precise/multiverse Translation-en                        
Hit http://76.73.4.58 precise/restricted Translation-en_GB                     
Hit http://76.73.4.58 precise/restricted Translation-en                        
Hit http://76.73.4.58 precise/universe Translation-en_GB                       
Hit http://76.73.4.58 precise/universe Translation-en                          
Hit http://76.73.4.58 precise-updates/main Translation-en_GB                   
Hit http://76.73.4.58 precise-updates/main Translation-en                      
Hit http://76.73.4.58 precise-updates/multiverse Translation-en_GB             
Hit http://76.73.4.58 precise-updates/multiverse Translation-en                
Hit http://76.73.4.58 precise-updates/restricted Translation-en_GB             
Hit http://76.73.4.58 precise-updates/restricted Translation-en                
Hit http://76.73.4.58 precise-updates/universe Translation-en_GB               
Hit http://76.73.4.58 precise-updates/universe Translation-en                  
Hit http://76.73.4.58 precise-backports/main Translation-en                    
Hit http://76.73.4.58 precise-backports/multiverse Translation-en              
Hit http://76.73.4.58 precise-backports/restricted Translation-en              
Hit http://76.73.4.58 precise-backports/universe Translation-en                
Hit http://76.73.4.58 precise-security/main Translation-en                     
Hit http://76.73.4.58 precise-security/multiverse Translation-en               
Hit http://76.73.4.58 precise-security/restricted Translation-en               
Hit http://76.73.4.58 precise-security/universe Translation-en                 
Fetched 2,520 kB in 7s (335 kB/s)                                              
Reading package lists... Done
scott@scott-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
scott@scott-desktop:~$ 


```

I still can't boot up properly :(

---

### Post by Bashing-om on 2014-07-18
dimmaz88; Humm, 

Still with quite a bit of clean up to do:

> 
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-3.fw for module r8169

I expect is the wireless module, Do not really know how to handle this one, but -> try :
```

sudo apt-get install --reinstall linux-firmware-nonfree

```

Nor do I comprehend the why of now having authentication errors with :
> 
WARNING: The following packages cannot be authenticated!
  linux-image-3.13.0-32-generic linux-image-3.2.0-67-generic-pae
<snip>

What now results from:
```

sudo apt-key update

```
------------------

You have a number of old kernels installed, I want to know how much overhead remains for us to work with. So, Also post back the results of terminal commands:
```

df -h
df -i

```
and last but not least:
> 
I still can't boot up properly
 does little to point us in a direction to find the cause. Like amplifying info such as what you did at what point in the boot process, what did you expect to happen and what actually did happen and what errors did you see on-screen ???
---------------

Getting there, system is updated and stable, cleaned up and now to a limited degree booting. Hopefully all that is left is small details.

[INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-18
When I boot up it still says 'broken pipe', just as before really. So like you say, no change there.

This is the output from the latest commands;
```
scott@scott-desktop:~$ sudo apt-get install --reinstall linux-firmware-nonfree
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-kde-en language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  linux-firmware-nonfree
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 3,952 kB of archives.
After this operation, 8,980 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  linux-firmware-nonfree
Install these packages without verification [y/N]? y
Get:1 http://76.73.4.58/ubuntu/ precise-updates/multiverse linux-firmware-nonfree all 1.11ubuntu2 [3,952 kB]
Fetched 3,952 kB in 5s (767 kB/s)                   
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 496958 files and directories currently installed.)
Unpacking linux-firmware-nonfree (from .../linux-firmware-nonfree_1.11ubuntu2_all.deb) ...
Setting up linux-firmware-nonfree (1.11ubuntu2) ...
scott@scott-desktop:~$ sudo apt-key update
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
scott@scott-desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb2       9.1G  6.9G  1.7G  81% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           394M  968K  393M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  140K  2.0G   1% /run/shm
/dev/sdb1       453M  341M   85M  81% /boot
/dev/sdb4       103G   15G   83G  16% /home
/dev/sr0        6.8G  6.8G     0 100% /media/Data disc (03 Apr 14)
scott@scott-desktop:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sdb2       610800 514386   96414   85% /
udev            207624    607  207017    1% /dev
tmpfs           212364    545  211819    1% /run
none            212364      3  212361    1% /run/lock
none            212364      6  212358    1% /run/shm
/dev/sdb1       121920    297  121623    1% /boot
/dev/sdb4      6807552  16252 6791300    1% /home
/dev/sr0             0      0       0     - /media/Data disc (03 Apr 14)
```

---

### Post by dimmaz88 on 2014-07-18
I just restarted and it now says 'starting the winbind daemon windind saned disabled;edit /etc/default/saned. *checking battery state

Also, if I just boot in recovery mode and select boot as normal it's fine.

Just thought this might shed a slither of light :)

---

### Post by Bashing-om on 2014-07-18
dimmaz88; Well, Looking better all the time.

So, with this new error, let's take the hint and have a look:
```

cat /etc/default/saned

```
See if we can see what the problem is.

Not in a real hurt at this time, but need to attend to space usage in '/' and /boot (81/85 %) soonest. -> do some house cleaning.
Remind me once more the release you are running:
```

lsb_release -a

```

Getting there
[INDENT][INDENT][INDENT]all shinny, like brand spanking new
[/INDENT][/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-19
Good to hear it's not too bad :)

```
scott@scott-desktop:~$ cat /etc/default/saned
# Defaults for the saned initscript, from sane-utils

# Set to yes to start saned
RUN=no

# Set to the user saned should run as
RUN_AS_USER=saned
scott@scott-desktop:~$ lsb-release -a
No command 'lsb-release' found, did you mean:
 Command 'lsb_release' from package 'lsb-release' (main)
lsb-release: command not found
scott@scott-desktop:~$ lsb_release -a
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:printing-3.2-ia32:printing-3.2-noarch:printing-4.0-ia32:printing-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


```

---

### Post by dimmaz88 on 2014-07-19
It's back to saying broken pipe on boot up.

---

### Post by Bashing-om on 2014-07-19
dimmaz88; shucks;

As around and round we go.

The notification of 'saned' disabled is true; as that is -> winbind daemon -> a part of "samba". Are you networking with Windows ? If so, is that connection fully functional ? Is this the source of the 'broken pipe ? ..
Else let's consider doing the house cleaning, and inquire of the package manager what the state of the system is.

[INDENT][INDENT]cause and effect
[/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-19
I have windows installed on a separate HD, would this be classed as networking?
How do I go about house cleaning?

---

### Post by Bashing-om on 2014-07-19
dimmaz88; Nah,

Dual booting with Windows should not necessitate having 'samba' // Presently do not know where/why samba would come into play here, as it obviously does.

But, yeah. let's clear the desk - so to speak - and see what the Package Manager advises.
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,A dist-upgrade will install new dependencies for packages already #installed and may remove packages if they are no longer needed. This will NOT bring you to a new release of ubuntu. 
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
##All that does is update it again.##

```

Be aware I do not do Windows, and have no experience with 'samba'. If this does turn into a 'samba' issue I will require assistance.

[INDENT][INDENT]poke at it 'til
[INDENT][INDENT][INDENT]something gives
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-19
Here's the output. 
```
scott@scott-desktop:~$ sudo apt-get autoclean
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del linux-headers-3.2.0-65-generic-pae 3.2.0-65.98 [977 kB]
Del linux-libc-dev 3.2.0-65.99 [861 kB]
Del linux-image-3.2.0-65-generic-pae 3.2.0-65.98 [38.4 MB]
Del libavformat53 4:0.8.12-0ubuntu0.12.04.1 [1,039 kB]
Del libswscale2 4:0.8.12-0ubuntu0.12.04.1 [195 kB]
Del linux-headers-generic-lts-trusty 3.13.0.30.26 [2,488 B]
Del linux-generic-pae 3.2.0.65.77 [1,724 B]
Del libavcodec-extra-53 4:0.8.12ubuntu0.12.04.1 [5,836 kB]
Del linux-headers-generic-pae 3.2.0.65.77 [2,482 B]
Del linux-image-generic-pae 3.2.0.65.77 [2,490 B]
Del linux-generic-lts-trusty 3.13.0.30.26 [1,748 B]
Del flashplugin-installer 11.2.202.378ubuntu0.12.04.1 [6,974 B]
Del linux-image-generic-lts-trusty 3.13.0.30.26 [2,492 B]
Del linux-headers-3.2.0-65 3.2.0-65.98 [11.7 MB]
Del libavutil-extra-51 4:0.8.12ubuntu0.12.04.1 [133 kB]
Del libpostproc52 4:0.8.12-0ubuntu0.12.04.1 [116 kB]
Del libavdevice53 4:0.8.12-0ubuntu0.12.04.1 [52.9 kB]
Del linux-libc-dev 3.2.0-65.98 [862 kB]
scott@scott-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  language-pack-kde-en language-pack-kde-en-base
0 to upgrade, 0 to newly install, 2 to remove and 0 not to upgrade.
After this operation, 3,399 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 497121 files and directories currently installed.)
Removing language-pack-kde-en-base ...
Removing language-pack-kde-en ...
Processing triggers for software-center ...
INFO:softwarecenter.db.update:translation information in database is up-to-date
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
scott@scott-desktop:~$ sudo apt-get clean
scott@scott-desktop:~$ #refresh
scott@scott-desktop:~$ sudo apt-get update #resync package index
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://76.73.4.58 precise Release.gpg                                      
Hit http://76.73.4.58 precise-updates Release.gpg                              
Hit http://76.73.4.58 precise-backports Release.gpg                            
Hit http://76.73.4.58 precise-security Release.gpg                             
Hit http://76.73.4.58 precise Release                                          
Hit http://76.73.4.58 precise-updates Release                        
Hit http://76.73.4.58 precise-backports Release                      
Hit http://download.ebz.epson.net lsb3.2 Release.gpg                           
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en_GB          
Hit http://76.73.4.58 precise-security Release                       
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://76.73.4.58 precise/main Sources                           
Hit http://76.73.4.58 precise/restricted Sources
Hit http://76.73.4.58 precise/universe Sources
Hit http://76.73.4.58 precise/multiverse Sources
Hit http://76.73.4.58 precise/main i386 Packages
Hit http://76.73.4.58 precise/restricted i386 Packages
Hit http://download.ebz.epson.net lsb3.2 Release
Hit http://76.73.4.58 precise/universe i386 Packages
Hit http://76.73.4.58 precise/multiverse i386 Packages
Hit http://76.73.4.58 precise/main TranslationIndex
Hit http://76.73.4.58 precise/multiverse TranslationIndex
Hit http://76.73.4.58 precise/restricted TranslationIndex
Hit http://76.73.4.58 precise/universe TranslationIndex
Hit http://76.73.4.58 precise-updates/main Sources
Hit http://76.73.4.58 precise-updates/restricted Sources
Hit http://76.73.4.58 precise-updates/universe Sources
Hit http://76.73.4.58 precise-updates/multiverse Sources
Hit http://download.ebz.epson.net lsb3.2/main i386 Packages
Hit http://76.73.4.58 precise-updates/main i386 Packages
Hit http://76.73.4.58 precise-updates/restricted i386 Packages
Hit http://76.73.4.58 precise-updates/universe i386 Packages
Hit http://76.73.4.58 precise-updates/multiverse i386 Packages
Hit http://76.73.4.58 precise-updates/main TranslationIndex
Hit http://76.73.4.58 precise-updates/multiverse TranslationIndex
Hit http://76.73.4.58 precise-updates/restricted TranslationIndex
Hit http://76.73.4.58 precise-updates/universe TranslationIndex
Hit http://76.73.4.58 precise-backports/main Sources
Hit http://76.73.4.58 precise-backports/restricted Sources
Ign http://download.ebz.epson.net lsb3.2/main TranslationIndex
Hit http://76.73.4.58 precise-backports/universe Sources
Hit http://76.73.4.58 precise-backports/multiverse Sources
Hit http://76.73.4.58 precise-backports/main i386 Packages
Hit http://76.73.4.58 precise-backports/restricted i386 Packages
Hit http://76.73.4.58 precise-backports/universe i386 Packages
Hit http://76.73.4.58 precise-backports/multiverse i386 Packages
Hit http://76.73.4.58 precise-backports/main TranslationIndex
Hit http://76.73.4.58 precise-backports/multiverse TranslationIndex
Hit http://76.73.4.58 precise-backports/restricted TranslationIndex
Hit http://76.73.4.58 precise-backports/universe TranslationIndex
Hit http://download.ebz.epson.net lsb3.2/main Translation-en_GB
Hit http://76.73.4.58 precise-security/main Sources
Hit http://76.73.4.58 precise-security/restricted Sources
Hit http://76.73.4.58 precise-security/universe Sources
Hit http://76.73.4.58 precise-security/multiverse Sources
Hit http://download.ebz.epson.net lsb3.2/main Translation-en
Hit http://76.73.4.58 precise-security/main i386 Packages
Hit http://76.73.4.58 precise-security/restricted i386 Packages
Hit http://76.73.4.58 precise-security/universe i386 Packages
Hit http://76.73.4.58 precise-security/multiverse i386 Packages
Hit http://76.73.4.58 precise-security/main TranslationIndex
Hit http://76.73.4.58 precise-security/multiverse TranslationIndex
Hit http://76.73.4.58 precise-security/restricted TranslationIndex
Hit http://76.73.4.58 precise-security/universe TranslationIndex
Hit http://76.73.4.58 precise/main Translation-en_GB
Hit http://76.73.4.58 precise/main Translation-en
Hit http://76.73.4.58 precise/multiverse Translation-en_GB
Hit http://76.73.4.58 precise/multiverse Translation-en
Hit http://76.73.4.58 precise/restricted Translation-en_GB
Hit http://76.73.4.58 precise/restricted Translation-en
Hit http://76.73.4.58 precise/universe Translation-en_GB
Hit http://76.73.4.58 precise/universe Translation-en
Hit http://76.73.4.58 precise-updates/main Translation-en_GB
Hit http://76.73.4.58 precise-updates/main Translation-en
Hit http://76.73.4.58 precise-updates/multiverse Translation-en_GB
Hit http://76.73.4.58 precise-updates/multiverse Translation-en
Hit http://76.73.4.58 precise-updates/restricted Translation-en_GB
Hit http://76.73.4.58 precise-updates/restricted Translation-en
Hit http://76.73.4.58 precise-updates/universe Translation-en_GB
Hit http://76.73.4.58 precise-updates/universe Translation-en
Hit http://76.73.4.58 precise-backports/main Translation-en
Hit http://76.73.4.58 precise-backports/multiverse Translation-en
Hit http://76.73.4.58 precise-backports/restricted Translation-en
Hit http://76.73.4.58 precise-backports/universe Translation-en
Hit http://76.73.4.58 precise-security/main Translation-en
Hit http://76.73.4.58 precise-security/multiverse Translation-en
Hit http://76.73.4.58 precise-security/restricted Translation-en
Hit http://76.73.4.58 precise-security/universe Translation-en
Reading package lists... Done
scott@scott-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
scott@scott-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
scott@scott-desktop:~$ sudo dpkg --configure -a
scott@scott-desktop:~$ 


```

---

### Post by Bashing-om on 2014-07-19
dimmaz88; Well .

That looks good ! .. A couple of index files rebuilt and obsolete files removed.

How about running:
```

sudo apt-get dist-upgrade

```
Does not do any distribution(release) upgrade, uses apt-get's smart mode to install additional files as needed.
 
What now results when you re-boot ?

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-20
I ran that already Bashing, just tried again though but nothing more to update.

Boot up is still the same :(

---

### Post by Bashing-om on 2014-07-20
dimmaz88; Well. well ...

System is intact, package manager is happy that only leaves an index file and/or config file "some where" in an inconsistent state.

All I know to do now is look at the log files and see what is recorded - looking for faults and errors. About all I can think of;  look at the files  "/var/log/syslog" and "/var/log/kern.log", for starters . Also what might be a possibility is to disable the splash screen to see the boot messages, tricky but the boot messages can be paged .

When all else fails, read the logs

---

### Post by dimmaz88 on 2014-07-21
Thanks Bashing, I've no idea how to  access those logs or disable splash screen.

I'm just thinking about re-installing, It's not long since I did it so it wouldn't be to much of a pain. I would rather fix the issue but I'm out of my depth at this point :)

---

### Post by Bashing-om on 2014-07-21
dimmaz88; Hey;

Mind you, we can work through these small issues.
It would be nice to discover the cause.
Maybe kernel related ? Presently just do not know .. We are seeing a number of issues on the forum in respect to the Hardware enablement stack, installing the 'trusty' kernel' in release 12.04.

Now I am forthright in recommending release 14.04. There are many enchancements over 12.04, and on my system 14.04 runs much faster than 12.04, and it is as solid as a rock. In addition 14.04 has support 'til 2019 .

> 
linux-headers-generic-lts-trusty linux-headers-generic-pae


Maybe we should look again and see what kernel you are running. Post back the output of terminal command:
```

uname -a

```

But it is your system, your time, and your effort - we are here to help, guide and assist -> but, it is your call what you want to do. We can keep pounding away at this and try and find the cause -> inquiring minds want to know.

To read the log files, the easy way, IF you are on a standard desktop install : dash -> log file (viewer) and navigate to the log files you want to read / may have to 'activate' some of those log files if they are not in the default list.

As we get no hints of the cause from the GUI startup, no hints from the package manager, the only other thing I know to do is to "read the logs".

------------------------
It is quite neat ( adds to your geekiness" to boot up with the boot messages on-screen). If you want to see - for a 1 time thing:
Boot ubuntu to the grub boot menu; 'e' key for edit mode with the top most "normal" kernel highlighted -> boot parameters screen; arrow down to the line similar " linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff" and arrow across to the terms "quiet splash" and replace these terms with the term "text" - without the quotes.
Key combo ctl+x to continue the boot process.
Now, if you like what you see and/or desire to make booting with text messaging a permanent thing, one edits the config file ' /etc/default/grub '.
On my system to pause the text output - key combo ctl+o .... and to resume, - key combo ctl+s . Your mileage may vary. Some systems the "Scroll Lock" works.
------------------------


[INDENT][INDENT]when all else fails 
[INDENT][INDENT][INDENT][INDENT]read the instructions ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-22
Hi Bashing, I decided to try the update to 14.04 for an easy fix. Now it won't let me on at all, not even through recovery mode.

Any ideas of how I can get on, I think I'll then just do a re-install.

Cheers

---

### Post by Bashing-om on 2014-07-22
dimmaz88; Yikes !


Now that just ain't good.


OK, as we now have a new set of problems to work on .... let's start a new thread and close this one.
That will gain a wider audience in the event you and I can not come up with a means to restore 14.04.

In that new thread .. provide the results:
Boot to the grub menu and the normal (non-recovery) kernel highlighted; press the 'c' key for a command line interface.
For a place to start, post the results of grub commands:
```

ls -lh (hd1,msdos1)
ls -lh (hd1,msdos1)/
ls -lh (hd1,msdos1)/boot
ls -lh (hd1,msdos1)/vmlinuz
ls -lh (hd1,msdos1)/initrd.img
ls -lh (hd1,msdos1)/boot/grub/grub.cfg

```
Prior to the release upgrade the hard drive was seen as 'sdb' .. maybe it is now correctly seen as 'sda' and maybe grub's config files are looking for UUIDs set to 'sdb' ??? If 'fdisk' - from the liveDVD - reports the hard drive now as 'sda' then replace 'hd1' with 'hd0' in the above commands.
Note, this is but one of the things that I am concerned about in this install, in that the hard drive was seen as 'sdb', I would expect that drive to be seen as 'sda' ( where 'sdb' is system speak for grub speak 'hd1').

To be honest, in a problematic situational (re-)install, it is best always to - back up your data - do a fresh clean install thereby leaving all the past problems in the past.
Nice clean slate to work from. 

Like I say, let's start a new thread and go from these.

[INDENT][INDENT]ain't nothing but a thing
[INDENT][INDENT][INDENT]now, maybe a big thing ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-23
I tried the list of commands and each said 'no such partition'

I tried using the boot repair disk I have, it didn't work but gave this summary

[http://paste.ubuntu.com/7841724/](http://paste.ubuntu.com/7841724/)

I don't know if that was any use.

I think I'll go ahead with a full re-install, I'm impatient and need the use of my pc. I can't stand using the windows partition :)

Cheers

---

### Post by Bashing-om on 2014-07-23
dimmaz88; Oh Boy,

Drive sdb does not contain the boot code.

Upfront, looking at the latest boot-repair, I see no easy way at all to fix this. Your 'better' course at this time is to back up your data and (RE-)install (again) all fresh and clean. The repartitioning to create a GPT- 'bios-boot' partition is risky business at best, and my GPT skills are skimpy , to say the least.
Boot up the liveDVD and mount/access the partitions on sdb and copy the files off of sdb in preparation to wipe/re-install.
Main reasons why:
See line 1270: drive sdb is now partitioned as GPT, GPT requires a BIOS-Boot partition to hold the boot code; non-existent.
Drive sdb partitions are all formatted as ext4 ; Windows can not read the "data" partitions.

I highly suggest you re-think how you want to use your system ... I see it presently as sda devoted to Windows ... and I would in that event re-install Windows boot code to sda; sdb devoted to ubuntu, with a shared data partition that should be formatted as "NTFS". Install ubuntu's boot manager grub to 'sdb' and chainload Windows to grub's boot menu -> setting in bios which drive to boot from.

I would highly recommend to re-partition sdb to MBR to match the partitioning scheme of sda, as mixed modes can get to be a source of great confusion.

That is my thought on this situation. Close this thread, as the original issue no longer has existence, and IF you have difficulties (RE-)installing ubuntu, by all means open a new thread to address that new issue.

Many paths lead to an end
[INDENT][INDENT][INDENT]pick one
[/INDENT][/INDENT][/INDENT]

---

### Post by dimmaz88 on 2014-07-23
Thank you so much for all of your help. I only wish I was a bit more ubuntu educated so I could give more details as to what initially went wrong.
I'll do as you say with regards to re-installing, and I will have to start a new thread in order to do so :)

Thanks again.
Scott

---

### Post by Bashing-om on 2014-07-23
dimmaz88; Good deal;

Keep in mind it is all a process in learning. With this operating system in particular, if one wants, it is a never-ending process. It evolves so rapidly !


[INDENT][INDENT]'til we meet again
[INDENT][INDENT][INDENT]my regards
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

