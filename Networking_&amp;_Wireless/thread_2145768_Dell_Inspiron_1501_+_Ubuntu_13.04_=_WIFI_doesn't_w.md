---
title: "Dell Inspiron 1501 + Ubuntu 13.04 = WIFI doesn't work"
date: 2013-05-16
forum: Networking &amp; Wireless
---

### Post by StephenWin on 2013-05-16
Hi,
I have a fresh install of Ubuntu 13.04 on my Dell Inspiron 1501 laptop and the WIFI doesn't work.
While connected to the Internet by a cable, late last night I just installed Ubuntu onto my Dell laptop. (Prior to this I had been using Windows Vista for 4 or 5 years.)
The WIFI isn't working, so I've been searching the Internet for who to get the WIFI working. Along the way I found this thread:[SIZE=2][ Broadcom BCM4311, Ubuntu 12.04 / 13.04]("http://ubuntuforums.org/showthread.php?t=1997880")[/SIZE]. Josh Rabbitt also had a Dell Inspiron 1501 as I do with a similar problem.

I saw that chil555 had give these instructions
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```

So I entered that code into my Terminal, and this was the outcome:

> 
stephen@stephen-Inspiron-1501:~$ sudo apt-get remove --purge bcmwl-kernel-source[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 23 not upgraded.
After this operation, 3,661 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 157292 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-19-generic
stephen@stephen-Inspiron-1501:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
The following NEW packages will be installed:
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 23 not upgraded.
Need to get 3,943 kB of archives.
After this operation, 8,982 kB of additional disk space will be used.
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/multiverse linux-firmware-nonfree all 1.14ubuntu1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-11 - System error)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-11 - System error)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


What should I do now to get my WIFI working? I now realize that I need to install a driver. Can anyone help me?
Best Wishes,
Stephen

---

### Post by Hadaka on 2013-05-16
Hi, please do..
```
sudo apt-get autoremove'
sudo apt-get update
sudo modprobe b43
```
does the wireless work now?

---

### Post by StephenWin on 2013-05-16
Hi, 
Before I received your response I retried 
> sudo apt-get install linux-firmware-nonfree
and got this:

> stephen@stephen-Inspiron-1501:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
The following NEW packages will be installed:
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 23 not upgraded.
Need to get 3,943 kB of archives.
After this operation, 8,982 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/multiverse linux-firmware-nonfree all 1.14ubuntu1 [3,943 kB]
Fetched 3,943 kB in 4s (813 kB/s)                   
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 157225 files and directories currently installed.)
Unpacking linux-firmware-nonfree (from .../linux-firmware-nonfree_1.14ubuntu1_all.deb) ...
Setting up linux-firmware-nonfree (1.14ubuntu1) ...


I had not got that before. (I think that I had a defective cord, which I've replaced.)

After I read your message I entered your code. Here is the output of that:

> stephen@stephen-Inspiron-1501:~$ sudo apt-get autoremove'
> 
> 
> ^C
stephen@stephen-Inspiron-1501:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg [933 B]      
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release.gpg [933 B]          
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release [40.8 kB]             
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg [72 B]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release.gpg                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release [40.8 kB]    
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources [7,543 B]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Sources                       
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources [1,982 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Sources                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources [697 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Sources              
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages [30.8 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main i386 Packages                     
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted i386 Packages             
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages [6,940 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe i386 Packages                 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages [1,389 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Translation-en     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en       
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Sources [12.2 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Sources [14 B]   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_US            
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Sources [9,167 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Sources [697 B]  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                        
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main i386 Packages [38.5 kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted i386 Packages [14 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe i386 Packages [27.1 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse i386 Packages [1,389 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en [14.9 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Translation-en_US   
Fetched 237 kB in 9s (25.3 kB/s)                                               
Reading package lists... Done
stephen@stephen-Inspiron-1501:~$ sudo modprobe b43


The WIFI Still doesn't work.

Stephen

---

### Post by Hadaka on 2013-05-16
ok. let's take a look at a couple things...
please Copy and paste the following into a terminal..

```
lspci -nn | egrep '0200|0280'
lsmod
cat /etc/modules
rfkill list all

sudo apt-get autoremove
```
post back the results
thanks.
*Note I accidently added a charcter to sudo apt-get autoremove before
so please run again

---

### Post by StephenWin on 2013-05-16
Hi,
Here is a copy of the printout.

> stephen@stephen-Inspiron-1501:~$ lspci -nn | egrep '0200|0280'
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
stephen@stephen-Inspiron-1501:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
udf                    83786  1 
crc_itu_t              12627  1 udf
parport_pc             27504  0 
ppdev                  12817  0 
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202069  10 bnep,rfcomm
snd_hda_codec_idt      63896  1 
snd_hda_intel          38307  3 
snd_hda_codec         117580  2 snd_hda_codec_idt,snd_hda_intel
b43                   351918  0 
radeon                870822  3 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
joydev                 17097  0 
snd_seq_midi           13132  0 
bcma                   39645  1 b43
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              526519  1 b43
snd_rawmidi            25114  1 snd_seq_midi
ttm                    71289  1 radeon
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
kvm_amd                50336  0 
drm_kms_helper         47545  1 radeon
drm                   228750  5 ttm,drm_kms_helper,radeon
kvm                   376505  1 kvm_amd
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
i2c_algo_bit           13197  1 radeon
cfg80211              436177  2 b43,mac80211
snd                    56485  15 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12600  1 snd
psmouse                81038  0 
sp5100_tco             13447  0 
shpchp                 32129  0 
ext2                   63166  1 
dell_laptop            17161  0 
dell_wmi               12601  0 
ssb_hcd                12749  0 
serio_raw              13031  0 
sparse_keymap          13658  1 dell_wmi
dcdbas                 14021  1 dell_laptop
k8temp                 12842  0 
i2c_piix4              13066  0 
ati_agp                13177  0 
wmi                    18590  1 dell_wmi
mac_hid                13037  0 
video                  18894  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
b44                    31137  0 
sdhci_pci              18158  0 
sdhci                  31824  1 sdhci_pci
pata_atiixp            13058  1 
ssb                    50628  3 b43,b44,ssb_hcd
ahci                   25507  2 
libahci                26108  1 ahci
stephen@stephen-Inspiron-1501:~$ 
stephen@stephen-Inspiron-1501:~$ 
stephen@stephen-Inspiron-1501:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

loop
lp
stephen@stephen-Inspiron-1501:~$ rfkill list all
stephen@stephen-Inspiron-1501:~$ sudo apt-get autoremove
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dkms
0 upgraded, 0 newly installed, 1 to remove and 23 not upgraded.
After this operation, 348 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 157388 files and directories currently installed.)
Removing dkms ...
Processing triggers for man-db ...


Stephen

---

### Post by StephenWin on 2013-05-16
Hadaka,
I have an appointment so I have to leave and will be gone most of the day. I really appreciate your help and will have a look at this again when I get back.
Thanks a lot,
Best Wishes,
Stephen

---

### Post by Hadaka on 2013-05-16
ok, when you get back please do this..
Let's make sure things are up to date since its a new load
please do..
```
sudo apt-get upgrade
sudo modprobe -rfv dell_wmi
sudo apt-get install --reinstall linux-firmware-nonfree
sudo modprobe -rfv b43
sudo modprobe b43
```
thanks.

---

### Post by StephenWin on 2013-05-17
Hi Hadaka,
Thanks for helping me. I copied and pasted each line below individually into the terminal.

```


sudo apt-get upgrade
sudo modprobe -rfv dell_wmi
sudo apt-get install --reinstall linux-firmware-nonfree
sudo modprobe -rfv b43
```
All seemed to be going well. I was leaving all the text output on the terminal screen so that I could copy and paste it all at one here.
 
But then I pasted this bottom code into terminal
 > sudo modprobe b43


As the terminal was processing this command, I think it crashed, or something. Anyway the screen froze up and showed a bunch of lines of  numbers and text that didn't mean anything to me. [SIZE=3]**SEE BOTTOM OF MESSAGE: I attached a picture of the screen below**[/SIZE]. The computer was froze up and wouldn't do anything. So I rebooted the computer.

*Note, because of the freeze up or crash, I lost all the text of the output of those commands. I don't know if perhaps the terminal kept a log of all that or not.*

As the computer was loading back up this came on the screen:

> Ubuntu 13.04
.  .  .  . 

An error occurred while mounting /boot.
Press S to skip mounting or M for manual recovery

the first time I think that I pressed M and it came up with this screen:

> Filesystem check or mount failed.
A maintenance shell will be now be started.
CONTROL-D will terminate this shell and continue booting after re-trying
filesystems. Any further errors will be ignored
root@stephen-Inspiron-1501:~#

I think that the computer was unable to continue loading after this, so I rebooted.

Again the screen gave this message:
> Ubuntu 13.04
.  .  .  . 

An error occurred while mounting /boot.
Press S to skip mounting or M for manual recovery
This time I pressed S, and the OS continued loading and brought up the desktop. However the desktop was frozen with the mouse pointer arrow in the middle of the screen. I couldn't get anything to work, so I rebooted again.

This time it booted up quickly and went straight to the logon. After entering the password, it went quickly to the desktop. Again the desktop was frozen with the mouse arrow in the middle of the screen.

At this point, I'm thinking of just reinstalling Ubuntu so that it would be clean without those errors in it. I don't have anything on the hard drive so nothing would be lost. It wouldn't bother me to reinstall.

What do you think?

Best Wishes
Stephen

---

### Post by StephenWin on 2013-05-17
Hi Hadaka,
   I want to express my appreciation for how kind and helpful you have  been in my attempts to get my Dell Inspiron 1501 laptop WIFI working  with Ubuntu.
As a follow up, I reinstalled Ubuntu 13.04, but continued to have  problems staying connected to the internet even using the wired  connection. I don't know if it was something wrong with my computer, or Ubuntu, or what. After reinstalling Ubuntu I was going to retry the above  instructions, but couldn't connect to the Internet through the wired  connect.
 As an assocciated note, During the process of the last couple of days of  trying to get the wifi working I had tried three different cables to  connect to the Internet. On and off Ubuntu said it was connected and the  later it wasn't connected to the Internet. So, besides the other  problems I've mentioned above, trying to do the updates and other stuff  through a seemingly defective Internet connect added additional  challenges. I think that your fixed would have worked (and I would have  probably just used Ubuntu) if I hadn't of had these wired Internet  issues.

However, even though I like Ubuntu, I thought that I would try another  Linux Distribution. During my search I found this article:[SIZE=2] [Ubuntu Versus Mint: Which Linux Distro Is Better For Beginners?]("http://www.lifehacker.com.au/2013/04/ubuntu-versus-mint-which-linux-distro-is-better-for-beginners/")[/SIZE]  
 As I did more research I found this thread (which had a Dell 1501 laptop like mine, with a similar non-working WIFI issue): [http://www.linuxquestions.org/questions/linux-mint-84/mint-13-wireless-configuration-problem-947621/](http://www.linuxquestions.org/questions/linux-mint-84/mint-13-wireless-configuration-problem-947621/)  the solution in the message had a very similar fix as yours.I ended up installing Linux Mint 14. 

Well, to sum it up, after installing Linux Min 14 (KDE) on my Dell laptop, I ran the above fix (which was easy) and after a reboot, the wifi is working. I will see how this goes.
Again, Hadaka, thank you for all of your help.

Best Wishes,
Stephen

---

### Post by Hadaka on 2013-05-17
Glad to hear you are up and running, if you are
satisfied with the results,please take the time to
mark this thread solved
How to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

