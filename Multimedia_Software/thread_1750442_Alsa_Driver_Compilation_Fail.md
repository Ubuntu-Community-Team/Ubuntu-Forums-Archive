---
title: "Alsa Driver Compilation Fail"
date: 2011-05-05
forum: Multimedia Software
---

### Post by mschlutt on 2011-05-05
Greetings,

Relative noob regarding ubuntu here.  I'm trying to get my sound to work by following the sticky "Comprehensive Sound Problems Solutions Guide".  After not finding my soundcard, and not having the correct module loaded, I tried getting the Alsa Modules from a fresh kernel.  After my soundcard was still not detected, I followed the guide to do a ALSA driver Compilation, using the module-assistant.  The progress bar gets to 47% and then it halts progress.  I look at the logfile and near the end I get this:

In file included from include/linux/pci.h:58:0,                             
 &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,   
 &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.c:1:      
 &#9474; /usr/src/modules/alsa-driver/include/linux/pci_ids.h:2:58: fatal error:     
 &#9474; @CONFIG_SND_KERNELSRC@/include/linux/pci_ids.h: No such file or directory   
 &#9474; compilation terminated.                                                     
 &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1        
 &#9474; make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2                   
 &#9474; make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2                 
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'        
 &#9474; make[2]: *** [compile] Error 2                                              
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                   
 &#9474; make[1]: *** [build-stamp] Error 2                                          
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                   
 &#9474; make: *** [kdist_image] Error 2 

My linux version is natty-narwhal.  Thanks for any help or suggestions you can provide.

---

### Post by lidex on 2011-05-05
I don't know why they still keep that info up. There are much better ways to upgrade alsa. Let's have a look at your problem. Can you describe the problem and provide your alsa-info.

Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by mschlutt on 2011-05-06
First, thanks for helping out lidex.  I really appreciate it.

So, I issued the command you recommended.  I'm pasting the output here, and I'm uploading the alsa-info.txt file that was created.

One thing that puzzles me is that I'm seeing /proc/asound doesn't seem to exist.  

~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2011-05-06 19:13:55--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org]("http://www.alsa-project.org")... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80]("http://www.alsa-project.org%7C77.48.224.243%7C:80")... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2011-05-06 19:13:58--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80]("http://www.alsa-project.org:80").
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [   <=>                                 ] 27,247      53.4K/s   in 0.5s    

2011-05-06 19:14:00 (53.4 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
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

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory
/sbin/alsactl: save_state:1519: No soundcards found...
cat: /tmp/alsa-info.g58ygFOPZv/alsactl.tmp: No such file or directory
Automatically upload ALSA information to [www.alsa-project.org?]("http://www.alsa-project.org?") [y/N] : N


Your ALSA information is in /tmp/alsa-info.txt.TQvTrwonY0

---

### Post by Yellow Pasque on 2011-05-06
So you got some alsa stuff compiled and installed, but the kernel module didn't build (hence no /proc/asound). You should just use the alsa upgrade script in lidex's sig and then run alsa-info again if that doesnt work.

---

### Post by lidex on 2011-05-06
Your alsa install is borked. Try re-installing:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by mschlutt on 2011-05-06
So, I ran your command to re-install alsa and I rebooted.  Still no sound, so I then ran the original wget command that was recommended.  I've pasted the output below, and I've also attached the ALSA info.  I really appreciate you all working with me on trying to fix this.  Thank you.


schlutt@schlutt-desktop:~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2011-05-06 20:16:14--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2011-05-06 20:16:15--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [   <=>                                 ] 27,247      53.7K/s   in 0.5s    

2011-05-06 20:16:16 (53.7 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
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

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory
/sbin/alsactl: save_state:1519: No soundcards found...
cat: /tmp/alsa-info.ZsIfsF5m58/alsactl.tmp: No such file or directory
Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : N


Your ALSA information is in /tmp/alsa-info.txt.Xg4VCAyceD

schlutt@schlutt-desktop:~$

---

### Post by lidex on 2011-05-06
@Temüjin
I didn't see you sneak in there - had to run out for some beverages. So a re-install is not enough to rebuild the module then?

@mschlutt
Follow Temüjin's advice and use the upgrade script he maintains. Use the link in my sig.

---

### Post by mschlutt on 2011-05-07
Hmmmm.   I used the set of scripts from the link in lidex's signature.  (AlsaUpgrade-1.0.24-2.sh -d, then -c, then -i, reboot).  Still no luck.  I type aplay -l and it still says no soundcards found.  Also, /proc/asound doesn't exist either.  This seems really strange.  Any more suggestions?  Any other logfiles you want to see or other diagnostics I can run?

Thanks for helping me.

---

### Post by Yellow Pasque on 2011-05-07
I would be interested to see the log from the -i step, to see if the kernel module (and other stuff) actually installed successfully.

---

### Post by mschlutt on 2011-05-07
Attached is the log from the -i option.  Thanks for your help!

---

### Post by mschlutt on 2011-05-10
Anyone have any suggestions?  Should I try to just reinstall Natty Narwhal?  Help(!) please.

Thanks.

---

### Post by lidex on 2011-05-10
```
sudo apt-get install --reinstall linux-headers-2.6.38-8-generic linux-image-2.6.38-8-generic && sudo dpkg-reconfigure linux-headers-2.6.38-8-generic linux-image-2.6.38-8-generic
```
Try that then reboot.

---

### Post by bincue on 2011-05-10
I have the same sound card
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
I have sound but only after I Alt+F2 type xterm then enter
then type 
```
sudo alsa force-reload
```
type a password and
then go to [http://last.fm](http://last.fm) to test sound.

I found a possible workaround for after reboot... [http://ubuntuforums.org/showpost.php?p=7142331&postcount=17](http://ubuntuforums.org/showpost.php?p=7142331&postcount=17)

good luck!

---

### Post by mschlutt on 2011-05-11
HI - thanks for your help, but still no luck.  I tried reloading linux-headeer-2.6.38-8-generic.  Still no sound.  Then I re-ran the scripts from the link in lidex's sig.  I have attached the -i output here.  Also, I ran sudo alsa force-reload and got this:

schlutt@schlutt-desktop:~/temp1$ sudo alsa force-reload
[sudo] password for schlutt: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /media/069a76d8-1bc2-4545-a864-e43c51fb8145_/home/schlutt/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /media/069a76d8-1bc2-4545-a864-e43c51fb8145_/home/schlutt/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
schlutt@schlutt-desktop:~/temp1$ 

Any other suggestions?  I feel like my system doesn't know where to look to make alsa work...

I had sound before upgrading to natty, however, I would sometimes have to run sudo alsa force-reload to get it to work.  Since th natty upgrade, I get nothing.  ?????  Other suggestions?  Please?

---

### Post by Yellow Pasque on 2011-05-11
The upgrade script's output says it was successful, so that's not helping in the diagnosis :\

---

### Post by lidex on 2011-05-11
So you re-installed and reconfigured both the kernel image and the headers and rebooted, correct? If you have done all these things run the alsa-info script again please.
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by mschlutt on 2011-05-11
Thanks for responding.  Yes, I re-installed and reconfigured the headers and image using the command you gave earlier.  I rebooted.  Then I applied the scripts from the link in your sig.  I ran the most recent command you recommended and I've attached the results to this response.  No ALSA modules loaded.  Hmmm.  Could this have anything to do with the fact that my home directory is on a different partition (which is mounted through /media) than where linux is loaded?  Maybe not.  I'm just trying to think of how my configuration might be different from the typical user.

Thanks again for helping me sort through this.  Going without sound is becoming a huge annoyance.

---

### Post by lidex on 2011-05-11
I was actually thinking of re-installing default alsa after the kernel. At any rate , try it now:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

BTW, what is this output:
```
dpkg -l | grep "alsa"
```
Do you have sound in other kernels?

---

### Post by mschlutt on 2011-05-11
HI,

I loaded the default alsa using the line you suggested, lidex.  I rebooted.  Still no sound.  I had sound in prior kernels (previous to natty narwhal).  I lost sound when I recent upgraded to natty.  Below is some more information that you requested.  Any other suggestions?  THANKS!

schlutt@schlutt-desktop:/$ sudo dpkg -l | grep "alsa"
ii  alsa-base                                          1.0.24+dfsg-0ubuntu1                       ALSA driver configuration files
ii  alsa-firmware-loaders                              1.0.24.1-0ubuntu1                          ALSA software loaders for specific hardware
ii  alsa-oss                                           1.0.17-4                                   ALSA wrapper for OSS applications
ii  alsa-source                                        1.0.24+dfsg-0ubuntu1                       ALSA driver sources
ii  alsa-tools                                         1.0.24.1-0ubuntu1                          Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                                     1.0.24.1-0ubuntu1                          GUI based ALSA utilities for specific hardware
ii  alsa-utils                                         1.0.24.2-0ubuntu6                          Utilities for configuring and using ALSA
ii  alsamixergui                                       0.9.0rc2-1-9                               graphical soundcard mixer for ALSA soundcard driver
ii  bluez-alsa                                         4.91-0ubuntu1                              Bluetooth ALSA support
ii  gnome-alsamixer                                    0.9.7~cvs.20060916.ds.1-2                  ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                 0.10.32-1ubuntu5                           GStreamer plugin for ALSA
rc  libsdl1.2debian-alsa                               1.2.13-4ubuntu4                            Simple DirectMedia Layer (with X11 and ALSA options)
ii  linux-backports-modules-alsa-2.6.35-28-generic-pae 2.6.35-28.20                               Ubuntu supplied Linux modules for version 2.6.35 ALSA snapshots.
schlutt@schlutt-desktop:/$

---

### Post by lidex on 2011-05-11
I see you still have linux-backports-modules-alsa-2.6.35-28-generic-pae installed so I'm guessing you needed that to get sound in maverick? 

This please:
```
aplay -l
```

---

### Post by mschlutt on 2011-05-11
I needed backports for something in the past (maybe jack(?) which I needed for my metronome) - not sure I need it now.  Here is the aplay -l.  Thoughts?

schlutt@schlutt-desktop:/$ aplay -l
aplay: device_list:240: no soundcards found...

---

### Post by lidex on 2011-05-11
> **mschlutt said:**
> I needed backports for something in the past (maybe jack(?) which I needed for my metronome) - not sure I need it now.  Here is the aplay -l.  Thoughts?

schlutt@schlutt-desktop:/$ aplay -l
aplay: device_list:240: no soundcards found...

Yeah, unprintable. I'm thinking system re-install at this point. Your thoughts?

---

### Post by mschlutt on 2011-05-12
What is the best way to go about re-installing natty?  Download it to a flash drive and install?  Let me know if you have an opinion.   In the meantime, I'll search the internets for suggestions on the best way to re-install the OS.

Thanks for working with me and trying to get my sound working.  Much appreciated.

---

### Post by lidex on 2011-05-12
> **mschlutt said:**
> What is the best way to go about re-installing natty?  Download it to a flash drive and install?  Let me know if you have an opinion.   In the meantime, I'll search the internets for suggestions on the best way to re-install the OS.

Thanks for working with me and trying to get my sound working.  Much appreciated.

You'll want a clean install for sure. You can move back anything you need later from backups.

I haven't tried the flash drive install but hear it works well - of course there will always be exceptions. LiveCD is what I've always used.

---

### Post by mc4man on 2011-05-12
> What is the best way to go about re-installing natty? _Download it to a flash drive and install?_ 
If you can do that it's very fast, especially if you either use a 1GB flash drive or if a bigger one don't enable persistence.
I'd say usually around 5-7 min. from creating the  usb boot drive to installed. 
(the 'Startup Disk Creator' works well here to create the usb boot drive, note you can't just "Download it to a flash drive and install"

i never allow the installer to do updates, better done after the install.

---

### Post by mschlutt on 2011-05-13
I copied my home directory to an external drive and then wiped my drive clean.  My previous partitioning scheme was pretty messed up.  I re-installed natty, and everything works!  Including sound!

Thanks for working through these problems with me.  I really appreciate it!

---

