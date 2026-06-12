---
title: "Realtek 8188CE &quot;wireless is disabled&quot; error, &quot;soft blocked?&quot;"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by erans on 2011-05-28
Hi there, 

I have a Thinkpad E420 with a Realtek 8188ce. I'm having a lot of problems getting the wireless to work. After bumbling with drivers (and installing the correct ones from Realtek), my wireless still won't work. I think it might be because of this: 
```
shayan@shayan-ThinkPad-E420:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
shayan@shayan-ThinkPad-E420:~$ 
```
I have a button on my keyboard that is supposed to toggle WiFi, but it doesn't seem to do anything. Any ideas? This is driving me CRAZY..

Here is my lspci and lsmod: ```
shayan@shayan-ThinkPad-E420:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
shayan@shayan-ThinkPad-E420:~$ 
```
```
shayan@shayan-ThinkPad-E420:~$ lsmod
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_conexant    57511  1 
binfmt_misc            17565  1 
joydev                 17606  0 
thinkpad_acpi          81587  0 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
i915                  514985  3 
uvcvideo               72195  0 
acer_wmi               23771  0 
sparse_keymap          13898  1 acer_wmi
rtl8192ce             141660  0 
videodev               82052  1 uvcvideo
snd_rawmidi            30486  1 snd_seq_midi
rtlwifi               117393  1 rtl8192ce
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              294370  2 rtl8192ce,rtlwifi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         42136  1 i915
v4l2_compat_ioctl32    17078  1 videodev
psmouse                73535  0 
drm                   227495  4 i915,drm_kms_helper
cfg80211              178528  2 rtlwifi,mac80211
soundcore              12680  1 snd
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  1 i915
nvram                  14419  1 thinkpad_acpi
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
libahci                26642  1 ahci
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
r8169                  48022  0 
shayan@shayan-ThinkPad-E420:~$ 

```

---

### Post by erans on 2011-05-29
Bump

---

### Post by chili555 on 2011-05-29
Let's see the result of these commands:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
rfkill list all
```Who da thunk a Lenovo would actually be an Acer?

If it works, we can tweak a couple of files and make it Acer-proof.

---

### Post by erans on 2011-05-29
I'll try that now. Is it possible to get this thread merged with the one I just created? Link is here: [http://ubuntuforums.org/showthread.php?t=1770914](http://ubuntuforums.org/showthread.php?t=1770914)

Here's the result of those commands: 

```
shayan@shayan-ThinkPad-E420:~$ sudo rmmod -f acer-wmi
[sudo] password for shayan: 
shayan@shayan-ThinkPad-E420:~$ sudo rmmod -f acer-wmi
ERROR: Removing 'acer_wmi': No such file or directory
shayan@shayan-ThinkPad-E420:~$ sudo rfkill unblock all
shayan@shayan-ThinkPad-E420:~$ rfkill list all
shayan@shayan-ThinkPad-E420:~$ 

```

---

### Post by erans on 2011-05-29
WOW, that worked!! How do I make this permanent? You are the man.

---

### Post by chili555 on 2011-05-29
> **erans said:**
> WOW, that worked!! How do I make this permanent? You are the man.Please do:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
gedit /etc/rc.local
```Add one line above exit 0```
rfkill unblock all
```Proofread, save and close gedit.```
exit
```Enjoy your new Thinkpad!

---

### Post by erans on 2011-05-29
Thanks so much. What a weird problem... wonder why that acer thing is there in the first place. Anyway, everything seems to be working great now. I'll link the other thread to this one. 

Thanks again! Hope this helps someone else.

---

### Post by mikec007 on 2011-05-30
Thanks for this chili555.

I had this same problem on my Acer Aspire One and you fix works well.  I used to run Linux Mint 10.04 and never had this problem.  Then I tied the 11.04 version of Ubuntu and Mint and had this wifi issue.  Glad that I got if fixed though so I can run Ubuntu 11.04 now on my machine.

On a site note, this is my first day totally windows free.  I was backing up files to a usb hard drive yesterday, explorer crashed(nothing else was running on the computer but explorer), corrupted the usb drive.  The next time that computer booted up it saw a ubuntu live cd.

---

### Post by erans on 2011-05-30
Uh oh. I'm now getting a kernel panic when I start my computer. I did another clean install of Ubuntu and only made the changes in this thread (new Realtek driver, blacklisted acer_wmi), and I still got it. Any ideas? It happens when I enable my wireless after boot, to be precise.

---

### Post by erans on 2011-05-30
This is what it says when I try to enable wireless: 

Kernel panic - not synching: Fatal exception in interrupt
Pid: 1509, comm: applet.py Tainted: G    D W 2.6.38-8generic #42-Ubuntu
Call Trace: 
panic occurred, switching back to text console

EDIT: I uninstalled my wireless drivers, undid the changes to the conf files that had the acer blacklist, and now my system freezes when I try to do the "sudo rfkill unblock all" command. Not sure what I did wrong here.

---

### Post by chili555 on 2011-05-30
> now my system freezes when I try to do the "sudo rfkill unblock all" command. Not sure what I did wrong here.I'm not sure either. Can you reproduce it in the live CD? Please open a terminal and do:```
sudo tail -f /var/log/syslog
```Leave the terminal open printing messages as you open a second terminal and do: ```
sudo rfkill unblock all
```What are the messages leading up to the freeze in the first terminal?> Kernel panic - not synching: Fatal exception in interrupt
Pid: 1509, comm: applet.py Tainted: G D W 2.6.38-8generic #42-Ubuntu
Call Trace:
panic occurred, switching back to text consoleWe'd need to examine the messages preceding this to see if there are further clues.

Did the compile for the wireless driver go well? Few warnings? Did you have to add your usb.id to any file before you compiled?

---

### Post by erans on 2011-05-30
> **chili555 said:**
> I'm not sure either. Can you reproduce it in the live CD? Please open a terminal and do:```
sudo tail -f /var/log/syslog
```Leave the terminal open printing messages as you open a second terminal and do: ```
sudo rfkill unblock all
```What are the messages leading up to the freeze in the first terminal?We'd need to examine the messages preceding this to see if there are further clues.

Did the compile for the wireless driver go well? Few warnings? Did you have to add your usb.id to any file before you compiled?
Well, I formatted and started over again, and the problem seems to begin when I install the new driver from the Realtek website. I formatted and just did the commands to remove and blacklist the acer module, and now I can connect to a wireless network and reboot without problems.

However, the default driver for the card is quite bad. It's slow and frequently disconnects, so I believe the problem is with the Realtek driver. I did receive some errors when compiling the driver, though I didn't install it this time. Also, I searched a bit and found someone with the same problem in another thread: [http://ubuntuforums.org/showthread.php?p=10806805](http://ubuntuforums.org/showthread.php?p=10806805)

The last post in that thread suggests that I might not be installing the right driver, but then I'm not sure which to install, especially if CE is for embedded cards. 

I'll post what happens when I compile the driver in a second.

Also, this is how I previously installed the driver. Not sure if this is the best, but it was what was in the readme: ```
sudo su
make
make install
reboot
```

---

### Post by erans on 2011-05-30
Compile for the driver with errors: 
```
shayan@shayan-ThinkPad-E420:~/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011$ make
make -C /lib/modules/2.6.38-8-generic/build M=/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/base.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rc.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/debug.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/regd.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/efuse.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/cam.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/ps.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/core.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/pci.o
  LD [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtlwifi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtlwifi.mod.o
  LD [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtlwifi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Entering directory `/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce'
make -C /lib/modules/2.6.38-8-generic/build M=/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/hw.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/table.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/sw.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/trx.o
/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/trx.c: In function ‘rtl92ce_rx_query_desc’:
/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/trx.c:593:24: warning: ‘sta’ may be used uninitialized in this function
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/led.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/fw.o
/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/fw.c: In function ‘rtl92c_download_fw’:
/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/fw.c:240:3: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long unsigned int’
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/phy.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/rf.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/dm.o
  LD [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/rtl8192ce.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/rtl8192ce.mod.o
  LD [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce/rtl8192ce.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Leaving directory `/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192ce'
make[1]: Entering directory `/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se'
make -C /lib/modules/2.6.38-8-generic/build M=/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/hw.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/table.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/sw.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/trx.o
/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/trx.c: In function ‘rtl92se_rx_query_desc’:
/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/trx.c:562:24: warning: ‘sta’ may be used uninitialized in this function
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/led.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/fw.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/phy.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/rf.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/dm.o
  LD [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/rtl8192se.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se/rtl8192se.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Leaving directory `/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192se'
make[1]: Entering directory `/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de'
make -C /lib/modules/2.6.38-8-generic/build M=/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/hw.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/table.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/sw.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/trx.o
/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/trx.c: In function ‘rtl92de_rx_query_desc’:
/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/trx.c:521:24: warning: ‘sta’ may be used uninitialized in this function
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/led.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/fw.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/phy.o
/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/phy.c: In function ‘rtl92d_phy_reset_iqk_result’:
/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/phy.c:3002:2: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/rf.o
  CC [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/dm.o
  LD [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/rtl8192de.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/rtl8192de.mod.o
  LD [M]  /home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de/rtl8192de.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Leaving directory `/home/shayan/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011/rtl8192de'
shayan@shayan-ThinkPad-E420:~/Downloads/rtl_92ce_92se_92de_linux_mac80211_0003.0401.2011$ 
```

---

### Post by pythonscript on 2011-05-30
I've been having similar problems with my Realtek wireless, also on a Thinkpad with Ubuntu 11.04 ([http://ubuntuforums.org/showthread.php?t=1771442](http://ubuntuforums.org/showthread.php?t=1771442)). From what I've read kernel v2.6.38 has issues with the Realtek hardware, regardless of what distro you're using.

---

### Post by erans on 2011-05-30
> **pythonscript said:**
> I've been having similar problems with my Realtek wireless, also on a Thinkpad with Ubuntu 11.04 ([http://ubuntuforums.org/showthread.php?t=1771442](http://ubuntuforums.org/showthread.php?t=1771442)). From what I've read kernel v2.6.38 has issues with the Realtek hardware, regardless of what distro you're using.
Oof. If that's true, where does that leave us?

---

### Post by pythonscript on 2011-05-30
A rolling release distro like Arch in the hope that a newer kernel will fix the problem? Or, an external wireless device (like a USB adapter). Despite how much I'll loathe using a USB wireless key with my laptop, if it's necessary then that's what I'll do. Any other suggestions?

---

### Post by chili555 on 2011-05-30
> The last post in that thread suggests that I might not be installing the right driver,Let's start there. Using the live CD and before you do anything else, run and post:```
lspci -nn
```Post the line that relates to your Realtek wireless card. We'll go from there.> Compile for the driver with errors: There were no errors; warnings, but not errors.

---

### Post by erans on 2011-05-30
Here's the line:
```
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
```

---

### Post by chili555 on 2011-05-30
> **erans said:**
> Here's the line:
```
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
```You posted lspci. I need:```
lspci [COLOR="Red"]-nn[/COLOR]
```Thanks.

---

### Post by erans on 2011-05-30
> **chili555 said:**
> You posted lspci. I need:```
lspci [COLOR="Red"]-nn[/COLOR]
```Thanks.

Sorry, here you go: ```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
03:00.0 System peripheral [0880]: Ricoh Co Ltd Device [1180:e823] (rev 04)
08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
```

---

### Post by pythonscript on 2011-05-30
Just for the record, erans, you have an identical wireless chip to mine. Hopefully I'm wrong and this isn't a wider problem so it can be fixed in short order.

---

### Post by chili555 on 2011-05-30
I believe you have built and installed the correct driver for your device:```
$ modinfo rtl8192ce | grep 8176
alias:          pci:v0000[COLOR="Red"]10EC[/COLOR]d0000[COLOR="Red"]8176[/COLOR]sv*sd*bc*sc*i*
```In post #5, it worked. Maybe we need to let acer-wmi load and initialize and remove it later. As a temporary experiment, please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Change the line we added with a pound sign:```
**[COLOR="Red"]#[/COLOR]**blacklist acer-wmi
```Proofread, save and close gedit. Now reboot and do:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```Does it work now? Maybe we can write a creative rc.local to do the same.

---

### Post by erans on 2011-05-30
Okay, so I did that and I can still connect to wireless. 

I should point out that I am currently not using the Realtek drivers from RT's website, but the drivers that came installed with Ubuntu since I had to format this morning. The only thing I need to do in order to connect to wireless is to disable the acer-wmi module. If I do that, I can reboot freely and connect to wireless. 

The connection with the default drivers is very poor, though. It frequently disconnects, pings very high, and does not reach max download speed. If I install the Realtek drivers, I can connect to the internet, but then I will not be able to reboot at all.

So I am wondering now if it is possible to install the Realtek drivers from the website without locking up my system and forcing a format.

EDIT: The compile log from a couple posts earlier was just me compiling the driver and posting the results in case there was a mistake there. I'm afraid to actually install those drivers because of the system lockup or whatever. I see now you were probably asking me to try removing the auto blacklist with the new drivers, right? I'll give it a shot now.

Pythonscript, are you having the same kind of problem?

---

### Post by erans on 2011-05-30
> **chili555 said:**
> I believe you have built and installed the correct driver for your device:```
$ modinfo rtl8192ce | grep 8176
alias:          pci:v0000[COLOR="Red"]10EC[/COLOR]d0000[COLOR="Red"]8176[/COLOR]sv*sd*bc*sc*i*
```In post #5, it worked. Maybe we need to let acer-wmi load and initialize and remove it later. As a temporary experiment, please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Change the line we added with a pound sign:```
**[COLOR="Red"]#[/COLOR]**blacklist acer-wmi
```Proofread, save and close gedit. Now reboot and do:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```Does it work now? Maybe we can write a creative rc.local to do the same.

Okay, I did all of this with the Realtek drivers installed. 

If I do this, I can boot into Ubuntu with no wireless. As soon as I do "sudo rmmod -f acer-wmi" my system totally locks up and I have to force power down.

---

### Post by pythonscript on 2011-05-30
Here's the problems I've been having, in sequence. 

1. After a default install of Ubuntu, the wireless module appears to work in that I can connect to my router and browse the internet. However, it's *incredibly* slow, most of the connections fail to resolve, and in general, it makes my wireless connection unusable. I wasn't having this problem with the other four laptops in my apartment, all of which are also connecting through a wireless link. 

2. To fix this, I installed the latest driver from the Realtek website. That broke the system completely and it wouldn't even boot. That was fixed through chrooting into the system with a live CD and uninstalling the Realtek driver. 

3. Now that the driver is uninstalled, the system will boot just fine, but as far as I can tell (from lspci -k) no wireless driver is even loaded, and I don't know which one to load to fix it. rtl8192ce isn't present on my system. 

That's where I am so far. I didn't have any of the problems with the acer_wmi module or anything like that. I don't even want my internet back to how it was after a fresh install, because even in that state, it was *virtually *unusable.

---

### Post by erans on 2011-05-30
Another interesting thing. If I uninstall the drivers, reboot, and then rmmod -f acer-wmi, my system does not lock up. It will only lock up if I try to rmmod with these drivers from Realtek installed.

---

### Post by chili555 on 2011-05-30
> I should point out that I am currently not using the Realtek drivers from RT's website, but ***the drivers that came installed with Ubuntu*** since I had to format this morning. Which are they? Maybe we can tweak, coax or fix them.

I am booted into 10.10 at the moment.

---

### Post by erans on 2011-05-30
Unfortunately, I installed the new drivers from Realtek since posting that, so now I don't have them running anymore. :( Unless there is a way to restore them... 

I found this thread, too. Not sure if it is useful: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775414](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775414)

---

### Post by erans on 2011-05-30
Also, this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/771758](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/771758)

---

### Post by chili555 on 2011-05-30
Here is the stock rtl8192ce:```
$ modinfo  rtl8192ce
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     7416041392B86CCB7B54065
alias:          pci:v000010ECd0000[COLOR="Red"][/COLOR]sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           swenc:using hardware crypto (default 0 [hardware])
```Can you run the live CD and try:```
sudo rmmod -f rtl8192ce
sudo modprobe rtl8192ce swenc=1
```The acer-wmi bug is well known on this forum. In most cases, it can be unloaded and everything works perfectly well. Yours is the first case I've seen where it was blacklisted to keep it from loading on boot and it locked up the machine.> Unless there is a way to restore them...There is; let's see if we can get the stock driver working first.

@pythoncript--
Will you try the fix I suggested and give us your report? Do you have an Acer?

---

### Post by erans on 2011-05-30
Okay. I booted from the live CD and ran those commands. Now I've rebooted without the live CD.

---

### Post by chili555 on 2011-05-30
> **erans said:**
> Okay. I booted from the live CD and ran those commands. Now I've rebooted without the live CD.Well, I was hoping while you were booted into the live CD and rtl8192ce was loaded with a possibly helpful parameter, namely swenc=1, you might try surfing the web and telling us if speed and reliability improved. Please redo.

While you are in the live CD mode, see if any other conflicting Realtek modules are loaded. Please in live mode, post:```
lsmod
```

---

### Post by pythonscript on 2011-05-30
Chili, are you wanting me to try the fix with these commands, running from a live CD, or just from my normal installation since I can boot mine just fine (except that I'm missing wireless)?

```

sudo rmmod -f rtl8192ce
sudo modprobe rtl8192ce swenc=1

```

No, I don't have an acer, either; I'm using a Lenovo Thinkpad SL510.

---

### Post by chili555 on 2011-05-30
> **pythonscript said:**
> Chili, are you wanting me to try the fix with these commands, running from a live CD, or just from my normal installation since I can boot mine just fine (except that I'm missing wireless)?

```

sudo rmmod -f rtl8192ce
sudo modprobe rtl8192ce swenc=1

```

No, I don't have an acer, either; I'm using a Lenovo Thinkpad SL510.I am wanting to see the result in a live CD. Are you missing wireless because acer-wmi is loaded? I've seen it in Lenovos before.```
lsmod | grep acer.
```If so, do:```
sudo rmmod -f acer-wmi
sudo rmmod -f rtl8192ce
sudo modprobe rtl8192ce swenc=1
```Does your wireless work well?

---

### Post by pythonscript on 2011-05-30
```
lsmod | grep acer
```returns nothing. I ran
```
sudo rmmod -f rtl8192ce
sudo modprobe rtl8192ce swenc=1

```as well, and after the first command, the wireless disconnects, and after the second command, it picks right back up again. The wireless internet appears to be working fine now (in the live CD) but as I've posted in another thread (this one: [http://ubuntuforums.org/showthread.php?t=1769743](http://ubuntuforums.org/showthread.php?t=1769743)) after a *fresh install* of 11.04, the internet is simply unusable. It was only getting worse, which is why I decided to install the new driver from the Realtek website, which brought me to a whole other set of problems, also documented in a different thread. 

I tried to load the rtl8192ce driver the last time I booted into my actual Ubuntu system, and it said "driver not found" or something to that effect; does this mean the driver is missing, and if so, is there a way for me to copy it from the live CD to somewhere on the harddrive where I can access it after I boot back in?

Thanks for all the help.

EDIT: Also, I've run lsmod | grep acer in my actual Ubuntu system before, and nothing has come up. I don't think I've ever had a problem with the acer module loading, as far as I know. This is the thread documenting the problem when I installed the driver from the Realtek website: [http://ubuntuforums.org/showthread.php?t=1771442](http://ubuntuforums.org/showthread.php?t=1771442).

---

### Post by erans on 2011-05-30
I went back into the live cd and did ```
sudo rmmod -f rtl8192ce sudo modprobe rtl8192ce swenc =1
```
Wireless still didn't work, so I tried ```
sudo rmmod -f acer_wmi
```
and wireless still does not work. 

Here is my lsmod. Looks like there are two rtl modules (rtlwifi and the previous one).```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
rtl8192ce             123008  0 
parport_pc             36959  0 
ppdev                  17113  0 
lp                     17825  0 
dm_crypt               22993  0 
parport                46458  3 parport_pc,ppdev,lp
binfmt_misc            17565  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_conexant    57511  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
thinkpad_acpi          81587  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12529  2 
joydev                 17606  0 
uvcvideo               72195  0 
rtlwifi                85089  1 rtl8192ce
snd                    67382  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               82052  1 uvcvideo
mac80211              294370  2 rtl8192ce,rtlwifi
psmouse                73535  0 
nvram                  14419  1 thinkpad_acpi
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              178528  2 rtlwifi,mac80211
v4l2_compat_ioctl32    17078  1 videodev
serio_raw              13166  0 
sparse_keymap          13898  0 
squashfs               36692  1 
aufs                  181143  4059 
nls_utf8               12557  1 
isofs                  40283  1 
dm_raid45              77827  0 
xor                    12890  1 dm_raid45
btrfs                 550402  0 
zlib_deflate           27074  1 btrfs
libcrc32c              12644  1 btrfs
i915                  514985  3 
ahci                   25951  2 
drm_kms_helper         42136  1 i915
libahci                26642  1 ahci
drm                   227495  4 i915,drm_kms_helper
r8169                  48022  0 
sdhci_pci              13989  0 
i2c_algo_bit           13400  1 i915
sdhci                  27387  1 sdhci_pci
video                  19438  1 i915
ubuntu@ubuntu:~$ 

```

---

### Post by chili555 on 2011-05-30
> I tried to load the rtl8192ce driver the last time I booted into my actual Ubuntu system, and it said "driver not found" or something to that effectIs your actual Ubuntu system running Natty? If you removed the downloaded Realtek driver correctly, with sudo make uninstall, the underlying stock driver should remain. If not and you have a wired ethernet connection you can do:```
sudo apt-get install --reinstall linux-image-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

Then try:```
sudo rmmod -f rtl8192ce
sudo modprobe rtl8192ce swenc =1
```Any errors? Any improvement?

---

### Post by pythonscript on 2011-05-30
When I run:
```
sudo modprobe rtl8192ce swenc=1
```

or ```
sudo modprobe rtlwifi
```

within my actual Ubuntu system, I get the error message saying:
```
FATAL: Module <name> not found. 
```

---

### Post by chili555 on 2011-05-30
> I went back into the live cd and did
```
sudo rmmod -f rtl8192ce sudo modprobe rtl8192ce swenc =1

```
?? I hope you did two separate commands:```
sudo rmmod -f rtl8192ce 
sudo modprobe rtl8192ce swenc =1
```Yes?

Your lsmod looks perfect. rtlwifi is a dependenciy of rtl8192ce.```
$ modinfo rtl8192ce
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     7416041392B86CCB7B54065
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
[COLOR="Red"]depends:        rtlwifi,mac80211[/COLOR]
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)

```

---

### Post by erans on 2011-05-30
> **chili555 said:**
> ?? I hope you did two separate commands:```
sudo rmmod -f rtl8192ce 
sudo modprobe rtl8192ce swenc =1
```Yes?

Your lsmod looks perfect. rtlwifi is a dependenciy of rtl8192ce.```
$ modinfo rtl8192ce
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     7416041392B86CCB7B54065
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
[COLOR="Red"]depends:        rtlwifi,mac80211[/COLOR]
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)

```
Yes, I did two separate commands. Apologies, didn't proofread before I posted. Wireless still not working on live... hm.

---

### Post by chili555 on 2011-05-30
> **pythonscript said:**
> When I run:
```
sudo modprobe rtl8192ce swenc=1
```

or ```
sudo modprobe rtlwifi
```

within my actual Ubuntu system, I get the error message saying:
```
FATAL: Module <name> not found. 
```If you have a wired ethernet connection you can do:
```
sudo apt-get install --reinstall linux-image-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

---

### Post by pythonscript on 2011-05-30
Chili, I reinstalled the kernel, rebooted, and ran the two commands from before. The module loaded fine, but now, I just see "disconnected" under Wireless Networks. I tried "sudo ifup wlan0" and redid the two commands again, but the wireless still says disconnected.

```

binfmt_misc            17565  1 
vboxnetadp             13382  0 
vboxnetflt             28297  0 
vboxdrv               268268  2 vboxnetadp,vboxnetflt
parport_pc             36959  0 
ppdev                  17113  0 
joydev                 17606  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
arc4                   12529  2 
rtl8192ce             123008  0 
rtlwifi                85089  1 rtl8192ce
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
snd_rawmidi            30486  1 snd_seq_midi
v4l2_compat_ioctl32    17078  1 videodev
i915                  514985  3 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
mac80211              294370  2 rtl8192ce,rtlwifi
drm_kms_helper         42136  1 i915
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
thinkpad_acpi          81587  0 
psmouse                73535  0 
drm                   227495  4 i915,drm_kms_helper
serio_raw              13166  0 
i2c_algo_bit           13400  1 i915
cfg80211              178528  2 rtlwifi,mac80211
nvram                  14419  1 thinkpad_acpi
snd                    67382  15 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
jmb38x_ms              17596  0 
soundcore              12680  1 snd
memstick               16520  1 jmb38x_ms
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
hid_apple              13324  0 
usbhid                 46956  0 
hid                    91020  2 hid_apple,usbhid
ahci                   25951  3 
sdhci_pci              13989  0 
libahci                26642  1 ahci
r8169                  48022  0 
sdhci                  27387  1 sdhci_pci

```

---

### Post by chili555 on 2011-05-30
> but the wireless still says disconnected.When you click the Network Manager icon, do you see your network? When you click your network, does it try to connect? How about:```
sudo iwlist wlan0 scan
dmesg | grep -e wlan -e 8192
```What time of night do Scots usually turn in?? Isn't it crazy late there?

---

### Post by erans on 2011-05-31
Well, I formatted again and just did the commands to remove and blacklist acer_wmi. 

Things are now up and running on the installed wifi drivers for the chipset. Wifi is still not good, but it's better than nothing right now.

EDIT: To clarify, in case Pythonscript is wondering, "not good" means that it pings very high to sites like google (I get around ~25ms consistently on my desktop, which is plugged into a wireless repeater for my main ssid and is also running 11.04. I get a mix of 25s and 500s on my laptop) and the internet connection just stops working at times. I have to reconnect to my wifi network in order to regain the connection, but I could still lose it seemingly at random. Wonder if there's a way to show logs or something to see what's happening to the wifi connection. 

Anyway, are our only options between Realtek drivers (which apparently cause our systems to crash) and using faulty default drivers? Or is there a way to modify the default drivers so they work properly?

I ran dmesg and it says wlan0: deauthenticating from [MAC address] by local choice (reason=3). 

Don't know if that helps, but that seems to be why we keep losing connection.

---

### Post by pythonscript on 2011-05-31
```
sudo iwlist wlan0 scan
```returns
```
wlan0     Interface doesn't support scanning : Network is down
```and 

```
dmesg | grep -e wlan -e 8192
```yields

```

[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800b5800000 s84416 r8192 d22080 u1048576
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u1048576 alloc=1*2097152
[   14.828410] rtl8192ce 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.828422] rtl8192ce 0000:05:00.0: setting latency timer to 64
[   14.848192] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.545124] rtl8192ce:rtl92c_download_fw():<0-0> Failed to request firmware!
[   15.695480] rtl8192ce:rtl92c_download_fw():<0-0> Failed to request firmware!

```I don't see my network listed when I click on the Network Manager icon, either. Good show on the pings, erans, I'd forgotten about that; I'll post what I'm getting once the connection is restored. 

@Chili - Edinburgh is on GMT time, so we'd be five hours ahead of you. Unfortunately, that location isn't accurate at the moment, since I'm in the States for several months doing research; I'm currently near Chicago so it wasn't terribly late. I'm not originally a Scot either; I'm at uni in Edinburgh as a postgraduate.

---

### Post by chili555 on 2011-05-31
> rtl8192ce:rtl92c_download_fw():<0-0> Failed to request firmware!I'm not quite sure if that means the firmware was not found because it's not on your system or if the driver, for some reason, didn't request and load it. Let's see if it exists:```
ls -al /lib/firmware/rtlwifi
```Here is the result from my system:> total 288
drwxr-xr-x  2 root root   4096 2011-05-18 17:52 .
drwxr-xr-x 58 root root  20480 2011-05-26 20:23 ..
-rw-r--r--  1 root root  13540 2010-11-18 16:20 rtl8192cfw.bin
-rw-r--r--  1 root root  16014 2010-12-13 09:10 rtl8192cufw.bin
-rw-r--r--  1 root root  20526 2011-02-11 09:07 rtl8192defw.bin
-rw-r--r--  1 root root  88856 2011-01-24 15:45 rtl8192sefw.bin
-rw-r--r--  1 root root 122328 2010-11-18 16:20 rtl8712u.bin
Here is what modinfo says:> $ modinfo rtl8192ce
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
[COLOR="Red"]firmware:       rtlwifi/rtl8192cfw.bin[/COLOR]
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     7416041392B86CCB7B54065
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
On my system, the firmware exists in the directory that the driver expects to find it. How about yours? If it's not there, get an ethernet connection and do:```
sudo apt-get install linux-firmware
```Reboot and you should be all set.

I'm glad we weren't keeping you awake till all hours working on wireless. It would be quite exciting for me to attend post-grad overseas. I hope it is for you.

---

### Post by pythonscript on 2011-05-31
The first set of commands didn't list anything, so I assume the firmware was somehow lost. However, I ran a version of your command:

```
sudo apt-get install --reinstall linux-firmware
```
and I'm back to the status quo and can connect to my wireless. All this leaves me with now is my same terrible connection, as evidence by the ping results:
```

PING www.l.google.com (74.125.225.52) 56(84) bytes of data.
64 bytes from 74.125.225.52: icmp_req=1 ttl=54 time=22.8 ms
64 bytes from 74.125.225.52: icmp_req=2 ttl=54 time=18.5 ms
64 bytes from 74.125.225.52: icmp_req=5 ttl=54 time=22.5 ms
64 bytes from 74.125.225.52: icmp_req=6 ttl=54 time=22.9 ms
64 bytes from 74.125.225.52: icmp_req=7 ttl=54 time=177 ms
64 bytes from 74.125.225.52: icmp_req=8 ttl=54 time=23.8 ms
64 bytes from 74.125.225.52: icmp_req=9 ttl=54 time=19.7 ms
^C64 bytes from 74.125.225.52: icmp_req=10 ttl=54 time=22.0 ms

--- www.l.google.com ping statistics ---
10 packets transmitted, 8 received, 20% packet loss, time 39191ms
rtt min/avg/max/mdev = 18.587/41.232/177.273/51.444 ms

```

I think I may just be stuck with this poor connection for the meanwhile, until I can find a wireless adapter to maybe use in place of it. 

Originally I'm not from the States either (where I did my undergraduate degree) so I have been away from home for quite a while now. Yes, though, it is certainly exciting!

---

### Post by chili555 on 2011-05-31
> I think I may just be stuck with this poor connection for the meanwhileIs the connection better or worse with:```
sudo rmmod -f rtl8192ce
sudo modprobe rtl8192ce swenc=1
```We can write a little conf file if it helps.

---

### Post by pythonscript on 2011-05-31
About the same, if not a little worse:

```
PING google.com (74.125.225.50) 56(84) bytes of data.
64 bytes from 74.125.225.50: icmp_req=1 ttl=54 time=20.8 ms
64 bytes from 74.125.225.50: icmp_req=5 ttl=54 time=21.7 ms
64 bytes from 74.125.225.50: icmp_req=6 ttl=54 time=22.0 ms
64 bytes from 74.125.225.50: icmp_req=7 ttl=54 time=20.2 ms
64 bytes from 74.125.225.50: icmp_req=9 ttl=54 time=200 ms
64 bytes from 74.125.225.50: icmp_req=11 ttl=54 time=24.1 ms
^C64 bytes from 74.125.225.50: icmp_req=14 ttl=54 time=25.5 ms

--- google.com ping statistics ---
14 packets transmitted, 7 received, 50% packet loss, time 38312ms
rtt min/avg/max/mdev = 20.208/47.912/200.858/62.463 ms
```

By the same, it's about the same as it was after a fresh install, which wasn't very usable.

---

### Post by chili555 on 2011-05-31
I'm frankly out of ideas/talent/mojo. All I can suggest is to email the authors:```
$ modinfo rtl8192ce
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
[COLOR="Red"]author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>[/COLOR]
srcversion:     7416041392B86CCB7B54065
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)

```They may refer you to a bug tracker and I'd suggest you follow through and file a bug. If you learn anything useful, please post back so we can all learn.

The 10ec:8176 is a fairly common chipset. As people upgrade to Natty, it won't take long for the screams to start.

---

### Post by pythonscript on 2011-05-31
I messaged them with a simple email about the basis of the problem, and pointed them to this thread to give a bit more information. Maybe something will come of it in the new few months (or more realistically, the next few Ubuntu releases). I hope the problem can be resolved by Ubuntu 12.04 LTS so I can upgrade to that version and remain with it for at least a few years.

---

### Post by erans on 2011-05-31
Thanks a lot for the help, chili. This is such a bummer. I'll be spending the next year conducting research and travelling (nothing compsci related, if it wasn't obvious from my lack of expertise) and I wanted to have a rock-solid Ubuntu laptop to do my work because 11.04 has been excellent on my desktop. Looks like I will have to switch to Windows until this problem is fixed. 

I'll post in this thread if I hear back from the authors. Thanks again!

---

### Post by erans on 2011-05-31
Actually, I'll try making this work in 10.04 first. Fingers crossed!

---

### Post by pythonscript on 2011-06-01
erans, I got your message and sent you my email address. However, I can't tell if the message went through or not, so if you receive two from me, my apologies.

---

### Post by erans on 2011-06-01
> **pythonscript said:**
> erans, I got your message and sent you my email address. However, I can't tell if the message went through or not, so if you receive two from me, my apologies.
No problem. I got it. I unpacked my laptop (couldn't resist) and tested the new drivers I received from the authors and this is what I found. 

As my system will apparently not boot with rfkill unblock all and acer_wmi blacklisted, I loaded each driver on a fresh install.

Then, I did```
sudo su
rmmod -f acer_wmi
rfkill unblock all
```

For each driver my system locked up permanently after rfkill.

So I thought maybe instead of doing that, I would just blacklist acer_wmi and try booting with that, since then maybe rfkill wouldn't be needed. 

If I did that, my system wouldn't boot at all. 

I sent my logs back to the devs (though since I couldn't find the logs they wanted, I ended up just sending the entire /var/log/ directory in a tar file) so we'll see what happens.

---

### Post by possumator on 2011-06-09
blacklisting acer_wmi worked for my Lenovo S12. 

Thanks

---

### Post by Atirag on 2011-06-16
Hello everyone, I figured I'll use this topic since I've been having similar issues with the exact same driver and there's a lot of good info here.

I have a Toshiba Satellite C655D. I have no problem with my wired connection but whenever I try using my wireless connection my computer freezes. Sometimes if I use my wired connection before using the wireless one then my wireless connection works fine. Whenever I try booting without having the network cable plugged then my computer hangs at boot, but if I plug the cable then it boots without a problem. So I figure the problem is the wireless driver. I had similar but not entirely the same issues with Ubuntu 10.10 so I don't want to go back and I'll rather fix the issues with 11.04. I've been using the driver that installs with the kernel, in Ubuntu 10.10 I used the driver from the Realtek website but I had similar problems. So a little info.

This is the output of 

```
modinfo rtl8192ce
``````
filename:       /lib/modules/2.6.38-8-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     7416041392B86CCB7B54065
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       2.6.38-8-generic-pae SMP mod_unload modversions 686 
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
```and this is the output of lsmod

```
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24140  2 
arc4                   12473  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
rtl8192ce             120897  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
rtlwifi                78961  1 rtl8192ce
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              257001  2 rtl8192ce,rtlwifi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            13213  1 
snd_timer              28659  2 snd_pcm,snd_seq
uvcvideo               66851  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2434640  89 
cfg80211              156212  2 rtlwifi,mac80211
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
psmouse                59039  0 
shpchp                 32345  0 
serio_raw              12990  0 
sp5100_tco             13456  0 
k10temp                12951  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_piix4              13095  0 
sparse_keymap          13666  0 
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
atl1c                  36237  0 
usb_storage            43946  0 
libahci                25548  1 ahci
uas                    17676  0 
```as you can see I have only one wireless driver installed.

Can someone please help me with this? I've been having this issue since probably a week now and I'm getting kind of desperate.

Should I install another kernel? or maybe try with another driver? is it a firmware issue? anybody having similar issues?

 Any help will be appreciated.

---

### Post by chili555 on 2011-06-16
I'm not sure I have any answer. I have battled that driver on several threads here. I suggest you email Realtek, try ndiswrapper or revert to 10.10. I guess you could also get a different card. I hate to be a pessimist, but I also hate banging my head against the wall until it's bloody.

---

### Post by Atirag on 2011-06-16
> **chili555 said:**
> I'm not sure I have any answer. I have battled that driver on several threads here. I suggest you email Realtek, try ndiswrapper or revert to 10.10. I guess you could also get a different card. I hate to be a pessimist, but I also hate banging my head against the wall until it's bloody.
Chili555

I just found this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/749871](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/749871) and I think I'm going to try some of the things they recommend there to see what happens. Ubuntu 10.10 doesn't work either as this bug report says.

Thanks a lot anyways!

---

### Post by chili555 on 2011-06-16
> **Atirag said:**
> Chili555

I just found this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/749871](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/749871) and I think I'm going to try some of the things they recommend there to see what happens. Ubuntu 10.10 doesn't work either as this bug report says.

Thanks a lot anyways!Please keep us posted. There are a few more ce ?fans? out there that will love to hear an answer. Thanks.

---

### Post by erans on 2011-06-17
I compiled and install compat-wireless. I don't get the system lockups when I unblock acer_wmi, but the internet connection is still poor. Bad pings, disconnects, etc.

---

### Post by Atirag on 2011-06-17
I also compiled and installed the compat-wireless but the lockups are still there. When the connection is up it seems to be fine my main issue is with the lockups. On the same bug report I linked to some users said that using Realtek's older drivers the ones for pre 2.6.35 kernels seem to make the system more stable than any other solution but still not completely. I will try that once I get home and post results.

---

### Post by Atirag on 2011-06-20
Just wanted to let people know that I tried the old drivers and the problem remains. The only way I have managed to make the system stable enough is by installing Ubuntu 10.10 64bit and installing Realtek's proprietary driver. The system still locks up from time to time but it is more stable than 11.04.

---

### Post by medusa569 on 2011-07-01
> **chili555 said:**
> Let's see the result of these commands:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
rfkill list all
```Who da thunk a Lenovo would actually be an Acer?

If it works, we can tweak a couple of files and make it Acer-proof.


I bow down to the God Chili....for weeks I've been trying to get my wifi working and it all came down to this simple fix....my connection was soft blocked ...what ever that is......
mt computer beamed its beautiful blue connection light and all is right with the world.

all hail chili !=D>=D>

---

### Post by chili555 on 2011-07-01
> soft blocked ...what ever that is......It means your wireless was turned off in *soft*ware; acer-wmi in your case. It is supposed to translate key presses, Fn+F5 for example, into action: "Please turn on the wireless, Mr. Kernel." If it doesn't tell the system that the wireless is turned on, it never ... well, turns on. Ironically, the way to turn it on is to *remove* acer-wmi.

Thank you for your very kind comments. Enjoy your newly enabled wireless!

---

### Post by medusa569 on 2011-07-02
> **chili555 said:**
> It means your wireless was turned off in *soft*ware; acer-wmi in your case. It is supposed to translate key presses, Fn+F5 for example, into action: "Please turn on the wireless, Mr. Kernel." If it doesn't tell the system that the wireless is turned on, it never ... well, turns on. Ironically, the way to turn it on is to *remove* acer-wmi.

Thank you for your very kind comments. Enjoy your newly enabled wireless!



well something in those 3 magic sentences unblocked me...but I have a broadcom adapter
in a Compaq computer.    I am really surprised how it wasn't mentioned as an automatic setup command in any of the other posts.  I'm sure it would save much agravation for others as well....and YES  I am enjoying wireless finally....!!! It only took about  six months since installing ubuntu on laptop.:D

---

### Post by marquivon on 2011-07-18
Specifically for Lenovo Thinkpad E420 model (I have Core i5 variant) with 2.6.38-10-generic & 2.6.38-10-generic-pae kernel in Ubuntu 11.04, this is what works without any trouble

a) Blacklist acer_wmi in /etc/modprobe.d/blacklist.conf

b) Reboot and press Fn+F1 when you see the Thinkpad logo so that you enter the bios. In there, in the wireless section, disable the Wimax and Wireless WLAN.

After that boot into your Ubuntu. It'll work reliably with optimum latency to the gateway.

---

### Post by erans on 2011-07-18
Thanks! I returned my E420 because the T420 was on sale for the same price, but I'm sure this will help someone. I made sure to get the Intel wifi chipset with the T420, so problem-free so far.

---

### Post by dnelson on 2011-07-28
Thanks marquivon for the E420 tip. Mine came yesterday and I was struggling with wireless using the Natty live cd. I followed your
2 steps, but nm said hardware switch is off. After re-enabling wireless in the bios it magically works. It seems pretty stable and fast. So I'm confused but relieved - all I did was blacklist acer_wmi.

---

### Post by marquivon on 2011-07-28
Though the machine appears to be stable, there are random lockups and kernel panics. I have not been fully able to use it for 2 days at a stretch. The worst part is, I am clueless about what's causing the screen freeze. I earlier thought is could be multiple 'suspend' that I do, but yesterday I freshly booted with no suspend and the machine gave a kernel panic in 3 hrs.

Which processor you have and which kernel? I tried with 32bit, 32bit-pae and now using 64bit.

---

### Post by dnelson on 2011-07-29
Mine is still working ok.

i5-2410M Processor (2.30GHz, 3MB L3, 1333MHz FSB) with Intel Turbo Boost Technology up to 2.9GH

kernel is 32-bit 2.6.38-10-pae

---

### Post by marquivon on 2011-07-29
I've the same processor with 4 GB RAM. I wasn't aware of the Turbo boost part, will check that out.

At some place I saw that there was a BIOS upgrade available. I'll try upgrading the BIOS, if that makes any difference.

---

### Post by marquivon on 2011-07-29
I tried to find out the "Turbo Boost" part, but couldn't see any option in BIOS. How can I check that out?

Also, my BIOS was version 1.10 (2011-03-30). I updated it to the latest one available from Lenovo site - 1.16 ; will check if it makes any difference. Can you let me know which BIOS version did you have by default? While booting you need to press Fn+F1 to get into the BIOS and there you can see the BIOS version.

---

### Post by jensrein on 2011-08-18
Thanks Chili! Removing the acer_wmi did the trick, hoping it sticks! 

For others with similar problems: I had to do that fix before I did anything else (like doing "sudo rfkill unblock all" or playing with the hardware and software switches), otherwise my wireless would get a hard block I wasn't able to get rid of. 

Cheers again!

---

### Post by mfmastrangelo on 2011-09-16
I've followed all these steps and had my wireless working till I rebooted.
I've tried to run rfkill to unblock like I had successfully done before but rfkill now does nothing or says "Can't open RFKILL control device: No such file or directory"
So cruel because I was so close. Also running a thinkpad e420 with the same chipset and realtek driver. 

Also blacklisted acer-wifi, the originally installed rt8192ce,  and rtlwifi, and added rfkill unblock all to /etc/rc.local

been trying to solve this problem for days now, seems like a lot of people are having it

---

### Post by chili555 on 2011-09-18
> Also blacklisted acer-wifi, ***the originally installed rt8192ce***, and rtlwifi, and added rfkill unblock all to /etc/rc.localWhat driver did you install to drive it since the built-in is now blacklisted?

---

### Post by samamclean on 2011-09-23
I have the same problem  - however, I can't get any signal at all. I've upgraded to the .38 kernel on a Lenovo l420. It says that my wirless is disconnected, and when I try to connect it using Fn+f5, the device becomes unavailable until I reboot my machine. I can't scan - because the wireless switch is off. What can I do to turn it on? 

I know it's not a driver issue, and I've reinstall linux-firmware about 4 or 5 times.. I just want to know a command that will turn on my wireless.

---

### Post by samamclean on 2011-09-23
I've gone back and have been reading through - I don't have acer-wmi.

---

### Post by samamclean on 2011-09-23
Also, I should have said that I have a Lenovo L420, running 10.10 with hte 2.6.38 generic kernel

---

### Post by samamclean on 2011-09-24
I apologise for hte multi-part post, but I have one last wrinkle to throw intothe mix - when I do rfkill list all, I have only one thing show up:
phy0 Wireless LAN
softblocked: NO
hardblocked: no


so.. I have no idea what's going on as my case seems to be slightly different.

---

### Post by chili555 on 2011-09-24
> so.. I have no idea what's going on as my case seems to be slightly different.Good! That's reason enough to start your own new thread! This one is a bit long. Please do so and post:```
rfkill list all
lspci -nn | grep 0280
```Leave a link here and I'll respond as soon as I see it.

---

### Post by samamclean on 2011-09-24
Actually... I can link you back to my topic where I've been trying to sort it out as well. 

[http://ubuntuforums.org/showthread.php?t=1847984](http://ubuntuforums.org/showthread.php?t=1847984)

it's also a little bit long - but the first few pages seem to be just me posting the same results from different things.

---

### Post by danger89 on 2011-09-26
Ubuntu 11.04 the wifi does work but TTLS (PAP auth) gives me an very unstable connection. The connection disconnect every 2 minutes.

---

### Post by gilmapie on 2012-02-16
wow it was great information!!
i've wasted much time because of this problem.
the solution was more simple than i thought
anyway _chili555_ , erans, thank you veryvery much
[]("http://ubuntuforums.org/member.php?u=35909")

---

