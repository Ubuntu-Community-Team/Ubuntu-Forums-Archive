---
title: "AC97 problem."
date: 2005-11-21
forum: Multimedia &amp; Video
---

### Post by dev3n on 2005-11-21
Alright, I am pretty new with linux/Ubuntu (1 day :p) and I am having issues with my Sound Card. When I first got Ubuntu running the sound card was working, except that I could only use it for 1 program, (for example: I was not able to play a game and listen to music at the same time.) So I started goofing around and doing what not. Now, my sound card is not working at all (in linux that is). Some guys have been trying to help me, but it ended up with no result. This is stuff I've been told to do:

lspci:

```
 0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 A GP]
0000:00:0a.0 RAID bus controller: Triones Technologies, Inc. HPT302 (rev 01)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 23)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 40)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 420 0] (rev a3)
```

modprobe -v snd_via82xx
```


root@Skynet:/# modprobe -v snd_via82xx
install modprobe --ignore-install snd-via82xx && { /lib/alsa/modprobe-post-insta ll snd-via82xx ; modprobe --quiet snd-seq ; }
FATAL: Module snd_via82xx not found.
FATAL: Error running install command for snd_via82xx

```

alsamixer
```

root@Skynet:/# alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory

```

If you need any more information about my system please tell me.

Thanks, Christopher.

---

### Post by heimo on 2005-11-21
Ups... Not _, it should be -, like this:
```
 modprobe -v snd-via82xx
```

Does it work?

---

### Post by dev3n on 2005-11-21
```
root@Skynet:/home/tokyo# modprobe -v snd-via82xx
install modprobe --ignore-install snd-via82xx && { /lib/alsa/modprobe-post-install snd-via82xx ; modprobe --quiet snd-seq ; }
FATAL: Module snd_via82xx not found.
FATAL: Error running install command for snd_via82xx

```

and, i tried 'lsmod | grep ac97' in the terminal, but it did'nt show anything..

---

### Post by heimo on 2005-11-21
That's odd. Running...
```
locate snd-via82xx.ko
```
shows nothing?

Try:
```
lsmod|grep snd
```
and post the output.

---

### Post by dev3n on 2005-11-21
```
locate snd-via82xx.ko
```

shows nothing...

'lsmod | grep snd' gives me: 
```

snd_mpu401              6344  1
snd_mpu401_uart         6784  1 snd_mpu401
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
snd                    48644  6 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd

```

---

### Post by heimo on 2005-11-21
Hmm... maybe locate db wasn't up to date. Try running:
```
find /lib/modules/ -iname 'snd-via*'

```
and
```

ls -al /lib/modules/$(uname -r)/kernel/sound/pci*

```
I'm amazed because it seems like you wouldn't have the usual kernel modules installed. If you don't have one, obviously it can't get loaded (that's what modprobe would do).

---

### Post by dev3n on 2005-11-21
```

root@Skynet:/home/tokyo# find /lib/modules -iname 'snd-via*'
root@Skynet:/home/tokyo# ls -al /lib/modules/$(uname -r)/kernel/sound/pci*
ls: /lib/modules/2.6.12-9-386/kernel/sound/pci*: Filen eller katalogen finns inte

``` 

where "Filen eller katalogen finns inte" means "No such File or Directory"

:confused:

---

### Post by dev3n on 2005-11-21
anyone ? :I

---

### Post by heimo on 2005-11-21
If you're running P4 or some new Intel processor, run:
```
sudo apt-get install linux-686

```If you're running AMD processor, run:
```
sudo apt-get install linux-k7

```
Reboot, run the previous commands (find/ls) again. If that doesn't work either... I'm lost. For what ever reason, you don't seem to have all the default kernel modules installed (on the disk) and this could be indication of other problems (or I'm just mistaken). Any problems during install? Errors, warnings?

---

### Post by dev3n on 2005-11-21
shoo, I got sound again :) 
I installed linux-k7, rebooted then went in to the kitchen and heard sound ! :D 

now, the only problem is to get my sound card to able to play up sounds from 2 different programs...

(Thanks a ***load)

---

### Post by heimo on 2005-11-22
You have something funny going on in your computer. That shouldn't have happened in the first place, and I'd be looking through logs, especially looking for any signs of bad blocks, IO-errors and such. Hopefully it's not failing disk and there's some other reason why you were missing files on the hard disk, but if I were you, I wouldn't trust the computer until I knew what's going on. Not to scare or anything, but it could be something more serious than missing sound (or it could be something as simple as failure to unpack kernel package during install and just those files were missing and now everything is solved).

Check /var/log/messages and run *dmesg|less *on terminal to check boot time errors/warning just after you've rebooted. If you find any errors/warnings, post them and we'll try to guess if there's something wrong. :) Guess very scientifically. ;) If there are no errors, I think it's fine now.

Which settings do you have in Multimedia Systems Selector? And could you run *lsmod|grep -i snd *again, I think you have same audio chipset as I've, and we can compare the modules that are loaded, maybe you're missing one. (I think one of those mixers is needed for multiple sound sources, but I'm definitely not too familiar with Linux sound architectures.)

---

### Post by dev3n on 2005-11-22
I think I solved the problem (almost), I figured out Quake 3 uses "OSS", which resulted that I can't listen to music while playing Quake 3 at the same time. i dunno if u can change it.

---

### Post by heimo on 2005-11-23
[quote=dev3n]I think I solved the problem (almost), I figured out Quake 3 uses "OSS", which resulted that I can't listen to music while playing Quake 3 at the same time. i dunno if u can change it.[/quote]

Oh. I don't know if it can be changed, but someone on gaming subforum might be able to help. :) Anyway, other than game+music, sounds are now ok? That's great. Enjoy Ubuntu, neighbour.

---

