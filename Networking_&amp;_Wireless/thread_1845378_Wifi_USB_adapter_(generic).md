---
title: "Wifi USB adapter (generic)"
date: 2011-09-16
forum: Networking &amp; Wireless
---

### Post by silvergoat on 2011-09-16
I have a USB card that my brother gave me, and it comes with Linux drivers.....the problem is that I come from Windows and don't reallly know how to install this.  I tried some commands from the web that came from Ubuntu, but they didn't work and as I read some of the 10's of files that are in the Linux subfolders....the readme says I have to compile.  Although I have an idea of what it means, I don't know how it is applied.

How can I make this work because I really don't want to run Windows again, and Lubuntu actually seems like it may be preferable to me over Ubuntu if I can just get enough practice with it.

Thanks-
Ozzie

---

### Post by praseodym on 2011-09-17
Hi,

please show the terminal outputs of

```
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by silvergoat on 2011-09-17
lsusb returned this-

```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lsmod returned this-

```
Module                  Size  Used by
dm_crypt               22463  0 
snd_intel8x0           33213  1 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
ppdev                  12849  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32111  1 
lp                     13349  0 
psmouse                73312  0 
serio_raw              12990  0 
shpchp                 32345  0 
snd                    55295  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport                36746  3 ppdev,parport_pc,lp
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
nouveau               621970  2 
ttm                    65184  1 nouveau
drm_kms_helper         40745  1 nouveau
drm                   184164  4 nouveau,ttm,drm_kms_helper
floppy                 60032  0 
tg3                   131476  0 
i2c_algo_bit           13184  1 nouveau
video                  18951  1 nouveau
```

iwconfig returned this-

```
lo        no wireless extensions.

eth0      no wireless extensions.
```

rfkill list returned nothing

---

### Post by praseodym on 2011-09-17
Download from here the Linux driver for kernel 2.6.35 and later:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

Save it on your Desktop and install the tools you need to compile:

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
cd ~/Desktop/[COLOR="Red"]NameOfFolder/[/COLOR]
sudo su
make
make install
exit
```

Reboot your system. After that update your system and install the metapackage for the kernel headers:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-generic
```
You may need to compile again with the new kernel.

Controls:

```
iwconfig
lsmod
dmesg | grep r8
sudo iwlist scan
```

---

### Post by wildmanne39 on 2011-09-17
Hi, I am looking for the driver for your adapter so I need this information please:
```
cat /etc/lsb-release; uname -a
```
Thank you

---

### Post by silvergoat on 2011-09-17
> **praseodym said:**
> Download from here the Linux driver for kernel 2.6.35 and later:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

Save it on your Desktop and install the tools you need to compile:

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
cd ~/Desktop/[COLOR="Red"]NameOfFolder/[/COLOR]
sudo su
make
make install
exit
```

Reboot your system. After that update your system and install the metapackage for the kernel headers:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-generic
```
You may need to compile again with the new kernel.

Controls:

```
iwconfig
lsmod
dmesg | grep r8
sudo iwlist scan
```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

```

lsmod

```
Module                  Size  Used by
dm_crypt               22463  0 
snd_intel8x0           33213  1 
ppdev                  12849  0 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
snd                    55295  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32111  1 
serio_raw              12990  0 
shpchp                 32345  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
nouveau               621970  2 
ttm                    65184  1 nouveau
drm_kms_helper         40745  1 nouveau
drm                   184164  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13184  1 nouveau
tg3                   131476  0 
video                  18951  1 nouveau
floppy                 60032  0 

```

dmesg | grep r8

no return

sudo iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

---

### Post by silvergoat on 2011-09-17
> **wildmanne39 said:**
> Hi, I am looking for the driver for your adapter so I need this information please:
```
cat /etc/lsb-release; uname -a
```
Thank you

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux simplypc-HP-d530-CMT-DS061AR 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux

```

---

### Post by wildmanne39 on 2011-09-17
Hi, did you do what praseodym said to do in his last post?
Thank you

---

### Post by silvergoat on 2011-09-17
> **wildmanne39 said:**
> Hi, did you do what praseodym said to do in his last post?
Thank you

yep-

Everything.

One issue though- during the first list of commands, before the restart, I exited out of the terminal after the first command ran.  I then remembered that each line was one command so I opened a terminal back up and proceeded with the other commands in order.

---

### Post by wildmanne39 on 2011-09-17
Hi, did it look like it finished compiling and installing after you opened the terminal again or did you get errors, or did you not really read what the terminal said? just asking so I will know how to proceed.
Thank you

---

### Post by silvergoat on 2011-09-17
All of the commands in the first set of instructions ran, but the 2nd set didn't install or update anything....I think they read that there were 0 changes made or something along those lines.

---

### Post by wildmanne39 on 2011-09-17
Hi, is this the driver you installed RTL8188CE-VAU?
Thank you

---

### Post by silvergoat on 2011-09-17
The folder files read 8192 am going to double check the download options on the realtek site again.

Edit:

It was not 8188CE-VAU, is that the one I needed?  I was directed to "Linux driver for kernel 2.6.35 (and later)", but 8188CE-VAU does not have that option.  Also, the 8188CE gives the same 92 marked folder.  I just downloaded the 8188CE-VAU.

---

### Post by silvergoat on 2011-09-18
I got it working!

The right drivers for my adapter were the 8192-8188 drivers you last suggested.  I ran the commands with the linux directory on my desktop and it now works.

Thanks, but I do have a question-  How do you figure out what drivers are necessary?  The drivers that came with the adapter didn't work, and there are no markings on the box or the adapter that indicate what model or brand it is.

---

### Post by wildmanne39 on 2011-09-18
Hi, sometimes it is a little complicated, we use this command
for usb devices it tells us the device.

This is your device Bus 001 Device 002: ID [COLOR="Red"]0bda:8176[/COLOR] Realtek Semiconductor Corp. 
```
lsusb
```
Then the numbers it gives we look it up with google or at this site.
[http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers)
but in your case it showed the wrong driver and the one I suggested works.

I know that because I helped someone else with that same adapter get his working and it used the driver I gave you according to the numbers we got when you ran lsusb.

If you think I helped even a little would you please click on the link in red in my signature and show your support for me becoming an ubuntu member? Also would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by silvergoat on 2011-09-18
Is there a command to examine the PCI wifi adapters?  I'm really liking this Lubuntu and I am likely going to install it on my work computer, but it has a PCI adapter instead of USB.....

I'll check that link out for you. ):P

---

### Post by wildmanne39 on 2011-09-18
Hi, this command will tell you almost all wireless adapters and wired too.
```
lspci -nn | grep -e 0280 -e 0200
```
Thank you I appreciate it very much.

---

### Post by silvergoat on 2011-09-18
> **wildmanne39 said:**
> Hi, this command will tell you almost all wireless adapters and wired too.
```
lspci -nn | grep -e 0280 -e 0200
```
Thank you I appreciate it very much.

Thanks again-

---

### Post by wildmanne39 on 2011-09-18
Hi, your very welcome! enjoy ubuntu and welcome to the community.

---

