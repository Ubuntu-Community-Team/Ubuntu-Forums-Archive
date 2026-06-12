---
title: "Problems installing Broadcom BCM4318"
date: 2013-02-11
forum: Networking &amp; Wireless
---

### Post by semicomatose on 2013-02-11
As far as I understand, what I have to do is,
sudo apt-get install firmware-b43-installer
sudo apt-get --reinstall install bcmwl-kernel-source

I've run into a small range of problems, the most current one being that when I try to install bcmwl-kernel-source, it installs until the terminal outputs "DKMS: install completed.", but then the terminal freezes there and won't return to the command prompt or anything.

Dell Inspiron 2200, trying to install Xubuntu 12.04

Thanks,
Joker

---

### Post by semicomatose on 2013-02-12
some help on this?

-Joker

---

### Post by Hadaka on 2013-02-12
Hi, from a wired connection please do

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
 
```

---

### Post by semicomatose on 2013-02-12
When I try to run
```
sudo apt-get remove --purge bcmwl-kernel-source
```
I get
```
"E: dpkg was interrupted, you musy manually run 'sudo dpkg --configure -a' to correct the problem."
```
When I run that, it looks like it's trying to install bcmwl again, and once again freezes at
```
DKMS: install completed.
```

Thanks for the reply,
Joker

---

### Post by Hadaka on 2013-02-12
Hi, please post the output of

```
lspci -nn | grep 0280
lsmod 
```
thanks

---

### Post by semicomatose on 2013-02-12
```
lspci -nn | grep 0280
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
joker@halper:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
wl                   3032542  1 
snd_rawmidi            25424  1 snd_seq_midi
dell_laptop            17767  0 
snd_seq_midi_event     14475  1 snd_seq_midi
dcdbas                 14098  1 dell_laptop
pcmcia                 39826  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                96718  0 
snd                    62218  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  419326  2 
cfg80211              178877  1 wl
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
e100                   36289  0 
serio_raw              13027  0 
lib80211               14040  1 wl
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
rfcomm                 38139  4 
bnep                   17830  2 
bluetooth             158479  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp

```

Thanks for any help,
Joker

---

### Post by Hadaka on 2013-02-12
Hi, please try this command again

```
sudo apt-get remove --purge bcmwl-kernel-source 
#and
sudo modprobe -rfv wl
```

---

### Post by semicomatose on 2013-02-12
```
joker@halper:~$ sudo apt-get remove --purge bcmwl-kernel-source 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

Maybe it's worth mentioning that, when I run
```
sudo dpkg --configure -a
```
and it freezes at
```
DKMS: install completed.
```
I usually try CTRL+C, which doesn't work, and then I usually close the Terminal window, which is probably the interruption that apt is telling me about.

-Joker

---

### Post by Hadaka on 2013-02-12
ok, did your run

[CODE]sudo modprobe -rfv wl [CODE]

---

### Post by semicomatose on 2013-02-12
```
sudo modprobe -rfv wl
```
When I run that, it gives no output, and then freezes, refusing to return to command prompt.

-Joker

---

### Post by Hadaka on 2013-02-12
Hi, lets see if the b43 will load
with a wired connection connected to the internet do
```
sudo apt-get install b43-fwcutter firmware-b43-installer 
```

---

### Post by semicomatose on 2013-02-12
```
sudo apt-get install b43-fwcutter firmware-b43-installer
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

Same issue. Thanks for your reply, took me an hour to notice that it went to page 2.

-Joker

---

### Post by Hadaka on 2013-02-12
Hi, how did you load the wl in the first place? I'm trying to figure
out how to cancel or remove the dpkg that is causing a problem.
as an aside, I am running an old dell inspiron 1300 here with just
a 40 gig drive and the same brcm 4318 card, its dual booting
ubuntu 11.10 and 12.04, same vintage as your 2200, so it will work
once the dpkg issue is sorted. see what you get from this command

```
dpkg -C 
```

---

### Post by semicomatose on 2013-02-12
```
joker@halper:~$ dkpg -C
No command 'dkpg' found, did you mean:
 Command 'dpkg' from package 'dpkg' (main)
dkpg: command not found
```

Doesn't seem to have liked that. I dunno where wl game from, probably was reading the wrong article and tried installing the wrong package. All I've used in trying to work this thing is apt-get and the Software Center.

-Joker

---

### Post by Hadaka on 2013-02-12
Yes, sorry about that..typo

```
dpkg -C 
```

and yeah..wl is the wrong driver for that card

---

### Post by semicomatose on 2013-02-12
```
sudo dpkg -C
The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 bcmwl-kernel-source  Broadcom 802.11 Linux STA wireless driver source.
```

My fault for not noticing the typo. What now?

-Joker

---

### Post by Hadaka on 2013-02-12
Hi, im learning as well here..sooo
try this
```
sudo dpkg -r bcmwl-kernel-source 
```

---

### Post by semicomatose on 2013-02-12
That seems to have worked to remove it. Gonna reboot for good measure and look out for the next step in a minute. I assume now is when I install the proper firmware, followed by the proper drivers? How is that accomplished?

-Joker

---

### Post by Hadaka on 2013-02-12
Hi, from a wired connection, connected to the internet do
```
sudo apt-get install b43-fwcutter firmware-b43-installer 
```
```
sudo modprobe b43 
```

---

### Post by semicomatose on 2013-02-12
It works. I'm connected to wireless now. I swear I did exactly those commands earlier and they didn't work. I'd bet that xubuntu somehow installed the wl driver without asking me and it's been blocking me all along.

-Joker

---

### Post by Hadaka on 2013-02-12
Great !, thanks for my education on this, just to make sure the
b43 loads at boot or restart please do

```
sudo su
echo b43 >> /etc/modules
exit
#and please post the output of..
lsmod
 
```

---

### Post by semicomatose on 2013-02-13
I ended up re-installing Xubuntu for other reasons, but this time I was prepared for the Wireless issue. It turns out I was right!

On first boot, it asks you if you want to install some proprietary drivers. You install them, assuming they're correct, and reboot. But then, you've got the wl driver installed, and when you try to install the correct b43 driver, it won't let you until you can uninstall wl. So this time, I said no to the recommended driver and went straight ahead with
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
and it worked perfectly!

-Joker

---

### Post by Hadaka on 2013-02-13
Hi, glad you have it all sorted out, I would guess
loading the incorrect driver by that method
happens quite often.
Please use thread tools and mark this SOLVED
"Thanks for the fun"

---

### Post by linsol on 2013-03-27
I'm trying to get my 4318 card working. this is what I get
bill@Laptop1:~$ sudo modprobe b43
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

How do I get rid of the blacklist?

Disreguard, got it working...somehow..lol.

---

### Post by 1tree2tall on 2013-04-08
hello
i registered just to say Thank you to op semicomatose and hadaka. i had the same problem as OP.
after hours of sudo this and sudo that sudo to no end..... i finally found my answer here! Thank you again
now i can sleep =P
i am new to linux btw

---

### Post by john51 on 2013-08-14
Thanks, very helpful for even my older Broadcom BCM43111 firmware needs!

---

### Post by isidora2 on 2013-09-22
Hi, I also registered just to say thanks! I was dealing with the same problem that semicomatosed had, only in Ubuntu, and this was very helpful.

Thanks!

---

### Post by bobclops on 2013-12-17
Worked for me, Grateful thanks from a technophobic old man.  The community spirit and time people spend helping others is fantastic.
Thanks again.

---

### Post by edward20 on 2014-12-15
Thanks a lot! That's really helpful. The problem afflicts me couples of days and finally solved here.

---

### Post by wildmanne39 on 2014-12-15
Old thread closed! please do not post in old threads.
Thanks

---

