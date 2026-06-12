---
title: "no sound card detected"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by ninotchka on 2006-06-02
i upgraded from Breezy to Dapper today, and now i have no sound whatsoever... 

> e@cm10225:~$ cat /proc/asound/cards
--- no soundcards ---
e@cm10225:~$ sudo gedit /etc/modprobe.d/alsa-base
Password:
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default


Needless to day (being the typical "end user"), i have absolutely no idea what's going on, and have no clue what to do next. I've already browsed the message board, to no avail. Please, help :(

---

### Post by DiESELMuSA on 2006-06-03
I have EXACTLY the same problem :/
Any wizards who can help us here? I use my computer mainly for music and I've upgraded not to loose all my settings/programs and so on. I dont want to switch back to Windows or do a clean install of Dapper :/

Hope anyone can help us here...

---

### Post by tavito on 2006-06-03
Hi, I also have the exactly same problem. It seems to be a problem with the kernel-modules (because I also have problems with other kernel module), but i'm not sure at all.

My sound card is a Intel on board sound card. The output of 'lscpi -v' is:
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
        Subsystem: EPoX Computer Co., Ltd.: Unknown device 4001
        Flags: bus master, medium devsel, latency 0, IRQ 9
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=64]

---

### Post by walding on 2006-06-03
Same problem for me, too.  I have 3 installs of Dapper on my hard disk now; one clean install, one upgrade that I screwed up (forgot to comment my sources.list) and one upgrade that went OK.  All 3 lack sound and can't detect the soundcard!

Any help appreciated!  This is my music PC.

---

### Post by walding on 2006-06-03
(forgot to subscribe to the thread on the last one).  sorry.e: no sound card detected

---

### Post by cardo on 2006-06-03
The same problem with ESS Maestro 3 sound card

~$ cat /proc/asound/cards
--- no soundcards ---
~$ sudo gedit /etc/modprobe.d/alsa-base
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave

Sound was ok on Breezy.

---

### Post by grapesmc on 2006-06-03
And another of us with the same problem. Just finished my upgrade. :( Hopefully one of us sorts it out soon. Need tunes.

---

### Post by andb on 2006-06-03
I had the same problem, no sound device found. Seems like everyone who is experiencing this upgraded from breezy to dapper. Was it with apt-get dist-upgrade? I did a clean install and all is well. Try the live cd. If sound works, then this is the "quick" fix...

---

### Post by jerzyUs on 2006-06-03
I too am experiencing the same problem.  I did an apt-get dist-upgrade and now my sound card is not detected.  Any one have any ideas....

---

### Post by djmadkins on 2006-06-04
What I did to get sound running on my system ( I have a soundblaster but I'm sure it is a similar process).

run the following from a terminal to determine if your system is seeing your soundcard.

```
lspci | grep audio
```

output from mine was :

```
0000:02:00.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
```

For my case the EMU10k1 section was what I was after. Now I can run the following to activate sound.

```
sudo modprobe snd-emu10k1
```

remember, you can't just use snd-emu10k1 unless you have the same card as me :)

Jeff

---

### Post by dwhli on 2006-06-04
[QUOTE=ninotchka]i upgraded from Breezy to Dapper today, and now i have no sound whatsoever... 



Needless to day (being the typical "end user"), i have absolutely no idea what's going on, and have no clue what to do next. I've already browsed the message board, to no avail. Please, help :([/QUOTE]

I have exactly the same problem, but the problem was gone after upgrading the kernel from 2.6.12 to 2.6.15.

---

### Post by deodatus on 2006-06-04
This is what I did to fix the same problem, I found something like this on a Fedora forum.
Open terminal:
#*sudo alsaconf*
follow instructions, then:
#*sudo gst-register-0.8* 
This registers all the GStreamer plug-ins among other things I don't know of.
*reboot*.  It wouldn't work until I rebooted. 
Soooo... I hope this works for everyone.

---

### Post by walding on 2006-06-05
Mine's sorted.  I'm afraid I can't tell you what fixed it.  I was tinkering with a few things, and noticed that I got sound back next reboot!  The 2 significant things I did were:

1. Upgrade from kernel 2.6.10.... to 2.6.15.... (My grub file was still pointing at the old kernel).
2. Ran Automatix 6.1 and kept the Automatix-recommended sources.list

Worth a shot of these two if you're still stuck.  I wish I'd done one at a time and rebooted after each to know for sure what did the trick.

---

### Post by DiESELMuSA on 2006-06-05
I did a kernel upgrade too (enabling all repos and doing sudo apt-get upgrade) and that worked. I found out that GRUB was booting my selfcompiled kernel, which did not boot under breezy, but now under Dapper, so I removed that and booted my newly upgraded kernel and now im running upgraded Dapper with XGL/Compiz..

---

### Post by walding on 2006-06-06
This is a novice question - is this a bug in the dist-upgrade process if it doesn't automatically point grub to the new kernel?  

A normal desktop user (which is where Ubuntu wants to gain market share from) wouldn't know how to do that; and I wouldn't encourage them to start editing the menu.lst.  (Is there a GUI grub configuration editor?)

---

### Post by pixel80r on 2006-06-13
[QUOTE=walding]Mine's sorted.  I'm afraid I can't tell you what fixed it.  I was tinkering with a few things, and noticed that I got sound back next reboot!  The 2 significant things I did were:

1. Upgrade from kernel 2.6.10.... to 2.6.15.... (My grub file was still pointing at the old kernel).
2. Ran Automatix 6.1 and kept the Automatix-recommended sources.list

Worth a shot of these two if you're still stuck.  I wish I'd done one at a time and rebooted after each to know for sure what did the trick.[/QUOTE]

How do I go about upgrading the kernel? Synaptic shows that 2.6.15 is installed, but it does not show up in grub. What do I need to do? I have no sound AND no automount for removable usb DVD. I'm hoping this will fix it before I resort to a new install.

menu.lst is:

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd1,0)
kernel		/vmlinuz-2.6.12-10-386 root=/dev/hdb3 ro quiet splash
initrd		/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd1,0)
kernel		/vmlinuz-2.6.12-10-386 root=/dev/hdb3 ro single
initrd		/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,0)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro quiet splash
initrd		/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,0)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro single
initrd		/initrd.img-2.6.12-9-386
boot

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd1,0)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hdb3 ro quiet splash
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd1,0)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hdb3 ro single
initrd		/initrd.img-2.6.10-5-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title		Microsoft Windows 2000 Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by DiESELMuSA on 2006-06-14
Try to do
```
sudo update-grub
```

---

### Post by Zorro on 2006-06-14
This is getting frustrating :( I followed this thread...  yet I still have no sound what so ever (where I did before).... In fact, on the splash screen I still hear the drums... YET...as soon as gnome loads I have no sound..  ( [http://home.avargo.com/~cam/screen-prob.jpg](http://home.avargo.com/~cam/screen-prob.jpg) ) will show you the error when I click the sound icon on the task panel.

Any other suggestions would be a great help, as this is really annoying..  Btw, I get this showing up...


root@desktop:~# lspci | grep audio
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)


It is an oboard audio card, nothing flash...... :/

---

### Post by andb on 2006-06-15
Zorro, I had a similar problem under Breezy a few months back. I made a second user account. Logged onto it, sound worked! But still, when I logged onto the old account it there was no sound! So then I gave the new acct sudo priviledges, backed up the old home, removed the original account, recreated the original account, and viola! it worked. I have no idea what actually was the problem, and didnt care, I was happy it just worked ;) I had a second sound problem with a breezy->dapper distro upgrade. Wiped the drive and did a clean install and all was fine. I admit, this isn't a very clean way of solving things... but if it works, it works.

Pixel, if you want to just edit /boot/grub/menu.lst then just add:
```
title           Ubuntu, kernel 2.6.15-23-386
root            (hd1,0)
kernel          /vmlinuz-2.6.15-23-386 root=/dev/hdb3 ro quiet splash
initrd          /initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd1,0)
kernel          /vmlinuz-2.6.15-23-386 root=/dev/hdb3 ro single
initrd          /initrd.img-2.6.15-23-386
boot

```

and remove
```
savedefault
```

from 
```
title Ubuntu, kernel 2.6.12-9-386
root (hd1,0)
kernel /vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro quiet splash
initrd /initrd.img-2.6.12-9-386
savedefault
```
I hope that I got all of the drives and partitions correct, should just be the same as the others, unless youve made other changes. There is also a 686 kernel available with a few enhancements, though overall performance won't change too dramatically.

---

### Post by Zorro on 2006-06-15
[QUOTE=andb]Zorro, I had a similar problem under Breezy a few months back. I made a second user account. Logged onto it, sound worked! But still, when I logged onto the old account it there was no sound! [/QUOTE]


Yeah just tried that and still no go :(  I will do a format and reinstall.. see what happens.... :(  

Thanks for the help...

---

### Post by Zorro on 2006-06-17
Formated reinstalled and now I have sound.... I think something is dodgy with the dist-upgrade or something... :(  Bit of a hassle but I now have sound so I'm a happy camper :P

---

### Post by pixel80r on 2006-06-17
[QUOTE=Zorro]Formated reinstalled and now I have sound.... I think something is dodgy with the dist-upgrade or something... :(  Bit of a hassle but I now have sound so I'm a happy camper :P[/QUOTE]

Same here. I wasn't able update grub to boot the newer kernel as suggested by another post in this thread because my Boot partition was full (30k). I thought I could use gparted boot disk to resize and move a partition to make room for it, but learned that you can only resize the end of a ext3 partition, which was what was after my boot partition so I was screwed. I needed to resize the front of it. Had no choice but to format and repartition. Backed up my home directory and got to it. Did a new install from disk and restored my home directory. Everything is good now. I can even automount usb devices again (something else that was lost after the dist-upgrade). To be honest, it was a lot easier to backup, reinstall, restore, than to keep trying to troubleshoot, install packages, uninstall packages, resolve dependencies, blah, blah....

Happy again..:D

---

### Post by Ozitraveller on 2006-06-17
I don't think a fresh install is the answer because I have done it 3 times so far and still can't get the sound to stay.

I have a Sound blaster vibra 16.

What I did, yesterday:
1. fresh Ubuntu 6.06 install alternate
2. used synapic to install the lastest updates. no changes were made to synaptic settings, it's as it was after the install. So I'm running the latest kernel and everything.
3. sudo modprobe snd-sb16
4. sudo gedit /etc/modules, added sb to end of file.
5. reboot gnome. I HAVE SOUND!
6. shutdown pc
7. cold boot pc, NO SOUND!!!!!!!

ozi@ubuntu01:~$ cat /proc/asound/cards
--- no soundcards ---
ozi@ubuntu01:~$ sudo gedit /etc/modprobe.d/alsa-base
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

---

### Post by andb on 2006-06-18
Ozitraveller, I had a few odd problems with the alternate install also. I really wanted to use LVM for all partitions and the graphical installer doesnt support this. But then I had lots of little problems. I can fidure out just about anything with a manual and time, but i have to ask myself, is it really worth it? So I just set normal partitions, used the graphical installer and voila! all good. I really hate to recommend reinstalling as a way to fix problems, but given the choice of fighting for hours and hours to get it exactly as I want or doing a simple install with a compromise or two... well, Id suggest trying the graphical installer for fun and see if your sound works :)

---

### Post by nmsa on 2006-06-19
[QUOTE=Zorro]Formated reinstalled and now I have sound.... I think something is dodgy with the dist-upgrade or something... :(  Bit of a hassle but I now have sound so I'm a happy camper :P[/QUOTE]
format was not required nor scratch install

I was until a few min ago in the same sittuation.
what I did is to create a new user, add it in the sudo  group and manual edit passwd file to have the new user pointing to the old *problematic* user home directory.
I loged out, loged in to the new created user
then I delete the original user and all things are ok

after that I tried again to add the old user having a diff dir as home. Still no sound.
something is bad managed there and all related to that user and no other. I hope will not happen again becouse I am not sure this w/a will work nor I want to reinstall all things on my system.

this happened to me as I upgraded the kernel to 2.6.15-25 on amd64 arch.

fyi, in case a reinstall is required and the current structure of the OS is to be maintained one can make use of:
```
dpkg --get-selections > installed-packages.txt
install from scratch
sudo apt-get update
dpkg --set-selections < installed-packages.txt
sudo apt-get upgrade
```

Regards

---

### Post by jerrykenny on 2006-06-21
This might be a debian ETCH issue (rather than specifically ubuntu) but heres what works for etch (on this box anyway)

apt-get install alsa-utils

alsaconf

answer the prompts and voila !   good old debian :p

---

### Post by pmshirey on 2006-06-21
[QUOTE=Zorro]Formated reinstalled and now I have sound.... I think something is dodgy with the dist-upgrade or something... :(  Bit of a hassle but I now have sound so I'm a happy camper :P[/QUOTE]<p>
<p>
Don't be afraid to just use the command line. I try to use it whenever I can.

---

### Post by papsu on 2006-09-16
I had the same problem as Zorro. Updated from Ubuntu dapper 2.6.15-25-386 -> 2.6.15-26-386 and after that sounds didn't work. **But I finally got it working!** 
This is what I had before installing and after installing the alsa-driver

```
$ lspci | grep audio
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
```

I think you might get your sounds working even if you don't have exactly the same sound card, just find your own infos from [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and choose your sound card manufacturer to "Choose manufacturer for more details"... The lspci showed that mine was VIA.

I tried to tell this short and simple how I got my sounds working:

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=VIA+southbridge+AC97+audio.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235%2C+VIA8237&module=via82xx](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=VIA+southbridge+AC97+audio.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235%2C+VIA8237&module=via82xx)

There you can found the longer 'howto'
So let's get working ;) :

Download the alsa-driver from [www.alsa-project.org](www.alsa-project.org)

Here's one url that I used for the newest driver(1.0.13):
[http://www.alsa-project.org/alsa/ftp/driver/alsa-driver-1.0.13.tar.bz2](http://www.alsa-project.org/alsa/ftp/driver/alsa-driver-1.0.13.tar.bz2)

Then open konsole and type these commads there:
```

$ sudo su
(root password)

**(First I installed using only sudo in front of every command, but it didn't install the driver properly. So remember to do this as root!!)**

# cd /usr/src
# mkdir alsa
# cd alsa

# cp /**where-alsa-driver-is-downloaded**/alsa-driver-1.0.13.tar.bz2 /usr/src/alsa/alsa-driver-1.0.13.tar.bz2

# bunzip2 alsa-driver-1.0.13.tar.bz2
# tar -xf alsa-driver-1.0.13.tar
# cd alsa-driver-1.0.13
# ./configure --with-cards=via82xx --with-sequencer=yes;make;make install

# modprobe snd-via82xx;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss

```

Now I got messages that "New audio device founded" and it worked.. exept I couldn't control volume, but after rebooting it started working too :)

**But** I'm not sure about if this also helped.. I edited my esd.conf file. So I guess you should do this also just to make sure :)
first type these to console:

```
# cp /etc/esound/esd.conf /etc/esound/esd.conf.backup
# gedit /etc/esound/esd.conf
```

And then edit it so it looks like this:

```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```


Hope my text wasn't too hard to understand. Please tell me if this solved your problem too! :)

---

