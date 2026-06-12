---
title: "no sound"
date: 2006-02-07
forum: Multimedia &amp; Video
---

### Post by Nabba on 2006-02-07
no sound what so ever:-| 
i have followed the 'how to' but with no luck
i have a acer apire 1642WLMi, i can up load screenshots to my website if u want me to take any, i may or missed some thing, so i am willing to try things again

---

### Post by wncben on 2006-02-08
Hey, 
  I'm a newbie myself, but am also having some sound issues.  

First off...   Do you get any sound?    I always get the drum beats on the login page, even when I don't get sound anywhere else.  Ubuntu sets the sound to mute as a default so check your volume control.  Unmute anything that is not an 'iec' device.  if you don't have an iec device (ie a high end fiber optic audio device) and it ie not muted it will cause a problem and no sound.  You might have to go to alsa mixer in the terminal to disable iec devices.

There is lots of other help out there, including a pretty indepth trouble shooting guide which is stickied to the top of the list.

Hope this helps,  I'm still learning myself.  

~ol' Ben

---

### Post by Nabba on 2006-02-08
yes i have no sound what so ever, i have tryed that, i have went tho the how to, i have also try the fix found here: [https://wiki.ubuntu.com/SoundProblemsHoary](https://wiki.ubuntu.com/SoundProblemsHoary) but when i tryed to test in in multimedia systems selecter but i get a error saying "failed to construct test pipeline for 'OSS - open sound system' which sucks:neutral: :cry: err
so any ideas ppl...lets have some brain storming

---

### Post by wncben on 2006-02-08
I feel your Pain:( 

  My sound problem is similar, when i try to test in multimedia system selector, I get the same result.  When I do have sound I get a tone and a little slide bar.  My problem is intermittant, sometimes I have sound, sometimes not.  I havent had sound for two days, now when I boot up I get sound all the sudden.  Haven't done anything different, just sometimes it decides to work and sometimes not.  Sorry I haven't been much help.  Just letting you know that you are not sufferin alone;) 

~Ol' Ben

---

### Post by FarEast on 2006-02-08
Hi Nabba and wncben;) ,

Let me cut in!
We have to know at first which sound chip Nabba's machine has.

Execute the command below.  It detects sound chips on PCI bus.
```
$ lspci -v | grep audio
```

If nothing is shown, the chip may be on ISA bus.
Install 'isapnptools' to scan the bus.
```
$ sudo apt-get install isapnptools
$ pnpdump > isabus.txt
$ gedit isabus.txt
```
Look for information regarding the sound chip and paste it.

---

### Post by Nabba on 2006-02-09
ok...i dont think this is good...

andrew@apple:~$ lspci -v | grep audio
andrew@apple:~$
andrew@apple:~$ sudo apt-get install isapnptools
Reading package lists... Done
Building dependency tree... Done
isapnptools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andrew@apple:~$ pnpdump > isabus.txt
Unable to get io permission for WRITE_DATA: Operation not permitted
andrew@apple:~$ gedit isabus.txt

and that opens a blank .txt
the screen shot is here:

[http://www.nabba64.co.uk/sound.png](http://www.nabba64.co.uk/sound.png)

this link goes to the driver for windows [http://support.acer-euro.com/drivers/notebook/as_1640.html](http://support.acer-euro.com/drivers/notebook/as_1640.html)  it is the reltek one

---

### Post by FarEast on 2006-02-09
> andrew@apple:~$ pnpdump > isabus.txt
> Unable to get io permission for WRITE_DATA: Operation not permitted

Sorry.  It must be executed as root.  Add 'sudo' before pnpdump.

---

### Post by Nabba on 2006-02-09
it does not look good....
ok here is what i typed:

andrew@apple:~$ lspci -v | grep audio
andrew@apple:~$
andrew@apple:~$ sudo apt-get install isapnptools
Reading package lists... Done
Building dependency tree... Done
isapnptools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andrew@apple:~$ sudo pnpdump > isabus.txt
REALTIME operation timeout exceeded - Switching to normal scheduling
nanosleep failed: Interrupted system call
andrew@apple:~$ gedit isabus.txt

which opened isabus.txt (~) - getit with the following in side:

# $Id: pnpdump_main.c,v 1.27 2001/04/30 21:54:53 fox Exp $
# Release isapnptools-1.26
# 
# This is free software, see the sources for details.
# This software has NO WARRANTY, use at your OWN RISK
# 
# For details of the output file format, see isapnp.conf(5)
# 
# For latest information and FAQ on isapnp and pnpdump see:
# [http://www.roestock.demon.co.uk/isapnptools/](http://www.roestock.demon.co.uk/isapnptools/)
# 
# Compiler flags:  -DREALTIME -DHAVE_PROC -DENABLE_PCI -DHAVE_SCHED_SETSCHEDULER -DHAVE_NANOSLEEP -DWANT_TO_VALIDATE
# 
# Trying port address 0273
# Trying port address 027b
# Trying port address 0283
# Trying port address 028b
# Trying port address 0293
# Trying port address 029b
# Trying port address 02a3
# Trying port address 02ab
# Trying port address 02b3
# Trying port address 02bb
# Trying port address 02c3
# Trying port address 02cb
# Trying port address 02d3
# Trying port address 02db
# Trying port address 02e3
# Trying port address 02eb
# Trying port address 02f3
# Trying port address 02fb
# Trying port address 0303
# Trying port address 030b
# Trying port address 0313
# Trying port address 031b
# Trying port address 0323
# Trying port address 032b
# Trying port address 0333
# Trying port address 033b
# Trying port address 0343
# Trying port address 034b
# Trying port address 0353
# Trying port address 035b
# Trying port address 0363
# Trying port address 036b
# Trying port address 0373
# Trying port address 037b
# Trying port address 0383
# Trying port address 038b
# Trying port address 0393
# Trying port address 039b
# Trying port address 03a3
# Trying port address 03ab
# Trying port address 03b3
# Trying port address 03bb
# Trying port address 03e3
# Trying port address 03eb
# Trying port address 03f3
# Trying port address 03fb
# No boards found


i think i am buggered

---

### Post by Nabba on 2006-02-09
ha...i think i have found my problem
i think it is some thing to do with Intel HDA and alas

i will post back if i have some luck finding a fix

---

### Post by chageman on 2006-02-09
Hi Far East
as a newbie am trying to get sound to work and have followed your earlier instructions to identify the pci sound chip as follows

dch@Zeus:~$ lspci -v | grep audio
0000:01:08.0 Multimedia audio controller: Rockwell International Riptide PCI Aud io Controller
dch@Zeus:~$

not sure where or how to go from here to install proper drivers - any assistance would be appreciated

Best regards
cal

---

### Post by FarEast on 2006-02-09
Hi Nabba,

Sorry, my suggestions have not help:( .
Now you can remove the package 'isapnptools' by executing
'sudo dpkg -r isapnptools', for you need it no more.

> i think it is some thing to do with Intel HDA and alas
Is it?  Quite a few people complain about the sound chip.
I hope you will be able to make it!

------------
Hi Chageman,

I have googled and found the driver.
[http://www.linuxant.com/drivers/riptide/downloads.php](http://www.linuxant.com/drivers/riptide/downloads.php)

It will take a while before I can make a suggestion.

---

### Post by Nabba on 2006-02-10
hello,
far east i don't think i will get round this problem any time soon, 
i had a look at some other peoples fixes and it takes a level of Linux knowledge that i just don't have...i had a go at some of the fixes and copy and paste just does not work. so it boils down to two ways of doing it

1. wait till dapper drake as i think they fix the problem(tho i think it alsa fault)

2. learn tons more about how Intel hda(or as i like to call it crap on stick[-( ) works and how to get the bugger to work with Ubuntu.

tho i don't blame Ubuntu as i think it is alsa fault, and Ubuntu offers the best value for money....FREE!! so it is Ubuntu for email surfing the net and office stuff, and M$(give me all your money and i spit in your face) windows xp for dvds and cd and swishmax(till i find a good Linux replacement)

and anyway, i don't want every thing handed on a plate for me(just 95% of it)

---

### Post by Cathbard on 2006-02-10
I just installed a fresh copy of Ubuntu and let it do an update. I have done this heaps of times on this machine and this is the first time this has happened.
I use a Soundblaster Audigy 2 on a P4 (Asus P4S8X) and I am also haviing alsa problems. When I try to test alsa I get "Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'
I have installed the things I normally do but this time it's a no go. I looked for /dev/dsp and it wasn't there but there is a dsp1. I created a symbolic link to dsp1 called dsp and most things started to work (including Teamspeak2 and gtkguitune)
However this is a sub-optimum and doesn't fix everything. Most things *are* working like Amarok and Kaffeine but I can't setup jackd and things because alsa is all screwy.

I am noticing alot of people having this problem with all sorts of different hardware so I am thinking this is a bug somewhere yes?

---

### Post by brucetan on 2006-02-10
dear all,

i just did a number of fresh installation of ubuntu, kubuntu and edubuntu, etc. (all in breezy badger release) in last 2 days to my old PC.  All was successful but no sound.   :cry: 

I had googled for past solutions but still no luck.

The PC configuration is as follows:
CPU:  AMD Althon 600Mhz
Memory: 256MB
HD: 30GB (IDE)
SoundCard: SB Live Value (Model CT4730)
CDRW/DVD R
OS: edubuntu Breezy Badger release 5.10

The output of "lsmod | grep snd" is as follows:
===============================
boon@edubuntu:~$ lsmod | grep snd
snd_ens1371            22240  3
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  12 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  1 snd_pcm
boon@edubuntu:~$
===========================

The output of "lspci | grep audio" is as follows:
===============================
boon@edubuntu:~$ lspci | grep audio
0000:00:0b.0 Multimedia audio controller: Creative Labs Ectiva EV1938
boon@edubuntu:~$

The output of "ps ax | grep esd" is as follows:
===============================
boon@edubuntu:~$ ps -ax | grep esd
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
 7984 ?        S      0:00 /usr/bin/esd -nobeeps
 9159 pts/0    S+     0:00 grep esd
boon@edubuntu:~$

The output of "lscat /etc/libao.conf" is as follows:
===============================
boon@edubuntu:~$ cat /etc/libao.conf
default_driver=esd
boon@edubuntu:~$

The output of "lsmod | grep oss" is as follows:
===============================
boon@edubuntu:~$ lsmod | grep oss
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd                    48644  12 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
boon@edubuntu:~$
 
Other attempts' were the following:
      (1) I have tried "modrobe snd_emu10k1"  but still  not working;
      (2) 1 also used "alsamixer" to ensure the speaker is not mute and Master and PCM are turned on.

Can someone help me?  many thanks in advance.

---

### Post by brucetan on 2006-02-10
The output of "cat /proc/asound/cards" for my PC is:
============================
boon@edubuntu:~$ cat /proc/asound/cards
0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                     Ensoniq AudioPCI ENS1371 at 0xa000, irq 10
boon@edubuntu:~$
>> i.e., not the same as the physical card which is SB Live PCI (model CT4730)!

Any way to correct this error?

---

### Post by Rasymas on 2006-02-10
I have same problems.. No sound for video files.. Does anyone know the soliution??? if that will help here's some info about my pc:

```
arnoldas@ubuntu:~$ lspci -v | grep audio
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)

```

---

### Post by Minyaliel on 2006-02-10
I remember it took me *ages* to figure out sounds and how to make DVD's play like they should... but anyway, don't be disencouraged :) I'm no good at the sound thing, regarding mp3's you should take a look at the restricted formats page in the wiki: [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29) (here you will also find info on how to make DVD's work).

---

### Post by wncben on 2006-02-10
It seems like having no sound is a very common problem, and that getting the ol' "unable to construct pipeline' message is a symptom of the problem.  Is the sound problem a constant with everybody or is it an intermittant problem like mine?  My problem seems to come and go with no rhyme or reason.  Sometimes I get sound, sometimes not.  If I fool around with alsa sometimes i can get sound, but it only lasts until i log out.  sometimes when I log in I get sound without even trying.  The only constant is the taunting drum beats at login.  (one weird thing, whin I don't have sound I get a double beat, ::badadum badadum:: but I know sound is going to work when I get a single  ::badum:: )
    I have tried most of the 'fixes' but nothing seems to fix the problem permanently.  
  I think that there is something in alsa, but the thing is that esd and oss also refuse to utter a beep when my sound is not working.  
  My biggest question is why does the sound change without notice,  without any changes on my part?  Why does it work sometimes and sometimes not?  I don't get it. :confused: 

~ol' Ben

---

### Post by wncben on 2006-02-10
Has anybody tried Kubuntu?  It seems like there are fewer sound complaints from Kubuntu users, but maybe there are just fewer of em:p   

~Ol' Ben

---

### Post by brucetan on 2006-02-11
I had tried Kubuntu.  The no sound problem was the same as in uBuntu and edubuntu!

Does anyone out there have a working ubuntu using SB Live 16 PCI with AMD Althlon? i.e., with sound.

---

### Post by Cathbard on 2006-02-11
I get sound but a lot of things only started after I created a symbolic link to /dev/dsp1. It isn't a complete solution because i can't setup alsa properly. Where is dsp? This is about the fourth time I've installed Ubuntu and it's the first time this has happened.
I'm tempted to remove the ubuntu alsa and compile the latest one from alsa themselves. Dunno ..........  I'll keep watching the forum anyway for this "Failed to construct test pipeline for 'ALSA error". It seems to be indicitive of a broader problem, it's probably one line of code somewhere. Maybe I should just be patient and observant.
Where's that book on Zen and The Art of Motorcycle Mechanics?

---

### Post by FarEast on 2006-02-11
Hi brucetan,

wsmoser2004 and I had once struggled with the issue.
The solution for the moment was to use OSS driver instead.

[http://ubuntuforums.org/showthread.php?t=114955](http://ubuntuforums.org/showthread.php?t=114955)

----------

Hi all,

Here I get the same error saying "Failed to construct test pipeline for ALSA"
when I try to test sound after choosing ALSA for the output/input in the
multimedia system selector(So I choose esd).  And yet I can listen to CDs
with CD-Player and mp3 files with xmms.

$ cat /proc/asound/cards
0 [YMF744         ]: YMF744 - Yamaha DS-XG (YMF744)
                     Yamaha DS-XG (YMF744) at 0xe9000000, irq 11
1 [SI7018         ]: SI7018 - SiS SI7018
                     SiS SI7018 PCI Audio at 0xd000, irq 11

$ ls -l /dev | grep dsp
crw-rw----  1 root audio    14,  12 2006-02-11 22:32 adsp
crw-rw----  1 root audio    14,  28 2006-02-11 22:32 adsp1
crw-rw----  1 root audio    14,   3 2006-02-11 22:32 dsp
crw-rw----  1 root audio    14,  19 2006-02-11 22:32 dsp1

They disappear when I remove the module 'snd-pcm-oss' by executing
$ sudo rmmod snd-pcm-oss

---

### Post by brucetan on 2006-02-12
Dear FarEast,

I had gone the url you suggested and tried out and also comfirm all version numbers.  But it just doesn't want to give me any sound!  

One thing I notice, I tried to play a audio cd with "CD Player" and at the same time, loaded the "Volume Monitor", I heard no sound but there are movement on the Volume Monitor.

I also tried to play the CD with XMMS, the volume monitor shows no movement and the player gave no sound.  

On the your old threads, when you said use OSS, I took it to set both Output and Input of Audio to OSS in "System"->"Preference"->"Multimedia Systems Selector".  Were I right?

I also tried the suggestion by dusu [http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567) but still it doesn't work!!

Any idea?

---

### Post by brucetan on 2006-02-12
dear fareast,

fyi. The CD player I used was Sound Juicer.  Hope you can help share some light on this.

---

### Post by FarEast on 2006-02-12
Hi brucetan,
We seem to have *hijacked* this thread :p  .

> On the your old threads, when you said use OSS, I took it to set both Output
> and Input of Audio to OSS in "System"->"Preference"->"Multimedia Systems
> Selector". Were I right?

Right!
Now you have to edit the files below to apply OSS driver instead of ALSA one.
[/etc/hotplug/blacklist] Add 'snd-ens1371'
[/etc/modules] Add 'ens1371'
Then restart the system ;) .

---

### Post by brucetan on 2006-02-12
Thanks Fareast.  I will try it now.  Thanks for your fast response.

---

### Post by brucetan on 2006-02-12
dear fareast,
---------------------
sudo gedit the following files and added the statement beside
[/etc/hotplug/blacklist] Add 'snd-ens1371'
[/etc/modules] Add 'ens1371'
Then restart the system
---------------------

It still doesn't give me any sound.  Here are the things I noticed now:
(1) where I click on the "Volume Control", it gave me "No volume control elements and /or devices found."

(2) When I activate Sound Juicer to play Audio CD, it gave "Error playing CD. Reason: Device "/dev/dsp" does not exist."

(3) When I activate Volume Control, it gave me "Cannot connect to sound daemon. Please run "esd" at a command prompt."

(4) I gone on to a terminal to check, the following were shown to me:
===========
boon@edubuntu:~$ sudo lsof /dev/dsp
=========================
lsof: status error on /dev/dsp: No such file or directory
lsof 4.75
 latest revision: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/)
 latest FAQ: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ)
 latest man page: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man)
 usage: [-?abhlnNoOPRstUvVX] [+|-c c] [+|-d s] [+D D] [+|-f]
 [-F [f]] [-g [s]] [-i [i]] [+|-L [l]] [+m [m]] [+|-M] [-o [o]]
[-p s] [+|-r [t]] [-S [t]] [-T [t]] [-u s] [+|-w] [-x [fl]] [--] [names]
Use the ``-h'' option to get more help information.

===============
boon@edubuntu:~$ esd
===============
ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver return ed error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned er ror: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned err or: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directo ry
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
boon@edubuntu:~$
================


I'm sorry the above are beyond me.  Hope they make some sense to you and the others.

---

### Post by FarEast on 2006-02-12
I wonder if the module 'snd-ens1371' is loaded.
> [/etc/hotplug/blacklist] Add 'snd-ens1371'
> [/etc/modules] Add 'ens1371'
I am not sure if I have been able to tell you correctly what you have to do.
I meant that you should describe names of the modules(i.e. snd-ens1371, ens1371).

Check if the module 'ens1371' is loaded in the following way.
$ lsmod | grep ens

---

### Post by brucetan on 2006-02-12
dear fareast,

after the edit & reboot, I did have a look at "multimedia system selector", they are still in OSS mode but when I did a pipeline test, it gave me "Failed to construct test pipeline for 'OSS - Open Sound System'."

---

### Post by FarEast on 2006-02-12
Unless the sound module is loaded, you get error from Multimedia System Selector :).
If nothing is shown when you execute 'lsmod | grep ens' , try the command
below and paste the output.
$ sudo modprobe ens1371

---

### Post by Rasymas on 2006-02-12
I tried various solutions but no success so far. 

I can hear music, it plays well, but when I press to play video files, no sounde is available to hear, but I can watch the video file, it's like MUTED or smth.. I've tried to play video files via MPlayer, but I recieved this error

```
Could not open/initialize audio device -> no sound
```

Any suggestions? :neutral:

---

### Post by FarEast on 2006-02-12
Hi Rasymas,
How about tweaking the preferences of MPlayer?
There are many options for audio output :).

-----
I go to bed now.  See you tomorrow!

---

### Post by brucetan on 2006-02-12
dear fareast,

I did gedit both files and added "snd-end1371" and "ens1371" respectively.  But when I did "lsmod | grep ens" I see nothing not even those "snd_*".

-------------
boon@edubuntu:~$ sudo lsmod | grep ens
Password:
i2c_sensor              3456  1 via686a
i2c_core               19728  4 i2c_acpi_ec,i2c_viapro,via686a,i2c_sensor
boon@edubuntu:~$ sudo lsmod | grep snd
boon@edubuntu:~$ sudo modprobe ens1371
FATAL: Module ens1371 not found.
boon@edubuntu:~$
------------------------

where can I get ens1371?

---

### Post by brucetan on 2006-02-12
dear fareast,

did you mean "sudo modprobe snd-ens1371" not "sudo modprobe ens1371"?

I just did a "sudo modprobe snd-ens1371".  It seems loaded ok.. see below but the volume is being muted and can't be changed to unmute?? When I did alsamixer to see, all speakers are not muted.

===========
boon@edubuntu:~$ lsmod | grep ens
i2c_sensor              3456  1 via686a
i2c_core               19728  4 i2c_acpi_ec,i2c_viapro,via686a,i2c_sensor
boon@edubuntu:~$ sudo lsmod | grep ens
Password:
i2c_sensor              3456  1 via686a
i2c_core               19728  4 i2c_acpi_ec,i2c_viapro,via686a,i2c_sensor
boon@edubuntu:~$ sudo lsmod | grep snd
boon@edubuntu:~$ sudo modprobe ens1371
FATAL: Module ens1371 not found.
boon@edubuntu:~$ modrobe snd-ens1371
bash: modrobe: command not found
boon@edubuntu:~$ sudo modprobe snd-ens1371
boon@edubuntu:~$ alsamixer

boon@edubuntu:~$ lsmod | grep ens
snd_ens1371            22240  2
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd                    48644  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
i2c_sensor              3456  1 via686a
i2c_core               19728  4 i2c_acpi_ec,i2c_viapro,via686a,i2c_sensor
boon@edubuntu:~$
boon@edubuntu:~$

===============

---

### Post by brucetan on 2006-02-12
dear fareast,

I googled the site : [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)
and found the following instruction (under "28. Troubleshooting's 28.4".)  I don't know if it makes sense and have not applied it yet.  What do you think, worth a try? (see below).
====================================
How to configure sound to work properly in GNOME

    * Read #General Notes
    * Read #How to add extra repositories 

sudo killall esd
sudo cp /etc/esound/esd.conf /etc/esound/esd.conf_backup
sudo gedit /etc/esound/esd.conf

    * Find this section 

...
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
...

    * Replace with the following lines 

auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default

    * Save the edited file 

sudo apt-get install libesd-alsa0
sudo gedit /etc/asound.conf

    * Insert the following lines into the new file 

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

    * Save the edited file 

sudo ln -fs /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

System -> Preferences -> Sound
Sound preferences

General Tab -> Sounds for events (Un-Checked)

    * Save and close all opened applications, Reboot computer 
==============================

---

### Post by brucetan on 2006-02-12
dear fareast,

I changed "ens1371" to "snd-ens1371" in the /etc/modules and then rebooted.  This seems to get rid the mute lock problem and I am able to lsmod and see all snd*.  The following the files edited and the additional info from terminal.  However, there is no sound.

============================
root@edubuntu:/home/boon# cat /etc/modules
============================
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
snd-ens1371


```

================================
root@edubuntu:/home/boon# cat /etc/hotplug/blacklist
================================
```
#
# Listing a module here prevents the hotplug scripts from loading it.
# Usually that'd be so that some other driver will bind it instead,
# no matter which driver happens to get probed first.  Sometimes user
# mode tools can also control driver binding.
#
# Syntax:  driver name alone (without any spaces) on a line. Other
# lines are ignored.
#

# uhci ... usb-uhci handles the same pci class
usb-uhci
# usbcore ... module is loaded implicitly, ignore it otherwise
usbcore

#evbug is a debug tool and should be loaded explicitly
evbug

# these drivers are very simple, the HID drivers are usually preferred
usbmouse
usbkbd

# replaced by e100
eepro100

# replaced by tulip
de4x5

# replaced by tmscsim
am53c974

# watchdog drivers should be loaded only if a watchdog daemon is installed
acquirewdt
advantechwdt
alim1535_wdt
alim7101_wdt
cpu5wdt
eurotechwdt
i810_tco
i8xx_tco
i810-tco
ib700wdt
indydog
machzwd
mixcomwd
pcwd
pcwd_pci
pcwd_usb
sa1100_wdt
sbc60xxwdt
sc1200wdt
sc520_wdt
scx200_wdt
shwdt
snd-ens1371
softdog
w83627hf_wdt
w83877f_wdt
wafer5823wdt
wdt285
wdt977
wdt
wdt_pci

# causes no end of confusion by creating unexpected network interfaces
eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
i2c_i801


```

================================
root@edubuntu:/home/boon# cat /etc/esound/esd.conf
================================
```
[esd]
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-as 5


```

==========================
root@edubuntu:/home/boon# lsof /dev/snd/*
==========================
```
COMMAND    PID USER   FD   TYPE DEVICE SIZE NODE NAME
mixer_app 7940 boon   35u   CHR  116,0      6183 /dev/snd/controlC0


```

=========================
root@edubuntu:/home/boon# lsof /dev/dsp
=========================
```
root@edubuntu:/home/boon#


```

===============================
root@edubuntu:/home/boon# lspci | grep Multimedia
===============================
```
0000:00:0b.0 Multimedia audio controller: Creative Labs Ectiva EV1938


```

==============================
root@edubuntu:/home/boon# modinfo snd-ens1371
==============================
```
filename:       /lib/modules/2.6.12-10-386/kernel/sound/pci/snd-ens1371.ko
author:         Jaroslav Kysela <perex@suse.cz>, Thomas Sailer <sailer@ife.ee.et hz.ch>
license:        GPL
description:    Ensoniq/Creative AudioPCI ES1371+
vermagic:       2.6.12-10-386 386 gcc-3.4
depends:        snd-pcm,snd-rawmidi,snd,gameport,snd-ac97-codec
alias:          pci:v00001274d00001371sv*sd*bc*sc*i*
alias:          pci:v00001274d00005880sv*sd*bc*sc*i*
alias:          pci:v00001102d00008938sv*sd*bc*sc*i*
srcversion:     D3D8CC5AD67BB5BCEE48E2D
parm:           joystick_port:Joystick port address. (array of int)
parm:           enable:Enable Ensoniq AudioPCI soundcard. (array of bool)
parm:           id:ID string for Ensoniq AudioPCI soundcard. (array of charp)
parm:           index:Index value for Ensoniq AudioPCI soundcard. (array of int)


```

===========================
root@edubuntu:/home/boon# lsmod |grep ens
===========================
```
i2c_sensor              3456  1 via686a
i2c_core               19728  4 i2c_acpi_ec,i2c_viapro,via686a,i2c_sensor
snd_ens1371            22240  1
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd                    48644  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97 _codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer


```

---

### Post by FarEast on 2006-02-12
Hi brucetan;) ,

> boon@edubuntu:~$ sudo modprobe ens1371
> FATAL: Module ens1371 not found.

I should have krinor1966's post in mind...
[http://ubuntuforums.org/showpost.php?p=674252&postcount=23](http://ubuntuforums.org/showpost.php?p=674252&postcount=23)

The OSS module for EV1938 is [COLOR="Red"]es1371[/COLOR], not ens1371#-o .

So you have to write 'es1371' in /etc/modules.  Keep 'snd-ens1371' in
/etc/hotplug/blacklist so that the system do not load the ALSA module.

I am sorry that I have given bad instruction...

---

### Post by brucetan on 2006-02-12
dear fareast,

no problem.  I will try it again.  many thanks.

Do also you think I need to apply the suggested steps from [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu), i.e., in section.28.4:

```
 How to configure sound to work properly in GNOME

    * Read #General Notes
    * Read #How to add extra repositories 

sudo killall esd
sudo cp /etc/esound/esd.conf /etc/esound/esd.conf_backup
sudo gedit /etc/esound/esd.conf

    * Find this section 

...
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
...

    * Replace with the following lines 

auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default

    * Save the edited file 

sudo apt-get install libesd-alsa0
sudo gedit /etc/asound.conf

    * Insert the following lines into the new file 

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

    * Save the edited file 

sudo ln -fs /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

System -> Preferences -> Sound
Sound preferences

General Tab -> Sounds for events (Un-Checked)

    * Save and close all opened applications, Reboot computer 
```

---

### Post by brucetan on 2006-02-12
by the way, there are more description about the above easylinux's by dusu that you may like to look at it on: 
[http://www.ubuntuforums.org/showthread.php?t=26567]("http://www.ubuntuforums.org/showthread.php?t=26567")

I did try it before your suggested change to es1371 but it didn't help to fix the sound for me.

---

### Post by brucetan on 2006-02-12
dear fareast,

after the change of the statement to es1371 in the /etc/modules, the CD player sounds the music from the audio  CD!!!  Thousand thanks!

One small question, do I need to do anything special to have the system event sounds.  Currently, there is no sound when I log in or clicking any menu...

---

### Post by FarEast on 2006-02-12
Congraturations, brucetan!!!

> Do also you think I need to apply the suggested steps from
> [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu), i.e., in section.28.4:

> by the way, there are more description about the above easylinux's
> by dusu that you may like to look at it on: 
> [http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

Thanks for the links.  I will check them after I go home.
One thing I can say now is that you do not need to disable esd for
normal use.  Without it, you cannot hear any system sound(notifications).
And be aware that your sound chip is driven by OSS module.  Some
instructions for ALSA may not valid.

> One small question, do I need to do anything special to have the system
> event sounds. Currently, there is no sound when I log in or clicking any
> menu...

Click system > preferences > sound and check if the sound server(esd) is
enabled.  You can test event sound on the tab 'system notifications'.

---

### Post by brucetan on 2006-02-13
> Click system > preferences > sound and check if the **_sound server(esd)_** is
enabled. You can test event sound on the tab _**'system notifications**_'.

Sorry fareast, "sound server(esd)" do you mean if it is checked for "enble sound server startup"? if it is, it is checked.  However, I notice there is no default sound card in the sound preference.  Also, there is no card in the list for me to select. 

When I did a lspci,it still shows:
```
0000:00:0b.0 Multimedia audio controller: Creative Labs Ectiva EV1938

```
Any thing wrong here?

---

### Post by FarEast on 2006-02-13
> "sound server(esd)" do you mean if it is checked for "enble sound server startup"?
Yes, I do.

> it is checked. However, I notice there is no default sound card in the sound
> preference. Also, there is no card in the list for me to select.
It is odd...anyway, pease try selecting 'esd' in 'multimedia system selector'.

---

### Post by brucetan on 2006-02-13
ok, i will try it shortly.

I was trying to bring volume monitor (vumeter). It gave me an error msg:

> Cannot connect to sound daemon.  Please run 'esd' at a command prompt.

I did a 'sudo esd' at the command prompt but got a lot of errors see below.
```
boon@edubuntu:~$ sudo esd
Password:
ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
boon@edubuntu:~$

```

Does this explains anything?

---

### Post by brucetan on 2006-02-13
dear fareast,

I set the default sink of output to "ESD" and reboot.  The result is no good.  I can't play the audio CD now. 

I did a test under ESD in multimedia systems selector, it gave me an error saying > Failed to construct test pipeline for 'ESD - Enlightenment Sound Daemon'

I then did a 'lsmod | esd' but it showed nothing.

I then did a 'sudo esd' at command prompt, it showed the same error as before ```
boon@edubuntu:~$ sudo esd
Password:
ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
boon@edubuntu:~$
```

I then try to bring the volume monitor.  It gave the error msg to run 'esd' at a command prompt.

I think somehow the esd module is not loaded.

---

### Post by brucetan on 2006-02-13
dear fareast,

I just did a apt-get libesd0 and removed lidesd-alsa0.  All the system sounds are working now so as my AudioCD.  To summarise the changes for the other users who use SB Live PCI card (model CT4730), the following are required:

```

(1) sudo gedit /etc/hotplug/esd.conf
insert a line anywhere that contains  'snd-ens1371' (with quotes)

(2) sudo gedit /etc/modules
insert a line anywhere that contains  'es1371' (with quotes)

(3) Go to System --> Preferences -->Multimedia Systems Selector
set default sink output to 'ESD' and default source input to 'OSS'

(4) Go to System --> Preferences -->Sound's general tap are all checked.

(5) Go to System --> Administration --> Synaptic Package Manager
Search for 'esd' and select 'libesd0' and mark to apply.  It will warning that libesd-alsa0 will be removed.  

(6) Reboot and check the speaker on the right hand top plane to ensure PCM, Master, Volume and PC Speaker are set to max and not muted.

 After this, you can try to play an audio CD or goto System --> Preferences --> Sound, and into the sound events tab & select any sound event to listen.

Otherwise, please get a newer sound card than SB Live...

```


Hope the above help the others.  Many thanks to Fareast's help to resolve this problem.

PS.  Please feel free to edit the above steps if I have missed any and correct any errors.  Cheers\\:D/

---

### Post by wncben on 2006-02-13
I found a good HOWTO, which has sort of fixed my sound problem.  I have applications sounds, but no system sounds, which is ok with me, those startup drums are sort of annoying;)  This is a huge improvement from no sound whatsoever.

[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

Inyhow, while going through this I found I had no /etc/asound.config file, so had to add it.  Not sure exactly what everything does, nor how to finish with my sound fix, but sofar so good.

Hope this helps

~ol'Ben

---

### Post by wncben on 2006-02-13
I got my system sounds back by going back to sound preferences and re-enabling the "enable sound server' button.

\\:D/ 

Now, if only this fix sticks around for awhile!

~Ol' Ben

---

### Post by brucetan on 2006-02-13
I share your happiness for the sound to work.  Congras.

---

### Post by wncben on 2006-02-13
ARRGh!  #-o :mad: :cry: ](*,) 


   I broke my sound again.......



       I hope it is just a little tweake I tried in asound.conf,  will try to put things right again.  I really hope that I have managed to actually fix the problem, and my having sound wasn't due to just one of the random times when it decided to work on it's own.

~Ol' Ben ::a few grey hairs later::

---

### Post by wncben on 2006-02-13
In case anyone is interested here is my asound.conf:
```

# Set default sound card 
# Useful so that all settings can be changed to a different card here.
 pcm.snd_card {
      type hw 
      card 0 
}

# Allow mixing of multiple output streams to this device
pcm.dmixer { 
      type dmix 
      ipc_key 1024 
      slave.pcm "snd_card" 
      slave { 
           # This stuff provides some fixes for latency issues.
           # buffer_size should be set for your audio chipset. 
           period_time 0 
           period_size 1024 
           buffer_size 8192 
           # rate 44100 
	} 

	bindings {
            0 0 
            1 1 
	} 
} 

# Allow reading from the default device. 
# Also known as record or capture. 
pcm.dsnooper { 
	type dsnoop 
	ipc_key 2048 
	slave.pcm "snd_card"

	bindings {
            0 0
            1 1 
	} 
} 

# This is what we want as our default device 
# a fully duplex (read/write) audio device. 
pcm.duplex { 
	type asym 
	playback.pcm "dmixer" 
	capture.pcm "dsnooper" 
} 

################### 
# CONVERSION PLUG # 
################### 
# Setting the default pcm device allows the conversion 
# rate to be selected on the fly. 
# duplex mode allows any alsa enabled app to read/write 
# to the dmix plug (Fixes a problem with wine). 

pcm.!default { 
	type plug 
	slave.pcm "duplex" 
} 

######## 
# AOSS # 
######## 
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)

pcm.dsp0 { 
	type plug 
	slave.pcm "dmixer" 
} 

# OSS control for dsp0 (needed?...this might not be useful) 
ctl.dsp0 { 
	type plug 
	slave.pcm "snd_card" 
} 

# OSS control for dsp0 (default old OSS is mixer0) 
ctl.mixer0 { 
	type plug 
	slave.pcm "snd_card" 
}

```


If anyone has any ideas, I would greatly appreciate it.

~Ol' Ben

---

### Post by wncben on 2006-02-13
Okay dokey,

  I made the following change to asound.conf:
  

I changed the pcm.!default back to the way I first had it:

```
pcm.!default { 
	type asym 
	playback.pcm "dmixer"
	capture.pcm "dsnooper" 
}

```

Now I get sound in the sound test, instead of the dreaded 'unable to construct pipeline'  but it is choppy.  I will try to reset my bufer back to where it was too.   I bumped the buffer up because mplayer sound is sometimes choppy and distorted, but maybe I am getting another conflict there too.

~Ol Ben

---

### Post by wncben on 2006-02-13
Alrighty then...
  The ubuntu brown clouds are starting to part, and I am beginning to see the light!  I got sound back to working for my apps, I will try to re- enable my  'enable sound server' and see if getting system sounds back breaks it.

btw, I reset my buffer in asound.conf to 4096.   

One weird thing I noticed is that sometimes I get a msg that it is trying to start at 44.1 htz at 16 bit then 44.1 htz 8 bit then it seems to finally start at 48 htz at 16 bit.  It seems like my asound.cnfg is set to 44.1, is there a way to change it to 48?  does it matter, or is that error, like so many of the weird perl errors I get, nothing to worry about.

~Ol' Ben

---

### Post by wncben on 2006-02-13
Otay,  I have system sounds too :)   But, (and I am not sure this is related, although I have read several other posts that had similar results,) when i rebooted the system froze on the brown screen before the ubuntu splash screen after you log in.  Rebooting in gnome safe mode also froze there, but reeboting and selecting gnome got me back on track.  Weird huh.

So, now I have sound\\:D/   and system sound\\:D/   although sometimes the sound is distorted :-k  hmmm...

~Ol' Ben

---

### Post by wncben on 2006-02-13
Here is another great HOWTO:
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

Gandalph has also got the buffer set for 48htz, which is what my system seems to use.  Hope this helps...
~Ol' Ben

---

### Post by wncben on 2006-02-13
Hey Brucetan, 
   I have been going through your posts, and while I have a different card than you, my problems, and error messages seem to be similar.  One of the issues seems to be that there are conflicts where alsa, esd, and oss don't play nice together.  I followed the advice in the post I linked to above and got my sound working, and tweaked it alittle, changing the buffer size and frequency to make the sound better.  It is not a very difficult process, although if you cut and paste you may have to respace the lines out so that the commands function properly.  If you have more than one command on a line it will not work.  

  Here is the asound.conf file I have installed and tweaked: 
To edit it:
```
sudo gedit etc/asound.conf
```
then make it look like this, just cut and paste or type it in.
```
# Set default sound card 
# Useful so that all settings can be changed to a different card here.
 pcm.snd_card {
      type hw 
      card 0 
}

# Allow mixing of multiple output streams to this device
pcm.dmixer { 
      type dmix 
      ipc_key 1024 
      slave.pcm "snd_card" 
      slave { 
           # This stuff provides some fixes for latency issues.
           # buffer_size should be set for your audio chipset. 
           # If your rate is 44100 change period and buffer size to 
           # 1024 and 4096 respectively, you can try buffer 8192
           # if sound is choppy
           period_time 0 
           period_size 2048 
           buffer_size 32768
           # rate 48000 
	} 

	bindings {
            0 0 
            1 1 
	} 
} 

# Allow reading from the default device. 
# Also known as record or capture. 
pcm.dsnooper { 
	type dsnoop 
	ipc_key 2048 
	slave.pcm "snd_card"

	bindings {
            0 0
            1 1 
	} 
} 

# This is what we want as our default device 
# a fully duplex (read/write) audio device. 
pcm.duplex { 
	type asym 
	playback.pcm "dmixer" [esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=[CODE]
```
	capture.pcm "dsnooper" 
} 

################### 
# CONVERSION PLUG # 
################### 
# Setting the default pcm device allows the conversion 
# rate to be selected on the fly. 
# duplex mode allows any alsa enabled app to read/write 
# to the dmix plug (Fixes a problem with wine). 

pcm.!default { 
	type asym 
	playback.pcm "dmixer"
	capture.pcm "dsnooper" 
} 

######## 
# AOSS # 
######## 
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)

pcm.dsp0 { 
	type plug 
	slave.pcm "dmixer" 
} 

# OSS control for dsp0 (needed?...this might not be useful) 
ctl.dsp0 { 
	type plug 
	slave.pcm "snd_card" 
} 

# OSS control for dsp0 (default old OSS is mixer0) 
ctl.mixer0 { 
	type plug 
	slave.pcm "snd_card" 
}
[/CODE]

  Also note that lines starting with '#' are notes, and do not effect the running of the program.  Feel free to add lines anywhere that start with '#' to leave youself notes (as I did above the buffer, to remind myself what the old values were)

The other thing I did was to change my esound/esd.conf:

```
sudo gedit /etc/esound/esd.conf
```

```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

save your changes and reboot and you should have sound.

These should make alsa oss and esd play nice together, although there will still be some conflicts.  I have my multimedia system selector audio ste to alsa for both, and everything seems to work ducky.

~Ol' Ben

---

### Post by bbqbaker on 2006-02-13
hi. i to am not hearing any sound. ive modified my esd and asound.conf files. i have a audigy soundblaster card with digital output. [SB0090]...please help.



here is my esd.conf

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default

#spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
#default_options=

///////////////////////here is my asound.conf
```

# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}
#############################

pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

```

---

