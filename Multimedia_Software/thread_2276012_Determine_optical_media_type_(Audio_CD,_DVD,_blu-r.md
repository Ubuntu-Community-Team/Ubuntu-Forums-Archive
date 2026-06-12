---
title: "Determine optical media type (Audio CD, DVD, blu-ray) by using UDEV and scripts"
date: 2015-04-29
forum: Multimedia Software
---

### Post by jlivin252 on 2015-04-29
Hello Lovely Ubuntu Folk :)


I am relatively new to linux having made the switch from Windows to have a headless media centre. So i am running KODIBuntu.


I am trying to achieve an automated ripping system to backup my hard copy media collection. I have loved the concept with linux that 'if you can dream it you can make it happen'.


What i'm aiming to achieve is that a disc is put into the drive and a script rips the content to my drive.


e.g disc inserted -> media type determined -> correct ripping script run


I have used lots of useful web pages through google searches to create scripts that will do the ripping work itself. I have done a bunch of reading and was pointed towards using 'HAL'....I then found that his function had been deprecated and replaced by udev. I did a bunch more reading and found out how to use UDEV and created the folowing rule which i have proved works by linking directly to a ripping script


[(https://github.com/littlejeem/CDRip/blob/master/80-AutoDiscInsert.rules)ACTION==&quot;change&quot;, SUBSYSTEMS==&quot;scsi&quot;, KERNEL==&quot;s[rg][0-9]*&quot;, ATTRS{vendor}==&quot;TSSTcorp&quot;, MODE=&quot;0660&quot;, GROUP=&quot;optical&quot;, RUN+=&quot;/home/jlivin25/myscripts/DiscTypeTest.sh&quot;I realised that I needed an intermediate script that would do the 'work' to determine what the optical media type is. Further reading led me to believe that I would need to use some kind of 'IF' statement.IF disc inserted then IF audio cd run rip script 1 IF DVD run rip script 2 IF blu-ray run rip script 3 ELSE no cd insertedI have done some more googling and found some code in various places that uses environmental variables to work. However from further information on google it appears that these variables are not defined until referenced by UDEV?My usual approach is to constuct a line of code, run in terminal and if i get what i want then i put all the lines together in a shell script?The code i have at the moment is below, any ideas folks about why this is not working as i want?I have used these pages to get information from [https://pathar.tl/blog/the-ultimate-automated-ripping-machine/](https://pathar.tl/blog/the-ultimate-automated-ripping-machine/) [http://confoundedtech.blogspot.co.uk/2012/12/ubuntu-1204-run-custom-command-on-cd.html](http://confoundedtech.blogspot.co.uk/2012/12/ubuntu-1204-run-custom-command-on-cd.html) [http://askubuntu.com/questions/359855/how-to-detect-insertion-of-dvd-disc](http://askubuntu.com/questions/359855/how-to-detect-insertion-of-dvd-disc)[https://github.com/littlejeem/CDRip/blob/master/DiscTypeTest.sh](https://github.com/littlejeem/CDRip/blob/master/DiscTypeTest.sh)#!/bin/bash # set -eu # # code below is derived from work by JimVanns, thanks # [https://github.com/jvanns/htpc/blob/master/dsc-trg-q](https://github.com/jvanns/htpc/blob/master/dsc-trg-q) # # ########################################################################### ###DEFINE VARIABLES HERE### ### $HOME DOES NOT NEED DEFINING AS IT SEEMS TO BE BUILT INTO BASH FROM ### ### WHAT POSTS I HAVE READ RELATING TO USING WHAT I THINK ARE UDEV### ###ENVIRONMENTAL VARIABLES E.G. $ID_CDROM_MEDIA_CD DO NOT APPEAR TO ### ###NEED DEFINING THEMSELVES, ALSO PART OF BASH OR LINUX COMMAND ### ###STRUCTURE CALLED BY BASH?### ########################################################################### # MEDIA= # ############################################################################## ### LEFT IN SO AS TO ALTER AS LITTLE AS POSSIBLE, I HAVE READ THAT DELAYS### ###OFTEN IRON OUT KINKS IN CODE,PLUS ALSO FOUND IT USEFULL TO ALLOW A### ###SMALL DELAY FOR CD-DRIVE TO DO ITS THING AFTER PUTTING DISK IN### ############################################################################## # sleep 2 # mkdir -p $HOME/myscripts/scriptlogsif [ &quot;$ID_CDROM_MEDIA_BD&quot; = &quot;1&quot; ] then MEDIA=bluray ( echo &quot;$MEDIA&quot; >> $HOME/myscripts/scriptlogs/DiscTypeTest.log ) & if [ &quot;$ID_CDROM_MEDIA_DVD&quot; = &quot;1&quot; ] then MEDIA=dvd ( echo &quot;$MEDIA&quot; >> $HOME/myscripts/scriptlogs/DiscTypeTest.log ) & elif [ &quot;$ID_CDROM_MEDIA_CD&quot; = &quot;1&quot; ] then MEDIA=cdrom ( echo &quot;$MEDIA&quot; >> $HOME/myscripts/scriptlogs/DiscTypeTest.log ) & fi"]https://github.com/littlejeem/CDRip/blob/master/80-AutoDiscInsert.rules]("http://Hello Lovely Ubuntu Folk :)I am relatively new to linux having made the switch from Windows to have a headless media centre. So i am running KODIBuntu.I am trying to achieve an automated ripping system to backup my hard copy media collection. I have loved the concept with linux that 'if you can dream it you can make it happen'.What i'm aiming to achieve is that a disc is put into the drive and a script rips the content to my drive.e.g disc inserted -> media type determined -> correct ripping script runI have used lots of useful web pages through google searches to create scripts that will do the ripping work itself. I have done a bunch of reading and was pointed towards using 'HAL'....I then found that his function had been deprecated and replaced by udev. I did a bunch more reading and found out how to use UDEV and created the folowing rule which i have proved works by linking directly to a ripping script[https://github.com/littlejeem/CDRip/blob/master/80-AutoDiscInsert.rules)


```
ACTION=="change", SUBSYSTEMS=="scsi", KERNEL=="s[rg][0-9]*", ATTRS{vendor}=="TSSTcorp", MODE="0660", GROUP="optical", RUN+="/home/jlivin25/myscripts/DiscTypeTest.sh"

```

I realised that I needed an intermediate script that would do the 'work' to determine what the optical media type is. Further reading led me to believe that I would need to use some kind of 'IF' statement.


IF disc inserted
then
IF audio cd run rip script 1
IF DVD run rip script 2
IF blu-ray run rip script 3
ELSE no cd inserted


I have done some more googling and found some code in various places that uses environmental variables to work. However from further information on google it appears that these variables are not defined until referenced by UDEV?


My usual approach is to constuct a line of code, run in terminal and if i get what i want then i put all the lines together in a shell script?


The code i am working on a the moment is below. I though that logically if i could get the script to output what it thinks is in the drive to a file /log that half the battle would be won and i could just substitute this for the script locations that would do the corresponding ripping task................any ideas folks about why this is not working as i want?


I have used these pages to get information from
[https://pathar.tl/blog/the-ultimate-automated-ripping-machine/](https://pathar.tl/blog/the-ultimate-automated-ripping-machine/)
[http://confoundedtech.blogspot.co.uk/2012/12/ubuntu-1204-run-custom-command-on-cd.html](http://confoundedtech.blogspot.co.uk/2012/12/ubuntu-1204-run-custom-command-on-cd.html)
[http://askubuntu.com/questions/359855/how-to-detect-insertion-of-dvd-disc](http://askubuntu.com/questions/359855/how-to-detect-insertion-of-dvd-disc)


[https://github.com/littlejeem/CDRip/blob/master/DiscTypeTest.sh](https://github.com/littlejeem/CDRip/blob/master/DiscTypeTest.sh)


```
#!/bin/bash
#
set -eu
#
# code below is derived from work by JimVanns, thanks
# https://github.com/jvanns/htpc/blob/master/dsc-trg-q
#
#
###########################################################################
###                        DEFINE VARIABLES HERE                        ###
### $HOME DOES NOT NEED DEFINING AS IT SEEMS TO BE BUILT INTO BASH FROM ###
###   WHAT POSTS I HAVE READ RELATING TO USING WHAT I THINK ARE UDEV    ###
###  ENVIRONMENTAL VARIABLES E.G. $ID_CDROM_MEDIA_CD DO NOT APPEAR TO   ###
###    NEED DEFINING THEMSELVES, ALSO PART OF BASH OR LINUX COMMAND     ###
###                      STRUCTURE CALLED BY BASH?                      ###
###########################################################################
#
MEDIA=
#
##############################################################################
### LEFT IN SO AS TO ALTER AS LITTLE AS POSSIBLE, I HAVE READ THAT DELAYS  ###
###  OFTEN IRON OUT KINKS IN CODE,  PLUS ALSO FOUND IT USEFULL TO ALLOW A  ###
###    SMALL DELAY FOR CD-DRIVE TO DO ITS THING AFTER PUTTING DISK IN      ###
##############################################################################
#
sleep 2
#
mkdir -p $HOME/myscripts/scriptlogs


if [ "$ID_CDROM_MEDIA_BD" = "1" ]
then
        MEDIA=bluray
        (
        echo "$MEDIA" >> $HOME/myscripts/scriptlogs/DiscTypeTest.log
        ) &
if [ "$ID_CDROM_MEDIA_DVD" = "1" ]
then
        MEDIA=dvd
        (
        echo "$MEDIA" >> $HOME/myscripts/scriptlogs/DiscTypeTest.log
        ) &
elif [ "$ID_CDROM_MEDIA_CD" = "1" ]
then
        MEDIA=cdrom
        (
        echo "$MEDIA" >> $HOME/myscripts/scriptlogs/DiscTypeTest.log
        ) &
fi

```

Thanks in advance

James

---

### Post by blm-ubunet on 2015-05-04
Have you set the execute bit/flag on the script file ?
It is possible (can't find definitive statement) that udev will not/can not execute scripts in your /home folder.
Udev does not run as your user or group.

I have udev launched scripts in /usr/local/bin with root:root as owner:group & same permissions as other programs.
My udev rule & script auto-mounts BDs only to a fixed mountpoint for MythTV etc.

Your script might have more success writing to file(s) in /tmp and/or /var/log .

I assume you have used
```
udevadm monitor
```
to watch the events fire?

---

### Post by Keith_Helms on 2015-05-04
I'd start by verifying what variables are actually being set.  Add the following to your script:

```
(set -o posix ; set) > *outputfile*
```

---

### Post by jlivin252 on 2015-05-07
blm-ubunet - thanks for the reply massively appreciate any help.

I must admit that I hadn't used: ```
[COLOR=#000000][FONT=Ubuntu Mono]udevadm monitor[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
[FONT=arial]but i have just done so now, i post the output below:[/FONT]

[/FONT][/COLOR]```
jlivin25@Kodibuntu:~$ sudo udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent


KERNEL[84423.382178] change   /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0/host6/target6:0:0/6:0:0:0/block/sr0 (block)
KERNEL[84427.496566] change   /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0/host6/target6:0:0/6:0:0:0/block/sr0 (block)
UDEV  [84427.500921] change   /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0/host6/target6:0:0/6:0:0:0/block/sr0 (block)
UDEV  [84429.573455] change   /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0/host6/target6:0:0/6:0:0:0/block/sr0 (block)

```

as for the script location i had assumed that because i could link udev to another script in the same location, which worked, that it (udev) would act in the same way in each instance. I'll move the scripts and try it again and post back.

Thanks for the thoughts :)

James

---

### Post by jlivin252 on 2015-05-07
Keith_Helms. Huge thanks for the response, this is exactly the type of guidance i was hoping for, i just didn't know how to test the variables being set.

I would assume that it would be inserted in the script at te beginning before the variables are asked to do anything, something like this?

```
#!/bin/bash
**set** -eu
# code below is derived from work by JimVanns, thanks
# [https://github.com/jvanns/htpc/blob/master/dsc-trg-q](https://github.com/jvanns/htpc/blob/master/dsc-trg-q)
#
MEDIA=
#
sleep 2
#
**mkdir** -p **"$HOME/myscripts/scriptlogs"**
(**set** -o posix ; **set**) > **"$HOME/myscripts/scriptlogs/DiscTypeTest.log"**
#
if [ **"$ID_CDROM_MEDIA_BD"** = **"1"** ]
```

etc etc....

---

### Post by jlivin252 on 2015-05-07
Hello Both

Tested your advice tonight unfortunately, i didn't get a change in behaviour and assuming i have put ([COLOR=#000000]Keith_Helms.) [/COLOR]idea into practice correctly i don't get any output to file....any thoughts :)

j```
livin25@Kodibuntu:~$ sudo udevadm monitor
[sudo] password for jlivin25: 
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent


KERNEL[88986.021660] change   /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0/host6/target6:0:0/6:0:0:0/block/sr0 (block)
KERNEL[88990.177806] change   /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0/host6/target6:0:0/6:0:0:0/block/sr0 (block)
UDEV  [88996.153299] change   /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0/host6/target6:0:0/6:0:0:0/block/sr0 (block)
UDEV  [88998.306432] change   /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0/host6/target6:0:0/6:0:0:0/block/sr0 (block)
```

Thanks

James

---

### Post by Keith_Helms on 2015-05-08
If the script is being kicked off by the udev subsystem, then it's probably running under root and not your ID.   Therefore $HOME is not set, so trying to write a file to "$HOME/myscripts/scriptlogs/DiscTypeTest.log" won't work.   Change $HOME to /home/*yourid* and try it again.

---

### Post by jlivin252 on 2015-05-10
Keith_Helms - did as you suggested and changed the location to read as you quoted.... No change that I can see.

Just to check I linked the udev rule back directly to a ripping script and this triggered successfully so I assume its this script that is not producing a result.

James

---

### Post by Keith_Helms on 2015-05-10
Is the script creating that subdirectory named myscripts/scriptlogs under your home directory?   You're not deleting that directory somewhere else are you?

---

### Post by Keith_Helms on 2015-05-10
Okay, I did some playing around and have the following information:

"set -o posix" is intended to make the variable listing "standardized".  The -o posix option works under bash, but will give an error when run under /bin/sh.  Without it, you might get some extra output such as the text for all shell functions that are defined.  On my system that ran to several hundred lines of output.  The plain shell variables were listed first, so it didn't reallly hurt anything.  Anyway, make sure the shell that is being executed is a Bash shell.  When I inserted (set -o posix ; set) in a /bin/sh script, I got no output from it because the -o posix caused it to fail with an error.  If you're not sure, take out the "set -o posix".

The parenthesis around the two commands runs them as a subshell.  That gives them their own temporary copy of the environment so that the posix option only applies to that subshell and not to the main script "above".  If you remove the set -o posix, then you don't need the parenthesis either, although they won't hurt anything beyond adding a little insignificant overhead to create a copy of the environment.

---

### Post by mc4man on 2015-05-10
I wish you all good luck with this but would mention - 
95% of what you want is already in place, just take a look at System Settings > Details > Removable Media, either right there or further in > Other Media

So you can simply write scripts for each media type & set that script as the default action per media type insertion, either executed from prompt acceptance or autorun with no interaction.

---

### Post by jlivin252 on 2015-05-11
Hello Keith_Helms

The script log location is under my home directory yes:

```
/home/user/myscripts/scriptlogs/
```

I have not tried changing the location of the file to write too. I change that to somewhere like user/bin

---

### Post by jlivin252 on 2015-05-11
Hello Keith_Helms

The script log location is under my home directory yes:

```
/home/user/myscripts/scriptlogs/
```

I have not tried changing the location of the file to write too. I change that to somewhere like user/bin

---

### Post by jlivin252 on 2015-05-12
> **mc4man said:**
> I wish you all good luck with this but would mention - 
95% of what you want is already in place, just take a look at System Settings > Details > Removable Media, either right there or further in > Other Media

So you can simply write scripts for each media type & set that script as the default action per media type insertion, either executed from prompt acceptance or autorun with no interaction.

Hi mc4man, thanks for taking the time to post. Take your comments on board but the point of my post is to find out how to do this in a headless environment...not sure if your suggestion would resolve this?

---

### Post by jlivin252 on 2015-05-12
> **Keith_Helms said:**
> Okay, I did some playing around and have the following information:

"set -o posix" is intended to make the variable listing "standardized".  The -o posix option works under bash, but will give an error when run under /bin/sh.  Without it, you might get some extra output such as the text for all shell functions that are defined.  On my system that ran to several hundred lines of output.  The plain shell variables were listed first, so it didn't reallly hurt anything.  Anyway, make sure the shell that is being executed is a Bash shell.  When I inserted (set -o posix ; set) in a /bin/sh script, I got no output from it because the -o posix caused it to fail with an error.  If you're not sure, take out the "set -o posix".

The parenthesis around the two commands runs them as a subshell.  That gives them their own temporary copy of the environment so that the posix option only applies to that subshell and not to the main script "above".  If you remove the set -o posix, then you don't need the parenthesis either, although they won't hurt anything beyond adding a little insignificant overhead to create a copy of the environment.

Hello Keith_Helms. Thanks for taking the time to guide still further, I will try this tonight when i get home. Will probably try to strip back my code a little to error check, will also create file in an area that may be better permissions wise (put script.log file somewhere like ```
 /usr/local/bin 
```. Hopefully this will give me an output to investigate.

thanks

James

---

### Post by blm-ubunet on 2015-05-12
James
Log files do not belong in /usr/local/bin/
Log files belong in /var/log/ or /tmp/ (short lived) or your home folder if you can resolve the path in script.

Your scripts should be in /usr/local/bin (all users) or in home folder (if you can resolve path & permissions).
Your script needs the right permissions (+ execute bit) & user:group.

Can use:
sudo chmod --reference=copy-this-file-perms  my-wrong-perms-file
Obviously the reference file needs to be chosen with care.

Copying file as root (or root user nautilus etc) will make the new file have user:group=root:root (good).

blm.

---

### Post by jlivin252 on 2015-05-12
> **blm-ubunet said:**
> James
Log files do not belong in /usr/local/bin/
Log files belong in /var/log/ or /tmp/ (short lived) or your home folder if you can resolve the path in script.

Your scripts should be in /usr/local/bin (all users) or in home folder (if you can resolve path & permissions).
Your script needs the right permissions (+ execute bit) & user:group.

Can use:
sudo chmod --reference=copy-this-file-perms  my-wrong-perms-file
Obviously the reference file needs to be chosen with care.

Copying file as root (or root user nautilus etc) will make the new file have user:group=root:root (good).

blm.

Hi blm

Thanks for the pointer, i will move the script log location as you suggest.

My scripts i have been working on in my home folder, however some other post suggested that user permission errors would cause me issues so suggested i use ```
/usr/local/bin
```

Thanks for the guidance

James

---

### Post by jlivin252 on 2015-05-12
> **jlivin252 said:**
> Hello Keith_Helms. Thanks for taking the time to guide still further, I will try this tonight when i get home. Will probably try to strip back my code a little to error check, will also create file in an area that may be better permissions wise (put script.log file somewhere like ```
 /usr/local/bin 
```. Hopefully this will give me an output to investigate.

thanks

James

ok Keith_Helm, soooo...

I used your posix code and inserted it into a script, ran the script for an experiment and got output to my log. What i notice is that the variables i am trying to use do not appear in this output

script read as follows
```

#!/bin/bash
# ID_CDROM_MEDIA_BD = Bluray
# ID_CDROM_MEDIA_DVD = DVD
# ID_CDROM_MEDIA_CD = CD
(**set** -o posix ; **set**) > **"/var/log/DiscTypeTest.log"**

```

This gave the following log:

```

BASH=/bin/bashBASHOPTS=cmdhist:complete_fullquote:extquote:force_fignore:hostcomplete:interactive_comments:progcomp:promptvars:sourcepath
BASH_ALIASES=()
BASH_ARGC=()
BASH_ARGV=()
BASH_CMDS=()
BASH_LINENO=([0]="0")
BASH_SOURCE=([0]="./DiscTypeTest3.sh")
BASH_VERSINFO=([0]="4" [1]="3" [2]="11" [3]="1" [4]="release" [5]="x86_64-pc-linux-gnu")
BASH_VERSION='4.3.11(1)-release'
DIRSTACK=()
DISPLAY=localhost:10.0
EUID=0
GROUPS=()
HOME=/home/jlivin25
HOSTNAME=Kodibuntu
HOSTTYPE=x86_64
IFS='
'
LANG=en_US.UTF-8
LC_ALL=en_US.utf8
LOGNAME=root
LS_COLORS='rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:t$
MACHTYPE=x86_64-pc-linux-gnu
MAIL=/var/mail/root
OPTERR=1
OPTIND=1
OSTYPE=linux-gnu
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
PIPESTATUS=([0]="0")
POSIXLY_CORRECT=y
PPID=2426
PS4='+ '
PWD=/usr/local/bin
SHELL=/bin/bash
SHELLOPTS=braceexpand:hashall:interactive-comments:posix
SHLVL=1
SUDO_COMMAND=./DiscTypeTest3.sh
SUDO_GID=1000
SUDO_UID=1000
SUDO_USER=jlivin25
TERM=xterm-256color
UID=0
USER=root
USERNAME=root
_=posix

``` 

So reinserted the elseif statements as follows:

```

#!/bin/bash# ID_CDROM_MEDIA_BD = Bluray
# ID_CDROM_MEDIA_DVD = DVD
# ID_CDROM_MEDIA_CD = CD
MEDIA=
if [ **"$ID_CDROM_MEDIA_DVD"**=**"1"** ]
then
        MEDIA=dvd
        (
        **echo** **"$MEDIA"** >> **"/var/log/DiscTypeTest.log"**
        ) &


elif [ **"$ID_CDROM_MEDIA_CD"**=**"1"** ]
then
        MEDIA=cdrom
        (
        **echo** **"$MEDIA"** >> **"/var/log/DiscTypeTest.log"**
        ) &
fi
(**set** -o posix ; **set**) > [B]"/var/log/DiscTypeTest.log"
[/B]
```This gives the following log

```


BASH=/bin/bash
BASHOPTS=cmdhist:complete_fullquote:extquote:force_fignore:hostcomplete:interactive_comments:progcomp:promptvars:sourcepath
BASH_ALIASES=()
BASH_ARGC=()
BASH_ARGV=()
BASH_CMDS=()
BASH_LINENO=([0]="0")
BASH_SOURCE=([0]="./DiscTypeTest3.sh")
BASH_VERSINFO=([0]="4" [1]="3" [2]="11" [3]="1" [4]="release" [5]="x86_64-pc-linux-gnu")
BASH_VERSION='4.3.11(1)-release'
DIRSTACK=()
DISPLAY=localhost:10.0
EUID=0
GROUPS=()
HOME=/home/jlivin25
HOSTNAME=Kodibuntu
HOSTTYPE=x86_64
IFS='
'
LANG=en_US.UTF-8
LC_ALL=en_US.utf8
LOGNAME=root
LS_COLORS='rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.t$
MACHTYPE=x86_64-pc-linux-gnu
MAIL=/var/mail/root
MEDIA=dvd
OPTERR=1
OPTIND=1
OSTYPE=linux-gnu
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
PIPESTATUS=([0]="0")
POSIXLY_CORRECT=y
PPID=2691
PS4='+ '
PWD=/usr/local/bin
SHELL=/bin/bash
SHELLOPTS=braceexpand:hashall:interactive-comments:posix
SHLVL=1
SUDO_COMMAND=./DiscTypeTest3.sh
SUDO_GID=1000
SUDO_UID=1000
SUDO_USER=jlivin25
TERM=xterm-256color
UID=0
USER=root
USERNAME=root
_=posix

```

I can see from the posix log that the variable $MEDIA is MEDIA=dvd which is correct, i will now try with a CD and see what that generates.

Thanks Keith_Helm, at least i'm starting to be able to 'see' whats happening...........

---

### Post by jlivin252 on 2015-05-12
> I can see from the posix log that the variable $MEDIA is MEDIA=dvd which is correct, i will now try with a CD and see what that generates.

Thanks Keith_Helm, at least i'm starting to be able to 'see' whats happening...........


.....bother! running the script with a cd inserted instead gives same log

```

BASH=/bin/bash
BASHOPTS=cmdhist:complete_fullquote:extquote:force_fignore:hostcomplete:interactive_comments:progcomp:promptvars:sourcepath
BASH_ALIASES=()
BASH_ARGC=()
BASH_ARGV=()
BASH_CMDS=()
BASH_LINENO=([0]="0")
BASH_SOURCE=([0]="./DiscTypeTest3.sh")
BASH_VERSINFO=([0]="4" [1]="3" [2]="11" [3]="1" [4]="release" [5]="x86_64-pc-linux-gnu")
BASH_VERSION='4.3.11(1)-release'
DIRSTACK=()
DISPLAY=localhost:10.0
EUID=0
GROUPS=()
HOME=/home/jlivin25
HOSTNAME=Kodibuntu
HOSTTYPE=x86_64
IFS='
'
LANG=en_US.UTF-8
LC_ALL=en_US.utf8
LOGNAME=root
LS_COLORS='rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.t$
MACHTYPE=x86_64-pc-linux-gnu
MAIL=/var/mail/root
MEDIA=dvd
OPTERR=1
OPTIND=1
OSTYPE=linux-gnu
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
PIPESTATUS=([0]="0")
POSIXLY_CORRECT=y
PPID=2753
PS4='+ '
PWD=/usr/local/bin
SHELL=/bin/bash
SHELLOPTS=braceexpand:hashall:interactive-comments:posix
SHLVL=1
SUDO_COMMAND=./DiscTypeTest3.sh
SUDO_GID=1000
SUDO_UID=1000
SUDO_USER=jlivin25
TERM=xterm-256color
UID=0
USER=root
USERNAME=root
_=posix

```

I will see what results are generated via udev when discs are inserted

James

---

### Post by blm-ubunet on 2015-05-13
James
The format of this is wrong:
```
if [ "$ID_CDROM_MEDIA_DVD"="1" ]
```
change all similar instances like to style/format of below
```
if [ $ID_CDROM_MEDIA_DVD = "1" ]  or
if [ "$ID_CDROM_MEDIA_DVD" = "1" ] or
if [ $ID_CDROM_MEDIA_DVD == "1" ]
```

Without the space, I believe it tests the return value of assignment (always true).
So your script was going to return just dvd.

You made a mess of the first line of script as well:
> #!/bin/bash# ID_CDROM_MEDIA_BD = Bluray

I have found this to be a very useful resource:
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html)

---

### Post by jlivin252 on 2015-05-13
> **blm-ubunet said:**
> James
The format of this is wrong:
```
if [ "$ID_CDROM_MEDIA_DVD"="1" ]
```
change all similar instances like to style/format of below
```
if [ $ID_CDROM_MEDIA_DVD = "1" ]  or
if [ "$ID_CDROM_MEDIA_DVD" = "1" ] or
if [ $ID_CDROM_MEDIA_DVD == "1" ]
```

Without the space, I believe it tests the return value of assignment (always true).
So your script was going to return just dvd.

You made a mess of the first line of script as well:


I have found this to be a very useful resource:
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html)

Well well well!!

blm-ubunet your advice is well taken, I have changed the construction of the 'if' statements to match and it is now working! :), thank you.
Keith_Helm I cant thank you enough for the posix code, this will enable me to further look into this. Thank you.

Udev rule as follows:
```

# ID_CDROM_MEDIA_BD = Bluray
# ID_CDROM_MEDIA_DVD = DVD
# ID_CDROM_MEDIA_CD = CD
ACTION=="change", SUBSYSTEMS=="scsi", KERNEL=="s[rg][0-9]*", ATTRS{vendor}=="TSSTcorp", ENV{ID_CDROM}=="?*", MODE="0660", GROUP="optical", RUN+="/usr/local/bin/DiscTypeTest3.sh"

```

links to script as follows

```

#!/bin/bash
# ID_CDROM_MEDIA_BD = Bluray
# ID_CDROM_MEDIA_DVD = DVD
# ID_CDROM_MEDIA_CD = CD
MEDIA=
if [ **$ID_CDROM_MEDIA_DVD** = **"1"** ]
then
        MEDIA=dvd
        (
        **echo** **"$MEDIA"** >> **"/var/log/DiscTypeTest.log"**
        ) &


elif [ **$ID_CDROM_MEDIA_CD** = **"1"** ]
then
        MEDIA=cdrom
        (
        **echo** **"$MEDIA"** >> **"/var/log/DiscTypeTest.log"**
        ) &
fi
(**set** -o posix ; **set**) > [B]"/var/log/DiscTypeTestVariables.log"
[/B]
```

produces the following output in ```
**/var/log/DiscTypeTest.log**
``` when an audio CD is inserted and then a dvd afterwards

```

cdrom
cdrom
dvd
dvd

```

SOLVED

---

### Post by blm-ubunet on 2015-05-14
Great news & well solved.
We've probably all made this mistake before & I'm likely to repeat it sometime in the future.

---

