---
title: "Intel Corporation WiFi Link 1000 Series stopped working with 2.6.32-32 kernel upgrade"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by solrac776 on 2011-05-31
Hello all

My Intel Corporation WiFi Link 1000 Series wireless card stopped working yesterday after I did an update via Update Manager.

After the upgrade, wireless is disabled and the option to enable it in Network Manager is grayed out.  I thought that it might be the new kernel, but changing back to the old kernel I still have the problem

lspci -nn says:
   03:00.0 Network controller [0280]: Intel Corporation WiFi Link 1000 Series [8086:0083]

ifconfig does not even list wlan

iwconfig says:
    wlan0     IEEE 802.11bgn  ESSID:off/any  
              Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
              Retry  long limit:7   RTS thr:off   Fragment thr:off
              Power Management:off

lsmod | grep iw gives:
    iwlagn                123060  0 
    iwlcore               125179  1 iwlagn
    mac80211              238896  2 iwlagn,iwlcore
    cfg80211              148341  3 iwlagn,iwlcore,mac80211
    led_class               3764  3 iwlcore,asus_laptop,sdhci


dmesg | grep iw gives:
    [   19.177779] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
    [   19.177782] iwlagn: Copyright(c) 2003-2009 Intel Corporation
    [   19.177837] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
    [   19.177844] iwlagn 0000:03:00.0: setting latency timer to 64
    [   19.177953] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 1000 Series BGN REV=0x6C
    [   19.207333] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
    [   19.207414] iwlagn 0000:03:00.0: irq 36 for MSI/MSI-X
    [   19.300505] phy0: Selected rate control algorithm 'iwl-agn-rs'


lshw -C network says:
      *-network DISABLED
           description: Wireless interface
           product: WiFi Link 1000 Series
           vendor: Intel Corporation
           physical id: 0
           bus info: pci@0000:03:00.0
           logical name: wlan0
           version: 00
           serial: 00:1e:64:3e:2e:d4
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
           configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11bgn
           resources: irq:36 memory:f4800000-f4801fff
      *-network
           description: Ethernet interface
           product: AR8131 Gigabit Ethernet
           vendor: Atheros Communications
           physical id: 0
           bus info: pci@0000:07:00.0
           logical name: eth0
           version: c0
           serial: e0:cb:4e:1a:87:42
           capacity: 1GB/s
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
           resources: irq:37 memory:f4600000-f463ffff ioport:b000(size=128)


lsb_release -d says:
    Description:	Ubuntu 10.04.2 LTS

uname -mr:
    2.6.32-32-generic x86_64

---

### Post by chili555 on 2011-05-31
What does this tell us?```
rfkill list all
lsmod | grep -e laptop -e wmi
```Thanks.

---

### Post by solrac776 on 2011-05-31
Thanks for your reply!

lsmod | grep -e laptop -e wmi gives:


snd_rawmidi            23420  1 snd_seq_midi
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
asus_laptop            20584  0 
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               3764  3 iwlcore,asus_laptop,sdhci

---

### Post by chili555 on 2011-05-31
And how about:```
rfkill list all
```Does your laptop have a wireless button? Does it respond as expected?

---

### Post by solrac776 on 2011-05-31
Thanks again Chili.

$ rfkill list all
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


I'm guessing that hard block is the problem?

I did:
$ sudo rfkill unblock all

...rfkill list all still says that it's blocked.

---

### Post by chili555 on 2011-05-31
> 3: phy0: Wireless LAN
Soft blocked: no
Hard blocked: yes


I'm guessing that hard block is the problem?Yes, indeed! Now please raise your right hand and solemnly swear that you have looked for and switched the wireless switch to 'On.' Does rfkill still say =yes? Is there a light or LED that changes when you press the switch? Does it work as expected?

---

### Post by solrac776 on 2011-05-31
Thanks for the suggestion Chili.

I didn't know that I had a hardware switch for the wireless until now.

---

### Post by chili555 on 2011-05-31
> **solrac776 said:**
> Thanks for the suggestion Chili.

I didn't know that I had a hardware switch for the wireless until now.So did you flip the switch and your wireless is working and you are a happy camper??

---

### Post by solrac776 on 2011-05-31
Yes to all those questions.  Thanks again chili.

---

