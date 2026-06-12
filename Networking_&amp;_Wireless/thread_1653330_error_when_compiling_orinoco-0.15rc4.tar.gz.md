---
title: "error when compiling orinoco-0.15rc4.tar.gz"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by kfwlil on 2010-12-26
Hi all,
I am very much a newbie to linux (and not overly computer literate otherwise, so please be gentle).  This is my first interaction with ubuntu (currently running karmic on an old gateway laptop with kernel 2.6.31-22-generic) and, as is par for how I handle challenges, I've jumped in with both feet - which is to say this is not a dual-boot situation. I've spent some time reading the forums (and other sources of information) and am grateful for all the knowledgeable people who are willing to share what they know.

My operating system seems to be functioning properly.   I can get online via ethernet, but not via wireless.  I have a lucent orinoco gold PC24E-H-FC (PCMCIA) card, which the computer isn't seeing.  I am trying to follow the instructions here: [https://help.ubuntu.com/community/WifiDocs/OrinocoKismet](https://help.ubuntu.com/community/WifiDocs/OrinocoKismet) to install the driver.  Everything is going well until I get to the sudo make line.  At that point I get the following display: 
make -C /usr/src/linux-headers-2.6.31-22-generic M=/usr/src/orinoco-0.15rc4 KERNELRELEASE= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-22-generic'
/usr/src/orinoco-0.15rc4/Kbuild:8: *** Wireless extensions are not enabled.  Stop.
make[1]: *** [_module_/usr/src/orinoco-0.15rc4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-22-generic'
make: *** [modules] Error 2

I am looking for suggestions as to how I can fix it so I can continue on with the instructions.  (For the record - if I just continue on, I can change directory in the next line, but I cannot remove either hermes or orinoco as "no such file or directory" seems to exist.)
Thanks for any help you can offer.
-Kris

---

### Post by gordintoronto on 2010-12-26
Did you install "build-essential" with Synaptic?

The instructions apply to a very old version of Ubuntu, but I don't know if that is important.

If you enter the command:
lspci
your wireless adapter does not appear?

One post I found in Google indicates that the orinoco gold only supports wireless-b, and does not support wpa encryption. Personally, I would discard it, if those things are true.

---

### Post by kfwlil on 2010-12-27
gordintoronto,
Thanks for taking the time to respond.  
I do have build essential (version 11.4) installed.  

The ouput to lspci is:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 CardBus bridge: Ricoh Co Ltd RL5c478 (rev 80)
00:08.1 CardBus bridge: Ricoh Co Ltd RL5c478 (rev 80)
00:0c.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator
00:0d.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 09)
00:0d.1 Serial controller: Xircom Device 00d3
01:01.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)
I don't know how to decipher all of this, but none of it looked to me like it is seeing my card.

Because it seems like it might also be relevant, here's the output to lspcmcia:
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:00:08.0)
Socket 1 Bridge:       [yenta_cardbus]     (bus ID: 0000:00:08.1)
Socket 1 Device 0:    [-- no driver --]    (bus ID: 1.0)
Here also, while I don't know exactly what I'm looking at, it doesn't seem to me like it is seeing the card.

I appreciate the advice to discard, but for now I'm pretty involved in wanting to solve this problem, for the satisfaction and the knowledge, in addition to the desire to get online without a wire. 

-Kris

---

### Post by kfwlil on 2011-01-22
I just wanted to post back with the results of this problem.
As of this morning while I had spent some more time trying to figure out my problem, I hadn't found a solution yet.  Then I spoke with the person who gave me this computer and in passing they mentioned that they just remembered the wireless card didn't work.  Clearly I no longer need to try and get this driver compiled.   
Thanks to those of you who took the time to read my post and/or offer advice.
-Kris

---

