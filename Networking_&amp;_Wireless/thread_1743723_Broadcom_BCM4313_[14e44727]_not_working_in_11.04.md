---
title: "Broadcom BCM4313 [14e4:4727] not working in 11.04"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by riso325 on 2011-04-29
Hi guys, after upgrading from 10.10 to 11.04 wifi ist working. I know that this ia a common problem. I tried everything that was here on the forum to solve it. I cant install b43 because **4727** isnt supported, i tried to reinstall/uninstall STA driver for broadcom using > sudo apt-get install bcmwl-kernel-source, nothing helped. So my last chance is to install driver from broadcom which is not in a deb rep and as a newbie i almost always when trying to install something from a terminal get an error. When installing driver from [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php") and using a command **make** i get this :


> administrator@Lenovo-B560:~/Plocha/wifi$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
  LD      /home/administrator/Plocha/wifi/built-in.o
  CC [M]  /home/administrator/Plocha/wifi/src/shared/linux_osl.o
  CC [M]  /home/administrator/Plocha/wifi/src/wl/sys/wl_linux.o
/home/administrator/Plocha/wifi/src/wl/sys/wl_linux.c: In function ‘wl_attach’:
/home/administrator/Plocha/wifi/src/wl/sys/wl_linux.c:485:3: error: implicit declaration of function ‘init_MUTEX’
make[2]: *** [/home/administrator/Plocha/wifi/src/wl/sys/wl_linux.o] error 1
make[1]: *** [_module_/home/administrator/Plocha/wifi] error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
make: *** [all] error 2

hope you can help me with this

---

### Post by josephmills on 2011-04-29
[http://wireless.kernel.org/en/users/Drivers/brcm80211](http://wireless.kernel.org/en/users/Drivers/brcm80211)

---

### Post by riso325 on 2011-04-29
i cant work with git, havent learned yet. can you help me with it ? :D

---

### Post by demonboy on 2011-04-30
I found myself at this page and I too do not understand what I am supposed to do here. I'd appreciate some help too. Thanks.

---

### Post by sbarlow on 2011-05-02
I installed Natty and found my Broadcom BCM4313 wireless card didn't work. 

I found this:
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

and followed the instructions at the end, in the section "HOW TO INSTALL A PRE-COMPILED DRIVER". 

Wireless works fine now.

Stu.

---

### Post by Olcay on 2011-05-05
I havent tried this on natty but it works on maverick, if you have a lenovo b560 laptop, after the STA driver installation run this command from terminal:

```
echo 'options acer_wmi wireless=1' | sudo tee /etc/modprobe.d/acer_wmi.conf
```

then reboot.

---

### Post by swaroop933 on 2011-05-07
This works.. Thank u

---

### Post by hsnfor on 2011-05-08
hi riso325,

have you successfully installed your Wireless yet? I have the same problem like yours and please help me if you have the solution. Many thanks

---

### Post by labord on 2011-05-18
Hi, 

I experience the same problem. I just upgraded to 11.04 and the wireless stopped working. I run an ASUS 1215P netbook. When I run lspci -vvnn | grep 14e4, I get

> 14e402:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

I tried everything I came across, including the brcm80211 wireless driver, but nothing worked. I have run out of ideas.

Any suggestions anyone?

---

### Post by josephmills on 2011-05-18
this card works with the b43sta mods/driver and the firmware-b43-installer or you could use the git tree I am a n00b I have no clue how to do that

---

### Post by labord on 2011-05-18
> this card works with the b43sta mods/driver and the firmware-b43-installer or you could use the git tree I am a n00b I have no clue how to do that

Thanks for that. Unfortunatelly, the b43/sta driver is the broadcom driver I was referring to as not working for me.

---

### Post by josephmills on 2011-05-18
> **labord said:**
> Thanks for that. Unfortunatelly, the b43/sta driver is the broadcom driver I was referring to as not working for me.

labord could we please see a ```
lspci -vnn | grep 14e4 
``` thanks

---

### Post by labord on 2011-05-18
> **josephmills said:**
> labord could we please see a ```
lspci -vnn | grep 14e4 
``` thanks

sure joseph, 

```
labord@*:~$ lspci -vnn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```

will appreciate any help

---

### Post by josephmills on 2011-05-18
please go to synaptic package manager enter in bcm into the search bar and take a pic like mine dont worry they should not be the same 
thanks 
**EDIT** could we also see a ```
rfkill list all
```
joseph

---

### Post by labord on 2011-05-18
Aye aye, sir:

```
labord@*:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: eeepc-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

Screenshot attached

labord

---

### Post by josephmills on 2011-05-18
> **labord said:**
> Aye aye, sir:

```
labord@*:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: eeepc-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

Screenshot attached

labord

please mark for removal the bcmwl-kernel-source press the apply button then  shut down you computer yes shut down then start it up again and install the bcmwl-kernel-source then the broadcom-sta-common and the broadcom-sta-source also install the firmware-b43-installer then shut down and then reboot tell us when you get that far thanks

---

### Post by labord on 2011-05-18
Ok, done, so far no change.

---

### Post by josephmills on 2011-05-18
```
rfkill list all 
``` and ```
lsmod
``` thanks also re-install the bcmwl-kernel-source

---

### Post by labord on 2011-05-18
> **josephmills said:**
> ```
rfkill list all 
``` and ```
lsmod
``` thanks

```
~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: eeepc-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
labord@*:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_hda_codec_realtek   255820  1 
sco                    17779  2 
bnep                   17785  2 
eeepc_wmi              18771  0 
l2cap                  48656  3 bnep
sparse_keymap          13666  1 eeepc_wmi
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
i915                  450944  3 
uvcvideo               66851  0 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
btusb                  18160  1 
ndiswrapper           192828  0 
psmouse                73312  0 
videodev               75143  1 uvcvideo
bluetooth              65565  8 sco,bnep,l2cap,btusb
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
atl1c                  36237  0 
```

---

### Post by josephmills on 2011-05-18
```
dmesg | grep wl
```and a ```
 sudo apt-get install --reinstall bcmwl-kernel-source
``` ```
lsmod | grep wl
``` thanks again

---

### Post by labord on 2011-05-18
> **josephmills said:**
> ```
dmesg | grep wl
```and a ```
 sudo apt-get install --reinstall bcmwl-kernel-source
``` thanks again

I thank you. The first command did not return any (perceptible) result, the reinstall went smoothly. 

labord

---

### Post by josephmills on 2011-05-18
> **labord said:**
> I thank you. The first command did not return any (perceptible) result, the reinstall went smoothly. 

labord

```
sudo modprobe wl
```

---

### Post by labord on 2011-05-18
> **josephmills said:**
> ```
sudo modprobe wl
```

no luck so far. Network Manager still says "Wireless network disconnected"...

---

### Post by josephmills on 2011-05-18
> **labord said:**
> no luck so far. Network Manager still says "Wireless network disconnected"...

you did not get any errors just went to the next line ? ```
lsmod | grep wl 
``` and a ```
dmesg | grep wl  
```

---

### Post by labord on 2011-05-18
no errors at all

---

### Post by josephmills on 2011-05-18
please see post 24 again thanks

---

### Post by labord on 2011-05-18
> **josephmills said:**
> you did not get any errors just went to the next line ? ```
lsmod | grep wl 
``` and a ```
dmesg | grep wl  
```

```
labord@*:~$ lsmod | grep wl
wl                   2642531  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
labord@*:~$ dmesg | grep wl
[ 2021.960351] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2021.960367] wl 0000:02:00.0: setting latency timer to 64
```

Is this a sign of hope? I wonder

---

### Post by josephmills on 2011-05-18
```
sudo reboot
``` I wonder if it is a backport that is holding this up?

---

### Post by labord on 2011-05-18
> **josephmills said:**
> ```
sudo reboot
``` I wonder if it is a backport that is holding this up?

Well, whatever it is, it has not gone away. The funny thing is that unless I do modprobe wl, the Network Manager does not even show the wireless in the drop down menu (I fear this is the result of my trying to use the windows driver via ndiswrapper, to no use alas. Before I tried ndiswrapper and the windows driver, there had also been no wireless conectivity, but at leat I could see that in the Network Manager in the menu without implementing modprobe wl).

What a mess...

labord

---

### Post by josephmills on 2011-05-18
> **labord said:**
> Well, whatever it is, it has not gone away. The funny thing is that unless I do modprobe wl, the Network Manager does not even show the wireless in the drop down menu (I fear this is the result of my trying to use the windows driver via ndiswrapper, to no use alas. Before I tried ndiswrapper and the windows driver, there had also been no wireless conectivity, but at leat I could see that in the Network Manager in the menu without implementing modprobe wl).

What a mess...

labord
I know right what a mess lets try this go back to additional drivers is there one there if so activate it then reboot again
could we also see a ```
iwlist scan
``` thanks again we are getting closer though

---

### Post by labord on 2011-05-18
> **josephmills said:**
> I know right what a mess lets try this go back to additional drivers is there one there if so activate it then reboot again
could we also see a ```
iwlist scan
``` thanks again we are getting closer though

Thanks for your patience. 

```
labord@*:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.
```

The additional driver seems to be in use (though it wasn't before I started to follow your suggestions). See the attached scrnshot.

labord

---

### Post by josephmills on 2011-05-18
un-activate it then reactivate it then you guessed it reboot again

---

### Post by josephmills on 2011-05-18
> **labord said:**
> Thanks for your patience. 

labord
 also thank you for your patience, as this is a lot of fun for me we will get this :D

---

### Post by labord on 2011-05-18
> **josephmills said:**
> also thank you for your patience, as this is a lot of fun for me we will get this :D

I wish you were right. Back after reboot, had to modprobe wl again, what now?

---

### Post by josephmills on 2011-05-18
> **labord said:**
> I wish you were right. Back after reboot, had to modprobe wl again, what now?

```
rfkill list all 
```

```
 dmesg | grep wl 
```
```
lsmod | grep wl 
``` 

also go to synaptic and type in bcm and give me a screenshoot thanks again

---

### Post by labord on 2011-05-18
```
~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: eeepc-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
labord@Jenovefa:~$ dmesg | grep wl
[  131.386721] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  131.386742] wl 0000:02:00.0: setting latency timer to 64
labord@Jenovefa:~$ lsmod | grep wl
wl                   2642531  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
```

I don't know whether that is of any importance, but I noticed in my blacklist.conf the following line

```
# replaced by b43 and ssb.
blacklist bcm43xx
```

---

### Post by josephmills on 2011-05-18
please uninstall the b43fwcutter thanks anything?

---

### Post by labord on 2011-05-18
I uninstalled it (had to also remove firmware b43 installer with it). no change

---

### Post by josephmills on 2011-05-18
ok when I have wireless troubles I use googlubuntu.com then I put the model number and chili555 as he is a Jedi!  this is what I found it is on compiling the driver your-self, [http://ubuntuforums.org/showthread.php?t=1480671&page=2](http://ubuntuforums.org/showthread.php?t=1480671&page=2)

Please read the  post #19 and on I know that this will work

---

### Post by labord on 2011-05-18
ok, thanks for your help.

---

### Post by labord on 2011-05-19
So I managed to make my wireless work, though am not sure what was it in the end:

1) I disabled the sta driver in System > Administration > Additional Drivers

2) I installed gdebi 

```
sudo apt-get install gdebi
```

3) I downloaded an old version of the driver here [http://se.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://se.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)

4) Installed it
```
sudo gdebi bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb
```

5) unplugged the ethernet cable to go offline and activated the driver via Additional Drivers (if I had stayed online, the system would have downloaded the newer version from the net). And that's all.

I found this solution at one non-English ubuntu site. However, there are still some questions pending. First of all, every time I boot to ubuntu, I have to modprobe wl, adding a wl line to etc/modules does not help. I thought this had to be related to one of the blacklisted drivers, so I fiddled with the config files and here comes the mystery: ever since I tried to use ndiswrapper (didn't work: Network Manager could see the wireless networks, but failed to connect to any), there appeared a ndiswrapper.conf in my etc/modprobe.d directory. There are planty of lines there

```
alias pci:v000014E4d00000576sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004303sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004313sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004314sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004315sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004316sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d0000431Asv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004321sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004322sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004329sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d0000432Asv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d0000432Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d0000432Csv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004340sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004341sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004350sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004351sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004353sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004354sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004357sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004716sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004722sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004727sv0000051Asd000014E4bc*sc*i* ndiswrapper
alias pci:v000014E4d00004727sv00002047sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000014E4d00004727sv00002A47sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000014E4d00004727sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d0000A8D6sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d0000A8D8sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d0000A8DAsv*sd*bc*sc*i* ndiswrapper
```

so I thought this might be blocking something during the boot, so I commented out (#) all of them. After reboot, the Network Manager indeed did recognize a wireless driver (without modprobe wl), but did not see any networks (not even after I ran modprobe wl)! Go figure! (btw. ndiswrapper is completely removed from the system)

Now I have my wifi connection back, but have to load manually the wl module every time I turn on the computer. So there's a mystery for all the wifi jedis out there to help me solve. 

labord

---

### Post by josephmills on 2011-05-19
hi there again after looking it over and contacting some real smart people I think that I may have figured it. You said that ndiswrapper is completely un-installed right? and it was there When we where working on it last? That could be it right there but lets get back to you black list lets see a ```
cat /etc/modprobe.d/blacklist.conf
``` also could we see a ```
lsmod 
``` and a ```
dmesg 
``` I know there are big lists but lets see them thanks and I think that we will get this going 
Joseph

---

### Post by chili555 on 2011-05-19
You can make the reply quite a bit smaller by making a text file with all the data in it, zipping it up and attaching it to your reply using the little paperclip tool at the top of the reply box:```
cat /etc/modprobe.d/blacklist.conf > labord.txt
lsmod >> labord.txt
dmesg >> labord.txt
zip labord.zip labord.txt
```Then attach the file labord.zip to your reply.

---

### Post by labord on 2011-05-20
Thank you, Joseph, for getting back to me, thanks for the suggestion, chilli, I followed your instructions.

labord

---

### Post by labord on 2011-05-20
Oh, and Joseph, no, ndsiwrapper wasn't there, when we were working on it. I tried a windows driver before I started posting about this problem.

---

### Post by chili555 on 2011-05-20
> **labord said:**
> Oh, and Joseph, no, ndsiwrapper wasn't there, when we were working on it. I tried a windows driver before I started posting about this problem.Your modules listing, *lsmod*, begs to differ:> Module                  Size  Used by
michael_mic            12540  4 
arc4                   12473  2 
lib80211_crypt_tkip    17203  0 
[COLOR="Red"]wl                   1965717  0 
lib80211               14570  2 lib80211_crypt_tkip,wl[/COLOR]
parport_pc             32111  0 
ppdev                  12849  0 
--- snip ---
videodev               75143  1 uvcvideo
[COLOR="Red"]ndiswrapper           192828  0 [/COLOR]
snd                    55295  13
--- snip ---Your dmesg confirms that both are loading. I'd suggest you unload ndiswrapper temporarily and see if your wireless pperforms better:```
sudo rmmod -f ndiswrapper
```Joseph may have other suggestions, as well.

---

### Post by labord on 2011-05-20
> **chili555 said:**
> Your modules listing, *lsmod*, begs to differ:Your dmesg confirms that both are loading. I'd suggest you unload ndiswrapper temporarily and see if your wireless pperforms better:```
sudo rmmod -f ndiswrapper
```Joseph may have other suggestions, as well.

Well, that's strange, because synaptic says there is no ndiswrapper on my computer. If I unload ndiswrapper nothing really changes, which means that I have to modprobe the wl module to activate my wifi. Would it be possible to prevent ndiswrapper from loading during boot? Thanks for your help, really appreciated.

---

### Post by chili555 on 2011-05-20
Please check:```
ls /etc/ndiswrapper
```Is there anything in there? If so, please do:```
sudo rm -rf /etc/ndiswrapper/*
```Now, let's blacklist ndiswrapper and automatically load wl:```
sudo su
echo "blacklist ndiswrapper" >> /etc/modprobe.d/blacklist.conf
echo wl >> /etc/modules
exit
```Now, let's look for and delete any directives in /etc/modprobe.d:```
ls /etc/modprobe.d | grep ndis
```If you find anything, remove it:```
sudo rm /etc/modprobe.d/ndis*
```Reboot and tell us how you wireless is working.

---

### Post by labord on 2011-05-20
> **chili555 said:**
> Please check:```
ls /etc/ndiswrapper
```Is there anything in there? If so, please do:```
sudo rm -rf /etc/ndiswrapper/*
```Now, let's blacklist ndiswrapper and automatically load wl:```
sudo su
echo "blacklist ndiswrapper" >> /etc/modprobe.d/blacklist.conf
echo wl >> /etc/modules
exit
```Now, let's look for and delete any directives in /etc/modprobe.d:```
ls /etc/modprobe.d | grep ndis
```If you find anything, remove it:```
sudo rm /etc/modprobe.d/ndis*
```Reboot and tell us how you wireless is working.

Great! This worked! thanks a million, Chili! ndiswrapper was the villain of the piece, well, rather of the episode, as the initial problem with Broadcom BCM4313 [14e4:4727] not working after upgrade to 11.04 was solved in steps described in post #41. Anyway, ndiswrapper was preventing the old STA driver from loading, at least that's my interpretation of things. Case solved! thanks Chili, thanks Joseph!

---

### Post by chili555 on 2011-05-20
Would you please use Thread Tools at the top and Mark Solved? Thanks.

---

### Post by labord on 2011-05-20
I would love to, but I am not the original poster... how do I do this? thanks

---

### Post by chili555 on 2011-05-20
> I am not the original poster... how do I do this?Doh! You can't; sorry I didn't catch that.

---

### Post by josephmills on 2011-05-20
Glad to see you guys got it all worked out yeah :P

---

### Post by CDSRV on 2011-05-24
not solved..

BCM4311.. worked fine in 9, 10.04, 10.10.. nothing seems to work in 11.04

after reading this and many other posts, adding the driver normally thru the menu, adding/removing various related packages, etc, etc.. (ndis is/was not loaded), and finally attempting to compile the broadcom drivers, its ended up with this compile error and *both* the wired and wireless devices showing up as "UNCLAIMED" .. 

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/700176](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/700176)

this seems to be a bug..  

for now, I guess its back down to 10.10..

---

### Post by ultracarl on 2011-05-24
I have another question about the BCM4313. I think I've tried just about every suggestion I can find around the net, but nothing seems to work. I'm running Ubuntu 11.04 on a Samsung Q330 laptop.

When I try to activate the proprietary STA wireless driver, i get this message:

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

This is what's in the log file:

2011-05-25 03:28:38,408 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-05-25 03:28:38,444 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-05-25 03:31:12,338 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-05-25 03:31:12,384 DEBUG: nvidia_current is not the alternative in use
2011-05-25 03:31:13,448 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-05-25 03:31:13,493 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-05-25 03:31:13,536 DEBUG: nvidia_current is not the alternative in use

I'm pretty new to Ubuntu (and Linux), and this stuff makes no sense to me. I've tried this: [http://wireless.kernel.org/en/users/Drivers/brcm80211](http://wireless.kernel.org/en/users/Drivers/brcm80211)
but it really makes no sense to me, and it also seems that the four firmware files in question is already located in the /lib/firmware/brcm folder.

I also tried this: [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) but this too is a bit over my head, and i got stuck on the insmod wl.ko bit.

And also, I had it working in 10.10, even though that was a bit of a mess too! Any ideas? (other than giving up and going back to 10.10)

---

### Post by chili555 on 2011-05-24
I'm not sure you can get the Broadcom module* wl* going in Natty 11.04. Please read posts #21 to #23 here:  [http://ubuntuforums.org/showthread.php?t=1753072&page=3](http://ubuntuforums.org/showthread.php?t=1753072&page=3)

---

### Post by ultracarl on 2011-05-25
Cheers. If I understand this correctly, there's not much to do to get this card working in 11.04. Guess I'll just have to wait for the next release :(. On the bright side, 11.04 is working like a charm on my desktop computer! :D

---

### Post by chili555 on 2011-05-25
The symptom is that rfkill shows hard blocked no matter the state of your wireless switch.```
rfkill list all
```It ought to work quite well in 10.10 or 10.04LTS.

---

### Post by riso325 on 2011-06-02
hi guys...sorry for not responding to my thread for a long time.
So i was reading the thread an when i use command rfkill list all i get :

> administrator@Lenovo-B560:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

What does it mean when it is soft blocked ?...labord didnt have it blocked. I tried to install/reinstall the drivers. And when i try to force to run WLAN with FN+F5 the system freezes - need reboot manually

---

### Post by chili555 on 2011-06-02
> **riso325 said:**
> hi guys...sorry for not responding to my thread for a long time.
So i was reading the thread an when i use command rfkill list all i get :



What does it mean when it is soft blocked ?...labord didnt have it blocked. I tried to install/reinstall the drivers. And when i try to force to run WLAN with FN+F5 the system freezes - need reboot manuallySoft-blocked means that some piece of sotware is shutting the wireless down. I suspect the piece of software is either a laptop module or wmi module that is supposed to transfer key presses like Fn+F5 to a signal the kernel recognizes; something like, "riso wants to use the wireless, please turn on the wireless." Instead, it freezes up the computer. Our job is to find the offending module and either fix it or remove it. Please run and post:```
lsmod
```We'll take a look at it and see if we can fix it.

This is a common problem with the module wl in Natty 11.04.

---

### Post by riso325 on 2011-06-02
ok here it is :


> administrator@Lenovo-B560:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_realtek   255820  1 
wl                   2642531  0 
lib80211               14570  1 wl
arc4                   12473  2 
snd_hda_intel          24140  4 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
nouveau               626066  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  450979  8 
brcm80211             690428  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  1 brcm80211
uvcvideo               66851  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65184  1 nouveau
videodev               75143  1 uvcvideo
psmouse                59039  0 
cfg80211              156212  2 brcm80211,mac80211
serio_raw              12990  0 
joydev                 17322  0 
snd                    55295  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_ips              17769  0 
drm_kms_helper         40745  2 nouveau,i915
drm                   184133  6 nouveau,ttm,i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  2 nouveau,i915
ideapad_laptop         13262  0 
sparse_keymap          13666  1 ideapad_laptop
video                  18951  2 nouveau,i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
hid_logitech           17421  0 
ff_memless             12945  1 hid_logitech
usbhid                 41704  1 hid_logitech
hid                    77084  2 hid_logitech,usbhid
ahci                   21591  4 
libahci                25548  1 ahci
atl1c                  36237  0 

---

### Post by josephmills on 2011-06-02
hi there again could you do a ```
rfkill unblock all && rfkill unblock wifi 
``` then post a ```
rfkill list all 
``` thanks

---

### Post by chili555 on 2011-06-02
> snd_hda_codec_realtek 255820 1
[COLOR="Red"]wl[/COLOR] 2642531 0
lib80211 14570 1 wl
arc4 12473 2
---
i915 450979 8
[COLOR="Red"]brcm80211[/COLOR] 690428 0
snd_seq 51291 2 snd_seq_midi,snd_seq_midi_event
mac80211 257001 1 brcm80211@joseph--

Does he have a little conflict going?

---

### Post by josephmills on 2011-06-02
> **chili555 said:**
> @joseph--

Does he have a little conflict going?

are you saying that the brcm80211 is not the right mod for the job and that it is for a different driver? like the [http://linuxwireless.org/en/users/Drivers/brcm80211](http://linuxwireless.org/en/users/Drivers/brcm80211)
and that he does not need two driver packages but only the wl package? or the brcm ? also what is this ```
cfg80211 156212 2 brcm80211,mac80211
``` when I read this [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)  it says that it works with either one but it is just one that he needs time to take a pick ? thanks Chili555

---

### Post by riso325 on 2011-06-02
> **josephmills said:**
> hi there again could you do a ```
rfkill unblock all && rfkill unblock wifi 
``` then post a ```
rfkill list all 
``` thanks

joseph when i tried 
```
rfkill unblock all && rfkill unblock wifi 
```
it caused system freeze
------------------------------------
```
rfkill list all 
```

administrator@Lenovo-B560:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

---

### Post by riso325 on 2011-06-02
i dont have b43 drivers installed because the dont support 14e4:4727 as you can see on b43 site...i have only the newest STA drivers

synaptic:
[http://i54.tinypic.com/28bci15.png]("http://i54.tinypic.com/28bci15.png")

---

### Post by chili555 on 2011-06-02
> **josephmills said:**
> are you saying that the brcm80211 is not the right mod for the job and that it is for a different driver? like the [http://linuxwireless.org/en/users/Drivers/brcm80211](http://linuxwireless.org/en/users/Drivers/brcm80211)
and that he does not need two driver packages but only the wl package? or the brcm ? also what is this ```
cfg80211 156212 2 brcm80211,mac80211
``` when I read this [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)  it says that it works with either one but it is just one that he needs time to take a pick ? thanks Chili555I think wl and brcm80211 are two different drivers that *MAY* conflict. I think one of them will drive his device and the other will not. I'm no expert on Broadcom or hardly anything else for that matter, but I'd remove first one and then the other and figure out which one is golden. I don't know for sure; I learn a ton every day.

These are dependencies of wl and brcm80211. See modinfo.```
$ modinfo brcm80211
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/staging/brcm80211/brcm80211.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     0039D58F094F7B0F75BAA6B
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
[COLOR="Red"]depends:        mac80211,cfg80211[/COLOR]
staging:        Y
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           msglevel:int
parm:           phymsglevel:int

```At this point, I have doubts that wl will work ***at all*** with Natty 11.04.

---

### Post by josephmills on 2011-06-02
> **chili555 said:**
> I think wl and brcm80211 are two different drivers that *MAY* conflict. I think one of them will drive his device and the other will not. I'm no expert on Broadcom or hardly anything else for that matter, but I'd remove first one and then the other and figure out which one is golden. I don't know for sure; I learn a ton every day.

These are dependencies of wl and brcm80211. See modinfo.```
$ modinfo brcm80211
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/staging/brcm80211/brcm80211.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     0039D58F094F7B0F75BAA6B
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
[COLOR="Red"]depends:        mac80211,cfg80211[/COLOR]
staging:        Y
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           msglevel:int
parm:           phymsglevel:int

```At this point, I have doubts that wl will work ***at all*** with Natty 11.04.

so then blacklist the wl mods and he should be good to go?

---

### Post by chili555 on 2011-06-02
> **josephmills said:**
> so then blacklist the wl mods and he should be good to go?Well, that's the thing; we don't yet know. I'd start with blacklisting wl first. If that doesn't do it, change the blacklist to brcm80211 and let wl load. One of them will cause young Mr. riso to cry, "Eureka!" and we will have learned a few things today.

I hope we don't have to remove brcmwl-kernel-source altogether.

---

### Post by riso325 on 2011-06-02
So i have to blacklist something ?.. im a newbie in linux and i dont know how to do that :P

---

### Post by josephmills on 2011-06-02
```
 sudo gedit /etc/modprobe.d/blacklist.conf
``` then add 
blacklist wl then save and reboot anything?

---

### Post by riso325 on 2011-06-02
the same....after FN+f5 -> freeze

---

### Post by josephmills on 2011-06-02
> **riso325 said:**
> the same....after FN+f5 -> freeze

what is fn+f5 your hot key ? could we now see a ```
lsmod
``` thanks

---

### Post by riso325 on 2011-06-02
it is a hotkey which is used to turn on wifi...i use it in windows and i used it in 10.10

lsmod:


> Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
nouveau               626066  0 
snd_timer              28659  2 snd_pcm,snd_seq
i915                  450979  8 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
brcm80211             690428  0 
ttm                    65184  1 nouveau
mac80211              257001  1 brcm80211
ideapad_laptop         13262  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sparse_keymap          13666  1 ideapad_laptop
drm_kms_helper         40745  2 nouveau,i915
uvcvideo               66851  0 
psmouse                59039  0 
videodev               75143  1 uvcvideo
joydev                 17322  0 
drm                   184133  6 nouveau,ttm,i915,drm_kms_helper
serio_raw              12990  0 
cfg80211              156212  2 brcm80211,mac80211
intel_ips              17769  0 
i2c_algo_bit           13184  2 nouveau,i915
video                  18951  2 nouveau,i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
hid_logitech           17421  0 
ff_memless             12945  1 hid_logitech
usbhid                 41704  1 hid_logitech
hid                    77084  2 hid_logitech,usbhid
ahci                   21591  4 
libahci                25548  1 ahci
atl1c                  36237  0 

---

### Post by josephmills on 2011-06-02
```
sudo apt-get remove --purge bcmwl-kernel-source && sudo reboot 
``` then after reboot ```
sudo apt-get install bcmwl-kernel-source 
``` anything ?

---

### Post by riso325 on 2011-06-02
well :D..now after isntalling i tried it to activate in the proprietary drivers and i get /var/log/jockey.log error

---

### Post by josephmills on 2011-06-02
> **riso325 said:**
> well :D..now after isntalling i tried it to activate in the proprietary drivers and i get /var/log/jockey.log error

```
sudo lshw -C network 
``` and a ```
rfkill list all 
``` thanks

---

### Post by riso325 on 2011-06-02
> *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: f0:de:f1:3b:63:49
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.103 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f2400000-f243ffff ioport:3000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: ac:81:12:3c:af:2e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcm80211 driverversion=2.6.38-8-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f2500000-f2503fff


rfkill list all


> 0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

i thank you for helping me :)

---

### Post by josephmills on 2011-06-02
```
rfkill unblock all 
```

---

### Post by riso325 on 2011-06-02
after enabling wifi in the network manager in the tray and hitting fn+f5 -> freeze

---

### Post by riso325 on 2011-06-02
and after hard restart (or how to call it in english) i dont have a wifi enable option in network manager

---

### Post by josephmills on 2011-06-02
> **riso325 said:**
> and after hard restart (or how to call it in english) i dont have a wifi enable option in network manager

rfkill list all

---

### Post by riso325 on 2011-06-02
well were heading somewhere :D ..weve got a change:


> 0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

---

### Post by josephmills on 2011-06-02
> **riso325 said:**
> well were heading somewhere :D ..weve got a change:

```
rfkill unblock bluetooth
``` and ```
iwlist scan 
```

---

### Post by riso325 on 2011-06-02
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

...well done!..now how to turn it on..

---

### Post by josephmills on 2011-06-02
> **riso325 said:**
> 0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

...well done!..now how to turn it on..

```
iwlist scan 
```

---

### Post by riso325 on 2011-06-02
iwlist scan
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by josephmills on 2011-06-02
is enable wireless still greyed out ?

---

### Post by riso325 on 2011-06-02
it is not even there..i will try to restart...

---

### Post by riso325 on 2011-06-02
> **riso325 said:**
> it is not even there..i will try to restart...

after restarting nothing changed...not even a grey option...just enable/disable wired network

---

### Post by josephmills on 2011-06-02
now take the wl out of the blacklist file the same way you put it in

---

### Post by riso325 on 2011-06-02
> **josephmills said:**
> now take the wl out of the blacklist file the same way you put it in

now there is a grey option...

---

### Post by josephmills on 2011-06-02
after you take the wl out blacklist the brcm80211 then open your terminal and type in ```
sudo apt-get remove --purge bcmwl-kernel-source && sudo reboot 
``` after rebooting do a ```
sudo apt-get install broadcom-sta-source && sudo apt-get install broadcom-sta-common && sudo apt-get install bcmwl-kernel-source && sudo reboot 

``` anything ?

---

### Post by riso325 on 2011-06-02
the option is still grey :(

---

### Post by riso325 on 2011-06-02
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by josephmills on 2011-06-02
> **riso325 said:**
> 0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

hit the wifi switch and then do a ```
rfkill unblock bluetooth 
``` then show us ```
rfkill list all 
``` also did you get any errors when doing post # 93 ? thanks

---

### Post by riso325 on 2011-06-02
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by riso325 on 2011-06-02
> **riso325 said:**
> 0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
after hitting the buttons fn+f5 it changes yes to no, no to yes

0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

---

### Post by josephmills on 2011-06-02
what kind of computer is this ? we want it to say all no with rfkill list all so we want it to look like this ```
0: ideapad_wlan: Wireless LAN
Soft blocked: no
Hard blocked: no
1: ideapad_bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
2: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: no
```

---

### Post by riso325 on 2011-06-02
Lenovo IdeaPad B560 i3-380
59070771

---

### Post by riso325 on 2011-06-02
but this is not just a ubuntu problem..i had it in fedora too...is it something with kernel ?

---

### Post by josephmills on 2011-06-02
woot woot  over 100 posts did you get it to all say no first get the hard blocks to say no then do the```
 rfkill unblock all 
```and ```
rfkill unblock bluetooth 
``` then we will go from there

---

### Post by riso325 on 2011-06-03
> **josephmills said:**
> woot woot  over 100 posts did you get it to all say no first get the hard blocks to say no then do the```
 rfkill unblock all 
```and ```
rfkill unblock bluetooth 
``` then we will go from there

this is the best i can get from it:


```
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

---

### Post by chili555 on 2011-06-03
Please do:```
sudo su
echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
echo b43 >> etc/modules
exit
```Now reboot and tell us if the wireless is working. If not, please run and post:```
dmesg | grep b43
```Thanks.

---

### Post by riso325 on 2011-06-03
echo b43 >> etc/modules

bash: etc/modules: directory or file does not exist

should i create that directory ?

---

### Post by chili555 on 2011-06-03
I made a mistake, sorry. It's actually:```
sudo su
echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
echo b43 >> [COLOR="Red"]**/**[/COLOR]etc/modules
exit
```Sorry about that.

---

### Post by riso325 on 2011-06-03
nothing happened, and there is not even greyed out wifi option in network manager...when i type dmesg | grep b43 i get nothing..no error message..no list...just blank

---

### Post by riso325 on 2011-06-03
> **riso325 said:**
> nothing happened, and there is not even greyed out wifi option in network manager...when i type dmesg | grep b43 i get nothing..no error message..no list...just blank

rfkill list
```
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

---

### Post by josephmills on 2011-06-03
Man I keep on hearing about this open source drivers it sucks. I just got the wl to work in natty. mods loaded easy but the firmware was a pain and a half ;) **edit** ok so I guess that they don't suck but I could not get it to work for the life of me. also it was not a 4727 but a 4329 that a friend had lying around.

---

### Post by riso325 on 2011-06-03
4727 is not supported by b43 drivers...that is what i know :D

---

### Post by josephmills on 2011-06-03
> **riso325 said:**
> 4727 is not supported by b43 drivers...that is what i know :D

take the wl out of the blacklist file and put the brcm80211 in then reboot after reboot try unload anythinbg that could get in the way ```
# modprobe -r b44 b43 b43legacy ssb brcm80211
``` then uninstall the bcmwl-kernel-source ```
sudo apt-get remove --purge bcmwl-kernel-source
``` then install the b43sta driver (wl) ```
sudo sudo apt-get install broadcom-sta-common && sudo apt-get install broadcom-sta-source && sudo apt-get install firmware-b43-installer && sudo reboot 
 
``` load the wl ```
modprobe wl
``` you should have wireless now
or you could try the unstable stuff here 
[http://ubuntuforums.org/showthread.php?t=1617380](http://ubuntuforums.org/showthread.php?t=1617380)

---

### Post by riso325 on 2011-06-03
modprobe wl
FATAL: Module wl not found.
FATAL: Error running install command for wl

---

### Post by josephmills on 2011-06-03
> **riso325 said:**
> modprobe wl
FATAL: Module wl not found.
FATAL: Error running install command for wl

did you take it out of the blacklist file?

---

### Post by riso325 on 2011-06-03
> **josephmills said:**
> did you take it out of the blacklist file?

yeah....ive got these things blacklisted just:

blacklist brcm80211
blacklist bcm43xx

---

### Post by josephmills on 2011-06-03
sudo sudo apt-get install broadcom-sta-common && sudo apt-get install broadcom-sta-source && sudo apt-get install firmware-b43-installer

---

### Post by riso325 on 2011-06-06
OK GUYS YOU WILL NOT BELIEVE THIS : I JUST PLUGED-IN BATTERY AND WIFI WORKS...can somebody explain why ? :D

---

