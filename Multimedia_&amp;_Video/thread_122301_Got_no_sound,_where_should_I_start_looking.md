---
title: "Got no sound, where should I start looking"
date: 2006-01-27
forum: Multimedia &amp; Video
---

### Post by lgmdaniel on 2006-01-27
After following a number of threads to install extra things, I've got no sound. 
These are the 2:
[General - HowTo: Speed up ubuntu boot process - the way you can feel it.]("http://www.ubuntuforums.org/showthread.php?t=89491")

[General - Picking the Kernel thats Right for You (Possible Speed Increase)]("http://www.ubuntuforums.org/showthread.php?t=85917&highlight=firewall")

Now I thought it was maybe that I turned off alsa but turning it on appears to have had no affect... Could someone confirm the run levels for me?

So maybe is the Kernel update.. but that seemed to all go ok, and no errors.

So could someone give me some clues as to where I should maybe start looking.

Thanks.

---

### Post by agapito on 2006-01-27
I think you might have deactivated some services you needed... Do this please,
ls /etc/rc3.d
and then post the output here.

---

### Post by lgmdaniel on 2006-01-27
Ok. I will when I get home.. I just wanted something to start on while I remembered to post... ;)

---

### Post by agapito on 2006-01-27
I'll be leaving soon, but I'll check it out latter. My guess is that you have deactivated ALSA... Double check your list of services.

Good luck. ;)

---

### Post by lgmdaniel on 2006-01-27
Stupid here forgot to take note of the services he did have running, so now I'm not even sure if ALSA was even on. I think it was using alsa-utils

---

### Post by FarEast on 2006-01-27
Hi,
Please try this:
$ cd /etc/rcS.d
$ sudo ln -s ../init.d/alsa-utils S50alsa-utils
Then restart the system.

---

### Post by lgmdaniel on 2006-01-28
Ok.. last one didn't work...
```

daniel@Grinch:~$ ls /etc/rc3.d
K01rmnologin     K80alsa      S13gdm          S20samba        S98usplash
K15fetchmail     K89atd       S14ppp          S20sensord      S99acpi-support
K20apmd          S05vbesave   S19cupsys       S21kdm          S99stop-bootlogd
K20hotkey-setup  S10acpid     S19hplip        S23ntp-server   S99timidity
K20pcmcia        S10sysklogd  S20firestarter  S25bluez-utils
K20rsync         S11klogd     S20makedev      S89anacron
K25mdadm         S12dbus      S20powernowd    S89cron
daniel@Grinch:~$
```

Any ideas?
Thanks.

---

### Post by FarEast on 2006-01-28
Hi;) ,
Make sure if the scripts 'alsa-utils' (which belongs to the package 'alsa-utils')
and 'alsa'(which belongs to 'alsa-base') exists in /etc/init.d .
And it is 'rc[COLOR="Red"]S[/COLOR].d' in which the symbolic link has to be created.

---

### Post by lgmdaniel on 2006-01-28
> **FarEast]Hi said:**
> S[/COLOR].d' in which the symbolic link has to be created.


yep the file exsits and the symbolic link too...

---

### Post by agapito on 2006-01-28
I can't see where's the trouble. I'll post the contents of my rc3.d and rcS.d .
I haven't messed with it much, so they may help you out but guess I have some extra stuff installed that you may not have on you system. This is a very old install (since Hoary first came out). My policy is upgrade and keep it running stable. Do not format. :)

agapito@pople:/etc/rc3.d$ ls
S05vbesave        S19cupsys             S20inetd           S20sensord              S91apache2     
S10acpid          S19hplip             S20makedev         S25bluez-utils          S98usplash     
S10sysklogd       S19spamassassin       S20pcmcia          S25mdadm             S99acpi-support
S11klogd          S20apmd               S20postfix         S89anacron                  S99fetchmail
S12dbus           S20festival           S20powernowd       S89atd                  S99rmnologin
S13gdm            S20firestarter        S20rsync           S89cron                 S99stop-bootlogd
S14ppp            S20hotkey-setup       S20samba           S90binfmt-support


agapito@pople:/etc/rcS.d$ ls
README                                  S26lvm               S40ifrename
S02mountvirtfs                          S27evms              S40networking
S04mdadm-raid                            S30checkfs.sh        S41hotplug-net
S04udev                                 S30procps.sh          S45mountnfs.sh
S05bootlogd                              S35mountall.sh       S48console-screen.sh
S05initrd-tools.sh                       S36lm-sensors        S50alsa-utils
S05keymap.sh                             S36mountvirtfs       S50hwclock.sh
S07hdparm                                S36udev-mtab         S51ntpdate
S10checkroot.sh                          S38pppd-dns          S55bootmisc.sh
S15linux-restricted-modules-common       S39dns-clean         S55urandom
S18ifupdown-clean                        S39ifupdown          S70screen-cleanup
S20module-init-tools                     S39readahead         S70xorg-common
S22hwclockfirst.sh                       S40hostname.sh       S75sudo
S25libdevmapper1.00                      S40hotplug


Note that I'm using alsa, to hear sounds from multiple apps at the same time. I followed [this]("http://ubuntuforums.org/showthread.php?t=32063") great howto to get it done.

---

### Post by lgmdaniel on 2006-01-28
I think some how the /dev entry has been removed though I'm not sure... I keep getting this error message when I try to use the sound:

```
Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device.
```

I can't see /dev/dsp so I asume that was the sound device file, but its vanished. God knows what caused that...

---

### Post by agapito on 2006-01-28
I can help you create a new device and we'll see if that does the trick. 
Ok the command to do that is mknod, and in your case do this:
```
sudo mknod /dev/dsp c 14 3
```

The c is to create a character (unbuffered) special file. 14 is the major and 3 is the minor (these are the ones I use, so it should work for you).
```

agapito@pople:/dev$ ls -l dsp
crw-rw----  1 root audio 14, 3 2006-01-28 17:52 dsp

```

Check if the permissions are correct and in if you bellong to the audio group, in the /etc/group file.  In my case:
```

...
audio:x:29:agapito
...

```

I have a new guess of what's going wrong. I think these devices are created at boot time by a script, which you may have disabled. I'm going to check that. Meanwhile, you can try this, to see if the missing device is the problem and post you rcS.d, so that I can check if something's missing there. Ok?

---

### Post by lgmdaniel on 2006-01-28
cool thanks... if this don't work I'm seriously considering a reinstall.. as lots of things seem to have stopped working. Printers.. Samba.. its all rather anoying.

---

### Post by TecSoft on 2006-01-28
You can do sudo alsaconf to configure your sound driver.

---

### Post by lgmdaniel on 2006-01-28
[QUOTE=TecSoft]You can do sudo alsaconf to configure your sound driver.[/QUOTE]


You might be able to:

```
daniel@Grinch:~$ sudo alsaconf
sudo: alsaconf: command not found
daniel@Grinch:~$

```

---

### Post by agapito on 2006-01-28
I don't have alsaconf...

---

### Post by lgmdaniel on 2006-01-28
OK.. looks like my sound card has some how removed its self form the system config as now I get this message.

```
daniel@Grinch:/dev$ /etc/init.d/alsa-utils start
* Setting up ALSA... 
* /etc/init.d/alsa-utils: Warning: 'alsactl restore' failed with error message 'alsactl: load_state:1236: No soundcards found...'. 
[ ok ]

```

need sleep.. cheers for the help so far...

---

### Post by agapito on 2006-01-28
What is your default runlevel? (I assumed It was 3, but I was wrong... I'm sorry. It's suposed to be 2. Check that in /etc/inittab:
```

# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

```
then post the an ls of that runlevlel's directory, please)

In the meanwhile, here's a bunch of questions:
Did you try to see if you had sound before rebooting or restarting any service?
If you rebooted, did that erase the /dev/dsp device?
Do you have alsa well configured?
Are you using alsa as your system's default? ( System-> Preferences->Streaming Services Configuration (or something like that. Mine is in Portuguese...)

It's getting late here too... I'll be around tomorow.

---

### Post by agapito on 2006-01-28
If you haven't messed with you system much, maybe the initial configurations will help you out. They are [here]("http://img485.imageshack.us/my.php?image=14ub.png") and [here]("http://img485.imageshack.us/my.php?image=25cr.png").

---

### Post by Jake83 on 2006-01-29
I've got the same problem. I did the HowTo: Speed up Ubuntu process aswell, and afterwards the sound didn't work anymore. I tried to undo the changes and actually after restart it worked, but after the second restart the sound was dead again. Amarok says it's a gstreamer error. Alsa sees my soundcard and master is not muted. I've no idea what to do.. anyone can help?

---

### Post by agapito on 2006-01-29
Hi Jake83,
Try starting amarok from the command line. That will give you some more info wich may help out. I'll be on the lookout for your posts here.

---

### Post by lgmdaniel on 2006-01-31
scus me that I haven't replied but I'm a bit sick at the moment... hopefull I'll be able to look at it this weekend. Thanks for the help so far.

---

### Post by mpvano on 2006-01-31
Your barking up the wrong tree.

Your card's driver is not "part" of the system - it's found and the driver is installed at every bootup by some of the other things you turned off. That's why alsaconf is not present in ubuntu (and wouldn't work right if it were).

By the way, everything except the barely minimal devices needed to boot is installed right after you boot and configured at that time. If you remove the tools that do this, you'll have a just barely running system.

All that stuff you removed to "speed things up" is needed for Ubuntu to boot properly. Systems like udev, hotplug, and others need to be running or your devices won't show up properly unless they are part of the tiny core of devices that are essential for booting to work.

Hope this stimulates your memory about what you deleted.

One thought is to try to log back into the terminal you used to do the deleting and examine the command history by holding down the shift key and using page-up and page-down to go through your recent commands. If you gave them from a root shell, you'll have to do this from a root shell.

I don't think anyone out here can figure out what your machine needs - the installer does a lot of that when you installed the system.

The thread you were reading sounds like a self-serve trojan....

Mario

---

### Post by lgmdaniel on 2006-02-02
I think I might have to do a refresh of the system to get things back how they where and leave the playing untill I have a bit more knowledge. Thanks for everyones help.

---

