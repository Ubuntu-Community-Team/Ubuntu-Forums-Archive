---
title: "headphone jack not recognised by ubuntu 10.10"
date: 2010-10-16
forum: Multimedia Software
---

### Post by lateefcs on 2010-10-16
Hi all,
I just installed the ubuntu  10.10 on my ideapad z460 everything is working fine except headphone.
I can here sound in built in speakers but not in headphone.

Also I observed that there is no headphone icon in sound preferences.
I installed the latest alsa drivers.

Please help me out.
Thanks in Advance
-AbduL

---

### Post by lidex on 2010-10-16
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Nihilism65 on 2010-10-18
Also having the same issue. Here is the link from the output of that command: [http://www.alsa-project.org/db/?f=87c37738c51dbc5017bd19a11ff1ab0f2c488565](http://www.alsa-project.org/db/?f=87c37738c51dbc5017bd19a11ff1ab0f2c488565)

---

### Post by lateefcs on 2010-10-21
Please find my alsa driver information
[http://www.alsa-project.org/db/?f=01bd7c7a47128d2899396c1de3c82063c80b4a63](http://www.alsa-project.org/db/?f=01bd7c7a47128d2899396c1de3c82063c80b4a63)
-AbduL

---

### Post by lateefcs on 2010-10-21
Thanks everybody for replying....
I found below link and it resolve my headphone problem
:)

---

### Post by Nihilism65 on 2010-10-21
lateefcs, can you provide a link to what helped you fix your problem please?

---

### Post by Jarradfz on 2010-10-22
Greetings everyone. I am also having the very same problem.
[http://www.alsa-project.org/db/?f=355e6bfeaf1f67003a4e6d771df3b43f3e6a091b](http://www.alsa-project.org/db/?f=355e6bfeaf1f67003a4e6d771df3b43f3e6a091b)
thanks

---

### Post by lidex on 2010-10-22
> **Jarradfz said:**
> Greetings everyone. I am also having the very same problem.
[http://www.alsa-project.org/db/?f=355e6bfeaf1f67003a4e6d771df3b43f3e6a091b](http://www.alsa-project.org/db/?f=355e6bfeaf1f67003a4e6d771df3b43f3e6a091b)
thanks

Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=laptop position_fix=1 enable=yes 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by Yellow Pasque on 2010-10-22
> **Nihilism65 said:**
> Also having the same issue. Here is the link from the output of that command: [http://www.alsa-project.org/db/?f=87c37738c51dbc5017bd19a11ff1ab0f2c488565](http://www.alsa-project.org/db/?f=87c37738c51dbc5017bd19a11ff1ab0f2c488565)

Since you have an unidentified Conexant chipset, you may have more luck with the linuxant drivers: [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

---

### Post by LaMooNa on 2010-10-23
hi all, I have the same problem with headphone jack
my laptop is toshiba satellite L650-11f
the output is :
[http://www.alsa-project.org/db/?f=87c37738c51dbc5017bd19a11ff1ab0f2c488565](http://www.alsa-project.org/db/?f=87c37738c51dbc5017bd19a11ff1ab0f2c488565)
could you please help me

---

### Post by Nihilism65 on 2010-10-23
> **Temüjin said:**
> Since you have an unidentified Conexant chipset, you may have more luck with the linuxant drivers: [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

After I installed this driver I don't have any sound at all now. I tried uninstalling it and I still have no sound. What can I do to fix this?

---

### Post by lidex on 2010-10-23
> **Nihilism65 said:**
> After I installed this driver I don't have any sound at all now. I tried uninstalling it and I still have no sound. What can I do to fix this?
On an alsa upgrade/install its likely your levels are reset (muted). Did you check those? How about an updated alsa-info output please.

---

### Post by kiwi_steve on 2010-10-25
[**FIXED**] For me anyway... I did some searching on the conexant chip id and found this link:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/637040](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/637040)

Which led me to try model=thinkpad in lidex's post earlier in this thread.  This has solved the problem :)

Thanks Lidex for the post, it sent me in the right direction.

Steve



Original post follows (from before I fixed it)
----------------------------------------------

Same laptop model, same distro, same problem...

Diagnostic info is here:
[http://www.alsa-project.org/db/?f=e62f3090b5c99d8b56c624790eee02887a8eed52](http://www.alsa-project.org/db/?f=e62f3090b5c99d8b56c624790eee02887a8eed52)

I'm sitting in a dead quiet study lab trying to go over old lecture videos and instead I am studying config files in Ubuntu... I may fail the course, but at least I'll understand ALSA a little better, lol :P

Anyone found any solution?

Cheers

Steve

[edit]
I did try lidex's solution - and also tried changing model=laptop to model=toshiba.  All to no avail
[/edit]

---

### Post by LaMooNa on 2010-10-26
great job man, this fixed my problem as well
thanks a lot ;)

---

### Post by mhdwaqar on 2010-10-29
Hi all,
I am also having the same problem . I just installed the ubuntu  10.10 on my ideapad z560 everything is working fine except headphone.
I can here sound in built in speakers but not in headphone.
Also I observed that there is no headphone icon in sound preferences.
I installed the latest alsa drivers.

Further my numeric keypad on the right side of the laptop also not working

Here is the link from the output of the command 
wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

[http://www.alsa-project.org/db/?f=6cf15114fae518df18b060d8e2d7968e98020ae7](http://www.alsa-project.org/db/?f=6cf15114fae518df18b060d8e2d7968e98020ae7)

---

### Post by lidex on 2010-10-30
> **mhdwaqar said:**
> Hi all,
I am also having the same problem . I just installed the ubuntu  10.10 on my ideapad z560 everything is working fine except headphone.
I can here sound in built in speakers but not in headphone.
Also I observed that there is no headphone icon in sound preferences.
I installed the latest alsa drivers.

Further my numeric keypad on the right side of the laptop also not working

Here is the link from the output of the command 
wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

[http://www.alsa-project.org/db/?f=6cf15114fae518df18b060d8e2d7968e98020ae7](http://www.alsa-project.org/db/?f=6cf15114fae518df18b060d8e2d7968e98020ae7)

I am pulling out my hair with this codec. Arrghhh. OK, let's see what sticks. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=thinkpad 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by random-user on 2010-11-02
by following kiwi_steve and lidex last posts, so in brief, by adding:
```
options snd-hda-intel model=thinkpad
```in the end of the file located at /etc/modprobe.d/alsa-base.conf

---

### Post by globalmac on 2010-11-07
Thank you Lidex. I was having the same problem with my Gateway NV52 and your fix worked like a charm.  I'm raising a cup of coffee in your honor:)

---

### Post by dmak004 on 2010-11-16
I am very new to Linux and am experiencing problems with the headphone  jack not working on my machine.  I have a gateway id49c07u and I ran the  alas script and uploaded my info here


[http://www.alsa-project.org/db/?f=516e2b1e1ced5503002130628b229fe1b0abd3df](http://www.alsa-project.org/db/?f=516e2b1e1ced5503002130628b229fe1b0abd3df)

Please help me.

---

### Post by nikileshsa on 2010-12-04
I also have the same issue. I tried the steps posted above, but in vain. Can anyone help me please?

The output to the script is in the below link.

[http://www.alsa-project.org/db/?f=4eb08c739310f05e04d7711d9b07185fb0049310](http://www.alsa-project.org/db/?f=4eb08c739310f05e04d7711d9b07185fb0049310)

---

### Post by lidex on 2010-12-04
> **nikileshsa said:**
> I also have the same issue. I tried the steps posted above, but in vain. Can anyone help me please?

The output to the script is in the below link.

[http://www.alsa-project.org/db/?f=4eb08c739310f05e04d7711d9b07185fb0049310](http://www.alsa-project.org/db/?f=4eb08c739310f05e04d7711d9b07185fb0049310)
I would then suggest removing your edit to alsa-base.conf and installing the linuxant driver:

[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

---

### Post by nikileshsa on 2010-12-04
First please accept my thanks for the suggestion. 

But now I have a BIGGER problem. The audio is totally out. I installed the driver as u told in the above link. 

Now someone has to definitely help me please...

---

### Post by nikileshsa on 2010-12-04
Also when I run alsamixer...I get the following error ....



nikileshsa@niki:~$ alsamixer
cannot open mixer: No such file or directory

---

### Post by stratosvoukel on 2010-12-04
Hey guys, I have an Inspiron N5010 and I also have this problem! Any help?

---

### Post by lidex on 2010-12-04
> **nikileshsa said:**
> Also when I run alsamixer...I get the following error ....



nikileshsa@niki:~$ alsamixer
cannot open mixer: No such file or directory
Looks like it didn't install correctly -- try it again.

---

### Post by nikileshsa on 2010-12-04
Also when I run alsamixer...I get the following error ....



nikileshsa@niki:~$ alsamixer
cannot open mixer: No such file or directory


I am a NEW BIE...

I lost my patience and I tried to uninstall alsamixer from the GNOME software installation wizard...but IT FAILED with an error(I did not capture the error).

then...I simply typed in the terminal..sudo apt-get install

n here is the output..

It says something about the alsa-driver-linuxant...PLEAE have a look..

nikileshsa@niki:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up alsa-driver-linuxant (1.0.23.1) ...
Building modules for the 2.6.35-23-generic kernel, please wait...


 done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.15245.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 alsa-driver-linuxant
E: Sub-process /usr/bin/dpkg returned an error code (1)


Help Please :)...

---

### Post by nikileshsa on 2010-12-04
When I try to re-install the driver...I get an ERROR message like this...

AN UNHANDLED ERROR OCCURRED...

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

---

### Post by nikileshsa on 2010-12-04
When I try to install the Alsamixer from the Ubuntu software center....my installation fails with the following details...

installArchives() failed: Selecting previously deselected package gnome-alsamixer.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 165573 files and directories currently installed.)
Unpacking gnome-alsamixer (from .../gnome-alsamixer_0.9.7~cvs.20060916.ds.1-2_amd64.deb) ...
Processing triggers for gconf2 ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up alsa-driver-linuxant (1.0.23.1) ...
Building modules for the 2.6.35-23-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.25882.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Setting up gnome-alsamixer (0.9.7~cvs.20060916.ds.1-2) ...
Errors were encountered while processing:
 alsa-driver-linuxant
Setting up alsa-driver-linuxant (1.0.23.1) ...
Building modules for the 2.6.35-23-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.29831.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2

---

### Post by lidex on 2010-12-04
Run this in a terminal and post the output:
```
cat /tmp/alsa-driver-linuxant.15245.log
```

Make sure these are installed:
```
sudo apt-get install make gcc
```

---

### Post by Hobs295 on 2010-12-09
Hi Lidex -  

I'm having a similar problem - speaker audio works just fine but headphone jack does not work.

[http://www.alsa-project.org/db/?f=36391f5440d049fd2421cac032abe1e11f3e940a](http://www.alsa-project.org/db/?f=36391f5440d049fd2421cac032abe1e11f3e940a)

I attempted mhdwaqar's fix but that did not seem to work.  

In alsamixer when I mute 'headphone' it mutes my laptop speakers...seems kind of odd.

Any help?  Thanks!

---

### Post by lidex on 2010-12-12
> **Hobs295 said:**
> Hi Lidex -  

I'm having a similar problem - speaker audio works just fine but headphone jack does not work.

[http://www.alsa-project.org/db/?f=36391f5440d049fd2421cac032abe1e11f3e940a](http://www.alsa-project.org/db/?f=36391f5440d049fd2421cac032abe1e11f3e940a)

I attempted mhdwaqar's fix but that did not seem to work.  

In alsamixer when I mute 'headphone' it mutes my laptop speakers...seems kind of odd.

Any help?  Thanks!

I'm curious as to how the "thinkpad" model quirk is being applied as it is not showing in your modprobe options. You should probably remove that.

---

### Post by bigboyka on 2010-12-14
Hi all im having the same problem im running ubuntu 10.10 on a Compaq prisario cq60 and have tried everything suggested but nothing i have no headphone option in alsa mixer.

my alsa info is here

[http://www.alsa-project.org/db/?f=0608e2b4a4ec5c98fa7282364650d2fe3b90b0ca](http://www.alsa-project.org/db/?f=0608e2b4a4ec5c98fa7282364650d2fe3b90b0ca)

---

### Post by lidex on 2010-12-14
> **bigboyka said:**
> Hi all im having the same problem im running ubuntu 10.10 on a Compaq prisario cq60 and have tried everything suggested but nothing i have no headphone option in alsa mixer.

my alsa info is here

[http://www.alsa-project.org/db/?f=0608e2b4a4ec5c98fa7282364650d2fe3b90b0ca](http://www.alsa-project.org/db/?f=0608e2b4a4ec5c98fa7282364650d2fe3b90b0ca)

Try changing your model quirk from "auto" to "dell-vostro"

---

### Post by durian86 on 2010-12-15
Also having the same issue. Here is the link from the output of that command:
[http://www.alsa-project.org/db/?f=922a4bac214c3949c0fce9c996675ee5c84e3549](http://www.alsa-project.org/db/?f=922a4bac214c3949c0fce9c996675ee5c84e3549)
thx

---

### Post by barkej on 2010-12-15
> **lidex said:**
> Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=laptop position_fix=1 enable=yes 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
This worked great for me. Thanks!

---

### Post by Kveldulv on 2010-12-15
I tried these fixes as well since I have the same problem, except my problem is also with my microphone. I have an HP Pavilion dv3.

Here is the output of the other command... it didnt look like it gave me any information, but here's the output...

brittany@Zoolander:~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2010-12-15 14:26:02--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 212.20.107.51
Connecting to [www.alsa-project.org|212.20.107.51|:80](www.alsa-project.org|212.20.107.51|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2010-12-15 14:26:03--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: 27026 (26K) [text/plain]
Saving to: `alsa-info.sh'

100%[======================================>] 27,026      70.1K/s   in 0.4s    

2010-12-15 14:26:04 (70.1 KB/s) - `alsa-info.sh' saved [27026/27026]

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

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] :

---

### Post by ray13z on 2010-12-16
Usually just changing the base conf file does the work but I've had no luck at all! In fact alsamixer doesn't even recognise my mic input (apart from headphone). I am using a Toshiba Satellite L650. Any suggestions?
[http://www.alsa-project.org/db/?f=2a8ee0eb5c718056526c20bbfd896d73cd177d2f](http://www.alsa-project.org/db/?f=2a8ee0eb5c718056526c20bbfd896d73cd177d2f)

---

### Post by lidex on 2010-12-16
@durian86
You only want to use one fix at a time. Post this output please:
```
cat /etc/modprobe.d/alsa-base.conf
```
@Kveldulv
After that last line you should input the letter Y and hit enter.
A generic fix for Dvx line:
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

@ray13z
Follow the above procedure excepting the line you want to add is:
```
options snd-hda-intel model=thinkpad
```

---

### Post by ray13z on 2010-12-16
> **lidex said:**
> 
@ray13z
Follow the above procedure excepting the line you want to add is:
```
options snd-hda-intel model=thinkpad
```

Awesome. Worked. Thanks.

---

### Post by byronbgs on 2010-12-18
No headphone output on a Toshiba L645D-S4058, Please help.

Thanks

Byron


[http://www.alsa-project.org/db/?f=8a4830cba5469760cd8671d4a52b26deff01e566](http://www.alsa-project.org/db/?f=8a4830cba5469760cd8671d4a52b26deff01e566)

---

### Post by byronbgs on 2010-12-18
> **byronbgs said:**
> No headphone output on a Toshiba L645D-S4058, Please help.

Thanks

Byron


[http://www.alsa-project.org/db/?f=8a4830cba5469760cd8671d4a52b26deff01e566](http://www.alsa-project.org/db/?f=8a4830cba5469760cd8671d4a52b26deff01e566)

Got it working, I tried this....options snd-hda-intel model=thinkpad and success. :popcorn:

---

### Post by durian86 on 2010-12-19
[QUOTE=lidex;10246987]@durian86
You only want to use one fix at a time. Post this output please:

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=laptop position_fix=1 enable=yes

my earphone still not working...plz help...thx

---

### Post by lidex on 2010-12-20
@durian86
What modifications have you made to your audio system? Did you create any conf files? These modprobe options are ridiculous:
```
!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=laptop position_fix=1 enable=yes
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=m51va position_fix=0
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: model=m51va position_fix=0 
```

---

### Post by mattieftw on 2010-12-23
[http://www.alsa-project.org/db/?f=02e9fe1896e49351a87a538266f8a5a181723cfc](http://www.alsa-project.org/db/?f=02e9fe1896e49351a87a538266f8a5a181723cfc)

Can't figure what I'm doing wrong either...

---

### Post by lidex on 2010-12-24
> **mattieftw said:**
> [http://www.alsa-project.org/db/?f=02e9fe1896e49351a87a538266f8a5a181723cfc](http://www.alsa-project.org/db/?f=02e9fe1896e49351a87a538266f8a5a181723cfc)

Can't figure what I'm doing wrong either...

Try this:
[http://ubuntuforums.org/showthread.php?p=9162799](http://ubuntuforums.org/showthread.php?p=9162799)

---

### Post by TimCV on 2010-12-27
The same problem for me, but my netbook its a point of view MobII
NB9040

---

### Post by Yellow Pasque on 2010-12-27
> **TimCV said:**
> The same problem for me, but my netbook its a point of view MobII
NB9040
Ok... so post your info using the links in lidex's signature.

---

### Post by Hobs295 on 2011-01-06
> **lidex said:**
> I'm curious as to how the "thinkpad" model quirk is being applied as it is not showing in your modprobe options. You should probably remove that.
Thanks but the same problem still exists.

I removed the line: 

```
 options snd-hda-intel model=thinkpad
```

...from the file opened using the line: 

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

...and now here is the new link to my ALSA info:
[http://www.alsa-project.org/db/?f=add7fc2be5b19036fbcda00346fbdcdb4ce8f432](http://www.alsa-project.org/db/?f=add7fc2be5b19036fbcda00346fbdcdb4ce8f432)

---

### Post by gustehn on 2011-01-06
Hey
Having the same problem!
My computer: Asus X52F

The link: [http://www.alsa-project.org/db/?f=dcbd480d6f130f3d92013c358785fed0e0a985d2](http://www.alsa-project.org/db/?f=dcbd480d6f130f3d92013c358785fed0e0a985d2)

---

### Post by lidex on 2011-01-07
> **Hobs295 said:**
> Thanks but the same problem still exists.

I removed the line: 

```
 options snd-hda-intel model=thinkpad
```

...from the file opened using the line: 

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

...and now here is the new link to my ALSA info:
[http://www.alsa-project.org/db/?f=add7fc2be5b19036fbcda00346fbdcdb4ce8f432](http://www.alsa-project.org/db/?f=add7fc2be5b19036fbcda00346fbdcdb4ce8f432)

How did you come up with "thinkpad"? No matter, the options you should try are:
```
ref
eapd
auto
```

---

### Post by nndurj on 2011-01-08
Add this to your /etc/modprobe.d/alsa-base.conf

*options snd-hda-intel model=ideapad*

It worked for my toshiba C650.

---

### Post by lidex on 2011-01-08
> **nndurj said:**
> 
It worked for my toshiba C650.
Thanks for the input, but these model quirks are hardware specific. What works for a toshiba C650 with a conexant CX20585 codec is not going to work with a gateway M-6851 with sigmatel stac9205. BTW, I have the model fix for C650 as thinkpad

---

### Post by Hobs295 on 2011-01-10
> **lidex said:**
> How did you come up with "thinkpad"? No matter, the options you should try are:
```
ref
eapd
auto
```

Probably something that got put in by me randomly looking for fixes before stumbling upon this thread.  I'm an Ubuntu (well Linux in general) newbie so I'm prone to make rash/illogical changes using terminal.

---

### Post by Hobs295 on 2011-01-10
> **lidex said:**
> How did you come up with "thinkpad"? No matter, the options you should try are:
```
ref
eapd
auto
```

Lidex,

Do you mean add these lines to my modprobe file?  If so like this:

```
 options snd-hda-intel ref 
```

? 

One at a time or all three at once?  I've tried a few permutations of this but want to make sure I'm putting your recommendation to use correctly. 

Thanks!

---

### Post by lidex on 2011-01-11
the correct syntax is:
```
options snd-hda-intel model=xxx
```

---

### Post by Hobs295 on 2011-01-11
> **lidex said:**
> the correct syntax is:
```
options snd-hda-intel model=xxx
```

eapd worked!  Thank you!!!

---

### Post by wazobia on 2011-01-24
Hi.

My laptop is a gateway m-6862 model. In my case, the once I put in the headphone jack the sound disappears, not even the speakers give out any sound. When I go to sound preferences, I have two devices, one called internal audio, and the other a radeon hd 2600 hdmi. If i activate the radeon device, i get no sound. When i run alsamixer in the terminal, and switch to the radeon hd card, the volume properties all disappear. Here is the link to my ALSA information 

[http://www.alsa-project.org/db/?f=3e9f9c292e53dc6b8e4a8635e1fc15effaca933b](http://www.alsa-project.org/db/?f=3e9f9c292e53dc6b8e4a8635e1fc15effaca933b)

and the output from my alsa base config 


# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=auto

Any help would be much appreciated. 

Thanks

---

### Post by wazobia on 2011-01-24
> **wazobia said:**
> Hi.

My laptop is a gateway m-6862 model. In my case, the once I put in the headphone jack the sound disappears, not even the speakers give out any sound. When I go to sound preferences, I have two devices, one called internal audio, and the other a radeon hd 2600 hdmi. If i activate the radeon device, i get no sound. When i run alsamixer in the terminal, and switch to the radeon hd card, the volume properties all disappear. Here is the link to my ALSA information 

[http://www.alsa-project.org/db/?f=3e9f9c292e53dc6b8e4a8635e1fc15effaca933b](http://www.alsa-project.org/db/?f=3e9f9c292e53dc6b8e4a8635e1fc15effaca933b)

and the output from my alsa base config 


# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=auto

Any help would be much appreciated. 

Thanks

Oops. I changed the "auto" in the last line to eapd and wow, it worked after rebooting! Almost ripped my hair out but it's fine now. 

Thanks a lot, Lidex. You've really helped a lot of people here.

---

### Post by lidex on 2011-01-25
> **wazobia said:**
> Oops. I changed the "auto" in the last line to eapd and wow, it worked after rebooting! Almost ripped my hair out but it's fine now. 

Thanks a lot, Lidex. You've really helped a lot of people here.
Glad to help.

---

### Post by bford16 on 2011-01-27
I had a problem with my HP dv7-1232NR laptop.  All was well, until an update, then suddenly the headphone jack did not work.  The issue was resolved with this fix.```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add the following line to the end of the file.```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```Save file, reboot, and all is well again.

---

### Post by lidex on 2011-01-27
> **bford16 said:**
> I had a problem with my HP dv7-1232NR laptop.  All was well, until an update, then suddenly the headphone jack did not work.  The issue was resolved with this fix.```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add the following line to the end of the file.```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```Save file, reboot, and all is well again.
Interesting, a Dv7 you say? Does the mic work with that fix? Internal speakers?

---

### Post by bford16 on 2011-01-28
> **lidex said:**
> Interesting, a Dv7 you say? Does the mic work with that fix? Internal speakers?
I haven't tried the microphone yet, but the internal speakers work just fine.  I can use the speakers, and when I plug in the headphones, sound switches to them.  The microphone appears to work; in Sound Preferences, the meter moves in response to the music playing (but I have to select 100% - the unamplified setting does not appear to work).

---

### Post by rahul.pache on 2011-01-30
hello,

I am facing the same problem.
here is the output I got after running mentioned script
[http://www.alsa-project.org/db/?f=b98b717f7f271f9c216838b6d95ce9e346010dfc](http://www.alsa-project.org/db/?f=b98b717f7f271f9c216838b6d95ce9e346010dfc)

Please suggest what to do.

---

### Post by lidex on 2011-01-30
> **rahul.pache said:**
> hello,

I am facing the same problem.
here is the output I got after running mentioned script
[http://www.alsa-project.org/db/?f=b98b717f7f271f9c216838b6d95ce9e346010dfc](http://www.alsa-project.org/db/?f=b98b717f7f271f9c216838b6d95ce9e346010dfc)

Please suggest what to do.

One reason we like to create separate threads is highlighted here. Your hardware is quite different and I would find it highly unlikely that this:
```
snd-hda-intel: index=0 model=toshiba position_fix=1
```
would work for you. Remove that entry and replace it with this:
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```
Reboot.

No joy try this:
```
options snd-hda-intel model=thinkpad
```

---

### Post by Hotel Bravo on 2011-02-11
Hello I am having the same problem here is my Alsa info
[http://www.alsa-project.org/db/?f=a867c9b380056e5e0c45eb22ff87951436818d11](http://www.alsa-project.org/db/?f=a867c9b380056e5e0c45eb22ff87951436818d11)
:D

---

### Post by lagooned on 2011-02-13
> **lidex said:**
> Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=laptop position_fix=1 enable=yes 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Worked Perfectly! Thank you! How did you figure all this out anyway?

---

### Post by lidex on 2011-02-15
> **Hotel Bravo said:**
> Hello I am having the same problem here is my Alsa info
[http://www.alsa-project.org/db/?f=a867c9b380056e5e0c45eb22ff87951436818d11](http://www.alsa-project.org/db/?f=a867c9b380056e5e0c45eb22ff87951436818d11)
:D

For you try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=asus-mode3" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by bdsatish on 2011-02-20
I was also having the same problem (Lenovo G560). That is, laptop speakers were working, but not the headphones. I solved it by adding:
```
options snd-hda-intel model=thinkpad position_fix=1 enable=yes
```
to the file /etc/modprobe.d/alsa-base.conf
Just for more info, my laptop's ALSA details are here: [http://www.alsa-project.org/db/?f=3de18ba1fe0ca9ff4362d7ca96a452af1fafa190](http://www.alsa-project.org/db/?f=3de18ba1fe0ca9ff4362d7ca96a452af1fafa190)
Also, the options model=laptop and model=eapd did not work for me.
[Update]: Oops, 'thinkpad' disables my internal mic.

---

### Post by Jenszor on 2011-02-22
I've been a long time Ubuntu user and never encountered any problems (the reason why I didn't post on here before), but now after installing 10.10 I too get this very annoying problem...

Results from the script:
```
http://www.alsa-project.org/db/?f=080f9179200ef535f0e0599334bbfb3d44adc49e
```

Thanks in advance :)

---

### Post by lidex on 2011-02-23
> **Jenszor said:**
> I've been a long time Ubuntu user and never encountered any problems (the reason why I didn't post on here before), but now after installing 10.10 I too get this very annoying problem...

Results from the script:
```
http://www.alsa-project.org/db/?f=080f9179200ef535f0e0599334bbfb3d44adc49e
```

Thanks in advance :)

Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by bdsatish on 2011-02-23
Thanks Lidex !
After updating the drivers, all three of them are working -- internal mic, headphones and internal laptop speakers !

---

### Post by Jenszor on 2011-02-23
Thank you very much Lidex :)

---

### Post by tdashroy on 2011-02-23
For anybody who is still having trouble with snd-hda-intel, I found this site very helpful:

[http://doc.ubuntu-fr.org/audio_intel_hda](http://doc.ubuntu-fr.org/audio_intel_hda)

---

### Post by fireballmatt on 2011-02-24
I've been trying to get my headphone jack working for awhile now, regular speakers work just fine...

My system info is here:
[http://www.alsa-project.org/db/?f=d8dfdd0fa625a28e8762d0301c4a00be90fd3843](http://www.alsa-project.org/db/?f=d8dfdd0fa625a28e8762d0301c4a00be90fd3843)

I've modified /etc/modprobe.d/alsa-base.conf so that the final line reads:

options snd-hda-intel model=auto position_fix=1 enable=yes

I've also tried "ref", "auto", and "eapd" for the model as well as using the "dell-m6", but none have worked. I've also tried taking out the last portion of the line reading "position_fix=1 enable=yes" out for each variation. No joy. (have been rebooting after every change)

alsamixer will display the headphones, but it does not have a vertical bar above it and is permanently set to 00.

Any ideas?

---

### Post by lidex on 2011-03-01
> **fireballmatt said:**
> I've been trying to get my headphone jack working for awhile now, regular speakers work just fine...

My system info is here:
[http://www.alsa-project.org/db/?f=d8dfdd0fa625a28e8762d0301c4a00be90fd3843](http://www.alsa-project.org/db/?f=d8dfdd0fa625a28e8762d0301c4a00be90fd3843)

I've modified /etc/modprobe.d/alsa-base.conf so that the final line reads:

options snd-hda-intel model=auto position_fix=1 enable=yes

I've also tried "ref", "auto", and "eapd" for the model as well as using the "dell-m6", but none have worked. I've also tried taking out the last portion of the line reading "position_fix=1 enable=yes" out for each variation. No joy. (have been rebooting after every change)

alsamixer will display the headphones, but it does not have a vertical bar above it and is permanently set to 00.

Any ideas?
Yeah, whatever you have in alsa-base.conf, take it out cause it's not working:
```
[   17.513762] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   18.523756] hda-intel: No response from codec, disabling MSI: last cmd=0x100f0000
[   19.531257] hda-intel: Codec #1 probe error; disabling it...
[   19.637036] hda_codec: ALC888: BIOS auto-probing.
```
Next try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```

---

### Post by ushio81 on 2011-03-02
Some days ago i had the headphones + mic issue. I resolved adding in /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=ref

Yesterday headphones stopped working when plugged in. I've tried using model=laptop, model=auto, model=dell, but it didn't work.

I've also tried with "position_fix=1 enable=yes" but nothing changes. Mic only works when using model=ref, but as i told, some days ago headphones worked too.

My laptop is a Dell E5510. What can i try?

---

### Post by Yellow Pasque on 2011-03-02
Look in alsamixer and check to see if headphones are muted

---

### Post by ushio81 on 2011-03-02
> **Temüjin said:**
> Look in alsamixer and check to see if headphones are muted

That's the first thing I've done after all the settings changes :)

Anyway in Alsamixer I have 2 Headphone columns: one with volume at 100% and the second one has MM over it (I suppose it's muted) but it goes away if I press M, but the volume is set to 0 and I cannot rise it up.

---

### Post by makalove on 2011-03-02
> **lidex said:**
> [code] options snd-hda-intel model=thinkpad [/code

This worked for me on a new Lenovo G560 & a fresh install of 10.10. i was getting no headphone/speaker jack sound at all, and no muting of the internal speakers when something was plugged into the jack.

Thanks!

---

### Post by ushio81 on 2011-03-02
After a google search I founded out that the audio issues are connected to the Suspension of the PC; I realized indeed that the headphones stopped to work after a suspension.

I paste you a guy who had EXACTELY my symptoms on a different laptop (but same audio device).

1. Sometimes after waking up from sleep, the screen is black and the machine doesn't respond, have to reboot
2. Sometimes after waking up from sleep, the mouse doesn't work properly (but restarting X restores it)
3. The external headphone jack doesn't seem to work

---

### Post by ushio81 on 2011-03-02
> **ushio81 said:**
> After a google search I founded out that the audio issues are connected to the Suspension of the PC; I realized indeed that the headphones stopped to work after a suspension.

I paste you a guy who had EXACTELY my symptoms on a different laptop (but same audio device).

1. Sometimes after waking up from sleep, the screen is black and the machine doesn't respond, have to reboot
2. Sometimes after waking up from sleep, the mouse doesn't work properly (but restarting X restores it)
3. The external headphone jack doesn't seem to work

Ok I founded out a solution for my problem: I've suspended the computer and when I reactivated it, headphones just worked. I've read it from another guy who had the same problem... Now I hope they'll resolve those bugs :p

---

### Post by lidex on 2011-03-02
The first thing you should do when something that worked fine suddenly stops working after a suspend/hibernate is to reboot.
Troubleshooting 101

---

### Post by Yellow Pasque on 2011-03-02
> **lidex said:**
> The first thing you should do when something that worked fine suddenly stops working after a suspend/hibernate is to reboot.
Troubleshooting 101
Yeah, the suspend/resume relies on the BIOS to get it right, and sadly, there are a lot of systems/mobos that don't do it perfectly. Oh, and Hi lidex ):P

---

### Post by ushio81 on 2011-03-03
> **lidex said:**
> The first thing you should do when something that worked fine suddenly stops working after a suspend/hibernate is to reboot.
Troubleshooting 101

The fact is that after the headphones stopped working, I've rebooted the system at least 10 times, testing different options in the configuration file for audio, but nothing changed. The headphones started working only after a new susped/reactivate cycle...
Troubleshooting 666

---

### Post by lidex on 2011-03-03
> **ushio81 said:**
> The fact is that after the headphones stopped working, I've rebooted the system at least 10 times, testing different options in the configuration file for audio, but nothing changed. The headphones started working only after a new susped/reactivate cycle...
Troubleshooting 666
Copy that. I've been wrong before. From alsa documentation:
> reloading modules across APM suspend-and-resume
-----------------------------------------------
During suspension many peripherals are switched off; on resuming the
machine these peripherals need to be re-initialized.  Many ALSA
drivers do this properly but some still do not.

If this problem affects you and if your ALSA drivers are built as
loadable modules and your kernel supports module unloading then you
can work around the problem by unloading the driver before suspending
and loading it again after resuming.  This will be done for you
automatically if you add the name of the problematic sound card driver
module to the variable force_unload_modules_before_suspend variable in
/etc/default/alsa.  E.g., if your CS46XX and AZX cards don't work
properly after resuming from APM suspend, add the names of their
driver modules to the list:

    force_unload_modules_before_suspend="snd-cs46xx snd-azx"


restoring sound volumes across APM suspend-and-resume
-----------------------------------------------------
alsa-base provides an APM script in /etc/apm/scripts.d/alsa to
automatically store/restore sound volumes during APM suspension.
Since this option relies on alsactl, please install the recommended
alsa-utils package.

unloading modules
-----------------
If you want to unload ALSA driver modules then you will have to stop
all applications that are using ALSA device files.  You can do both
in one step by running:

    alsa force-unload

How you doing Temüjin?

---

### Post by Hip-Hopapotamus on 2011-03-09
Installed 10.10, initially laptop speakers worked, but headphone jack didn't. After updates no sound at all. I have an Asus K52 and followed the steps on this model's thread with no success.

Having a problem with alsa-driver-linuxant. It said the build failed and to review the buld log.

Then it listed this:

dpkg: error processing alsa-driver-linuxant (--install):
subprocess installed post-installation script returned error exit status 2

Is there any way I can post the log file?

---

### Post by azeemj on 2011-03-12
> **lidex said:**
> One reason we like to create separate threads is highlighted here. Your hardware is quite different and I would find it highly unlikely that this:
```
snd-hda-intel: index=0 model=toshiba position_fix=1
```would work for you. Remove that entry and replace it with this:
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```Reboot.

No joy try this:
```
options snd-hda-intel model=thinkpad
```

Dear
Plz tell me what i will insert at end of alsa base confg file here is my system info


**uname -a**
Linux desktop01 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux


**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


**cat /proc/asound/version** 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Mar  2 2011 for kernel 2.6.32-30-generic (SMP).



**head -n 1 /proc/asound/card*/codec#***
Codec: Realtek ALC259

---

### Post by lidex on 2011-03-17
@azeemj
I haven't seen any model switches for that codec. Try updating your alsa modules:
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
Still no joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by wvandael on 2011-03-18
Same problem on the Dell Latitude E6410. Does anybody know the right settings for snd-hda_intel ?

[http://www.alsa-project.org/db/?f=0060fc975b252ba5899beb06834fbbf2b742d2e4]("http://www.alsa-project.org/db/?f=0060fc975b252ba5899beb06834fbbf2b742d2e4")

---

### Post by wvandael on 2011-03-18
> **wvandael said:**
> Same problem on the Dell Latitude E6410. Does anybody know the right settings for snd-hda_intel ?

[http://www.alsa-project.org/db/?f=0060fc975b252ba5899beb06834fbbf2b742d2e4](http://www.alsa-project.org/db/?f=0060fc975b252ba5899beb06834fbbf2b742d2e4)


OK, I fixed it by updating the drivers. I also put model=auto back in there. I did those two changes simultaneously so I don't know what did the trick, but the important thing is that I have sound in the headphones ;)

[http://www.alsa-project.org/db/?f=c42e072d052c97b7cf7cc94672d1563c152aee4f](http://www.alsa-project.org/db/?f=c42e072d052c97b7cf7cc94672d1563c152aee4f)

---

### Post by emailmyremail on 2011-03-18
I have a new install of 10.10 on a Toshiba Satellite with a dual boot of win7.  

I installed 10.10 and on the first night I swore the headphone jack sent  sound to my external speakers (may of been plugged in during install).   Then the next day I couldn't get any sound out of the jack.  Sound kept  coming out of my internal speakers.  In win7 the jack worked normally.

In Ubuntu I have checked sound preferences and my alsa mixer.  There is no listing for a headphone jack (so it is not muted).  

here is my alsa info:
[http://www.alsa-project.org/db/?f=47...d30a4c8b8f34af]("http://www.alsa-project.org/db/?f=471694b28ddcdc2e25237c9a6fd30a4c8b8f34af")
[]("http://www.linuxant.com/alsa-driver/")

---

### Post by Yellow Pasque on 2011-03-18
> **emailmyremail said:**
> I have a new install of 10.10 on a Toshiba Satellite with a dual boot of win7.  

I installed 10.10 and on the first night I swore the headphone jack sent  sound to my external speakers (may of been plugged in during install).   Then the next day I couldn't get any sound out of the jack.  Sound kept  coming out of my internal speakers.  In win7 the jack worked normally.

In Ubuntu I have checked sound preferences and my alsa mixer.  There is no listing for a headphone jack (so it is not muted).  

here is my alsa info:
[http://www.alsa-project.org/db/?f=47...d30a4c8b8f34af]("http://www.alsa-project.org/db/?f=471694b28ddcdc2e25237c9a6fd30a4c8b8f34af")
[]("http://www.linuxant.com/alsa-driver/")
The satellite 655 uses the same codec and needs keyword "options snd-hda-intel model=ideapad" for all jacks to work properly. Try thinkpad if that doesn't work. Here's the full list:
```
Conexant 5066
=============
  laptop	Basic Laptop config (default)
  hp-laptop	HP laptops, e g G60
  asus		Asus K52JU, Lenovo G560
  dell-laptop	Dell laptops
  dell-vostro	Dell Vostro
  olpc-xo-1_5	OLPC XO 1.5
  ideapad       Lenovo IdeaPad U150
  thinkpad	Lenovo Thinkpad
```

---

### Post by emailmyremail on 2011-03-18
> **Temüjin said:**
> The satellite 655 uses the same codec and needs keyword "options snd-hda-intel model=ideapad" for all jacks to work properly. Try thinkpad if that doesn't work. Here's the full list:
```
Conexant 5066
=============
  laptop    Basic Laptop config (default) 
  hp-laptop    HP laptops, e g G60
  asus        Asus K52JU, Lenovo G560
  dell-laptop    Dell laptops
  dell-vostro    Dell Vostro
  olpc-xo-1_5    OLPC XO 1.5
  ideapad       Lenovo IdeaPad U150
  thinkpad    Lenovo Thinkpad
```

I put in the ideapad code rebooted and played music from though my external speakers and danced when sound actually came out!  Thank You Temujin!

---

### Post by lidex on 2011-03-18
> **wvandael said:**
> OK, I fixed it by updating the drivers. I also put model=auto back in there. I did those two changes simultaneously so I don't know what did the trick, but the important thing is that I have sound in the headphones ;)

[http://www.alsa-project.org/db/?f=c42e072d052c97b7cf7cc94672d1563c152aee4f](http://www.alsa-project.org/db/?f=c42e072d052c97b7cf7cc94672d1563c152aee4f)

Does that actually work after a reboot?

---

### Post by aener on 2011-03-20
Hi
I'm afraid I'm stuck here in the same boat.
I've tried just about every solution posted in this thread and none of it has worked.
I'm a newbie, which means I've gotten lost in all the changes I've made.
Any chance you could help yet another newbie out?

I have an Advent 5411 trying to run Ubuntu 10.10

I've done that ALSA information thing - here's the link: [http://www.alsa-project.org/db/?f=a871cfebc96162355e09f1db551748f506419d22](http://www.alsa-project.org/db/?f=a871cfebc96162355e09f1db551748f506419d22)

I also made a couple of changes - though I can't remember what to alsa-base.conf. I'll paste the whole file just below 'cause I'm not sure what you might need.

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=thinkpad






I think the only change I've made is that last line, and changed it from model=laptop to a few different things. I know I don't have a thinkpad - but it's the last thing I tried.
Thanks for any help you can give.

---

### Post by lidex on 2011-03-20
@aener
Advent? Not familiar with that one. Can you post these outputs please:
BIOS / Motherboard info:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by aener on 2011-03-21
> **lidex said:**
> @aener
Advent? Not familiar with that one. 
Count yourself lucky! They're a nightmare for drivers (in Windows), and seem to be problematic in Linux too :(

BIOS results:
```
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Flex
    Version: DT.92.12
    Release Date: 07/17/2008
    Address: 0xE59B0
    Runtime Size: 108112 bytes
    ROM Size: 1024 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PC Card (PCMCIA) is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        ACPI is supported
        USB legacy is supported
        AGP is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
```

MoBo results:
```
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Advent
    Product Name:         
    Version: Rev1.DT.92.12
    Serial Number: V87RM00X07499F311X

Handle 0x0012, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Disabled
    Description: HD-Audio

```It's a real shame this is such an issue. It's a bloody nice OS, otherwise.

---

### Post by Hip-Hopapotamus on 2011-03-22
> **Hip-Hopapotamus said:**
> Installed 10.10, initially laptop speakers worked, but headphone jack didn't. After updates no sound at all. I have an Asus K52 and followed the steps on this model's thread with no success.

Having a problem with alsa-driver-linuxant. It said the build failed and to review the buld log.

Then it listed this:

dpkg: error processing alsa-driver-linuxant (--install):
subprocess installed post-installation script returned error exit status 2

Is there any way I can post the log file?

Any advice as to why alsa-driver-linuxant is causing problems?

---

### Post by lidex on 2011-03-22
@Hip-Hopapotamus
The kernel upgrade probably overwrote your linuxant driver. Let's see your alsa info:
```
dpkg -l | grep "alsa"
```
AND
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by aener on 2011-03-23
Does not responding again mean you don't know about this one?
Fine if not - thought I'd ask so I know whether to give up on it or not.

---

### Post by pbutto42 on 2011-03-23
i am having same problem with headphone jack i have a dell inspiron m5010 headphones worked last night and this morning not nothing. this is realy driving me nuts this is link      [http://www.alsa-project.org/db/?f=82954d191f07b1589c4f0561d528e46ed412bf6f](http://www.alsa-project.org/db/?f=82954d191f07b1589c4f0561d528e46ed412bf6f)

---

### Post by lidex on 2011-03-23
> **aener said:**
> Does not responding again mean you don't know about this one?
Fine if not - thought I'd ask so I know whether to give up on it or not.

Very hard to find info on this board. From what I have gleaned, it is a rebadged ECS. A bios update may be helpful, but first try changing the model using these options:
 ```

  ref		Reference board
  dell-m42	Dell (unknown)
  dell-m43	Dell Precision
  dell-m44	Dell Inspiron
  eapd		Keep EAPD on (e.g. Gateway T1616)
  auto		BIOS setup (default)
```

Try 'ref' and 'auto' first.

---

### Post by aener on 2011-03-24
> **lidex said:**
> Very hard to find info on this board.

:( Apologies for being a pain.
What do I do with these codes? (I'm a bit of a n00b :oops: )
Are they different things to put on the last line of the alsa-base.conf?

---

### Post by lidex on 2011-03-24
> **aener said:**
> :( Apologies for being a pain.
What do I do with these codes? (I'm a bit of a n00b :oops: )
Are they different things to put on the last line of the alsa-base.conf?

Yes.Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model= 
```
Save. Close. Reboot.

---

### Post by aener on 2011-03-25
[FONT=Courier New]##### # # ##### # # # # # # ##### # # # #[/FONT]
[FONT=Courier New]# # # # # ## # # # # # # # # # # #[/FONT]
[FONT=Courier New]# ##### ##### # # # ## # # # # # # #[/FONT]
[FONT=Courier New]# # # # # # ## # # # # # # # [/FONT]
[FONT=Courier New]# # # # # # # # # # ##### ##### # #[/FONT]

[FONT=Courier New]eapd got it working for me![/FONT]

[FONT=Courier New]Many many many many loves.[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]Edit: Forum ASCII art fail :oops:[/FONT]
[FONT=Courier New]It DID say a big "THANK YOU!!"[/FONT]
[FONT=Courier New]...The thought's there still ;)[/FONT]

---

### Post by FloydPink on 2011-03-25
@lidex,

I posted [this thread]("http://ubuntuforums.org/showthread.php?p=10601237") yesterday and from a reply there I got to this thread.

This is the output from the alsa-info.sh script - [http://www.alsa-project.org/db/?f=85fcef10c898915d64ebe47b5ab2d6d842241150](http://www.alsa-project.org/db/?f=85fcef10c898915d64ebe47b5ab2d6d842241150)

It would be great if you could help me fix the problems with the docking station...

Thank you

---

### Post by David Anders on 2011-03-31
Same problem, link is: [http://www.alsa-project.org/db/?f=8d9c851e99c2cbcaac0f8a354634f9c49e338702](http://www.alsa-project.org/db/?f=8d9c851e99c2cbcaac0f8a354634f9c49e338702) ... Haven't done anything with alsa re-installation yet, but I'll try it when I get home.

---

### Post by Yellow Pasque on 2011-03-31
> **David Anders said:**
> Same problem, link is: [http://www.alsa-project.org/db/?f=8d9c851e99c2cbcaac0f8a354634f9c49e338702](http://www.alsa-project.org/db/?f=8d9c851e99c2cbcaac0f8a354634f9c49e338702) ... Haven't done anything with alsa re-installation yet, but I'll try it when I get home.
googling around, i found 5 -10 reports of the same thing for that model and no one was able to fix it.

---

### Post by lidex on 2011-03-31
> **FloydPink said:**
> @lidex,

I posted [this thread]("http://ubuntuforums.org/showthread.php?p=10601237") yesterday and from a reply there I got to this thread.

This is the output from the alsa-info.sh script - [http://www.alsa-project.org/db/?f=85fcef10c898915d64ebe47b5ab2d6d842241150](http://www.alsa-project.org/db/?f=85fcef10c898915d64ebe47b5ab2d6d842241150)

It would be great if you could help me fix the problems with the docking station...

Thank you

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=basic" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**
Now post this output:
```
aplay -l
```

---

### Post by FloydPink on 2011-03-31
@lidex, Thank you for the reply...

Here is the output:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by lidex on 2011-04-01
> **FloydPink said:**
> @lidex, Thank you for the reply...

Here is the output:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I think your issue has something to do with the lack of a digital device. Can you provide this output please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```
Next boot into windows and make sure audio is configured and working properly in the dock, then restart into ubuntu without shutting down. Check aplay for digital device.

---

### Post by ElSid on 2011-04-01
Hi all, I have a slightly different problem with my headphones. I'm a new Ubuntu user running 10.10 on an asus eee pc. When i plug in my headphones i only get sound from the left. Ive tried fiddling around with the sound settings but nothing seems to work. Testing the laptop speakers you get sound right an left, different connectors dont improve it and changing the balance doesnt work (full left gives what you would expect, full right gives you no sound) Its kinda weird in that when i connect my surround sound through the headphone jack i get sound in all the speakers. Tried a few different headphones so its not them that are broken.

Any ideas?

Thanks.

---

### Post by Yellow Pasque on 2011-04-01
@ElSid: That sounds like a good one to send upstream: [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/docs/HD-Audio.html#_speaker_and_headphone_output](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/docs/HD-Audio.html#_speaker_and_headphone_output)

---

### Post by ElSid on 2011-04-02
Thanks Temujin, that looks like it could be solution. But excuse my ignorance that i still cant work out how to fix it! I guess i need to fiddle with the audio driver, but how do i get at it? Thanks again.

---

### Post by nitinroger123 on 2011-04-02
Hi,

I've been having similar problems. My headphone jack is not detected and also my mic does not work. I'm lost. Here are the details of wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

Alsa info :  [http://www.alsa-project.org/db/?f=562e6f88408cf23dc5de62747d6129e2e70b5a62](http://www.alsa-project.org/db/?f=562e6f88408cf23dc5de62747d6129e2e70b5a62)


Thanks a lot for your help!

---

### Post by lidex on 2011-04-02
> **nitinroger123 said:**
> Hi,

I've been having similar problems. My headphone jack is not detected and also my mic does not work. I'm lost. Here are the details of wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

Alsa info :  [http://www.alsa-project.org/db/?f=562e6f88408cf23dc5de62747d6129e2e70b5a62](http://www.alsa-project.org/db/?f=562e6f88408cf23dc5de62747d6129e2e70b5a62)


Thanks a lot for your help!
Try changing the position fix value in alsa-base.conf
Currently you have this:
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```
Change the digit 1 to digit 0 save and reboot. Then post this output:
```
aplay -l
```

To edit:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```

---

### Post by FloydPink on 2011-04-02
> **lidex said:**
> I think your issue has something to do with the lack of a digital device. Can you provide this output please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```Here's the output:```
hari@laptop:~$ sudo dmidecode -t bios
[sudo] password for hari: 
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: R0110F2
    Release Date: 12/22/2005
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 512 kB
    Characteristics:
        PCI is supported
        PC Card (PCMCIA) is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        8042 keyboard services are supported (int 9h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported

hari@laptop:~$ sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.3 present.

hari@laptop:~$ 
```> **lidex said:**
> Next boot into windows and make sure audio is configured and working properly in the dock, then restart into ubuntu without shutting down. Check aplay for digital device.aplay was unchanged after a restart from WinXP```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```No luck as yet with getting the speakers to work... Thanks nevertheless, for all the help...

---

### Post by lidex on 2011-04-03
@FloydPink
I think you should look at a bios update.

---

### Post by caleberx on 2011-04-03
Here is my info, much appreciated.

[http://www.alsa-project.org/db/?f=1d0ea714ea1ac9d871d4dba3de4abd76bbdaf0bc](http://www.alsa-project.org/db/?f=1d0ea714ea1ac9d871d4dba3de4abd76bbdaf0bc)

---

### Post by lidex on 2011-04-03
> **caleberx said:**
> Here is my info, much appreciated.

[http://www.alsa-project.org/db/?f=1d0ea714ea1ac9d871d4dba3de4abd76bbdaf0bc](http://www.alsa-project.org/db/?f=1d0ea714ea1ac9d871d4dba3de4abd76bbdaf0bc)
So...no headphone, headphone doesn't mute speakers, ???
Add these lines to alsa-base.conf and reboot:
```
options snd-hda-intel model=lenovo-101e
options snd-hda-intel position_fix=1 enable=yes

```
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by caleberx on 2011-04-04
> **lidex said:**
> So...no headphone, headphone doesn't mute speakers, ???
Add these lines to alsa-base.conf and reboot:
```
options snd-hda-intel model=lenovo-101e
options snd-hda-intel position_fix=1 enable=yes

```
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

No sound out of headphone port, and it does not mute the computer speakers.  I also tried the the suggestion above, and it did not work.

---

### Post by lidex on 2011-04-04
Try changing the model to laptop

---

### Post by caleberx on 2011-04-04
> **lidex said:**
> Try changing the model to laptop

Still nope.

---

### Post by lidex on 2011-04-04
> **caleberx said:**
> Still nope.

OK. Edit alsa-base.conf again. Remove completely the second line and in the first change the model to ideapad

---

### Post by cubeist on 2011-04-05
My netbook uses the cx5084 chip and to save people some time I have tried every model I can think of in the model="xxxxxx" with no success.

It appears that while the cx5085 will work with ideapad or thinkpad, some of the other conexant chips like the cx5084 of cx5082 are subtly different.

---

### Post by lidex on 2011-04-05
> **cubeist said:**
> My netbook uses the cx5084 chip and to save people some time I have tried every model I can think of in the model="xxxxxx" with no success.

It appears that while the cx5085 will work with ideapad or thinkpad, some of the other conexant chips like the cx5084 of cx5082 are subtly different.

Doesn't matter. Sometimes the same chip on different boards requires a different model; sometimes a different chip on different boards takes the same model. So it's really the combination of codec chip + mobo configuration that matters.

---

### Post by cubeist on 2011-04-05
> **lidex said:**
> Doesn't matter. Sometimes the same chip on different boards requires a different model; sometimes a different chip on different boards takes the same model. So it's really the combination of codec chip + mobo configuration that matters.

That's interesting. Would you mind looking at my alsa info to see if I missed an option? thanks!
[http://www.alsa-project.org/db/?f=0c9444ec28e3f971422a18158cdcd2f59e879cd0](http://www.alsa-project.org/db/?f=0c9444ec28e3f971422a18158cdcd2f59e879cd0)

---

### Post by lidex on 2011-04-05
> **cubeist said:**
> That's interesting. Would you mind looking at my alsa info to see if I missed an option? thanks!
[http://www.alsa-project.org/db/?f=0c9444ec28e3f971422a18158cdcd2f59e879cd0](http://www.alsa-project.org/db/?f=0c9444ec28e3f971422a18158cdcd2f59e879cd0)

Not to be a killjoy, but this thread is for maverick - you're using natty, which is in development, and any issues with it need to go into the development forum:
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

And please file a bug against natty. Remove any alsa-base.conf edits and bring your alsa back to default:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

For the bug:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by JohnWillyam on 2011-04-06
Compaq Presario:
Digital and Analog audio output

I'm using the digital out for speakers, works fine, even though sound preference output shows "analog speakers".

headphones do not work, no options for headphones in sound preferences(other than output-connector-analog headphones.. but has no change).

and console alsamixer doesn't show the slider for the headphones(it does show the mute/unmute box).

[http://www.alsa-project.org/db/?f=9395e1948339fe96efcdc1ae225ca6524e173b16](http://www.alsa-project.org/db/?f=9395e1948339fe96efcdc1ae225ca6524e173b16)

thanks

---

### Post by lidex on 2011-04-07
> **JohnWillyam said:**
> Compaq Presario:
Digital and Analog audio output

I'm using the digital out for speakers, works fine, even though sound preference output shows "analog speakers".

headphones do not work, no options for headphones in sound preferences(other than output-connector-analog headphones.. but has no change).

and console alsamixer doesn't show the slider for the headphones(it does show the mute/unmute box).

[http://www.alsa-project.org/db/?f=9395e1948339fe96efcdc1ae225ca6524e173b16](http://www.alsa-project.org/db/?f=9395e1948339fe96efcdc1ae225ca6524e173b16)

thanks

Hopefully just adding a model quirk will solve that. A lot to choose from for that codec, let's narrow it down:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

Also unmute your 'Front' mixer element.

---

### Post by JohnWillyam on 2011-04-07
```
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Phoenix Technologies, LTD
    Version:  5.13
    Release Date: 02/16/2007
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 512 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
    BIOS Revision: 5.13

Handle 0x0013, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 3
        n|US|iso8859-1
        n|US|iso8859-1
        r|CA|iso8859-1
    Currently Installed Language: n|US|iso8859-1

``````
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: ASUSTek Computer INC.
    Product Name: LEONITE
    Version: 5.00
    Serial Number: MS1C72S10501986

Handle 0x0012, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Enabled
    Description: Intel(R) HD Audio

```

---

### Post by caleberx on 2011-04-07
> **lidex said:**
> OK. Edit alsa-base.conf again. Remove completely the second line and in the first change the model to ideapad

Still no.

Also I do not know if I posted it earlier but this is from lscpi.

```

00:01.1 Audio device: ATI Technologies Inc Device 1314
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)

```

---

### Post by lidex on 2011-04-08
> **JohnWillyam said:**
> ```
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Phoenix Technologies, LTD
    Version:  5.13
    Release Date: 02/16/2007
    

```

I'm going to suggest a bios update. In the meantime try this:
```
echo "options snd-hda-intel model=asus-p5q" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by JohnWillyam on 2011-04-09
using the wrong selections I CAN get headphones and speakers, together or separate.

now headphones work using digital output selection on "speakers", and the digital speakers(4.1) still only work on the analog output selection for speakers and headphones.

maybe the product spec can help anything? motherboard P5LP-LE[U]:
[/U][http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00877022&lc=en&dlc=en&cc=us&lang=en&product=3377255#N79](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00877022&lc=en&dlc=en&cc=us&lang=en&product=3377255#N79)

I'll be glad to help if it matters to make it correct.

thanks lidex

---

### Post by lidex on 2011-04-09
> **JohnWillyam said:**
> using the wrong selections I CAN get headphones and speakers, together or separate.

now headphones work using digital output selection on "speakers", and the digital speakers(4.1) still only work on the analog output selection for speakers and headphones.

maybe the product spec can help anything? motherboard P5LP-LE[U]:
[/U][http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00877022&lc=en&dlc=en&cc=us&lang=en&product=3377255#N79](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00877022&lc=en&dlc=en&cc=us&lang=en&product=3377255#N79)

I'll be glad to help if it matters to make it correct.

thanks lidex
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Try changing the model in the line beginning 'snd-hda-intel'
One a a time. Save and reboot each time. Options:
```
auto
6stack-dig
w2jc
```

---

### Post by conualfy on 2011-04-11
The solution for other Toshiba laptop (L650, etc.) works for Satellite C650 too:



```
sudo gedit /etc/modprobe.d/alsa-base.conf
```add this in the end:

```
options snd-hda-intel model=thinkpad position_fix=1 enable_msi=1 
```enjoy the headphones!

---

### Post by JohnWillyam on 2011-04-12
thanks for the help lidex,

it looks like I'll have to live with the 6stack-dig option for now.

it's the best one so far, at least this way I can now get headphones, and speakers properly.. it's just that they aren't labeled properly..

I pulled out some old analog speakers and tested all the analog surround connections and it all seems fine.

I'll go read-up on alsa to see if I can get the SPDIF stuff working properly.

thanks again!

---

### Post by lidex on 2011-04-12
> **JohnWillyam said:**
> thanks for the help lidex,

it looks like I'll have to live with the 6stack-dig option for now.

it's the best one so far, at least this way I can now get headphones, and speakers properly.. it's just that they aren't labeled properly..

I pulled out some old analog speakers and tested all the analog surround connections and it all seems fine.

I'll go read-up on alsa to see if I can get the SPDIF stuff working properly.

thanks again!

There are other models, but those seemed most appropriate.
Enter this command and scroll down to the ALC888 section:
```
zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
```

Did you look into a bios update?

---

### Post by henriette on 2011-04-30
Hello!

thanks to Lidex I managed to get sound out of my headphones by adding this line: options snd-hda-intel model=thinkpad to the the end of the file located at /etc/modprobe.d/alsa-base.conf

Now the headphones work great but the microphone is not working anymore. I tested it in skype and also tried in alsamixer and pulse audio volume control to adjust settings for the mic, but it seem like no microphones (no eternal and no internal) are even recognised "no input devices available", or "no capture devices installed" is what I see there now.

I also tried to update alsa but no effect. 

Here is the link to the alsa info output: [http://www.alsa-project.org/db/?f=5b7e64ff2e025ea296394d30fead0118944a3727](http://www.alsa-project.org/db/?f=5b7e64ff2e025ea296394d30fead0118944a3727)

I really hope one of you can help me with this!

Maybe you should know that I've only installed Ubuntu about a week ago.. this is all completely new to me, so please forgive me if I sound confused!

---

### Post by lidex on 2011-04-30
> **henriette said:**
> Hello!

thanks to Lidex I managed to get sound out of my headphones by adding this line: options snd-hda-intel model=thinkpad to the the end of the file located at /etc/modprobe.d/alsa-base.conf

Now the headphones work great but the microphone is not working anymore. I tested it in skype and also tried in alsamixer and pulse audio volume control to adjust settings for the mic, but it seem like no microphones (no eternal and no internal) are even recognised "no input devices available", or "no capture devices installed" is what I see there now.

I also tried to update alsa but no effect. 

Here is the link to the alsa info output: [http://www.alsa-project.org/db/?f=5b7e64ff2e025ea296394d30fead0118944a3727](http://www.alsa-project.org/db/?f=5b7e64ff2e025ea296394d30fead0118944a3727)

I really hope one of you can help me with this!

Maybe you should know that I've only installed Ubuntu about a week ago.. this is all completely new to me, so please forgive me if I sound confused!

Not sure how you updated alsa, but it doesn't look complete. Try the alsa-upgrade script via the link in my sig.

---

### Post by MarcW10 on 2011-05-02
Same problem. Laptop type Medion Akoya, sound card is ATI X1200, audio codec is Sigmatel STAC9205. Any ideas? Please, I've been two days trying to figure this out and it's making me crazy!

---

### Post by JAS_21 on 2011-05-30
I have the same issue on my Toshiba laptop, model L645D


I entered: gksudo gedit /etc/modprobe.d/alsa-base.conf

Results:
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2



I am a noob to linux BTW. So any help is appreciated.

---

### Post by lidex on 2011-05-30
Headphone problems in maverick??

[http://www.google.com/search?q=headphone+10.10+maverick&sitesearch=ubuntuforums.org](http://www.google.com/search?q=headphone+10.10+maverick&sitesearch=ubuntuforums.org)

---

### Post by JAS_21 on 2011-05-30
> **lidex said:**
> Headphone problems in maverick??

[http://www.google.com/search?q=headphone+10.10+maverick&sitesearch=ubuntuforums.org](http://www.google.com/search?q=headphone+10.10+maverick&sitesearch=ubuntuforums.org)


I got it. Sorry, I did search before I posted. I wasn't sure which model to type in. I couldn't find the one for my model number.

---

### Post by lidex on 2011-05-31
> **JAS_21 said:**
> I got it. Sorry, I did search before I posted. I wasn't sure which model to type in. I couldn't find the one for my model number.

```
zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
```
For the models.

The basics you need to select a model are the make/model/codec.
The first two you know, find the third thusly:
```
head -n 1 /proc/asound/card*/codec#*
```

---

### Post by techtornado on 2011-07-04
I do have the same problem....My front mic and headphone are not working in 10.10 and 11.04 while it was working fine with 10.04....mine is a desktop  with asus motherboard....here is my ALSA information 
[http://www.alsa-project.org/db/?f=10d0c0fde891ecd4698590eb4dc33999d1b26ae3](http://www.alsa-project.org/db/?f=10d0c0fde891ecd4698590eb4dc33999d1b26ae3)

---

### Post by lidex on 2011-07-05
> **techtornado said:**
> I do have the same problem....My front mic and headphone are not working in 10.10 and 11.04 while it was working fine with 10.04....mine is a desktop  with asus motherboard....here is my ALSA information 
[http://www.alsa-project.org/db/?f=10d0c0fde891ecd4698590eb4dc33999d1b26ae3](http://www.alsa-project.org/db/?f=10d0c0fde891ecd4698590eb4dc33999d1b26ae3)

Try this using a Terminal
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by techtornado on 2011-07-06
Terminal showed this -- "options snd-hda-intel model=auto" ,as i entered the code...but still mic and headphone are not working.....

---

### Post by lidex on 2011-07-06
> **techtornado said:**
> Terminal showed this -- "options snd-hda-intel model=auto" ,as i entered the code...but still mic and headphone are not working.....

Post amixer output please:
```
amixer
```

---

### Post by techtornado on 2011-07-07
> **lidex said:**
> Post amixer output please:
```
amixer
```


Simple mixer control 'Master Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 11 [35%] [-18.00dB] [on]
  Front Right: Playback 11 [35%] [-18.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 251 [98%] [0.80dB]
  Front Right: Playback 251 [98%] [0.80dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 42 [100%] [0.00dB] [on]
  Front Right: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 3 [100%] [30.75dB]
  Front Right: Capture 3 [100%] [30.75dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 42 [100%] [0.00dB] [on]
  Front Right: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 42
  Mono: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 42
  Mono: Playback 42 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 12 [39%] [-16.50dB] [on]
  Front Right: Playback 12 [39%] [-16.50dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 3 [100%] [30.75dB]
  Front Right: Capture 3 [100%] [30.75dB]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 30 [97%] [28.50dB] [on]
  Front Right: Capture 30 [97%] [28.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'OFF' 'ON'
  Item0: 'OFF'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Stereo Mixer' 'Rear Mic' 'Front Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [on]
  Front Right: Playback 0 [0%] [-34.50dB] [on]
Simple mixer control 'Smart 5.1',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]

---

### Post by lidex on 2011-07-07
Try toggling the independent HP value

---

### Post by techtornado on 2011-07-08
> **lidex said:**
> Try toggling the independent HP value


toggled it (ON/OFF)....but still no sound...please help!

---

### Post by lidex on 2011-07-08
> **techtornado said:**
> toggled it (ON/OFF)....but still no sound...please help!

For the mic try changing the input to rear mic and adjusting the level up on one side only.
```
Simple mixer control 'Input Source',0
Capabilities: cenum
Items: 'Stereo Mixer' 'Rear Mic' 'Front Mic' 'Line'
Item0: [COLOR="Red"]'Front Mic'[/COLOR]

Simple mixer control 'Rear Mic',0
Capabilities: pvolume pswitch penum
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left:[COLOR="Red"] Playback 0 [0%][/COLOR] [-34.50dB] [on]
Front Right: Playback 0 [0%] [-34.50dB] [on]
```

---

### Post by kaiwen123 on 2011-07-09
Thank you so much "lidex". I was able to solve problem "speaker jack on sound issue" on my Toshiba L645D-S4050 with your suggestion by doing the two steps below. Thank you so much!!!
 gksudo gedit /etc/modprobe.d/alsa-base.conf Insert this line at the bottom:
 	Code:
 	 options snd-hda-intel model=thinkpad

---

### Post by kf7fdb on 2011-07-19
I am also having the problem of my headphone jack not working. 

[http://www.alsa-project.org/db/?f=a626e9939505b6b8e1bfc79a46861eed9e63f7ee](http://www.alsa-project.org/db/?f=a626e9939505b6b8e1bfc79a46861eed9e63f7ee)

---

### Post by cubanjinx on 2011-07-20
I hope that this thread isn't dead. Have been trying to find a fix with (obviously) no avail.

Acer Aspire
[http://www.alsa-project.org/db/?f=484a065a53a6db7f40314f9c1510859f9d17164f](http://www.alsa-project.org/db/?f=484a065a53a6db7f40314f9c1510859f9d17164f)

I used to have the "dummy output" problem but after a fresh install of Natty I have sound back in my speakers, just not in my headphones.


Update:
I have tried
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```
and
```
options snd-hda-intel model=acer position_fix=1 enable=yes
```
and
```
options snd-hda-intel model=aspire position_fix=1 enable=yes
```

Each one of those gives me sound back in my headphones, but outputs to my speakers as well.




Thanks for any help/tips in advance!

---

### Post by ritchiewall on 2011-07-20
Hey there. So frustrated with the lack of my microphone that I tried to do a fresh install to ensure there were no errors but that took hours and didn't work. 

So, please can someone look at this link and help? I am new to linux and it's great apart from not being able to use google talk and skype!

[http://www.alsa-project.org/db/?f=2a2ad94018e3376d8291fc980e37806671292aab]("http://www.alsa-project.org/db/?f=2a2ad94018e3376d8291fc980e37806671292aab")

---

### Post by claudehopper on 2011-07-20
no sound

here's the alsa output

[http://www.alsa-project.org/db/?f=08ead7fc4051b89ffe645e0fb0f1d22d3766865c](http://www.alsa-project.org/db/?f=08ead7fc4051b89ffe645e0fb0f1d22d3766865c)

sound worked when the system was running with windows drivers and with ubuntu running on a partition but now that it is the only o/s there is no sound from neither the line out or the headphone socket

any suggestions? ](*,)

---

### Post by lidex on 2011-07-22
@kf7fdb
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

@cubanjinx
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**
[You'll need to remove any previous entries]

@ritchiewall
You are off-topic. How do you plead? I'll allow it , even though I shouldn't. Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=asus-mode3" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` [B]Reboot[/B

@claudehopper
Off-topic as well.
You will need to supply make/model/motherboard info.

---

### Post by cubanjinx on 2011-07-22
@cubanjinx
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**
[You'll need to remove any previous entries]

After removing all lines I currently had in there, with that code my headphones no longer worked. Once I put back one of the codes I previously had, they began to work again. Still no automute. I think it just might be a bug they haven't address for my machine yet, sadly.

---

### Post by sunilsaini on 2011-07-23
here is the output link 
[http://www.alsa-project.org/db/?f=9a017c85f25e03414656aa742fb0a2abfb59d2d9](http://www.alsa-project.org/db/?f=9a017c85f25e03414656aa742fb0a2abfb59d2d9)

---

### Post by todovan on 2011-08-24
i have kind of the same problem, also, it's not just headphone, comes with integrated microphone, please help me.


[http://www.alsa-project.org/db/?f=fb2795cc70723f7a9583b5f3c932ebb9d0f86b7b](http://www.alsa-project.org/db/?f=fb2795cc70723f7a9583b5f3c932ebb9d0f86b7b)

---

### Post by conualfy on 2011-08-24
You should try to upgrade your system to Natty (11.4) as at some point the upgraded Natty fixed my problem without any manual hack. Maybe it works with yours, too.


> 
i have kind of the same problem, also, it's not just headphone, comes with integrated microphone, please help me.

---

### Post by todovan on 2011-08-24
> **conualfy said:**
> You should try to upgrade your system to Natty (11.4) as at some point the upgraded Natty fixed my problem without any manual hack. Maybe it works with yours, too.

thanks for the recommendation, actually i just upgraded to 11.04, but i don't know why it didn't work since on 10.4 i had the problem of dual reproduction, also, i did this.

> **lidex said:**
> Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=laptop position_fix=1 enable=yes 
```Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct  soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.[I]
and it worked for me, that solves the heaphone problem, any idea what to do with the microphone? thanks in advance.
[/I]

---

### Post by conualfy on 2011-08-24
So now your Ubuntu is version 11.4 with up-to-date updates?

I have no idea how to fix your problem, but check not to have any "mute" checked or some microphones with mute button on.

---

### Post by todovan on 2011-08-24
> **conualfy said:**
> So now your Ubuntu is version 11.4 with up-to-date updates?

I have no idea how to fix your problem, but check not to have any "mute" checked or some microphones with mute button on.

actually i just noticed some new updated (new kernel i think), i'll update and see how it goes (hope it doesn't screw up again the audio thing and it fixes the mic)

---

### Post by conualfy on 2011-08-24
Since your version have been lots of kernel updates and more other updates. I first installed 10.10, then 11.4 and permanently updated/upgraded. Switching Ubuntu versions did not work very well, I had to reinstall and it worked better.

In time I could see more bugs being repaired, so have patience and try to be updated. 
By the way, you will see a major difference as you'll have a different interface, Unity. It looks and works more like MacOS bar; it has some minuses, but mainly it's better than the old Gnome taking too much space on screen. As a tip: try to install CCSM and in Unity settings disable autohide and set icon size to minimum, 32 pixels.


Now I work on a virtual machine with the following Ubuntu (Oneiric Ocelot, 11.10) which seems to be even nicer, but it's still in alpha.


I learned it's better to have /home as a different partition, not to lose your personal data when reinstalling :)

---

