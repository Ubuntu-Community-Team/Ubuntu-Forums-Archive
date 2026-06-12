---
title: "*-network UNCLAIMED   -    so how do I  'claim' it?"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by tjsilver on 2009-11-04
Hi,

I've just put Jaunty on a Toshiba NB200 netbook. Got all 9.04 updates using a 3G dongle (so that works!).

I am trying to install a Netgear 3G Broadband Wireless Router. I'm pretty sure that I've set it up correctly as I can access the web (wirelessly) from my Windows laptop, as I'm using it now.

I can connect to the web using my 3G mobile broadband dongle directly connected. My problem - I just can't figure out how to configure things for wireless in Jaunty!

I know the wifi wasn't disabled in Windows (apparently, that would mean it could never be enabled in Linux) and I have downloaded the 'backports' for Jaunty (which is supposed to help) - but I still cannot find any wireless networks available.

```
lspci
```

told me that the network controller is an Atheros AR9285.

```
lshw -C network
```

returned

[I]*-network UNCLAIMED
[INDENT]description: Network controller
product: AR9285 Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000.03.00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0[/INDENT][/I]

Now, I'm afraid that I have no idea what that means, but I'm guessing that 'unclaimed' may mean something - how do I 'claim' it?. I'm fully aware that this is due to my short-comings and not Ubunto. What is that 'stupid something' that I either have or haven't done? Please, point me on my way to a suitable tutorial.

Tim

---

### Post by chili555 on 2009-11-04
'Unclaimed' typically means no driver has attached to it. If you have an internet connection by ethernet, I suggest you open a terminal and do:```
sudo apt-get install linux-backports-modules-jaunty
```Reboot and you should be good to go.

---

### Post by t0mppa on 2009-11-04
What it means that there's no driver claiming it and thus it's not going to work until one does. For your card, you'll need the ath9k driver. And if you installed the backports, then you should indeed have the latest version available.

Try opening up a terminal and running **lsmod | grep ath**, if the output is empty, it means there are no modules with "ath" in them loaded. If it does show some, then run **sudo modprobe -r <module_name>** for each possibility (ath_pci, ath5k & ath9k - the rest depend on these and get unloaded as the driver module is unloaded). Afterwards run **sudo modprobe ath9k** to load the ath9k and then try *lshw* again to see if it gets associated this time.

---

### Post by tjsilver on 2009-11-04
Guys, thank you.

I'd downloaded the backports, but I hadn't rebooted! What an old fool!

Many thanks,

Tim

---

### Post by fernando_pinhal on 2011-08-16
> **t0mppa said:**
> What it means that there's no driver claiming it and thus it's not going to work until one does. For your card, you'll need the ath9k driver. And if you installed the backports, then you should indeed have the latest version available.

Try opening up a terminal and running **lsmod | grep ath**, if the output is empty, it means there are no modules with "ath" in them loaded. If it does show some, then run **sudo modprobe -r <module_name>** for each possibility (ath_pci, ath5k & ath9k - the rest depend on these and get unloaded as the driver module is unloaded). Afterwards run **sudo modprobe ath9k** to load the ath9k and then try *lshw* again to see if it gets associated this time.

Man... lol...

I got this error after I tried to use a Ndiswrapper driver... then the network goes unclaimed...

When I loaded the modprobe, the network became "claimed".

Thank You! :D:D:D

---

### Post by fernando_pinhal on 2011-08-17
> **fernando_pinhal said:**
> Man... lol...

I got this error after I tried to use a Ndiswrapper driver... then the network goes unclaimed...

When I loaded the modprobe, the network became "claimed".

Thank You! :D:D:D

Oh my god... guys... now I found something that made me mad... 

On a new boot, I used a lsmod and didn't find any ath9k modules... so, I used a sudo modprobe ath9k, then the modules was found on the next lsmod... how can I set the ath9k module to load with the computer boot??

---

### Post by chili555 on 2011-08-17
Open a terminal and do:```
sudo su
echo ath9k >> /etc/modules
exit
```You should be all set.

---

### Post by fernando_pinhal on 2011-08-18
> **chili555 said:**
> Open a terminal and do:```
sudo su
echo ath9k >> /etc/modules
exit
```You should be all set.

Man.. thank you so much... unfortunately... I formated my HD last night when I discovered that the wireless conected and didn't surf on the network...

The windows, worked fine... so the problem should be any mess the I made with the Lubuntu... 

I'll kept this information you gave me safe.

Thanks.:guitar:

---

### Post by zack0273 on 2013-01-04
I have an Intel DQ67EP motherboard with the 82579LM NIC onboard.  It is showing up as unclaimed when i run lshw -C network.

I installed the e1000e 2.1.4 driver directly from intel
I follewed the make install process then 
I then rmmod e1000e
then modprobe e1000e
I have also rebooted

when i did both of these activities the add in nic which is detected lost connectivity and came back but the onboard one is still unclaimed.
Any help would be appreciated.


```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 00
       serial: 68:05:ca:0d:4b:2a
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-NAPI duplex=full firmware=1.8-0 ip=10.1.1.125 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:16 memory:fe5c0000-fe5dffff memory:fe500000-fe57ffff ioport:e000(size=32) memory:fe5e0000-fe5e3fff memory:fe580000-fe5bffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:fe600000-fe61ffff memory:fe628000-fe628fff ioport:f080(size=32)
```

```

uname -a
Linux Polymethia 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

```


lsmod
Module                  Size  Used by
e1000e                195811  0 
w83627ehf              38805  0 
hwmon_vid              12827  1 w83627ehf
coretemp               13525  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224066  1 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
dm_multipath           23230  0 
psmouse                87692  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              13211  0 
tpm_tis                18804  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  472941  4 
joydev                 17693  0 
mac_hid                13253  0 
drm_kms_helper         46978  1 i915
drm                   242038  5 i915,drm_kms_helper
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
mei                    41616  0 
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
dm_raid45              78155  1 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20918  1 dm_mirror
dm_log                 18564  4 dm_raid45,dm_mirror,dm_region_hash

```

---

### Post by Glornax on 2013-01-31
So I have managed to do even worse, and this is the situation for both my Ethernet and Wireless connections!  Is there a way of finding out which particular drivers I need, and installing them from a USB stick or something?

I have a Realtek RTL8111/8168B ethernet controller, and a Intel Centrino Wireless-N Network controller.

Any ideas?

---

### Post by chili555 on 2013-01-31
> **Glornax said:**
> So I have managed to do even worse, and this is the situation for both my Ethernet and Wireless connections!  Is there a way of finding out which particular drivers I need, and installing them from a USB stick or something?

I have a Realtek RTL8111/8168B ethernet controller, and a Intel Centrino Wireless-N Network controller.

Any ideas?Assuming you are running 12.04 or later, the driver for your ethernet is r8169 and for your wireless iwlwifi. Both are already installed by default. If they are not loading automatically, something else may be wrong. Let's try to troubleshoot your wireless. Please open a terminal and do:```
sudo modprobe iwlwifi
dmesg | grep iwl
rfkill list all
lsb_release -d
```That pipe symbol | is on the right side of my US keyboard on the same key with \.

Post the results and we'll figure out what's wrong.

---

### Post by buttolph on 2013-02-08
I have a similar problem! I have a brand new system with an AR8161 Gigabit Ethernet controller, and I see that I need to download and install a new driver in order for Ubuntu to be able to access my network, and therefore, the internet. But how in the heck can you download and install the driver if you can't get on the internet through the Ubuntu install (or livecd or usb)? On my system, I am trying to do a dual boot with Windoze 7 where I have internet access. Can I download onto a usb and transfer or something, or download while booted on windows and save to a hard disk file or something, somehow, in order to get that driver to marry with my Ubuntu installation?  I have been grinding away for 2 weeks on this issue. I have had lessons on how to build a driver from scratch, (but it required internet access), how to download a new driver recently minted (but it required internet access), but am still dead in the water. If you can help with a detailed suggestion, you will be my hero!!

---

### Post by chili555 on 2013-02-08
> Can I download onto a usb and transfer Exactly! Before we proceed, let's verify the exact device. It is likely that someone else has the same device and therefor the same solution applies. Please open a terminal and run and post:```
lspci -nn | grep 0200
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Thanks.

---

### Post by buttolph on 2013-02-08
Excellent! Thanks!!!

Here is what I get when I run the command you suggested:

ubuntu@ubuntu:~$ lspci -nn | grep 0200
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)
ubuntu@ubuntu:~$

I am currently running Ubuntu off of a liveCD (so I imagine if I install a new driver via usB or whatever your idea is to solve this problem, this would need to be done after I actually install Ubuntu, or during the install process, or something.. perhaps there is a way to test to see if this proposed solution works when I am running Ubuntu off of livecd?)

---

### Post by chili555 on 2013-02-08
We know it works. If it were me, I'd install it first and then install the ethernet driver. It uses the driver *alx*.```
$ modinfo Desktop/Forum/compat-wireless-3.6.8-1-snpc/drivers/net/ethernet/atheros/alx/alx.ko | grep 1091
alias:          pci:v0000[COLOR="Red"]1969[/COLOR]d0000[COLOR="Red"]1091[/COLOR]sv*sd*bc*sc*i*
```Here is a thread that describes the process, including the 'no internet' conumdrum: [http://ubuntuforums.org/showthread.php?t=2050126](http://ubuntuforums.org/showthread.php?t=2050126)

Please see post #6 and following. If you are installing 12.10, substitute quantal for each occurence of precise here.

You could download linux-backports-modules-cw-quantal-generic. However, its dependencies are every bit as challenging.

Last, I'd suggest this package instead of that in the thread I linked: compat-wireless-3.6.8-1-snpc.

Post back any questions or concerns.

If wireless is an option, we can be done in three minutes!

---

### Post by buttolph on 2013-02-08
This is fantastic. I have reviewed the links and process you suggest, and noted the great acclaim you received from the other person for your easy to follow directions. The pressure is on for me to not look like an idiot and screw this up and ask for more help! First I will install Ubuntu and study the details, and give it a try. I am doing this at work, with pesky customers taking priority so it might take me anywhere from an hour to a day to get back at this, but I will surely come back and mark this SOLVED assuming it all works (as I am highly confident it will!) Or ask for your patience on another dumb question or two as the case may be. Thank you SO much!

---

### Post by chili555 on 2013-02-08
Ask all the questions you want. That's what I do and I enjoy it. I look forward to your success!

---

### Post by buttolph on 2013-02-08
Ok, I installed 12.04 64 bit Ubuntu. Have a small problem (I think small), as I can not access windows 7 on the dual boot. I assume I have some maintenance on my grub file or something, and hope once I get internet on my Ubuntu I can resolve that. But I have a "newbie" question on getting the driver and components necessary onto the USB drive to sneaker-net them over to my desktop. I went to post #6 as you suggested. I downloaded "build-essential", "dpkg-dev", "g++", "gcc", "libc6", and "make" files, and simply copied them to the USB (I assume I don't have to burn them or some darn thing). Then I noted the instructions said I needed to get the linux headers. "uname -r" says the following: 

3.2.0-29-generic

The instructions also say this: 

"This package depends on the headers matching your running kernel. That means that, in addition to the 'generic' or generic-pae' package, you'll also need linux-headers for your kernel. For example, if the uname -r command shows that you are running 3.2.0-23-generic, you will need linux-headers-3.2.0-23-generic."

I assume that I need to copy to my USB another file here, but the file that I find to download at the referenced link is this:

 Exact hits

Package linux-headers-generic

precise (devel): Generic Linux kernel headers 
3.2.0.37.45 [security]: amd64 i386

So here is my question: since the instructions say I need an EXACT MATCH to my header, and my "uname -r" said I am 3.2.0-23-generic, and this one at the link says "3.2.0.37.45", is THIS the file (64 bit version) that I need to download and copy to the USB even though it doesn't match the 3.2.0-23?  My head hurts but I am hanging in there.... :-)

---

### Post by chili555 on 2013-02-08
>  my "uname -r" said I am 3.2.0-23-generic, Then you need this:  [http://packages.ubuntu.com/precise/linux-headers-3.2.0-23-generic](http://packages.ubuntu.com/precise/linux-headers-3.2.0-23-generic)

Be sure you need 32- or 64-bit:```
arch
```32-bit will return i686 and 64-bit returns x86_64.

You are doing well so far; keep on keepin' on!

---

### Post by buttolph on 2013-02-08
okay, I think I'm getting closer. One thing - when I saw the red dots meaning that there was a dependency on the files, and then click on the red dotted file, and I find yet another page with more red dotted files, am I supposed to copy all of those as well, and keep nesting until there are no more red dotted files? If so, I am probably missing some. But anyway, I dragged all the files to the desktop and typed "cd desktop" in a terminal. No such file or directory. So then I figured maybe I was already in the desktop by default? Anyway, then I typed sudo dpkg -i *deb. It asked for my password. Encouraging. Then it said "error processing *.deb (--install): cannot access archive: no such file or directory
Errors were encountered while processing *.deb. I am truly a neophyte at the command line. What is the stupid command to be in the right directory here? (I used to know how to do this about a hundred years ago with DOS - looks vaguely familiar...)  :-)

Thank you once again! I'm making a career out of this but I smell victory ahead!

---

### Post by chili555 on 2013-02-09
You are getting closer!> when I saw the red dots meaning that there was a dependency on the files, and then click on the red dotted file, and I find yet another page with more red dotted files, am I supposed to copy all of those as well, and keep nesting until there are no more red dotted files?At some point they are all ready installed on your system. I'd just download the first level and try it. You will get an obvious warning if something else is needed; something like:> Package A not configured. Package A depends on Package B which is not installed so leaving A unconfigured.So that tells you to go download and install B.> I dragged all the files to the desktop and typed "cd desktop" in a terminal. No such file or directory.It is actually:```
cd [COLOR="Red"]D[/COLOR]esktop
```I know, go figure! Then list the contents of the directory:```
ls
```If the listing includes all the .deb files, please proceed.

---

### Post by buttolph on 2013-02-09
I kept looking for your post and not seeing one, figured you might take the weekend off! But then I see I am only on page 2 of 3, and you posted 6 hrs ago on page 3! Well, am I a dope or what?  Anyway, I changed the desktop to Desktop and let 'er rip. made it through with maybe a half dozen additional dependencies, so I went back and downloaded those, sneaker-net it back to the Umbuntu desk top and executed sudo dpkg again. More dependencies noted! Even more than before, plus warning notes that "more than one copy of package bla bla bla has been unpacked in this run. One in particular concerns me because it said dpkg-dev depends on ligdpkg-perl (= 1.16.1.2ubuntu7); however: Version of libdpkg-perl on system is 1.16.7ubuntu6. But I had copied 1.16.1.2ubuntu7 already. Do I have to do something to un-install 1.16.7ubuntu6 beforehand or something? Maybe I goofed by executing sudo command a second time when I should have un-sudo'ed first from my previous attempt? Or maybe I should have just executed the missing dependencies one by one? Or something? Thanks again!

---

### Post by chili555 on 2013-02-09
I am not quite sure I understand. Did you download to your desktop  ligdpkg-perl-1.16.1.2ubuntu[COLOR="Red"]7[/COLOR]? Do things work better if you manually install it first?```
cd ~/Desktop
sudo dpkg -i ligdpkg-perl*.deb
```If it installs without complaint, then I'd try the others.> Maybe I goofed by executing sudo command a second time when I should have un-sudo'ed first from my previous attempt? To modify your system; i.e. adding or removing software, sudo is *always* required.> But then I see I am only on page 2 of 3, and you posted 6 hrs ago on page 3! Been there and done that. Don't feel bad.

---

### Post by buttolph on 2013-02-09
I assume you meant libdpg-perl-1.16.1.2ubuntu7 ("b" instead of "d"), and yes, I had downloaded that, but for some reason on a subsequent sudo command, the response said "dpkg-dev depends on ligdpkg-perl (= 1.16.1.2ubuntu7); however: Version of libdpkg-perl on system is 1.16.7ubuntu6." That puzzled me because I had copied the ubuntu7 file and had executed it (or so I thought) with a *.deb command as it was on my desktop with all the others. I am guessing that one of the later wave of dependent files must have somehow unpacked and reloaded the ubuntu6 version, undoing what I had done. Or something. 

In any event, I tried what you suggested - 

cd ~/Desktop
sudo dpkg -i ligdpkg-perl*.deb (except with a "b" instead of a "d").

That one said I have a dependency issue where libtimedate-perl is not installed. So are you saying I should just try these one at a time, try downloading and installing libtimedate-perl first, then if it works, retry libdpg-perl*.deb (and if there is another dependency problem, install THAT first, and so on, one at a time?). At this point, I am getting confused on what "the others" are. I don't mind paying close attention to a whole series of one-at-a-time installs in the interest of finally getting this to work.

---

### Post by chili555 on 2013-02-10
> So are you saying I should just try these one at a time, try downloading and installing libtimedate-perl first, then if it works, retry libdpg-perl*.deb (and if there is another dependency problem, install THAT first, and so on, one at a time?Exactly. Of course, post back if you feel like you are lost or at a dead end.

---

### Post by buttolph on 2013-02-17
Hi again - I'll bet you thought I was all done! HA! Another week down, another week without internet on Ubuntu. I am stuck trying to install the dependencies for build-essentials. I followed all of the individual dependencies, copying them file by file, for build essential's dependent unit dpkg-dev, and I think I have that one squared away. The problem is in the g++. In trying to install g++, it indicates that this depends on having g++-4.6 (>= 4.6.3-1~). Following the links you suggested to get that "red dot" file, it shows a dependency on libstdc++6-4.6.dev (=4.6.3-1ubuntu5). Fair enough. But in copying and trying to install libstdc++6-4.6.dev, it says it is dependent on g++-4.6 (>= 4.6.3-1~)! Each of these two files indicates a dependency on the other when I try to install them. I seem to be stuck in an infinite loop of interdependency here. Any ideas?  Thanks as always! (At least I am getting good at my terminal command lines!)

---

### Post by chili555 on 2013-02-17
I've never actually tried this, but you might try installing both in one command:```
sudo dpkg -i g++*.deb  libstdc++*.deb
```If that doesn't work, install the first one ignoring dependencies:```
sudo dpkg -i --ignore-depends=libstdc++  g++*.deb
```Then the second one ought to install easily:```
sudo dpkg -i libstdc++*.deb
```Keep going! You are closing in on it!

---

### Post by buttolph on 2013-02-17
Your two-for the price of one command worked, by the way. And then I was able to install build-essentials. And then I was able to install my header. And then I was able to download the compat-wireless file, and I followed your directions to build and install the driver, and then....... (drum roll please....)   IT WORKED!!!!!!!!!!!!!! I am online with ubuntu!!!! Hail to chili555, the Ubuntu guru!!!!! Thank you Thank you Thank you!!!! Now that this massive success has been achieved... just one more question - can I somehow save this new driver to a cd, along with the idiot-proof directions on installation... so if I have to reinstall ubuntu I can just load it rather than going on this quest through the frozen tundra of Siberia to create it again?

---

### Post by chili555 on 2013-02-17
> and then....... (drum roll please....) IT WORKED!!!!!!!!!!!!!! Awesome! Great job, my friend.> can I somehow save this new driver to a cd, along with the idiot-proof directions on installation... so if I have to reinstall ubuntu I can just load it rather than going on this quest through the frozen tundra of Siberia to create it again? The only thing I know you can do is transfer the all the deb files to the CD, along with the compat package.

When Update Manager offers a newer kernel version, also known as linux-image and to complete the update, you reboot, you'll need to recompile compat-wireless:```
cd Desktop/compat-wireless_whatever
sudo su
make clean
make
make install
modprobe alx
exit
```We have taken a few shortcuts, so please clean up:```
sudo apt-get install linux-headers-generic
```All we installed was the headers for your running kernel version; the -generic package will make sure the headers are updated every time linux-image is updated.

Post back if you have more questions. You did a superb job.

---

### Post by slapperig on 2013-02-17
I am having a similar problem with my 12.04 install. (by the way, Chili555, you are the man, I really hope you can help me.)

I recently upgraded my wife's woefully out-of-date install to 12.04, and the computer no longer recognizes either wired or wireless connections. This is a 64-bit system, a Dell Inspiron 1721.

Running 
```
sudo lshw -C network
```
returns 
```
*-network
description: Network controller
product: BCM4311 802.11b/g WLAN
vendor: Broadcom Corporation
physical id:0
bus info: pci@0000:0b:00.0
version 01
width 32 bits
clock: 33 MHz
capabilities: pm msci pciexpress bus_master cap_list
configuration: driver=wl latency=0
resources: irq:17 memory:fe8fc000-fe8fffff

*-network UNCLAIMED
description: Ethernet controller
product: BCM4401-B0 100Base-TX
vendor: Broadcom corporation
physical id:0
bus info: pci@0000:03:00.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=64
resources: memory:fe5fe000-fe5fffff
```

Running
```
lspci -nn | grep 0200
```
returns
```
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev02)
```

Running
```
rfkill list all
```
Returns
```
0: dell-wifi: Wireless LAN
softblocked: no
hard blocked: no
1: dell-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
```
However, it still refuses to acknowledge there are wireless capabilities ("No network devices available")

I somehow managed to get it to recognize that there was a wired connection last night, however during an update the computer froze, and after restarting it goes into a kernel panic every few minutes. I've since booted an earlier kernel and the wired connection no longer works.

Anything you can do to help would be greatly appreciated.

---

### Post by chili555 on 2013-02-17
> lspci -nn | grep 0200I'd much rather see:```
lspci -nn | grep 02[COLOR="Red"]8[/COLOR]0
```I suspect we will fix wired and wireless at one step! Magic, eh?

---

### Post by slapperig on 2013-02-17
Sure thing ```
 lspci -nn | grep 0280
```
returns```
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev01)
```

Thank you for your quick reply!

---

### Post by chili555 on 2013-02-17
Hook up your seemingly inoperative ethernet and do:```
sudo modprobe b44
sudo modprobe ssb
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```Detach the ethernet and tell us how it's all working.

bcmwl-kernel-source whick provides the driver wl is incorrect for your wireless. It also blacklists ssb which is needed by your ethernet.

---

### Post by slapperig on 2013-02-17
See, I knew you were the man.

Just to let you know, none of the modprobes return any information at all, but as soon as I ran ```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```

both wireless and wired started working.

You are amazing!

---

### Post by chili555 on 2013-02-17
Glad it's working! Have fun.

---

### Post by buttolph on 2013-02-20
Hi again, Chili555. I'll bet you thought I was done, eh? Well, I got reading things you should do when you install 12.04, such as download all updates, and I did that which kicked me off the internet again. I am trying to follow the directions to re-do what I did before, having saved all the files to a cd, and I see that I think I have a new header so I guess I need a new header file. I get this when executing uname -r:

3.2.0-38-generic

It used to say 3.2.0-23-generic

I need a new header file, correct? Would you be kind enough to tell me where I can get one? Thanks so much! I am so far down the learning curve now thanks to you!

---

### Post by buttolph on 2013-02-20
ok, I think I might have been barking up the wrong tree thinking I needed a new header file. I gather that I have a generic header file installed now. Does that make sense? So I copied all of the .deb files from my last crusade onto my desktop as you suggested (having carefully saved them to CD) and then did this:

cd Desktop
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx

I got the "Processing new driver-select request..." message, and then a number of "Backup exists: Makefile.bk" messages, all very encouraging. I figured all that was left was to do this:

make
sudo make install
sudo modprobe alx

But no... I typed "make" and got this message:

/bin/sh: 1: callot create /home/jim/Desktop/compat-wireless-3.5.1-1-snpc/.config
: Permission denied
make: *** [/home/jim/Desktop/compat-wireless-3.5.1-1-snpc/,compat_autoconf_compa
t-wireless-v3.5.1-1-snpc] Error 2.

HUH?

Any help? Thanks so much as always!!!

---

### Post by Yellow Pasque on 2013-02-20
> Permission denied
This means you need "sudo make" even though you're in your home directory (probably because you used sudo to extract something or create a directory).

---

### Post by buttolph on 2013-02-20
Gosh, I thought I had tried sudo before, but I did it now and it worked! I must have typo-ed something before or something.... beats me. Anyway, I am back online!! Took me three weeks last time to learn how to sneaker-net the parts over from an internet machine to build this stupid driver, with many headaches along the way, this time down to about a half hr invested. I love screaming down the learning curve!  Thanks, guys!!!! (If this were windows and I had a glitch, they would convince me that I did something wrong but then they would throw up their hands and tell me to reinstall....)

---

### Post by chili555 on 2013-02-20
> This means you need "sudo make" even though you're in your home directory (probably because you used sudo to extract something or create a directory). Exactly!

However, whenever you build again where building has gone on previously, it's always wise to ask the apprentices to clean up the construction site so you start...well, clean:```
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe alx
exit
```I'm glad it's working. It reminds me of my first venture in Linux when I compiled HomePNA (!!) drivers. The first time, it took me a week; the second time, an hour; and the tenth time, ten minutes!

---

### Post by buttolph on 2013-02-20
Thank you once again! Finding you guys on Ubuntu makes a big difference figuring out my way around the operating system. You have been a BIG help!

(By the way, next time I will do the "Sudo Su" and "Make Clean" as you suggest, but for now, I ain't touching it!!! It works.. don't anyone breath!!

:D

Thanks again

---

### Post by alpimj on 2013-05-07
> **chili555 said:**
> 'Unclaimed' typically means no driver has attached to it. If you have an internet connection by ethernet, I suggest you open a terminal and do:```
sudo apt-get install linux-backports-modules-jaunty
```Reboot and you should be good to go.


what if, there is no access to the internet?

---

### Post by chili555 on 2013-05-07
> **alpimj said:**
> what if, there is no access to the internet?Wow! You aren't still running Jaunty, are you? Please post:```
lspci -nn | grep 0280
lsb_release -d
```Thanks.

---

### Post by Yellow Pasque on 2013-05-07
@alpimj: please use your original thread for support. You are confusing people by cross-posting and quoting ancient posts.

@chili555: this person has already started a thread with more information: [http://ubuntuforums.org/showthread.php?t=2143039](http://ubuntuforums.org/showthread.php?t=2143039)

---

### Post by sempervirenses on 2013-11-12
Chili, thank you for all that you do. You are helping solve this issue for so many people, and now you just solved it for me as well, thank you!! You are awesome! I was working at this for hours upon hours, for several days now, after upgrading from ubuntu 10.04 to 13.10, and having no wired or wireless connection. Then someone posted to you with the same network controller as mine: Broadcam BCM4311, and with one seemingly non-functioning ethernet cable and the magic code in post #33, lo and behold, connection!! Thank you :)

---

### Post by sempervirenses on 2013-11-13
Hey Chili, once again the codes in post #33 got my internet working (we only have wired ethernet connection available here so I haven't been able to check wifi, but it looks like my laptop is ready for wifi now too) the only issue is, when I reboot my computer, the changes aren't saved, and I am back to having no connection. For now - I can just re-enter these codes into the terminal, but a permanent save and solution would be ideal. Thank you for your help!

---

### Post by chili555 on 2013-11-13
> **sempervirenses said:**
> Hey Chili, once again the codes in post #33 got my internet working (we only have wired ethernet connection available here so I haven't been able to check wifi, but it looks like my laptop is ready for wifi now too) the only issue is, when I reboot my computer, the changes aren't saved, and I am back to having no connection. For now - I can just re-enter these codes into the terminal, but a permanent save and solution would be ideal. Thank you for your help!Sometimes, the reason that the b43 driver doesn't load automagically is that the blacklist file wasn't removed. Let's do do:```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```Other times, it doesn't get loaded for reasons I can't fathom; everything is just perfect, except it doesn't work! Let's fix that, too:```
sudo -i
echo b43 >> /etc/modules
echo b44 >> /etc/modules
exit
```Now it ought to work properly on boot but if not, post back and we'll be happy to help.

---

### Post by sempervirenses on 2013-11-13
that solved it, thank you!!

---

