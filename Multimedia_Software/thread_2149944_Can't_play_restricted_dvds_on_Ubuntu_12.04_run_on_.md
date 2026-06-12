---
title: "Can't play restricted dvds on Ubuntu 12.04 run on VM Virtual Box"
date: 2013-05-30
forum: Multimedia Software
---

### Post by wsfield99 on 2013-05-30
Hi,

Here's a puzzler.  I am running Ubuntu 12.04 in a VM Virtual Box on a Windows 8 machine.  I am trying play encrypted dvds (which I am able to do with no problem on my other Ubuntu setups) but I've encountered an interesting issue.  I have the restricted packages installed as well as libdvdread4 but when I reboot after executing sudo /urs/share/doc/libdvdread4/install-css.sh, it does not take.  If I open the terminal and execute sudo /usr/share/doc/libdvdread4./install-css.sh, it is as if I am doing it for the first time.  I am using the default dvd player and not VLC.  Thanks in advance.  Scott

sudo apt-get install libdvdread4
[LIST]
[*]Then open a terminal window and execute: 
[/LIST]

sudo /usr/share/doc/libdvdread4/install-css.sh
[LIST]
[*]Rebooting may be necessary.
[/LIST]

---

### Post by Vontux on 2013-05-30
> **wsfield99 said:**
> Hi,

Here's a puzzler.  I am running Ubuntu 12.04 in a VM Virtual Box on a Windows 8 machine.  I am trying play encrypted dvds (which I am able to do with no problem on my other Ubuntu setups) but I've encountered an interesting issue.  I have the restricted packages installed as well as libdvdread4 but when I reboot after executing sudo /urs/share/doc/libdvdread4/install-css.sh, it does not take.  If I open the terminal and execute sudo /usr/share/doc/libdvdread4./install-css.sh, it is as if I am doing it for the first time.  I am using the default dvd player and not VLC.  Thanks in advance.  Scott

sudo apt-get install libdvdread4
[LIST]
[*]Then open a terminal window and execute: 
[/LIST]

sudo /usr/share/doc/libdvdread4/install-css.sh
[LIST]
[*]Rebooting may be necessary.
[/LIST]

A few questions, what is the model of your computer, is it one that came with windows 8? How does Windows 8 handle playing restricted dvds on this computer? Could you try attached a thumb drive to this computer, installing ubuntu on said thumb drive and see how that does with playing restricted dvds on this computer?

---

### Post by wsfield99 on 2013-06-18
I have an HP Envy with AMD processors.  It came with windows 8 pro installed.  I don't have a problem playing restricted dvds when running widows 8.  I tried installing Ubuntu on a thumb drive, however windows 8 is configured in a way that does not allow me to boot into it.  I have two other machines with Ubuntu 12.04 installed.  I do not have any trouble playing most restricted formats.  The problem seems to be that for some reason when I run sudo /urs/share/doc/libdvdread4/install-css.sh it does not compile.  Thanks, Scott

scott@scott-VirtualBox:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2013-06-18 15:57:07--  [http://packages.medibuntu.org/dists/raring/free/binary-i386/Packages](http://packages.medibuntu.org/dists/raring/free/binary-i386/Packages)
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7927 (7.7K) [application/octet-stream]
Saving to: &#8216;/tmp/dvdcss-gjAnDL/Packages&#8217;

100%[======================================>] 7,927       --.-K/s   in 0.002s  

2013-06-18 15:57:08 (4.32 MB/s) - &#8216;/tmp/dvdcss-gjAnDL/Packages&#8217; saved [7927/7927]

--2013-06-18 15:57:08--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_i386.deb)
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 39684 (39K) [application/octet-stream]
Saving to: &#8216;/tmp/dvdcss-gjAnDL/libdvdcss.deb&#8217;

100%[======================================>] 39,684      87.6KB/s   in 0.4s   

2013-06-18 15:57:08 (87.6 KB/s) - &#8216;/tmp/dvdcss-gjAnDL/libdvdcss.deb&#8217; saved [39684/39684]

(Reading database ... 186093 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.12-0.0medibuntu1 (using .../dvdcss-gjAnDL/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.12-0.0medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
scott@scott-VirtualBox:~$

---

### Post by mc4man on 2013-06-18
> **wsfield99 said:**
>  The problem seems to be that for some reason when I run sudo /[COLOR="#FF0000"]urs[/COLOR]/share/doc/libdvdread4/install-css.sh it does not compile.  Thanks, Scott
You could open a terminal, copy & paste this in, post the complete terminal output if it 'fails' in some manner

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

or just copy & paste the complete code box in this thread, will only take a minute or so to complete
[http://ubuntuforums.org/showthread.php?t=2146227&p=12652448&viewfull=1#post12652448](http://ubuntuforums.org/showthread.php?t=2146227&p=12652448&viewfull=1#post12652448)

---

### Post by wsfield99 on 2013-06-18
I opened a terminal and pasted the above code.  It did not produce any output indicating a failure.  It just doesn't work.  I can play dvds that are not encrypted with no problem though.  I have done a number of google searchs and can not find any other examples of this particular issue.

---

### Post by wsfield99 on 2013-07-07
I have learned that Oracle VirtualBox does not play encrypted dvds.  I will mark this thread as solved.

---

### Post by gordintoronto on 2013-07-07
Have you installed the Virtualbox Extension Pack?

---

