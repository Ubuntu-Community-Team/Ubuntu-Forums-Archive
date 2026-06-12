---
title: "Lost sound after update"
date: 2010-08-08
forum: Multimedia Software
---

### Post by RickGB on 2010-08-08
I have had such good sucess with Ubuntu that this took me by surprise.  Last week after an update I was suddenly without sound in Karmic Koala.  Fortunately. I also have Lucid Lynx and the sound is OK there.  I really gave it a dedicated try but was unable to get any sound.  
Here is information that may help:

                                       [LEFT]rick@rick-desktop:~$ aplay -l[/LEFT]
    [LEFT]aplay: device_list:223: no soundcards found...[/LEFT]
        [LEFT]

rick@rick-desktop:~$ lspci | grep Audio[/LEFT]
    [LEFT]00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)[/LEFT]
        [LEFT]

rick@rick-desktop:~$ dmesg | grep Audio[/LEFT]
        [LEFT]

rick@rick-desktop:~$ lsmod | grep snd[/LEFT]
    [LEFT]snd_pcm_oss            37568  0 [/LEFT]
    [LEFT]snd_mixer_oss          16284  1 snd_pcm_oss[/LEFT]
    [LEFT]snd_pcm                76928  1 snd_pcm_oss[/LEFT]
    [LEFT]snd_seq_dummy           2752  0 [/LEFT]
    [LEFT]snd_page_alloc          9124  1 snd_pcm[/LEFT]
    [LEFT]snd_seq_oss            29184  0 [/LEFT]
    [LEFT]snd_seq_midi            6624  0 [/LEFT]
    [LEFT]snd_seq_midi_event      7036  2 snd_seq_oss,snd_seq_midi[/LEFT]
    [LEFT]snd_seq                50928  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event[/LEFT]
    [LEFT]snd_rawmidi            22432  1 snd_seq_midi[/LEFT]
    [LEFT]snd_timer              21412  2 snd_pcm,snd_seq[/LEFT]
    [LEFT]snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi[/LEFT]
    [LEFT]snd                    61988  10 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi,snd_timer,snd_seq_device[/LEFT]
    [LEFT]soundcore               7264  1 snd[/LEFT]
    [LEFT]rick@rick-desktop:~$ [/LEFT]
       
  
If anyone knows how to get my sound going I will be most greatful.  I'm not sure but it seems to me that the UPDATE trashed my proprietary sound drivers, but that's just a guess.

---

### Post by lidex on 2010-08-08
First remove conflicting/old config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**
Now re-install alsa:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

---

### Post by RickGB on 2010-08-09
Many thanks to you "lidex", both for your prompt reply and your thorough instructions.  Unfortunately I seem to still be without sound.  Here is the response of the Terminal to the inputs that were given:

                                           [LEFT][/LEFT]
    [LEFT]rick@rick-desktop:~$ rm -r ~/.pulse ~/.asound* [/LEFT]
    [LEFT]rm: cannot remove `/home/rick/.asound*': No such file or directory[/LEFT]
    [LEFT]

rick@rick-desktop:~$ sudo rm /etc/asound.conf[/LEFT]
    [LEFT][sudo] password for rick: [/LEFT]
    [LEFT]rm: cannot remove `/etc/asound.conf': No such file or directory[/LEFT]
    [LEFT]

rick@rick-desktop:~$ [/LEFT]
    [LEFT][/LEFT]
    [LEFT]

rick@rick-desktop:~$ sudo apt-get update[/LEFT]
    [LEFT]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg[/LEFT]
    [LEFT]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US[/LEFT]
    [LEFT]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release[/LEFT]
    [LEFT]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages[/LEFT]
    [LEFT]Reading package lists... Done[/LEFT]
    [LEFT][/LEFT]
    [LEFT]

rick@rick-desktop:~$ sudo apt-get purge linux-sound-base alsa-base alsa-utils[/LEFT]
    [LEFT]Reading package lists... Done[/LEFT]
    [LEFT]Building dependency tree       [/LEFT]
    [LEFT]Reading state information... Done[/LEFT]
    [LEFT]The following packages were automatically installed and are no longer required:[/LEFT]
    [LEFT]  libotr2 pidgin-data[/LEFT]
    [LEFT]Use 'apt-get autoremove' to remove them.[/LEFT]
    [LEFT]The following packages will be REMOVED:[/LEFT]
    [LEFT]  alsa-base* alsa-utils* asoundconf-gtk* linux-sound-base* ubuntu-desktop*[/LEFT]
    [LEFT]0 upgraded, 0 newly installed, 5 to remove and 1 not upgraded.[/LEFT]
    [LEFT]After this operation, 2,728kB disk space will be freed.[/LEFT]
    [LEFT]Do you want to continue [Y/n]? [/LEFT]
    [LEFT](Reading database ... 221551 files and directories currently installed.)[/LEFT]
    [LEFT]Removing ubuntu-desktop ...[/LEFT]
    [LEFT]Removing alsa-base ...[/LEFT]
    [LEFT]Purging configuration files for alsa-base ...[/LEFT]
    [LEFT]Removing asoundconf-gtk ...[/LEFT]
    [LEFT]Removing alsa-utils ...[/LEFT]
    [LEFT]Purging configuration files for alsa-utils ...[/LEFT]
    [LEFT]Removing linux-sound-base ...[/LEFT]
    [LEFT]Purging configuration files for linux-sound-base ...[/LEFT]
    [LEFT]Processing triggers for desktop-file-utils ...[/LEFT]
    [LEFT]Processing triggers for man-db ...[/LEFT]
    [LEFT]Processing triggers for ureadahead ...[/LEFT]
    [LEFT]ureadahead will be reprofiled on next reboot[/LEFT]
    [LEFT][/LEFT]
    [LEFT]

rick@rick-desktop:~$ sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop[/LEFT]
    [LEFT]Reading package lists... Done[/LEFT]
    [LEFT]Building dependency tree       [/LEFT]
    [LEFT]Reading state information... Done[/LEFT]
    [LEFT]E: Couldn't find package linux-sound-base[/LEFT]
    [LEFT][/LEFT]
    [LEFT]rick@rick-desktop:~$ [/LEFT]
   
  
I hope that this will help in further tracking the problem.  Again many thanks.

---

### Post by lidex on 2010-08-09
Was that all of the output? Did the re-install complete? This is not good:
```
E: Couldn't find package linux-sound-base
```

Why are you using a PPA and do you have ubuntu repositories enabled?

---

### Post by RickGB on 2010-08-10
Thank you again for staying with me.  I do most graciously appreciate it, as I believe I know just about enough of what I am doing to get myself into much difficulty.
 First of all, I did check to see if I had all the appropriate repositories turned on.  This is what I found by searching for Ubuntu Repositories in Synaptic Package Manager. In checking The Repository in Synaptic, I found the switches turned off.  I'm not sure how this happened but now thay have been turned on and the PPA switch has been turned off, so here is a replay of the original instructions:
  
rick@rick-desktop:~$ rm -r ~/.pulse ~/.asound*  
 rm: cannot remove `/home/rick/.asound*': No such file or directory
  
rick@rick-desktop:~$ sudo rm /etc/asound.conf
 [sudo] password for rick:  
 rm: cannot remove `/etc/asound.conf': No such file or directory
  
rick@rick-desktop:~$ sudo apt-get update
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US
 Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
 Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
 Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release
 Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
 Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
 Reading package lists... Done
  
rick@rick-desktop:~$ sudo apt-get purge linux-sound-base alsa-base alsa-utils
 Reading package lists... Done
 Building dependency tree       
 Reading state information... Done
 Package linux-sound-base is not installed, so not removed
 Package alsa-base is not installed, so not removed
 Package alsa-utils is not installed, so not removed
 The following packages were automatically installed and are no longer required:
  libotr2 pidgin-data
 Use 'apt-get autoremove' to remove them.
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
  
rick@rick-desktop:~$ sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
 Reading package lists... Done
 Building dependency tree       
 Reading state information... Done
 gdm is already the newest version.
 The following packages were automatically installed and are no longer required:
  libotr2 pidgin-data
 Use 'apt-get autoremove' to remove them.
 The following extra packages will be installed:
  f-spot rhythmbox
 Suggested packages:
  apmd alsa-oss oss-compat python-coherence
 Recommended packages:
  empathy
 The following NEW packages will be installed:
  alsa-base alsa-utils f-spot linux-sound-base rhythmbox ubuntu-desktop
 0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
 Need to get 4,462kB of archives.
 After this operation, 27.3MB of additional disk space will be used.
 Do you want to continue [Y/n]?  
 Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main linux-sound-base 1.0.20+dfsg-1ubuntu5 [32.8kB]
 Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main alsa-base 1.0.20+dfsg-1ubuntu5 [270kB]
 Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main alsa-utils 1.0.20-2ubuntu6 [1,079kB]
 Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main f-spot 0.6.1.3-2 [1,437kB]         
 Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main rhythmbox 0.12.5-0ubuntu4 [1,613kB]
 Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main ubuntu-desktop 1.175 [30.6kB]      
 Fetched 4,462kB in 36s (121kB/s)                                               
 Preconfiguring packages ...
 Selecting previously deselected package linux-sound-base.
 (Reading database ... 221427 files and directories currently installed.)
 Unpacking linux-sound-base (from .../linux-sound-base_1.0.20+dfsg-1ubuntu5_all.deb) ...
 Selecting previously deselected package alsa-base.
 Unpacking alsa-base (from .../alsa-base_1.0.20+dfsg-1ubuntu5_all.deb) ...
 Selecting previously deselected package alsa-utils.
 Unpacking alsa-utils (from .../alsa-utils_1.0.20-2ubuntu6_i386.deb) ...
 Selecting previously deselected package f-spot.
 Unpacking f-spot (from .../f-spot_0.6.1.3-2_i386.deb) ...
 Selecting previously deselected package rhythmbox.
 Unpacking rhythmbox (from .../rhythmbox_0.12.5-0ubuntu4_i386.deb) ...
 Selecting previously deselected package ubuntu-desktop.
 Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.175_i386.deb) ...
 Processing triggers for man-db ...
 Processing triggers for ureadahead ...
 ureadahead will be reprofiled on next reboot
 Processing triggers for hicolor-icon-theme ...
 Processing triggers for desktop-file-utils ...
 Processing triggers for menu ...
 Setting up linux-sound-base (1.0.20+dfsg-1ubuntu5) ...
 Setting up alsa-base (1.0.20+dfsg-1ubuntu5) ...
 Setting up alsa-utils (1.0.20-2ubuntu6) ...
 Setting up f-spot (0.6.1.3-2) ...
 Setting up rhythmbox (0.12.5-0ubuntu4) ...
 Setting up ubuntu-desktop (1.175) ...
 Processing triggers for menu ...
 Processing triggers for libc-bin ...
 ldconfig deferred processing now taking place
  
rick@rick-desktop:~$


O yes, I put 'aplay -l' in the Terminal and got 'aplay: device_list:223: no soundcards found...' 
Does this help ?    Sound is still off, however.

---

### Post by simosx on 2010-08-10
lidex, I think we should ask the guy to do the alsa-info.sh thing.

Something keeps Alsa from detecting the hardware which is very low level.

---

### Post by lidex on 2010-08-11
> **simosx said:**
> lidex, I think we should ask the guy to do the alsa-info.sh thing.

Something keeps Alsa from detecting the hardware which is very low level.

Yeah. I was hoping for an easy fix.

*RickGB:*
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by RickGB on 2010-08-11
Alsa analysis Uploaded

rick@rick-desktop:~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh 
--2010-08-11 08:31:51--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) 
Resolving [www.alsa-project.org](www.alsa-project.org)... 212.20.107.51 
Connecting to [www.alsa-project.org|212.20.107.51|:80](www.alsa-project.org|212.20.107.51|:80)... connected. 
HTTP request sent, awaiting response... 302 Found 
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following] 
--2010-08-11 08:31:53--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) 
Resolving git.alsa-project.org... 212.20.107.51 
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80). 
HTTP request sent, awaiting response... 200 OK 
Length: unspecified [text/plain] 
Saving to: `alsa-info.sh' 
 
    [   <=>                                 ] 27,026      54.7K/s   in 0.5s     
 
2010-08-11 08:31:54 (54.7 KB/s) - `alsa-info.sh' saved [27026] 
 
ALSA Information Script v 0.4.59 
-------------------------------- 
 
This script visits the following commands/files to collect diagnostic 
information about your ALSA installation and sound related hardware. 
 
  dmesg 
  lspci 
  lsmod 
  aplay 
  amixer 
  alsactl 
  /proc/asound/ 
  /sys/class/sound/ 
  ~/.asoundrc (etc.) 
 
See 'alsa-info.sh --help' for command line options. 
 
/sbin/alsactl: save_state:1502: No soundcards found... 
cat: /tmp/alsa-info.969KUze9Jj/alsactl.tmp: No such file or directory 
Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] :  
 
 
Your ALSA information is in /tmp/alsa-info.txt.eOflHTLjdQ 
 
rick@rick-desktop:~$  

  	 	 	 	 	 	  I followed the given instruction in this latest exchange.  It seems as though the upload option and the output link were all included in the Terminal command.  I am concerned to know if the alsa-info-script reached the proper place.  Thanks much.
 

 Perhaps it may be of some interest to you as to how I reacted to some things I encountered in these exchanges on the Forum.
 

 First, on the original set of instructions you will notice that I did not respond to the UPGRADE as I did with the UPDATE.  The reason: I did not understand that the UPGRADE that you had in mind was for Alsa.  My concern was that this would upgrade my release from Karmic Koala to perhaps Lucid Lynx and this I did not want to happen as I already have Lucid on another partition.  While I am explaining this I might also share that I want to get Koala sound the way it was because, as a matter of fact, Koala runs more smoothly and I feel more comfortable with it than I do with Lucid.  I'm sure in time I will come to feel somewhat the same about Lucid as I've noticed that releases, like good wine (good updates), seem to improve with age.
 

 The other point of interest to you may be why I seemed to ignore the list at the bottom of your latest instructions.  (Alsa Upgrade Script | Boot Info Script | Compiz-Check | Pulse Audio).  To be truthful they went unnoticed because they, at first, seemed to be just a set of general topics of information being dealt with here.  It was not until I clicked on one that I realized that these were information gathering scripts and that you needed these pieces to continue helping me.  I can put the result of these up on the Forum if you wish, however, the Boot Info Script tallies out to around 39 pages.  Please advise.
 

 I did get Alsa-Upgrade-1.0.23-2.tar and also alsa-info.tar.  I am of necessity going carefully with this as there is much to digest on the Alsa upgrade page.  I find that when I go too quickly, I end up regretting it.
 I'm sure you understand.
 

 Thanks again for all the attention.  I assure you that it is most deeply appreciated. (Windows was never like this !)

---

### Post by lidex on 2010-08-11
If you haven't rebooted, the alsa-info script output may still be in your /tmp folder.
> Your ALSA information is in /tmp/alsa-info.txt.eOflHTLjdQ 
Don't need boot info.

Note also that when terminal asks for input, the upper-case option is the default when you hit the enter key.
> Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : 
To choose the non-default option you would simply type 'y' minus the quotes and press enter.

---

### Post by RickGB on 2010-08-12
SUCCESS – I have sound !
 

 rick@rick-desktop:~$ cat /proc/asound/version 
 Advanced Linux Sound Architecture Driver Version 1.0.23. 
 Compiled on Aug 12 2010 for kernel 2.6.31-22-generic (SMP). 
 rick@rick-desktop:~$ aplay -l 
 **** List of PLAYBACK Hardware Devices **** 
 card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235] 
   Subdevices: 4/4 
   Subdevice #0: subdevice #0 
   Subdevice #1: subdevice #1 
   Subdevice #2: subdevice #2 
   Subdevice #3: subdevice #3 
 card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235] 
   Subdevices: 1/1 
   Subdevice #0: subdevice #0 
 rick@rick-desktop:~$  
 

 After finally running the Alsa Script, I HAVE SOUND.  What a great piece of Fixware this script is.  I could not believe my eyes as I watched the entire script being opened and installed and then checked right in front of my eyes.  All I can say is “WOW” !   
 

 I did try to produce the logs but since I had already restarted, I lost track of the procedure.  If they need to be recovered I will need to know how.
 

 Again I cannot begin to express how grateful I am to you for all your considerations and help.  This is the very thing that makes Ubuntu head and shoulders  above any other Operating System.  Thank you again.

---

### Post by lidex on 2010-08-13
Good news. Please mark the thread solved using 'Thread Tools' up top.

---

