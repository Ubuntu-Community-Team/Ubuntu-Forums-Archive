---
title: "Azurewave AD-SP200 (Twinhan 1027) Setup"
date: 2009-09-05
forum: Multimedia Software
---

### Post by megacrypto on 2009-09-05
I just got this card a week ago, and I found out that (naturally) it is not yet supported by v4l-dvb except with some patched vanilla kernel. So, I tried to follow the guides I found here and there on the net and this is what I reached at the end:

First of all my H/W:
Mobo: MSI K9N2GM with onboard Nvidia GeForce 8200
CPU: AMD X2 250 (3GHz, 3MB Cache)
Memort: 2GB
TV-Tuner: Azurewave AD-SP200 (aka Twinhan 1027)

So here are the steps I got to get the card working:
1. I installed Ubuntu 8.10 Desktop (which I since some time and had the kernel 2.6.27-7-generic
2. Did the following update:
```

sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r) subversion git-core mercurial kernel-package libncurses5-dev

```
3. Removed the nvidia-common (for reason it results in an error when installing the compiled kernel
```

sudo chmod -x /etc/kernel/postinst.d/nvidia-common
sudo apt-get remove nvidia-common

```
4. Got the required kernel (kernel.org) which is 2.6.27.10 and extracted it into /usr/src:
```

sudo tar xvf /home/user/linux-2.6.27.10.tar.bz2 -C /usr/src

```
note: change the path to where you downloaded the kernel

5. Created a sym-link:
```

cd /usr/src
sudo ln -s linux-2.6.27.10 linux

```

6. compiled the new kernel with the patch (attached here)
```

cd linux
sudo cp /boot/config-`uname -r` ./.config 
sudo cp /boot/config-`uname -r` .config 
sudo patch -p1 < /home/user/kernel-2.6.27.10-twinhan.patch
sudo make oldconfig 
sudo make-kpkg clean
sudo fakeroot make-kpkg --initrd --append-to-version=-dvb kernel_image kernel_headers 

```
Notes:
coping the config from the current kernel, I found in some guide that it points to ./.config and in another to .config, so I just did the two (not really sure which one is correct at this stage)

also when doing the make oldconfig, you will be asked a few questions, and with either Y or M.
7. installed the new kernel:
```

cd ..
sudo dpkg -i linux-image-2.6.27.10-dvb_2.6.27.10-dvb-10.00.Custom_i386.deb
sudo dpkg -i linux-headers-2.6.27.10-dvb_2.6.27.10-dvb-10.00.Custom_i386.deb

```

8. rebooted
```
sudo reboot
```

once the system rebooted i checked for the running kernel by:
```
uname -r
```
and it gave me: 2.6.27.10-dvb which i have just built
also checked if my card was identified by:
```
dmesg | grep -i dvb
```
and it gave me a long list:
```

[    0.000000] Linux version 2.6.27.10-dvb (root@homeserver) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Sat Sep 5 19:25:59 EET 2009
[   11.319992] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   11.319993] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   11.319997] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   11.319998] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   11.320010] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   11.320013] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   11.320022] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   11.320023] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   11.320033] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   11.320034] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   11.320036] cx88[0]:    card=39 -> KWorld DVB-S 100
[   11.320037] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   11.320038] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   11.320040] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   11.320042] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   11.320043] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   11.320046] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   11.320054] cx88[0]:    card=52 -> Geniatech DVB-S
[   11.320055] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   11.320060] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   11.320070] cx88[0]:    card=63 -> Geniatech X8000-MT DVBT
[   11.320071] cx88[0]:    card=64 -> DViCO FusionHDTV DVB-T PRO
[   11.320077] cx88[0]:    card=68 -> Twinhan VP-1027 DVB-S
[   11.512830] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   11.512832] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   11.512835] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   11.512837] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   11.512840] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   11.512842] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   11.512851] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   11.512852] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   11.512861] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   11.512864] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   11.512866] cx88[0]:    card=39 -> KWorld DVB-S 100
[   11.512867] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   11.512869] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   11.512870] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   11.512872] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   11.512873] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   11.512876] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   11.512884] cx88[0]:    card=52 -> Geniatech DVB-S
[   11.512885] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   11.512890] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   11.512899] cx88[0]:    card=63 -> Geniatech X8000-MT DVBT
[   11.512901] cx88[0]:    card=64 -> DViCO FusionHDTV DVB-T PRO
[   11.512906] cx88[0]:    card=68 -> Twinhan VP-1027 DVB-S

```

Now my card is there at no 68 [Twinhan VP-1027 DVB-S], so in order to tell ubuntu to use this card, I did the following:
```

sudo -s
cd /etc/modprobe.d
echo "options cx88xx card=68" > cx88xx
modprobe -r cx8800
modprobe cx8800

```
then I rebooted again

and now if i dmesg i get the following:
```

[    0.000000] Linux version 2.6.27.10-dvb (root@homeserver) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Sat Sep 5 19:25:59 EET 2009
[   11.321063] cx88[0]: subsystem: 153b:117a, board: Twinhan VP-1027 DVB-S [card=68,insmod option]
[   11.544877] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   11.544879] cx88/2: registering cx8802 driver, type: dvb access: shared
[   11.544882] cx88[0]/2: subsystem: 153b:117a, board: Twinhan VP-1027 DVB-S [card=68]
[   11.544884] cx88[0]/2: cx2388x based DVB/ATSC card
[   11.590628] DVB: registering new adapter (cx88[0])
[   11.590632] DVB: registering frontend 0 (Fujitsu MB86A16 DVB-S)...

```

all I need right now is to figure out how to get remote to work??

any ideas?

---

### Post by megacrypto on 2009-09-05
I tried the same steps, but now with 9.04 server, and it worked on the kernel 2.6.27.10 still I have no remote control working?

---

### Post by megacrypto on 2009-09-06
i have noticed (and im not an expert in patches at all) that the patch being applied here defines the [CX88_BOARD_TWINHAN_VP1027_DVBS] and adds it to the list of cards in the cx88-cards.c and also does that in the cx88-dvb.c but it does not add it in the cx88-input.c !!

so, im guessing here, that when the (patched) drivers are installed, there is no mentioning for the Twinhan card in the input file, and therefore there is no remote control support? 


I have attached the cx88 folder of the 2.6.27.10 kernel (original before patching) in the hope that someone with some knowledge in patching could take a look at it and maybe help out.

---

### Post by megacrypto on 2009-09-06
ok .. this is what i got now, i added a line to the cx88-input.c for the remote and recompiled the kernel, now when i list the input devices, i get:
```

I: Bus=0001 Vendor=153b Product=117a Version=0001
N: Name="cx88 IR (Twinhan VP-1027 DVB-S)"
P: Phys=pci-0000:01:09.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/0000:01:09.0/input/input5
U: Uniq=
H: Handlers=kbd event5
B: EV=100003
B: KEY=c0904 10004800000000 0 2018000 18000000001 9e000000000000 90000ffe

```

i installed lirc, and select linux input layer and select event5 as the input layer, but when i irrecord to set my conf file, it does not pick up anything. 

could anyone help out here?

---

### Post by justnick on 2009-09-09
i have the same card but i installed mythbuntu 9.04 and with no luck to run this card
i compiled the kernel 2.6.27.10 and patcheds it with the patcher attached in this topic after i reboot 
the terminal loaded and no x window
i used sudo starx to load the window x  but the computer freeze
i'm waiting for solution

---

### Post by megacrypto on 2009-09-12
> **justnick said:**
> i have the same card but i installed mythbuntu 9.04 and with no luck to run this card
i compiled the kernel 2.6.27.10 and patcheds it with the patcher attached in this topic after i reboot 
the terminal loaded and no x window
i used sudo starx to load the window x  but the computer freeze
i'm waiting for solution

when you reboot, do you log into the compiled kernel? you can find that out by writting:
```
uname -r
```
and see if you're logged into the correct kernel

next you need to see if that card is loaded by:
```
dmesg | grep -i dvb
```

next if you want to check if the card is working or not, you can do that by installing the dvb-utils and scanning for channels:
```

sudo apt-get install dvb-utils
# use -s<#> if there is a diseq
# use -t1 to scan only TV Services
sudo scan -v -s0 -t1 /usr/share/dvb/dvb-s/Nilesat101+102-7.0W > /home/mylin/channels.conf
# or this to scan all types of channels
sudo scan -v -s0 /usr/share/dvb/dvb-s/Nilesat101+102-7.0W > /home/mylin/channels.conf

```

as for mythbuntu, i honestly have never tried it myself, but lets say if you wanted to start mythtv manually from the prompt, what command will you give? i would suggest that you would look for that command and try it out and if that luanches mythtv, then just add that to /etc/rc.local to launch it automatically on startup

---

### Post by kathem_1 on 2010-05-06
My friend it's a good tutorial but Now the kernal is 2.6.32 only we need just update for this tutorial it is seem to be tho only solution i found over the net 

and I want to have a look on this patch if you could install it Just give us the headlines 

[https://patchwork.kernel.org/patch/79753/](https://patchwork.kernel.org/patch/79753/)

it is a new patch for this Card and thanx for all your offers

---

### Post by megacrypto on 2010-05-15
> **kathem_1 said:**
> My friend it's a good tutorial but Now the kernal is 2.6.32 only we need just update for this tutorial it is seem to be tho only solution i found over the net 

and I want to have a look on this patch if you could install it Just give us the headlines 

[https://patchwork.kernel.org/patch/79753/](https://patchwork.kernel.org/patch/79753/)

it is a new patch for this Card and thanx for all your offers

unfortunately i don't have this card anymore.

---

### Post by akha666 on 2010-11-23
[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]Thanks for this guide
I have Q
Did your batch working with Ubuntu 10.10 with Kernel 2.6.35-24-generic ?
I have the same card and I like make it working with ubuntu , I don't like to [/COLOR][/SIZE][/FONT][FONT=Comic Sans MS][SIZE=3][COLOR=Blue]restart [/COLOR][/SIZE][/FONT][FONT=Comic Sans MS][SIZE=3][COLOR=Blue]any more to Win 7 to watch my DVB-S if I got it working fine in Ubuntu
can you help me[/COLOR][/SIZE][/FONT]

---

### Post by elshabrawi on 2011-01-08
i have the same issue i hope i could find help to make it work on ubuntu 10.10

---

