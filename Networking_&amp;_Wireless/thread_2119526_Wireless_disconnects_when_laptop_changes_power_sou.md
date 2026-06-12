---
title: "Wireless disconnects when laptop changes power source."
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by gloabalruss on 2013-02-22
[I]Mod note
Reference thread : [http://ubuntuforums.org/showthread.php?t=2099160](http://ubuntuforums.org/showthread.php?t=2099160)[/I]
---------------------------

I'm suffering from the same problem.  I have followed the instructions provided by [[COLOR=#000000]Pjotr123[/COLOR]]("http://ubuntuforums.org/showthread.php?p=12426628") to disable the power management for the wireless adapter, but it hasn't changed the behaviour.  Here's the output of iwconfig:
```

wlan0     IEEE 802.11abgn  ESSID:"*removed*"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 48:5B:39:xx:xx:xx   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:56   Missed beacon:0

```
Any further suggestions please?

---

### Post by varunendra on 2013-02-24
Post moved to its own thread.
------------------------

Welcome to the forums gloabalruss! :)

Please post the outputs of -
```
lspci -nnk | grep -iA2 net
lsmod
dmesg | tail -20
```
Run the last dmesg command about 4-6 seconds after it disconnects.

Also, use 'Code' tags while posting the outputs (follow the link in my signature to see an example).

---

### Post by gloabalruss on 2013-02-26
Hello varunendra, thanks for the welcome, tip and help!

Here are the outputs you requested:

lspci -nnk | grep -iA2 net
```

00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:30db]
    Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4236]
    Subsystem: Intel Corporation Device [8086:1011]
    Kernel driver in use: iwlwifi

```lsmod
```

Module                  Size  Used by
nls_utf8               12493  1 
udf                    84576  1 
pci_stub               12550  1 
vboxpci                22911  0 
vboxnetadp             13328  0 
vboxnetflt             27240  0 
vboxdrv               252189  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 38139  14 
bnep                   17830  2 
tpm_infineon           13200  0 
binfmt_misc            17292  1 
snd_hda_codec_analog    75395  1 
pata_pcmcia            16938  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12473  2 
snd                    62218  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
ppdev                  12849  0 
lp                     17455  0 
tpm_tis                18308  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
iwlwifi               366524  0 
pcmcia                 39826  1 pata_pcmcia
joydev                 17393  0 
i915                  423416  2 
drm_kms_helper         45466  1 i915
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
mac80211              436493  1 iwlwifi
cfg80211              178877  2 iwlwifi,mac80211
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
btusb                  17948  2 
bluetooth             158479  23 rfcomm,bnep,btusb
mac_hid                13077  0 
drm                   197641  3 i915,drm_kms_helper
hp_accel               25728  0 
mei                    36570  0 
i2c_algo_bit           13199  1 i915
lis3lv02d              19268  1 hp_accel
hp_wmi                 13652  0 
input_polldev          13648  1 lis3lv02d
parport_pc             32114  1 
psmouse                96718  0 
sparse_keymap          13658  1 hp_wmi
serio_raw              13027  0 
parport                40930  3 ppdev,lp,parport_pc
wmi                    18744  1 hp_wmi
video                  19115  1 i915
firewire_ohci          40180  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  2 udf,firewire_core
e1000e                140131  0

```4-6 seconds after disconnect...

demsg | tail -20
```

No command 'demsg' found, did you mean:
 Command 'dmesg' from package 'util-linux' (main)
demsg: command not found

```I think you probably did mean 'dmesg' ;)

```

dmesg | tail -20
[186936.561325] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[186936.561328] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[186936.561331] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[186936.561333] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[186936.580302] e1000e 0000:00:19.0: PME# enabled
[186936.759907] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[186936.808929] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[186936.829659] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[186936.830040] iwlwifi 0000:02:00.0: Radio type=0x0-0x2-0x0
[186936.884817] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[186936.907249] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[186936.907630] iwlwifi 0000:02:00.0: Radio type=0x0-0x2-0x0
[186936.955602] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[186944.571645] wlan0: authenticate with 48:5b:39:xx:xx:xx (try 1)
[186944.576987] wlan0: authenticated
[186944.581129] wlan0: associate with 48:5b:39:xx:xx:xx (try 1)
[186944.584875] wlan0: RX AssocResp from 48:5b:39:xx:xx:xx (capab=0x411 status=0 aid=2)
[186944.584879] wlan0: associated
[186944.591922] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[186955.120064] wlan0: no IPv6 routers present

```(xx'ed the MAC address of my router as I'm no security expert!)

Just to clarify the behaviour: if I disconnect the power from the laptop, the wifi disconnects, then a few seconds later reconnects.  Same is true when I plug the power back in.

Many thanks for you help, please let me know if you need any further info!

---

### Post by varunendra on 2013-02-26
> **gloabalruss said:**
> I think you probably did mean 'dmesg' ;)
Indeed :)
..and looks like I may need more than what it returned.
But before that, let's try an old trick first. Run the following in the terminal-
```
ls /etc/pm/power.d/
```
It should return no outputs - meaning the directory is empty and we're good to proceed. If it does return an output, stop here and post back the output.

Again, (in case of no output) run the following-
```
sudo touch /etc/pm/power.d/wireless
```
Then change the power source and see if it disconnects again. If it does, run **iwconfig** and make sure power management is turned off. If it is, and still it disconnects, then it's war time!

To get more info we need to start with system logs. In order to avoid a huge log and get only relevant log messages, please do the following after a system reboot -

As soon as wireless is up and working, change power source and let it disconnect -> reconnect. Then copy-paste the following in the terminal -
```
cd Desktop
dmesg > russ.txt
echo -e "\n\nsyslog" >> russ.txt
cat /var/log/syslog >> russ.txt
echo -e "\n\nparams" >> russ.txt
grep -R [0-9a-zA-Z] /sys/bus/pci/drivers/iwlwifi/module/parameters/ >> russ.txt
echo -e "\n\niwpriv" >> russ.txt
iwpriv >> russ.txt

tar cjf russ.tar.bz2 russ.txt
```

The last command would create a "russ.tar.bz2" file on your desktop. Attach it in your next post. You might wish to take a look at the "russ.txt" file and edit it to remove your mac address before archiving it with the last command.

I hope the pm-utils trick should do the job and we won't need to begin the war :P

---

### Post by gloabalruss on 2013-02-27
Hello varunendra

```
ls /etc/pm/power.d/
wireless

```

Here's the content of the file:
```

#!/bin/sh
/sbin/iwconfig wlan0 power off


```

In an attempt to learn more, I backed up the **wireless** file, deleted it, and created a new file with the **touch** command as you suggested.  No luck though, the wireless was still disconnecting with the power source change and **iwconfig** reporting the power management as off.  Bah!  Backup file restored.  Worth a try though, right? :)

Should I post the logs you requested now, or do you have a different suggestion based on the **wireless** file being present?

Thanks again for your help!

---

### Post by varunendra on 2013-02-27
> **gloabalruss said:**
> or do you have a different suggestion based on the **wireless** file being present?
Yeah, make it 'not present' for another test and reboot to see if there is any change (positive or negative).

Any file in that directory takes precedence over the script with the same name in /usr/lib/pm-utils/power.d/ directory. A blank file was meant to simply disable the "wireless" script there that is supposed to dicipline the drivers that don't play nicely with the 'power off' option of iwconfig command.

I was suspectig maybe that script itself could be causing trouble due to complex routines, but now the presence of the wireless file in /etc.... directory suggests it wasn't effective at all.

So let's just move the file temporarily to make the other script effective, and see if it can do what it is supposed to do.

The command -
```
sudo mv /etc/pm/power.d/wireless ~/
```
..will move the file to your home directory.

Just to make ultra sure, reboot and run iwconfig to make sure power management is off. Then redo the power cycle test and see if the miracle happned. If there is still no joy, then yes, we do need those logs I asked for (with little hope tbh).

---

### Post by gloabalruss on 2013-02-27
Hello varunendra, I removed the file, rebooted etc.  Same problem, so please find the logs attached.

I hope that having tried your suggestions tonight I haven't made it more difficult that it might otherwise be to find the source of the problem ;)

---

