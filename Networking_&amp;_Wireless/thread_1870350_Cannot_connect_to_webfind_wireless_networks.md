---
title: "Cannot connect to web/find wireless networks"
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by _powerplay on 2011-10-27
I just partitioned my Computer so that I can boot with Ubuntu or Windows. The installation process was fine but when I click on the wireless sign (or triangle I guess), the "view wireless networks" is greyed out and I cannot click on it. I tried manually installing my connection but that did not work either.

I found my Wireless driver which is D-Link DWA-525 and I tried running some commands I found like...

Sudo lsmod | D-Link DWA-525
Sudo apt-get install Wireless-tools
lspci | grep Network

These were just some commands I read would help but they did nothing.

I put NetworkMananger and NetworkManager Applet on my USB but they would not open in Ubuntu. 

I downloaded my wireless driver, put it on my USB and tried to install in Ubuntu and it would not work.

I just wanted to state that I have been trying very hard to figure this out and I still am _completely clueless_ as to how I can get internet running in Ubuntu. Very frustrating.

Any help would be GREATLY appreciated. 

I will diligently follow instructions if I can figure this out!!!

---

### Post by chili555 on 2011-10-27
Let's see what your wireless device actually is. Please open a terminal and run and post the result of these commands.```
lspci -nn | grep 0280
uname -r
```Thanks.

---

### Post by lintoon on 2011-10-27
Stupid question but is your wireless enabled.
You may have a wireless switch.  If not you may have to press the "Fn" key with one of your function keys (F1, F2, F3 etc).  You should notice which of the function keys has a wireless symbol on it.  The symbols on the function keys are the  same colour as the "Fn" key.

---

### Post by lintoon on 2011-10-27
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

Find your wireless adapter, follow the link.

---

### Post by _powerplay on 2011-10-27
> **chili555 said:**
> Let's see what your wireless device actually is. Please open a terminal and run and post the result of these commands.```
lspci -nn | grep 0280
uname -r
```Thanks.

When I use those commands, all it told me was this...

3.0.0-12-generic

Which is the Linux that it says that I'm running when I boot Ubuntu. It said nothing about a wireless device.

Should I just un-installl Ubuntu and install 11.04 or something?

---

### Post by _powerplay on 2011-10-27
> **lintoon said:**
> [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

Find your wireless adapter, follow the link.

I did.

The first hyperlink said that the page did not exist yet and the second hyperlink just takes me to Ralinteck.com

---

### Post by _powerplay on 2011-10-28
I understand what this is a very basic question for Ubuntu users but I have really been trying on my own to figure this out and cannot come close. Noob questions or not, I really want to start using Ubuntu and Linux OS but I need internet access in order to do this.

If somebody can help me out here, I would really appreciate it.

I had to bump my own thread, instead of making a new one.

---

### Post by lintoon on 2011-10-28
Try this page.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

It will show you compatibility and installation method.

---

### Post by _powerplay on 2011-10-28
> **lintoon said:**
> Try this page.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

It will show you compatibility and installation method.

I've been their.

I go to the DWA-525 Model (which is my wireless model)

and then I downloaded RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT2860/RT2760/RT2890/RT2790) from Ralinteck.com under the Support>Downlods Tab.

I put it on my USB and tried to install it in Ubuntu but I have no idea how to install it and the "README" in the folder does not help.

It's hard for me to grasp how an OS created by people has so many errors (I mean, there's like 5 threads about inability to access internet just on the 1st page alone).

---

### Post by varunendra on 2011-10-28
> **_powerplay said:**
> It's hard for me to grasp how an OS created by people has so many errors (I mean, there's like 5 threads about inability to access internet just on the 1st page alone).
It is so because not all of the developers are wireless developers and most of the commercial companies do not care for compatibility of their cards with linux. Besides, those with successfully working hardware don't come here creating threads only to tell their success stories, else who knows there could be 5 pages of praise before one problem thread, don't you think so? :)

Anyway, your problem is already being handled by *chili555 *himself - the best guy around here for such problems, so I shouldn't have jumped in. But since he seems to be away for the moment and you seem a bit impatient, may I dare to ask for a few outputs please? Just to confirm you have downloaded the correct driver for your device (your device model no. does not tell what chip it is using). So please post the output of:
```
lspci -nnk | grep -iA2 net
```(please note it is 'piping' symbol between -nnk and grep, not a small 'L'. Just copy-paste to avoid mistakes).

If that does not return any outputs, make sure your card is enabled in BIOS and is physically turned On.

---

### Post by _powerplay on 2011-10-28
> **varunendra said:**
> It is so because not all of the developers are wireless developers and most of the commercial companies do not care for compatibility of their cards with linux. Besides, those with successfully working hardware don't come here creating threads only to tell their success stories, else who knows there could be 5 pages of praise before one problem thread, don't you think so? :)

Anyway, your problem is already being handled by *chili555 *himself - the best guy around here for such problems, so I shouldn't have jumped in. But since he seems to be away for the moment and you seem a bit impatient, may I dare to ask for a few outputs please? Just to confirm you have downloaded the correct driver for your device (your device model no. does not tell what chip it is using). So please post the output of:
```
lspci -nnk | grep -iA2 net
```(please note it is 'piping' symbol between -nnk and grep, not a small 'L'. Just copy-paste to avoid mistakes).

If that does not return any outputs, make sure your card is enabled in BIOS and is physically turned On.

That makes complete sense. Sorry my impatience was so blatant last night. I had just spent like 8 hours searching forums and Google trying to figure all of this out and I just ended up frustrated. I guess learning how to operate a new OS when I was used to one for 13 or 14 years might take some time ;)

Anyways, the code you asked me to use returned this...

[I]net

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
	Subsystem: Dell Dimension 8400 [1028:0177]
	Kernel driver in use: tg3
--
04:01.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]
	Subsystem: D-Link System Inc DWA-525 Wireless N 150 Desktop Adapter (rev.A1) [1186:3c04]
	Kernel driver in use: rt2800pci[/I]

I put the code you asked me to do on a Notepad doc then put it on my USB, restarted Windows and booted with Ubuntu, opened the Notepad file from my USB and typed the code into the Ubuntu Terminal then copied the returning results onto the same notepad file, restarted my comp and loaded Windows then copied the Ubuntu results onto here. Is there any easier way of doing this? Haha

Thank you very much for your help.

---

### Post by varunendra on 2011-10-29
> **_powerplay said:**
> I put the code you asked me to do on a Notepad doc then put it on my USB, restarted Windows and booted with Ubuntu, opened the Notepad file from my USB and typed the code into the Ubuntu Terminal then copied the returning results onto the same notepad file, restarted my comp and loaded Windows then copied the Ubuntu results onto here. Is there any easier way of doing this? Haha
How simple!! Can't be simpler :lolflag:

> **_powerplay said:**
> [I]
04:01.0 Network controller [0280]: Ralink corp. [COLOR=Red]**RT3060 Wireless 802.11n**[/COLOR] 1T/1R [1814:3060]
    Subsystem: D-Link System Inc DWA-525 Wireless N 150 Desktop Adapter (rev.A1) [1186:3c04]
    Kernel driver in use: [COLOR=Red]**rt2800pci**[/COLOR][/I]So apparently, you have downloaded the correct driver. But I have no idea either what kind of package it is and thus how to install it. It might have been a piece of cake for chili, but since he still seems away, let me try something in the meanwhile. To me, the current driver 2800pci doesn't seem a suitable one. So please try:
```
sudo modprobe -r rt2800pci
sudo modprobe rt2860sta
```
rt2860 is a native driver and seems to work with your card. However, I'm not sure if any additional steps are required or if it is the right approach at all. In any case, it is not going to do any harm to the existing status.

If this doesn't work, please post output of:
```
lsmod
```
Since this would be a rather long output, please wrap it between [noparse]```
..and..
```[/noparse] tags by selecting (only) the pasted output then clicking on the **#** symbol at the top of edit box in which you write your posts. (it is recommended for all kind of outputs).

To help with your currently downloaded driver installation, I'll need a list of downloaded packages + maybe the readme file too (believe me, it's just 'me' who needs it, simply because I have absolutely no idea so far about their package). If it is a .tar or .gz archive, you'll need to extract it to a folder, then you can simply use ls command to get a listing of the extracted files. For example, if the files are extracted in a folder named "driver" on the desktop, then:
```
cd Desktop/driver
ls -l ./ > list.txt
```
will generate a "list.txt" file in the same folder, whose contents you can then copy-paste here to let me know which files are there in the package.

Sorry if I made it sound more complex, but as I said, it's just me.

---

### Post by _powerplay on 2011-10-29
> **varunendra said:**
> How simple!! Can't be simpler :lolflag:

So apparently, you have downloaded the correct driver. But I have no idea either what kind of package it is and thus how to install it. It might have been a piece of cake for chili, but since he still seems away, let me try something in the meanwhile. To me, the current driver 2800pci doesn't seem a suitable one. So please try:
```
sudo modprobe -r rt2800pci
sudo modprobe rt2860sta
```

rt2860 is a native driver and seems to work with your card. However, I'm not sure if any additional steps are required or if it is the right approach at all. In any case, it is not going to do any harm to the existing status.

If this doesn't work, please post output of:
```
lsmod
```
Since this would be a rather long output, please wrap it between [noparse]```
..and..
```[/noparse] tags by selecting (only) the pasted output then clicking on the **#** symbol at the top of edit box in which you write your posts. (it is recommended for all kind of outputs).

To help with your currently downloaded driver installation, I'll need a list of downloaded packages + maybe the readme file too (believe me, it's just 'me' who needs it, simply because I have absolutely no idea so far about their package). If it is a .tar or .gz archive, you'll need to extract it to a folder, then you can simply use ls command to get a listing of the extracted files. For example, if the files are extracted in a folder named "driver" on the desktop, then:
```
cd Desktop/driver
ls -l ./ > list.txt
```
will generate a "list.txt" file in the same folder, whose contents you can then copy-paste here to let me know which files are there in the package.

Sorry if I made it sound more complex, but as I said, it's just me.

This was the response to the first command you asked me to run in your other post...

*lspci -nnk | grep -iA2 net*

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
	Subsystem: Dell Dimension 8400 [1028:0177]
	Kernel driver in use: tg3
--
04:01.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]
	Subsystem: D-Link System Inc DWA-525 Wireless N 150 Desktop Adapter (rev.A1) [1186:3c04]
	Kernel driver in use: rt2800pci


These were the results from the commands you asked me to run in your last post

[I]sudo modprobe -r rt2800pci
sudo modprobe rt2860sta[/I]

RESULT: FATAL: Module rt2860sta not found.

*lsmod*

RESULT

Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
binfmt_misc            17292  1 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  0 
radeon                925020  3 
usbhid                 41905  0 
hid                    77367  1 usbhid
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
ttm                    65224  1 radeon
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
serio_raw              12990  0 
drm_kms_helper         32889  1 radeon
drm                   192226  5 radeon,ttm,drm_kms_helper
dcdbas                 14098  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
ppdev                  12849  0 
parport_pc             32114  1 
i2c_algo_bit           13199  1 radeon
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            44173  1 
uas                    17699  0 
tg3                   132972  0 



*cd Desktop/driver*
RESULT: bash: cd: Desktop/driver: No such file or directory

*ls -l ./ > list.txt*

(no results returned from this command)

When I click on my wireless button now, about half of the options have disappeared also.

Hopefully this makes more sense to you than it does to me :confused:

Also sometimes in the Terminal it asks me to put my password in but then it doesn't allow me to type anything in.

---

### Post by varunendra on 2011-10-30
> **_powerplay said:**
> [I]
sudo modprobe rt2860sta[/I]
RESULT: FATAL: Module rt2860sta not found.This indicates perhaps rt2860 is not included in Ubuntu 11.10. I have 11.04 and it is there. You may try to locate it by:
```
locate rt2860sta
```However, I did some search after making the last post, and it seems you will end up compiling the same driver you have downloaded. But before that, **please try this first:**
(again, just copy-paste commands to avoid mistakes)
```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2814031/angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz

tar xzvf angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz

cd angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/

sudo make

sudo make install

echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf

sudo modprobe -rfv rt2800pci

sudo modprobe -v rt3562sta
```(Commands copied from [here]("http://ubuntuforums.org/showpost.php?p=11404530&postcount=6"). Thanks to praseodym)



**_PS_:**
Now a few things about your doubts-
> **_powerplay said:**
> 
*cd Desktop/driver*
RESULT: bash: cd: Desktop/driver: [COLOR=Red]No such file or directory[/COLOR]Means there is no directory named "driver" on your desktop. It was just an example: > For example, if the files are extracted in a folder named "driver" on the desktop, then..> **_powerplay said:**
> *ls -l ./ > list.txt*
(no results returned from this command)The ">" symbol 'redirects' the output (which otherwise would appear on the terminal) to a file that you mention after it. So the above command would have created a file named "list.txt" in the directory in which you were (by default your 'home' directory) when you executed this command. That file contains the output of the command.

But anyway, since you were not in the directory in which the driver files were extracted, that file would have nothing useful in it. If the above instructions didn't work for you, we may need to do it right this time to let me know of the contents of the file you have downloaded from realtek's website..

> **_powerplay said:**
> When I click on my wireless button now, about half of the options have disappeared also.I guess this means you have successfully blacklisted rt2800pci and it's a result of that. If so, you won't need to run 7th and 8th commands I copied above from *praseodym's* post. But it won't hurt running them anyway (it will just result in blacklisting rt2800pci in two places, which is ok).


> **_powerplay said:**
> Also sometimes in the Terminal it asks me to put my password in but then it doesn't allow me to type anything in.Ah, that's the most interesting thing for you to know. Terminal will almost always ask you for your password whenever you run a command with "root" privileges (which is obtained by using *sudo*, *su *or *gksu *before a command). However, if you have supplied it your password recently (within 15 min. I guess), it won't ask for it again.

Now when you see nothing appearing on the terminal while typing your password, it is actually logging each and every key you press, it just doesn't appear on the screen for security purpose. More about sudo:
[http://www.gratisoft.us/sudo/intro.html](http://www.gratisoft.us/sudo/intro.html)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

Hope you are still awake ;). If so, please execute those commands suggested under "**please try this first:**" and tell us if it helped or not.

---

### Post by _powerplay on 2011-10-30
> **varunendra said:**
> ```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2814031/angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz

tar xzvf angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tar.gz

cd angepasster-DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/

sudo make

sudo make install

echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf

sudo modprobe -rfv rt2800pci

sudo modprobe -v rt3562sta
```

This is what I got from that code...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essential
E: Unable to locate package dkms

I also tried the "locate rt2860sta" but no results were returned.

Thank you very much for all of the other information, as well, I am just too exhausted to delve much further.

---

### Post by varunendra on 2011-10-30
> **_powerplay said:**
> This is what I got from that code...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essential
E: Unable to locate package dkms
You need to be connected to internet (through wired connection of course). If you are, open Software Center and see if those packages (*dkms* and *build-essential*) are installed. If they are not, just install them from there.

If you can not connect via cable, just confirm whether those packages are already installed or not (see in Software Center). We can take it from there.

---

