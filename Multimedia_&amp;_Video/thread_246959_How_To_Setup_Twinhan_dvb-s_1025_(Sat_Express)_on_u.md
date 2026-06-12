---
title: "How To Setup Twinhan dvb-s 1025 (Sat Express) on ubuntu"
date: 2006-08-30
forum: Multimedia &amp; Video
---

### Post by mfarouk30 on 2006-08-30
hello to everyone here.
i will explain how could i get my DVB-s card to work with me as it take alot of time to do that.

There are two notes i want mention before beginning:

First: Note that i only tried this way with my card 
Second: My card is twinhan DVB-S 1025 sat Express 

the source of this HowTo is LinuxTVwiki.

As of my experience, there is no need to install driver so we will make the following step directly:

[COLOR="Blue"]**Step 1: Download some packages**[/COLOR]
```
[COLOR="Red"]sudo [/COLOR]apt-get install mercurial linux-headers-$(uname -r) build-essential
```

note: sudo command is optional if you aready use root account. 
another note: since Ubuntu has no root account so you should use sudo


**[COLOR="Blue"]Step 2: Obtain some data from v4l website.[/COLOR]**
```
hg clone http://linuxtv.org/hg/v4l-dvb
```


**[COLOR="Blue"]Step 3: Going to the directory of video4linux (the driver)[/COLOR]**
```
cd v4l-dvb
```


**[COLOR="Blue"]Step 4: Compiling the driver.[/COLOR]**
```
[COLOR="Red"]sudo[/COLOR] make
```


[COLOR="Blue"]**Step 5: Installing what the driver.**[/COLOR]
```
[COLOR="Red"]sudo[/COLOR] make install
```


[COLOR="Blue"]**Step 6: Restart the computer**[/COLOR]
```
[COLOR="Red"]sudo[/COLOR] reboot
```

[COLOR="Blue"]**Step 7: getting firmware**[/COLOR]
In this card you don't need to a firmware so i will skip this step. Go to Step 8.

[COLOR="Blue"]**Step 8: Edit "modules" file to auto load the driver's modules**[/COLOR]
After reboot, we must edit the file /etc/[COLOR="Blue"]modules[/COLOR] to make the process of
loading the driver modules is done automatic every startup. edit this file as root and add the following lines
```
#VP-1025
bttv i2c_hw=1 card=0x71
dvb-bt8xx
dst
```

[COLOR="Red"]NOTE THAT THIS CODE IS FOR THIS CARD ONLY.[/COLOR]


**[COLOR="Blue"]Step 9: Download Kaffeine[/COLOR]**
We have to download and install Kaffeine media player as it has a DVB support.
```
apt-get install kaffeine
```

[COLOR="Blue"]**Step 10: Preparing the file of frequency**[/COLOR]

[COLOR="Red"]**note:** If the sattelite you aim to watch is popular so may be the file of frequency is bundled with kaffeine. 
check this so you may be able to skip this step.[/COLOR]

Now you need to get at least one frequency of your sattelite that you want to recieve.

So if you get a freqency so do the following

1.open a new document (plain text) put the frequency on it like this

```
# NILESAT
# freq pol sr fec
S 11938000 V 27500000 3/4
```

the first and the second sentence is optional 
the third one is important

the first S: i put it as you say and i don't really know the penefit of it but i think you must type it.

11938000: this is the frequency i put to scan on Nile sat,change the frequency by one you have in the sattelite 

v:for vertical ,if your polarity is horizental then change it to h

27500000: i don't remember what this refer to but you must have a number like that at the information of your frequency

3/4: also replace this with the number of yours

after this save this file with anyname (DVB for example) and save it the following directory:

```
/[COLOR="Red"]**yourname**[/COLOR]/.kde/share/apps/kaffeine/dvb-s
```

note: you must replace [COLOR="Red"]yourname[/COLOR] in the code with your login name

noe that the folder .kde is hidden and to show it you must do the following in the file manager

```
View --> show hidden files
```

**[COLOR="Blue"]The final step: Make scan from kaffeine[/COLOR]**
```
Open kaffeine --> DVB menu --> Configure DVB
```
now select the file we created before DVB then Press OK

```
DVB menu --> channels
```
and make scan then save the list


after all the hardwork we do it must now work.

the end of the help

please give me any attention about the help

note: i changed alot this Howto to make it better, so give me your opinion.

GOOD BYE

---

### Post by Mufasa on 2006-09-21
> **mfarouk30 said:**
> hello to everyone here.
i will explain how could i get my DVB-s card to work with me as it take alot of time to do that.

First: Note that i only tried this way with my card 
Second: My card is twinhan DVB-S 1025 sat Express 

the source is LinuxTVwiki

as my experience the driver is not installed so we will make the following

```
[sudo] apt-get install mercurial linux-headers-$(uname -r) build-essential
```

note: sudo command is optional if you aready use root account.

```
hg clone http://linuxtv.org/hg/v4l-dvb
```

this is the code to otain the code of viedo 4 linux.

```
cd v4l-dvb
```

this code to go to the directory of video4linux

```
[sudo] make
```

is to compile the program
note:you may use sudo command if you didn't logged in  as root

```
[sudo] make install
```

this for istalling what we compiled
again take care of sudo command.

```
[sudo] reboot
```

this command will make your computer to restart. i do it but i don't know if this is effective :-k .

in my card i didn't need a firmware to i will skip this step.

now we are almost done 

just get at least one frequency of your sattelite you want to recieve or at  least get channel list.

so if you get a freqency so do the following

1.open anew document (plain text) put the frequency on it like this

```
# NILESAT
# freq pol sr fec
S 11938000 V 27500000 3/4
```

the first and the second sentence is optional 
the third one is important

the first S: i put it as you say and i don't really know the penefit of it but i think you must type it.

11938000: this is the frequency i put to scan on Nile sat,change the frequency by one you have in the sattelite 

v:for vertical ,if your polarity is horizental then change it to h

27500000: i don't remember what this refer to but you must have a number like that at the information of your frequency

3/4: also replace this with the number of yours

after this save this file with anyname (DVB for example) and save it in your home directoy.

```
apt-get install dvb-utils
```

after this 

```
mkdir /home/[COLOR="Red"]yourname[/COLOR]/.szap
```

note: you must replace [COLOR="Red"]yourname[/COLOR] in the code with your lonin name

scan /home/[COLOR="Red"]yourname[/COLOR]/DVB \
    > /home/[COLOR="Red"]yourname[/COLOR]/.szap/channels.conf

if all goes well you must see some thing of channels names appear
wait untell it finished.

then you will have channels.conf file in this directory

```
/home/[COLOR="Red"]yourname[/COLOR]/.szap
```

now we need a program to run DVB channels .i will install gxine by this command

```
apt-get install gxine
```

after this completed. go to your home directory then 

```
View --> show hidden files
```

then you will find a directory named .szap
go to it (enter it or whatever) then usually you will find a file named channels.conf (that what we do above) go and copy it (right click --> copy)
then go back to your home directory and then go to .xine directory and paste the file onto this directory.

so the final step go to the menu application then sound & video then gxine 

after running it go to file list then select DVB from the list.

after all the hardwork we do it must now work and run any of the channels stored in channels.conf

the end of the help

please give me any attention about the help


This worked for me, but I had to use make xconfig and remove the ACI Mixer for it to compile 100%

Added to /etc/modules:

#VP-1025
bt878
dst
dvb-bt8xx

Added to /etc/modprobe.d/options

#VP-1025
options dvb_core dvb_shutdown_timeout=0
options bttv i2c_hw=1 card=0x71


now she is a working!!!

---

### Post by Lusse on 2006-09-23
How do you add the modules ;)

---

### Post by mfarouk30 on 2006-09-24
> **Lusse said:**
> How do you add the modules ;)

hello 

if you mean how to add the modules in the modules text file then 
just open it and put the name of the module in the file

the screenshot is good example

---

### Post by Lusse on 2006-11-18
Ok thanks :-)

---

### Post by lowmax on 2007-10-04
> **Mufasa said:**
> This worked for me, but I had to use make xconfig and remove the ACI Mixer for it to compile 100%

Added to /etc/modules:

#VP-1025
bt878
dst
dvb-bt8xx

Added to /etc/modprobe.d/options

#VP-1025
options dvb_core dvb_shutdown_timeout=0
options bttv i2c_hw=1 card=0x71


now she is a working!!!

I've got the VP-1030 model, does anyone know what is it that I have to change in the /etc/modules and /etc/modprobe.d/options or will the above settings work too.

Thanks

---

### Post by lowmax on 2007-10-04
Hi, I've been trying for days to get my PCI Twinhan DVB-S, bt878 chip set, to work, to no avail. My last attempt was following the guide found here. I've got as far as reboot, but nothing seems to work, I tried all dvb players, and it seems the card is still not detected.

I tried to include any information that I thought will be valuable to solve this issue, but just incase I forgot something, and i'm sure I did, then please request it with the method to obtain it, I'm quite new at Ubuntu and Linux in general.

dmesg
```
[   60.737723] bttv: driver version 0.9.17 loaded
[   60.737729] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   60.737821] bttv: Bt8xx card found (0).
[   60.737852] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 22 (level, low) -> IRQ 20
[   60.737867] bttv0: Bt878 (rev 17) at 0000:02:01.0, irq: 20, latency: 32, mmio: 0xec7fe000
[   60.737882] bttv0: using: Twinhan DST + clones [card=113,insmod option]
[   60.737904] bttv0: gpio: en=00000000, out=00000000 in=00fdecfd [init]
[   60.737984] bttv0: using tuner=4
[   60.951423] bttv0: add subdevice "dvb0"
[   61.136848] bt878: AUDIO driver version 0.0.0 loaded
[   61.139363] bt878: Bt878 AUDIO function found (0).
[   61.139388] ACPI: PCI Interrupt 0000:02:01.1[A] -> GSI 22 (level, low) -> IRQ 20
[   61.139397] bt878_probe: card id=[0x0], Unknown card.
[   61.139398] Exiting..
[   61.139404] ACPI: PCI interrupt for device 0000:02:01.1 disabled
[   61.139410] bt878: probe of 0000:02:01.1 failed with error -22
[   61.234034] dvb_bt8xx: unable to determine DMA core of card 0,
[   61.234039] dvb_bt8xx: if you have the ALSA bt87x audio driver installed, try removing it.
[   61.234047] dvb-bt8xx: probe of dvb0 failed with error -14
[   61.338649] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   61.338685] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   61.348905] ieee80211_crypt: registered algorithm 'WEP'
[   61.761266] SoftMAC: Open Authentication completed with 00:11:50:92:a1:4a
[   61.770580] NET: Registered protocol family 10
[   61.770749] lo: Disabled Privacy Extensions
[   61.770833] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   61.771702] intel8x0_measure_ac97_clock: measured 55975 usecs
[   61.771707] intel8x0: clocking to 48000
[   61.775732] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   62.812822] lp0: using parport0 (interrupt-driven).
[   62.855174] ivtv:  ==================== START INIT IVTV ====================
[   62.855181] ivtv:  version 1.0.0 (2.6.22-12-generic SMP mod_unload 586 ) loading
[   62.855237] ivtv:  ====================  END INIT IVTV  ====================

```

lspci
```
02:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```

lsmod | grep bt8xx
```
dvb_bt8xx              18180  0 
dvb_core               82216  2 dst,dvb_bt8xx
bt878                  11832  2 dst,dvb_bt8xx
dvb_pll                15492  1 dvb_bt8xx
bttv                  177012  2 dvb_bt8xx,bt878
i2c_core               26112  10 cx88xx,dst,ivtv,dvb_bt8xx,dvb_pll,tuner,bttv,i2c_algo_bit,tveeprom,nvidia

```

:~$ scan /home/my username/DVB \
> /home/my username/.szap/channels.com
```
scanning /home/my username/DVB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
```

When I checked there isn't any dvb folder inside dev.

Any clues?
Thanks

---

### Post by mieze on 2008-01-12
Hi,

your problem may be related to the one I had when upgrading to a new SuSE version.
Please read this posting:

[http://www.suseforums.net/index.php?showtopic=41573&pid=222748&mode=threaded&show=&st=&#entry222748](http://www.suseforums.net/index.php?showtopic=41573&pid=222748&mode=threaded&show=&st=&#entry222748)

---

### Post by m0rtal on 2008-06-18
thanks! now my VP-1030 works :)

---

