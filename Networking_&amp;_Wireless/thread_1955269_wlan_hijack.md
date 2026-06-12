---
title: "wlan hijack"
date: 2012-04-07
forum: Networking &amp; Wireless
---

### Post by FroheOstern on 2012-04-07
Hi everyone,

I have a samsung n100 MA05 Netbook which came with Nokia's Meego OS.

My friend installed easy peasy via usb on my device and ever since then the WLan isnt working. HELP??

My system summary tells me i am using Ubuntu 10.04 lucid, Kernel Linux 2.6.32-37-generic, GNOME 2.30.2. I hope someone could help me with this. I don't have much knowledge about computers and software so if someone could help me step by step, it would make my day. I don't even know how to type in a command...


Thanks a lot!

---

### Post by FroheOstern on 2012-04-08
hey i have the exact problem!!!! samsung n100 Ubuntu 10.04 lucid, Kernel Linux  2.6.32-37-generic

the problem seems to be solved and i would like to try it out but i have very little knowledge about computers. where would i type in all these commands that you posted???

---

### Post by praseodym on 2012-04-08
Open a terminal with "CTRL+ALT+T" and c/p these lines one by one

---

### Post by FroheOstern on 2012-04-08
hey thanks for getting back to me - um so it didnt work, but im sure i didnt enter it correctly. am i supposed to hit "enter" after every line? also i am not using the root account for this

---

### Post by FroheOstern on 2012-04-08
so i am getting this kind of error:

```
~$ sudo modprobe -rfv iwlagn 
~$ wget http://elektronenblitz63.de/download..._ubuntu.tar.gz
--2012-04-08 22:13:01--  http://elektronenblitz63.de/download..._ubuntu.tar.gz
Resolving elektronenblitz63.de... 82.165.83.231
Connecting to elektronenblitz63.de|82.165.83.231|:80... connected.
HTTP request sent, awaiting response... 300 Multiple Choices
Length: 427 [text/html]
Saving to: `download..._ubuntu.tar.gz.2'

100%[===================================================================================>] 427         --.-K/s   in 0s      

2012-04-08 22:13:01 (9.16 MB/s) - `download..._ubuntu.tar.gz.2' saved [427/427]

~$ tar xvf compat-wireless-2011-10-29_patched_ubuntu.tar.gz
tar: compat-wireless-2011-10-29_patched_ubuntu.tar.gz: Cannot open: No such file or directory
~$ cd compat-wireless-2011-10-29_patched_ubuntu
bash: cd: compat-wireless-2011-10-29_patched_ubuntu: No such file or directory
~$ make
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by Ms. Daisy on 2012-04-09
Easy Peasy is a Linux operating system that is built on an Ubuntu base. Basically they take Ubuntu and make a bunch of modifications to turn it into a new, different operating system. 

I would tell you to check out the easy peasy [support]("https://getsatisfaction.com/easypeasy") forum or wikis, but frankly they seem to seriously suck based on my quick review.  (I searched "wireless" in their wikis and got [this]("http://wiki.geteasypeasy.com/Wifi").  There are only 479 members in the support forum.)

You actually installed Easy Peasy on the hard drive of this computer, correct?  When  you turn on the computer it starts into Easy Peasy even if nothing is in the USB ports?

It sounds to me like you need a wireless driver.  Open a terminal (in */Applications/Utilities/* or query *Terminal* ```
  lspci -nn
```  
where it's a lower case "L" and not a number "one" in the first position.

---

### Post by Tanvile on 2012-04-09
> **FroheOstern said:**
> so i am getting this kind of error:

```
~$ sudo modprobe -rfv iwlagn 
~$ wget http://elektronenblitz63.de/download..._ubuntu.tar.gz
--2012-04-08 22:13:01--  http://elektronenblitz63.de/download..._ubuntu.tar.gz
Resolving elektronenblitz63.de... 82.165.83.231
Connecting to elektronenblitz63.de|82.165.83.231|:80... connected.
HTTP request sent, awaiting response... 300 Multiple Choices
Length: 427 [text/html]
Saving to: `download..._ubuntu.tar.gz.2'

100%[===================================================================================>] 427         --.-K/s   in 0s      

2012-04-08 22:13:01 (9.16 MB/s) - `download..._ubuntu.tar.gz.2' saved [427/427]

**/////// cd Downloads missing here :) ////**

~$ tar xvf compat-wireless-2011-10-29_patched_ubuntu.tar.gz
tar: compat-wireless-2011-10-29_patched_ubuntu.tar.gz: Cannot open: No such file or directory
~$ cd compat-wireless-2011-10-29_patched_ubuntu
bash: cd: compat-wireless-2011-10-29_patched_ubuntu: No such file or directory
~$ make
make: *** No targets specified and no makefile found.  Stop.
```


Please write:
```
pwd
``` and hit Enter.

Did it print out your home folder address?

The ```
tar xvf compat-wireless-2011-10-29_patched_ubuntu.tar.gz
```

works only in the immediate folder. It doesn't search recursively for files to extract.

Thus, you need to enter:
```
cd Downloads
```

and then use the code from tar xvf line. Write how it goes, ok? :)

_____________________________________

@**praseodym** Ah, now it finds the networks, but won't easily connect or doesn't connect at all. At first it was ok. The second day it didn't connect only when in my room. Now, it doesn't connect even near the router. And it's not traffic problems or such. We tried 24/7 with all other PC plugged off, only mine on.

---

### Post by FroheOstern on 2012-04-09
Hey Ms.Daisy thanks for getting back to me! Yep I installed easy peasy to my harddrive and yes you are right the easy peasy forums suck a lot!!! i entered what you suggested into the terminal but nothing happened. 

in another thread someone with the same netbook and ubunutu 10.04 had the same problem and could solve it with this code which doesnt seem to work for me... unless i type it in incorrectly in the terminal because im not so good with computer stuff

echo "blacklist iwlagn" | sudo tee -a /etc/modprobe.d/blacklist.conf # Ubuntu 10.04 only
sudo modprobe -rfv iwlagn 
wget [http://elektronenblitz63.de/download..._ubuntu.tar.gz]("http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz")
tar xvf compat-wireless-2011-10-29_patched_ubuntu.tar.gz 
cd compat-wireless-2011-10-29_patched_ubuntu
make
sudo make install
sudo modprobe iwlwifi      # Ubuntu 10.04 only, from 10.10 the module name is still "iwlagn"
ifconfig
iwconfig
iwlist chan
sudo iwlist scan
lsmod
dmesg | grep iwl

---

### Post by FroheOstern on 2012-04-09
hey Tanville - and I thought I was the only one with a n100 :)

so i did what you suggested and i got further this time with the codes but still getting some errors. 

```
pema@pema-laptop:~$ cd Downloads tar xvf compat-wireless-2011-10-29_patched_ubuntu.tar.gz
pema@pema-laptop:~/Downloads$ cd compat-wireless-2011-10-29_patched_ubuntu
bash: cd: compat-wireless-2011-10-29_patched_ubuntu: No such file or directory
pema@pema-laptop:~/Downloads$ make
make: *** No targets specified and no makefile found.  Stop.
pema@pema-laptop:~/Downloads$ sudo make install
make: *** No rule to make target `install'.  Stop.
pema@pema-laptop:~/Downloads$ sudo modprobe iwlwifi      # Ubuntu 10.04 only, from 10.10 the module name is still "iwlagn"
FATAL: Module iwlwifi not found.
pema@pema-laptop:~/Downloads$ 
```

---

### Post by praseodym on 2012-04-09
Check:

> locate compat-wireless-2011-10-29_patched_ubuntu.tar.gz

---

### Post by Ms. Daisy on 2012-04-09
Well that's something to start with.  Can you post a link to the thread where you got those direction?

In general I find it much easier to copy commands from the browser, then paste it into terminal using right click - paste.  I'm notorious for typos when I try to re-type it.

Let's also slow down running through the commands you posted. So you typed in each line and then pressed enter?  Then terminal returned some text and finally a prompt, then you typed in the next command?  As you did this, did you get errors or warnings?  If so please post those.  You can use your mouse to highlight everything in terminal, then (right click - copy) and paste them here.  Put the pasted text inside of the code tags (#), click the "Go Advanced" button to find the code tags.

---

### Post by FroheOstern on 2012-04-09
hm i did that but nothing happened. i also rebooted after that and no wlan connections appear.

---

### Post by FroheOstern on 2012-04-09
yes i did it line by line. i did not finish going through the whole thing this time as i got error messages right in the beginning as you can see here:

```
pema@pema-laptop:~$ cd Downloads tar xvf compat-wireless-2011-10-29_patched_ubuntu.tar.gz
pema@pema-laptop:~/Downloads$ cd compat-wireless-2011-10-29_patched_ubuntu
bash: cd: compat-wireless-2011-10-29_patched_ubuntu: No such file or directory
pema@pema-laptop:~/Downloads$ make
make: *** No targets specified and no makefile found.  Stop.
pema@pema-laptop:~/Downloads$ sudo make install
make: *** No rule to make target `install'.  Stop.
pema@pema-laptop:~/Downloads$ sudo modprobe iwlwifi      # Ubuntu 10.04 only, from 10.10 the module name is still "iwlagn"
FATAL: Module iwlwifi not found.
pema@pema-laptop:~/Downloads$
```
and the link to the thread is here:

[http://ubuntuforums.org/showthread.php?t=1880270&page=2](http://ubuntuforums.org/showthread.php?t=1880270&page=2)

---

### Post by praseodym on 2012-04-09
Hi,

please show

```
lspci -nnk | grep -iA2 net
lsusb
iwconfig
lsmod
sudo iwlist scan
```

---

### Post by praseodym on 2012-04-09
Did you forget to un-"tar" the package?

---

### Post by FroheOstern on 2012-04-09
un tar - what does that mean. so sorry, i have no clue

---

### Post by FroheOstern on 2012-04-09
Allright, here we go, it's long!
```

pema@pema-laptop:~$ lspci -nnk | grep -iA2 net
05:00.0 Network controller [0280]: Intel Corporation Device [8086:08ae]
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Kernel driver in use: r8169
    Kernel modules: r8169
pema@pema-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2232:1006  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
pema@pema-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pema@pema-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
dm_crypt               11331  0 
snd_hda_codec_realtek   203440  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
joydev                  8740  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               57438  0 
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  289715  4 
drm_kms_helper         29329  1 i915
drm                   163747  5 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
r8169                  34140  0 
video                  17375  1 i915
ahci                   32680  2 
mii                     4381  1 r8169
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
pema@pema-laptop:~$ sudo iwlist scan
[sudo] password for pema: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

---

### Post by FroheOstern on 2012-04-09
ok i just looked up what it means to untar. at what point in the code line though should i do that?

---

### Post by coffeecat on 2012-04-09
@FroheOstern, I have merged all your posts from one thread you joined, plus all the responses, into your original thread. As far as I can see they are for the same issue.

Please do not post support questions for the same problem in different threads or parts of the forum. This dilutes community effort.

---

### Post by Elfy on 2012-04-09
> **coffeecat said:**
> @FroheOstern, I have merged all your posts from one thread you joined, plus all the responses, into your original thread. As far as I can see they are for the same issue.

Please do not post support questions for the same problem in different threads or parts of the forum. This dilutes community effort.


That'll be why I had to fight vbulletin then :p

---

### Post by FroheOstern on 2012-04-09
oh ok thanks and sorry. it was just that noone replied to the thread and then i came across a solved problem with the exact same netbook model and op version that i had

---

### Post by praseodym on 2012-04-09
After "wget" the "tar" line, then "cd " and "make", etc

---

### Post by FroheOstern on 2012-04-09
hm ok so to untar the file would be the tar xvf command right? 

because with this i always get the 'no such file or directory found' error. initially the file is saved to my homefolder. i have also moved it once to downloads and done as tanville suggested but also then i get no such file or directory found.

---

### Post by praseodym on 2012-04-09
Take this direct link, and save it in /home, remove the others. Then open a new terminal, and continue with the tar-command:

[http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz](http://elektronenblitz63.de/downloads/compat-wireless-2011-10-29_patched_ubuntu.tar.gz)

---

### Post by FroheOstern on 2012-04-09
ok so this seemed to work. after downloading the direct link to home folder i proceeded with the tar command and this time the command seemed to work. so then many many lines and codes kept popping up. i had it finished and then wanted to proceed to enter 

make

and then i got another error message i think:

```
make -C /lib/modules/2.6.32-37-generic/build M=/home/pema/compat-wireless-2011-10-29_patched_ubuntu modules
/usr/src/linux-headers-2.6.32-37-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.32-37-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-37-generic'
/usr/src/linux-headers-2.6.32-37-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
  LD      /home/pema/compat-wireless-2011-10-29_patched_ubuntu/compat/built-in.o
/bin/sh: ar: not found
make[3]: *** [/home/pema/compat-wireless-2011-10-29_patched_ubuntu/compat/built-in.o] Error 127
make[2]: *** [/home/pema/compat-wireless-2011-10-29_patched_ubuntu/compat] Error 2
make[1]: *** [_module_/home/pema/compat-wireless-2011-10-29_patched_ubuntu] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-37-generic'
make: *** [modules] Error 2
pema@pema-laptop:~/compat-wireless-2011-10-29_patched_ubuntu$ 

```

---

### Post by praseodym on 2012-04-09
Did you install the tools to compile?

> sudo apt-get install build-essential linux-headers-$(uname -r)

---

### Post by FroheOstern on 2012-04-09
oh darn - i didnt! thanks for pointing it out to me. i'm doing it right now!

---

### Post by FroheOstern on 2012-04-09
so i did run the command to unpack those headers and at the end this comes. im not sure, does it mean i have to just reboot and then run the commands which could enable wlan?

```
Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.

pema@pema-laptop:~/compat-wireless-2011-10-29_patched_ubuntu$ 
```

---

### Post by houseworkshy on 2012-04-09
Just some handy tips for people who haven't used the terminal.  
Typing "man" in front of any command will bring up its' manual page, typing "q" will close that manual page.  
One can have many terminals open at the same time and copy and paste between them if you wish.  I usually have one open for the manual and another open to do things in.  
I noticed that the original poster was not familliar with the command line so this is timely and not off topic.
Amazing by the way, getting up to compiling that fast ( make file ) is pretty phenominal, at that rate could be a mod in a couple of weeks.
 
Oh and for future referance there is utility called "sysinfo" which can save a lot of time when you want to know/post system specs:  "sudo apt-get install sysinfo"  would be the command line way of getting it.  When installing it puts a link to itself in your Applications>System tools.   
Good luck with it all

---

### Post by FroheOstern on 2012-04-10
hi - thanks for the tips, it's all pretty new to me so every piece of information is useful to me.

so could someone help me figure out what this error message means so that i could proceed with the original command?

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.

pema@pema-laptop:~/compat-wireless-2011-10-29_patched_ubuntu$

---

### Post by FroheOstern on 2012-04-30
OK SOLVED :) whoever might be in a similar situation...

so in my case i had to install the latest linux headers AND the latest firmware in order to use the command that was suggested in one of the first posts to get my wlan working :)

thanks for everyones help

---

