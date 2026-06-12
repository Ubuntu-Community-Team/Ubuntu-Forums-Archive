---
title: "libdvdcss question"
date: 2016-05-30
forum: Multimedia Software
---

### Post by chris331 on 2016-05-30
Hi all, thank you for welcoming me into the Ubuntu community!  As a new member, I must say that I really do enjoy this OS =)

I am having difficulty using libdvdcss to watch Dvds on my Acer laptop.  I've installed **libdvdcss2** via Synaptic Package manager, as well as:

[B]libdvd-pkg
libdvdcss-dev
libdvdnav-dbg
libdvdnav-dev
libdvdnav-doc
libdvdnav4
libdvdread-dbg
libdvdread-dev
libdvdread4
[/B]
I am running Ubuntu 16.04 (Xenial), and although I love it's refreshing change from the vanilla Windows Oses I've used all my adult life, I am at a complete loss as to what to do now as far as watching movies from my DVD player.

I didn't want to bug you guys with this, because I've found numerous questions just like mine around the this, and other forums, and I didn't want to post a redundant question.
However, I'm beginning to think my problem is unique from the others.  I am new to the package system that Linux OSes employ, which may be a big part of this problem.  
I've used 'apt-get' to install, reinstall, clean, update, remove --purge, and reinstall again, to no avail..
I've downloaded numerous video players, including Xine, SMplayer, and others.  
The Ubuntu-Restricted-Extras and Ubuntu-Restricted-Addons have been installed and reinstalled. 

Please tell me what other information is needed to diagnose this situation properly and potentially fix it.  I'll readily supply it.

---

### Post by QDR06VV9 on 2016-05-30
> **chris331 said:**
> Hi all, thank you for welcoming me into the Ubuntu community!  As a new member, I must say that I really do enjoy this OS =)

I am having difficulty using libdvdcss to watch Dvds on my Acer laptop.  I've installed **libdvdcss2** via Synaptic Package manager, as well as:

[B]libdvd-pkg
libdvdcss-dev
libdvdnav-dbg
libdvdnav-dev
libdvdnav-doc
libdvdnav4
libdvdread-dbg
libdvdread-dev
libdvdread4
[/B]
I am running Ubuntu 16.04 (Xenial), and although I love it's refreshing change from the vanilla Windows Oses I've used all my adult life, I am at a complete loss as to what to do now as far as watching movies from my DVD player.

I didn't want to bug you guys with this, because I've found numerous questions just like mine around the this, and other forums, and I didn't want to post a redundant question.
However, I'm beginning to think my problem is unique from the others.  I am new to the package system that Linux OSes employ, which may be a big part of this problem.  
I've used 'apt-get' to install, reinstall, clean, update, remove --purge, and reinstall again, to no avail..
I've downloaded numerous video players, including Xine, SMplayer, and others.  
The Ubuntu-Restricted-Extras and Ubuntu-Restricted-Addons have been installed and reinstalled. 

Please tell me what other information is needed to diagnose this situation properly and potentially fix it.  I'll readily supply it.
Try this in the terminal.
```
sudo dpkg-reconfigure libdvd-pkg
```
And watch for any further prompts.
And if you are still unsuccessful **delete ~/.dvdcss **folder inside your Home Directory to see that you have to enable View Hidden Files.
You can do that by Opening Home or your user name and using Keyboard Combo of **"Ctrl+h"**

---

### Post by Bashing-om on 2016-05-30
chris331; Hello;

I have not seen 16.04 to this time, so I do not know that it is still required:
```

sudo /usr/share/doc/libdvdread4/install-css.sh

```
to propagate the proprietary codecs to the system.

[INDENT][INDENT]but hey
[INDENT][INDENT][INDENT]it could be
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris331 on 2016-05-30
> **runrickus said:**
> Try this in the terminal.
```
sudo dpkg-reconfigure libdvd-pkg
```
And watch for any further prompts.
And if you are still unsuccessful **delete ~/.dvdcss **folder inside your Home Directory to see that you have to enable View Hidden Files.
You can do that by Opening Home or your user name and using Keyboard Combo of **"Ctrl+h"**

Thank you so much for your swift reply -

This is the result from your first bit of advice:

```
aandk@aandk-Aspire-V3-731:~$ sudo dpkg-reconfigure libdvd-pkg
[sudo] password for aandk: (entered)
libdvd-pkg: guest package [libdvdcss2/1.4.0-1~local] is already installed.
```

Forgive my ignorance, but as I said I am new to the linux kernel and to Ubuntu:
What does it mean "guest package"?  
Is this a problem?
I'm now going to **delete ~/.dvdcss **folder inside my Home Directory.  Cheers

> **Bashing-om said:**
> chris331; Hello;

I have not seen 16.04 to this time, so I do not know that it is still required:
```

sudo /usr/share/doc/libdvdread4/install-css.sh

```
to propagate the proprietary codecs to the system.
[INDENT][INDENT]but hey[INDENT][INDENT][INDENT]it could be
[/INDENT]



Hello there;
I have seen this before in my hunt for solutions to my problem, and guess what?  I didn't check to see that inside my /usr/share/doc/libdvdread4 directory, I have no install-css.sh script!   Am I supposed to retrieve that from some other place? It didn't come with any package... where do I get it?
Thanks in advance!

---

### Post by QDR06VV9 on 2016-05-30
Now run this again after deleting that file i had suggested earlier.
```
sudo dpkg-reconfigure libdvd-pkg
```

---

### Post by chris331 on 2016-05-30
Ok I deleted the **~/.dvdcss **folder inside my Home directory, then I ran
```

aandk@aandk-Aspire-V3-731:~$ sudo dpkg-reconfigure libdvd-pkg
[sudo] password for aandk: (entered)
libdvd-pkg: guest package [libdvdcss2/1.4.0-1~local] is already installed.

```

Huh?  I just deleted it... don't get it.  Also I have to ask, what does it mean that it's a guest package?

---

### Post by Bashing-om on 2016-05-30
chris331; Well, well ..

The executable in question should have been a part of the libdvdread4 install.

Maybe re-install ?
```

sudo apt install --reinstall libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh

```
the " install-css.sh " is a command .. with the fore going the path to the command.
execute the command as given in terminal .

As to " libdvd-pkg " will have to leave that to runrickus to address as I do not have the package installed. I have no direct access to troubleshoot the issue.

[INDENT][INDENT]if I knew better
[INDENT][INDENT]I would say else
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris331 on 2016-05-30
Ok Bashing-om,
I reinstalled libdvdread4 and tried to execute the script, this is what I got:

```

aandk@aandk-Aspire-V3-731:~$ sudo apt install --reinstall libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 49.6 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 libdvdread4 amd64 5.0.3-1 [49.6 kB]
Fetched 49.6 kB in 0s (115 kB/s)       
(Reading database ... 385532 files and directories currently installed.)
Preparing to unpack .../libdvdread4_5.0.3-1_amd64.deb ...
Unpacking libdvdread4:amd64 (5.0.3-1) over (5.0.3-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up libdvdread4:amd64 (5.0.3-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
aandk@aandk-Aspire-V3-731:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
sudo: /usr/share/doc/libdvdread4/install-css.sh: command not found
aandk@aandk-Aspire-V3-731:~$ 



```

So .. is the executable just not part of the regular libdvdread4 install now??
Yikes

Runrickus: Are you still available?  I did as you asked, and gave the results a couple posts above.  Now what?
> **Bashing-om said:**
> chris331; Well, well ..

The executable in question should have been a part of the libdvdread4 install.

Maybe re-install ?
```

sudo apt install --reinstall libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh

```
the " install-css.sh " is a command .. with the fore going the path to the command.
execute the command as given in terminal .

As to " libdvd-pkg " will have to leave that to runrickus to address as I do not have the package installed. I have no direct access to troubleshoot the issue.[INDENT][INDENT]if I knew better[INDENT][INDENT]I would say else
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by QDR06VV9 on 2016-05-30
Chris have a look here [http://ubuntuforums.org/showthread.php?t=2312060](http://ubuntuforums.org/showthread.php?t=2312060)
It has gotten a bit more difficult for some on 16.04.

---

### Post by chris331 on 2016-05-30
Runrickus:
Yes I see that, thank you for your help, as well as well as this new link.  I will keep trying.
If and when I find a solution to my problem, should I post it here for others who are in the same boat as me and need the same assistance? 

> **runrickus said:**
> Chris have a look here [http://ubuntuforums.org/showthread.php?t=2312060](http://ubuntuforums.org/showthread.php?t=2312060)
It has gotten a bit more difficult for some on 16.04.

---

### Post by QDR06VV9 on 2016-05-30
> **chris331 said:**
> Runrickus:
Yes I see that, thank you for your help, as well as well as this new link.  I will keep trying.
If and when I find a solution to my problem, should I post it here for others who are in the same boat as me and need the same assistance?
If anything you did different from that link I would say Yes then post it here.
Keep us posted though and Good Luck.:)

---

### Post by Bashing-om on 2016-05-30
@runrickus; ole buddy .

To aid my thought process for 16.04 is the file " /usr/share/doc/libdvdread4/install-css.sh " no longer generated ?
Does it exist on your 16.04 install ?

[INDENT][INDENT]amazing how quick
[INDENT][INDENT][INDENT]we can get out-of-date
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2016-05-30
> **Bashing-om said:**
> @runrickus; ole buddy .

To aid my thought process for 16.04 is the file " /usr/share/doc/libdvdread4/install-css.sh " no longer generated ?
Does it exist on your 16.04 install ?
[INDENT][INDENT]amazing how quick[INDENT][INDENT][INDENT]we can get out-of-date
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

It was not for me during the Dev Cycle and just got carried over when I changed to Yakkety.
But from the Wiki Page [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
> Ubuntu 15.10 and newer
From Ubuntu 15.10 onwards, libdvd-pkg is available to ease the installation of libdvdcss.
    Install the libdvd-pkg package (no need to add third party repositories) via Synaptic or command line: 

```
sudo apt-get install libdvd-pkg
```
1.Follow libdvd-pkg's instructions to let it download, compile, and install libdvdcss.
But it has tripped a few users up.:D

---

### Post by mc4man on 2016-05-30
> **Bashing-om said:**
> @runrickus; ole buddy .

To aid my thought process for 16.04 is the file " /usr/share/doc/libdvdread4/install-css.sh " no longer generated ?
Does it exist on your 16.04 install ?

[INDENT][INDENT]amazing how quick
[INDENT][INDENT][INDENT]we can get out-of-date
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
No, it is no longer part of libdvdread, users should use libdvd-pkg & the run the command as mentioned after it is installed.

---

### Post by chris331 on 2016-05-30
Ok, runrickus and bash-om, thank you both for your help.

Runrickus, I followed the link, and still cannot run movies from the dvd player. 
I did, however, get some code out of the deal that maybe you can use to help me??
First I removed and reinstalled libdvd-pkg:

```

aandk@aandk-Aspire-V3-731:~$ sudo apt-get remove libdvd-pkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libdvd-pkg libdvdcss-dev libdvdcss2
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 165 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 385567 files and directories currently installed.)
Removing libdvdcss-dev:amd64 (1.4.0-1~local) ...
Removing libdvdcss2:amd64 (1.4.0-1~local) ...
Removing libdvd-pkg (1.4.0-1-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...

```

Here I am reinstalling:
```

aandk@aandk-Aspire-V3-731:~$ sudo apt-get install libdvd-pkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libdvd-pkg
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.9 kB of archives.
After this operation, 78.8 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/multiverse amd64 libdvd-pkg all 1.4.0-1-1 [14.9 kB]
Fetched 14.9 kB in 0s (55.6 kB/s)     
Preconfiguring packages ...
Selecting previously unselected package libdvd-pkg.
(Reading database ... 385522 files and directories currently installed.)
Preparing to unpack .../libdvd-pkg_1.4.0-1-1_all.deb ...
Unpacking libdvd-pkg (1.4.0-1-1) ...
Setting up libdvd-pkg (1.4.0-1-1) ...
libdvd-pkg: dpkg database is locked. You may need to use command "sudo dpkg-reconfigure libdvd-pkg".
libdvd-pkg: Building and installation of package(s) [libdvdcss2 libdvdcss-dev] postponed till after next APT operation.

```

and here I am using sudo dpkg-reconfigure to install the rest of the packages:

```

aandk@aandk-Aspire-V3-731:~$ sudo dpkg-reconfigure libdvd-pkg
libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.0.orig.tar.bz2: OK
libdvd-pkg: Unpacking and configuring...
libdvd-pkg: Building the package... (it may take a while)
libdvd-pkg: Build log will be saved to /usr/src/libdvd-pkg/libdvdcss2_1.4.0-1~local_amd64.build
Current: = cap_chown,cap_dac_override,cap_dac_read_search,cap_fowner,cap_fsetid,cap_kill,cap_setgid,cap_setuid,cap_setpcap,cap_linux_immutable,cap_net_bind_service,cap_net_broadcast,cap_net_admin,cap_net_raw,cap_ipc_lock,cap_ipc_owner,cap_sys_module,cap_sys_rawio,cap_sys_chroot,cap_sys_ptrace,cap_sys_pacct,cap_sys_admin,cap_sys_boot,cap_sys_nice,cap_sys_resource,cap_sys_time,cap_sys_tty_config,cap_mknod,cap_lease,cap_audit_write,cap_audit_control,cap_setfcap,cap_mac_override,cap_mac_admin,cap_syslog,cap_wake_alarm,cap_block_suspend,37+ep
Bounding set =cap_chown,cap_dac_override,cap_fowner,cap_wake_alarm,cap_block_suspend,37
Securebits: 024/0x14/5'b10100
 secure-noroot: no (unlocked)
 secure-no-suid-fixup: yes (unlocked)
 secure-keep-caps: yes (unlocked)
uid=0(root)
gid=0(root)
groups=0(root)
libdvd-pkg: Installing...
Selecting previously unselected package libdvdcss-dev:amd64.
(Reading database ... 385552 files and directories currently installed.)
Preparing to unpack .../libdvdcss-dev_1.4.0-1~local_amd64.deb ...
Unpacking libdvdcss-dev:amd64 (1.4.0-1~local) ...
Selecting previously unselected package libdvdcss2:amd64.
Preparing to unpack .../libdvdcss2_1.4.0-1~local_amd64.deb ...
Unpacking libdvdcss2:amd64 (1.4.0-1~local) ...
Setting up libdvdcss2:amd64 (1.4.0-1~local) ...
Setting up libdvdcss-dev:amd64 (1.4.0-1~local) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...

```

Success --

Now I am running Vlc at command-line level to show you what happens when I try to run a movie from the dvd player:

```

aandk@aandk-Aspire-V3-731:~$ vlc
VLC media player 2.2.2 Weatherwax (revision 2.2.2-0-g6259d80)
[000000000120c148] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 5.0.3
libdvdnav: DVD Title: HERO
libdvdnav: DVD Serial Number: 31528311
libdvdnav: DVD Title (Alternative): 
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4


libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient


libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000137
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000028a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0000028a)!!
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002d1a7a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002d1a7a)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002d282b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00337666
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x00337666)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003b192f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003b92bc
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x003b92bc)!!
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 3
[00007f42fc0009b8] core input error: ES_OUT_RESET_PCR called
[00007f42fc0009b8] core input error: ES_OUT_RESET_PCR called
[00007f42fc0009b8] core input error: ES_OUT_RESET_PCR called
[00007f42fc0009b8] core input error: ES_OUT_RESET_PCR called




```

Does this last bit of code with the errors tell you guys anything?  What should I do?

---

### Post by Bashing-om on 2016-05-30
et al: :)

Think'n ^^ suitably reset ..

[INDENT][INDENT]thanks to all
[/INDENT][/INDENT]

---

### Post by mc4man on 2016-05-30
> **chris331 said:**
> Hi all, thank you for welcoming me into the Ubuntu community!  As a new member, I must say that I really do enjoy this OS =)

I am having difficulty using libdvdcss to watch Dvds on my Acer laptop.  
Maybe post some info on your drive - 
Insert a dvd, let drive settle, close any pop up.
Then run this, copy & post the complete  section of  *-cdrom
```
sudo lshw -c disk
```

---

### Post by chris331 on 2016-05-30
Hi mc4man, 
Ok, I inserted a movie dvd, got no pop-ups, waited, 
ran this:
```

aandk@aandk-Aspire-V3-731:~$ sudo lshw -c disk
[sudo] password for aandk: (entered)

```

and got this from the section of *-cdrom:

```

*-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ8C0
       vendor: MATSHITA
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       logical name: /media/aandk/HERO
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8 state=mounted status=ready



```
> **mc4man said:**
> Maybe post some info on your drive - 
Insert a dvd, let drive settle, close any pop up.
Then run this, copy & post the complete  section of  *-cdrom
```
sudo lshw -c disk
```

---

### Post by mc4man on 2016-05-30
A matshita dvd drive must have a region set & will only play dvd's from the set region. There is no workaround to that.
So 1st. ck. if a region is set - 
Install regionset
```
sudo apt install regionset
```
After it's installed,  with any disk in the drive (current dvd will suffice) run this command. For the moment answer no (n), then post the complete result along with what country you live in.
```
regionset
```

---

### Post by chris331 on 2016-05-30
> **mc4man said:**
> A matshita dvd drive must have a region set & will only play dvd's from the set region. There is no workaround to that.
So 1st. ck. if a region is set - 
Install regionset
```
sudo apt install regionset
```
After it's installed,  with any disk in the drive (current dvd will suffice) run this command. For the moment answer no (n), then post the complete result along with what country you live in.
```
regionset
```


You sir, are pure genius!  Thank yous to all 3 of you for getting my OS to play dvds!  I've been working on this for 2 days and it finally works!
Cheers!!!

=)

---

### Post by chris331 on 2016-05-30
For those that live in the U.S. or canada and using a dvd drive like mine that requires a region to be set, and want to watch dvds from your area, make sure you're root and use regionset to set your region to 1.

---

### Post by mc4man on 2016-05-30
Just remember that a dvd drive can only have the region set 5 times before it forever locks at the last setting.
So matshita owners really can only play disks from one region whereas owners of almost all other dvd drives can play from any region as open source players don't enforce region coding.
Matshita (panasonic??) decided to enforce regions at the hardware level even though there was/is no requirement for hardware to do so.

---

### Post by QDR06VV9 on 2016-05-30
Hey that is Great:D
Now if you are happy with the solution would you be as kind as to mark this as Solved to help others.
How to mark solved [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
Kind Regards

---

### Post by mc4man on 2016-05-30
While it probably doesn't matter regionset works without being root.

---

### Post by chris331 on 2016-05-30
> **mc4man said:**
> Just remember that a dvd drive can only have the region set 5 times before it forever locks at the last setting.
So matshita owners really can only play disks from one region whereas owners of almost all other dvd drives can play from any region as open source players don't enforce region coding.
Matshita (panasonic??) decided to enforce regions at the hardware level even though there was/is no requirement for hardware to do so.
 

Wow.. any idea why Mashita did that?  If this is getting too off-topic just send me a link for further reading on this subject, if you know of one.
Thanks

---

