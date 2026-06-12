---
title: "Wifi not recognized after waking from suspend"
date: 2012-01-15
forum: Networking &amp; Wireless
---

### Post by laurac1022 on 2012-01-15
Hi to all,

I need some assistance to resolve this issue.  Whenever my computer resumes from suspend it drops the wireless connection and will not recognize the wlan.  I am currently connected by wired connection as the wireless is not working.

Using ubuntu 11.04 on toshiba satellite laptop with an Atheros AR5001 adapter running with ath5k driver.

Not too familiar with linux so I am kinda stuck.

I will post the output of a few commands while my wireless is AWOL.  I can post output of other commands as well just let me know which ones are needed.
```

laura@Satellite:~$ sudo iwlist scan
[sudo] password for laura: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

vboxnet0  Interface doesn't support scanning.

``````
laura@Satellite:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"ryan&laura"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

``````
laura@Satellite:~$ lspci | grep net
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

``````

laura@Satellite:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
parport_pc             36959  0 
ppdev                  17113  0 
nfsd                  316512  11 
lockd                  85732  1 nfsd
nfs_acl                12883  1 nfsd
auth_rpcgss            52881  1 nfsd
sunrpc                234297  12 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs               12998  1 nfsd
snd_hda_codec_realtek   336771  1 
joydev                 17606  0 
arc4                   12529  2 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
radeon                982182  3 
snd_seq_midi           13324  0 
ath5k                 153264  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath                    23779  1 ath5k
mac80211              296672  1 ath5k
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72195  0 
ttm                    76664  1 radeon
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
drm_kms_helper         42394  1 radeon
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 49166  0 
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   227534  5 radeon,ttm,drm_kms_helper
cfg80211              181865  3 ath5k,ath,mac80211
edac_core              53845  0 
tifm_7xx1              13042  0 
soundcore              12680  1 snd
yenta_socket           27846  0 
pcmcia_rsrc            18372  1 yenta_socket
tifm_core              15654  1 tifm_7xx1
psmouse                73535  0 
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              13166  0 
sp5100_tco             13744  0 
edac_mce_amd           23464  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
k8temp                 13016  0 
i2c_algo_bit           13400  1 radeon
i2c_piix4              13303  0 
shpchp                 37297  0 
sparse_keymap          13898  0 
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
ahci                   25951  4 
r8169                  48022  0 
libahci                26642  1 ahci
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13165  0 

```

---

### Post by homeuser1 on 2012-01-15
I have the same issue about once a week.  I never have figured it out.  Usually, shutting down and restarting will reconnect it.  Sometimes, it takes several shutdowns.  Eventually, it reconnects until the next time.  Good luck.

---

### Post by varunendra on 2012-01-15
It looks like a resurrected bug in ath5k driver: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769092](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769092)

Going through comments on the same bug-report page, a few things seem worth trying:

First: Try updating your system to see if it gets fixed automatically.

Second: If updates don't fix it, try this temporary workaround (comment #11):
[INDENT]right before going to suspend/hibernate, unload the ath5k module by:
```
sudo modprobe -rv ath5k
```

and when you resume from suspend/hibernate, do this:
```
sudo modprobe -v ath5k
```
you may (or may not) also have to run:
```
sudo ifconfig wlan0 up
``` after the above command if wireless appears as 'disabled' after resuming and modprob'ing.

[/INDENT]If this proves to be working every time, we can try to automate it so that we don't have to do it manually at each suspend/resume.

---

### Post by kurt18947 on 2012-01-15
Hi

You can cyber-slap me if this seems insulting; I don't intend it to be.  Are you sure you're disconnected? For example, the 'ping' command shows no connection?  I'm using gnome-shell on Ubuntu 11.10.  Every time I suspend and resume, I get a 'no network found' message or words to that effect.  The network is most assuredly NOT disconnected, it works fine.  I assume the message is from when the suspend command is executed and the network connection is disconnected.  it reconnects automatically for me but doesn't clear the disconnected message.

---

### Post by varunendra on 2012-01-15
> **kurt18947 said:**
> You can cyber-slap me if this seems insulting
Tell me how it can be done..!! (not that I'm intending to, but the knowledge can be useful at times ;))

Ok, that was a joke. Are you using the same ath5k driver? Because given the amount of complains and the bug report having a 'confirmed' status at bugzilla, I don't think it can be as simple as that.

---

### Post by laurac1022 on 2012-01-15
Im pretty sure that it is not really connected as I cannot access internet or network when it is not working.  But of course as soon as someone wants to help me, it starts working flawlessly.

---

### Post by laurac1022 on 2012-01-15
Also when the wireless is down and I try to scan for networks using 'sudo iwlist scan' the output will be either the one like in post #1 or if I issue the same command in the same terminal the wlan0 part will say 'Interface doesn't support scanning.  Device is busy' 
I would post the output to show you but of course the wireless is working now.

---

### Post by praseodym on 2012-01-15
Its a known issue which can be solved easily.

Check with

```
lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv' 
```
which modules can cause problems (left column) and add your wireless driver (here **ath5k**) to this list. Create a file with:

```
sudo touch /etc/pm/config.d/00sleep_module
sudo chmod +x /etc/pm/config.d/00sleep_module 
gksudo gedit /etc/pm/config.d/00sleep_module
```
and add these modules according to this example:

```
SUSPEND_MODULES="$SUSPEND_MODULES ehci-hcd uhci-hcd usbcore forcedeth" 
```
save, close, and check SUSPEND/HIBERNATE

Edit: This unloads the modules and reloads them, so wake-on-wireless will not work (anymore)

---

### Post by laurac1022 on 2012-01-16
Ok I have made the file as you suggested.  Do the contents of it look correct?
```
SUSPEND_MODULES="$SUSPEND_MODULES mac80211 cfg80211 firewire_ohci sdhci_pci firewire_core usbhid hid sdhci r8169 ahci libahci ath5k"
```
and for reference this is the lsmod:
```
laura@Satellite:~$ lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv'
mac80211              296672  1 ath5k
cfg80211              181865  3 ath5k,ath,mac80211
firewire_ohci          40370  0 
sdhci_pci              13989  0 
firewire_core          62646  1 firewire_ohci
usbhid                 46956  0 
hid                    91020  1 usbhid
sdhci                  27387  1 sdhci_pci
r8169                  48022  0 
ahci                   25951  4 
libahci                26642  1 ahci

```

---

### Post by laurac1022 on 2012-01-17
Also something interesting I thought would be worth mentioning.....a little while ago when I woke my laptop up the wireless was not working and I needed it to access a movie I wanted to watch;  so I caved and decided to just boot into win7.  Well to my surprise the wireless would not work in win 7 either.   

How could this issue possibly cause win 7 to not be able to connect?  maybe something to do with the ip lease??? im so confused:confused:

---

### Post by laurac1022 on 2012-01-18
I marked the thread solved as adding that file to unload/load modules did the trick.

Thank you very much :D

---

