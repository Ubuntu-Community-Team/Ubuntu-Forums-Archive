---
title: "ASUS U56e wireless problem."
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by jwx330 on 2012-10-28
It just keeps asking for the network key, but doesn't ever connect. Wired connection works just fine. 

From reading other threads Here is some information, 

kandj@kandj-U56E:~$ dmesg | grep iwl 
[   12.196589] iwlwifi 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.196599] iwlwifi 0000:02:00.0: setting latency timer to 64
[   12.196629] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   12.196631] iwlwifi 0000:02:00.0: pci_resource_base = ffffc9000579c000
[   12.196633] iwlwifi 0000:02:00.0: HW Revision ID = 0x67
[   12.196726] iwlwifi 0000:02:00.0: irq 51 for MSI/MSI-X
[   12.196766] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[   12.196836] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   12.207561] iwlwifi 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
[   12.207565] iwlwifi 0000:02:00.0: Device SKU: 0X150
[   12.207567] iwlwifi 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   12.208275] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   12.395394] iwlwifi 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[   12.397715] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.267736] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   13.267885] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   13.424508] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   13.424658] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   48.426186] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[   48.426189] iwlwifi 0000:02:00.0: Current read_ptr 6 write_ptr 9
[   48.426191] iwlwifi 0000:02:00.0: On demand firmware reload
[   48.993174] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[   48.993606] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   48.993754] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   69.017291] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[   69.017303] iwlwifi 0000:02:00.0: Current read_ptr 3 write_ptr 6
[   69.017309] iwlwifi 0000:02:00.0: On demand firmware reload
[   69.296794] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[   69.297315] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   69.297466] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   77.334364] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[   77.334375] iwlwifi 0000:02:00.0: Current read_ptr 0 write_ptr 3
[   77.334382] iwlwifi 0000:02:00.0: On demand firmware reload
[   77.605895] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[   77.606513] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   77.606670] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  142.549335] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  142.549346] iwlwifi 0000:02:00.0: Current read_ptr 9 write_ptr 12
[  142.549353] iwlwifi 0000:02:00.0: On demand firmware reload
[  142.956655] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  142.957351] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  142.957506] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  151.006083] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  151.006087] iwlwifi 0000:02:00.0: Current read_ptr 0 write_ptr 3
[  151.006089] iwlwifi 0000:02:00.0: On demand firmware reload
[  151.265742] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  151.266388] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  151.266544] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  158.812147] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  158.812158] iwlwifi 0000:02:00.0: Current read_ptr 0 write_ptr 3
[  158.812164] iwlwifi 0000:02:00.0: On demand firmware reload
[  159.526906] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  159.527523] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  159.527680] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  173.553626] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  173.553630] iwlwifi 0000:02:00.0: Current read_ptr 3 write_ptr 6
[  173.553632] iwlwifi 0000:02:00.0: On demand firmware reload
[  174.152648] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  174.153208] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  174.153376] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  254.108613] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  254.108624] iwlwifi 0000:02:00.0: Current read_ptr 0 write_ptr 3
[  254.108629] iwlwifi 0000:02:00.0: On demand firmware reload
[  254.268427] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  254.269071] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  254.269228] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  277.298585] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  277.298596] iwlwifi 0000:02:00.0: Current read_ptr 0 write_ptr 3
[  277.298601] iwlwifi 0000:02:00.0: On demand firmware reload
[  277.570224] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  277.570907] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  277.571071] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  285.611769] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  285.611773] iwlwifi 0000:02:00.0: Current read_ptr 0 write_ptr 3
[  285.611775] iwlwifi 0000:02:00.0: On demand firmware reload
[  285.891485] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  285.892009] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  285.892165] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  293.933013] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  293.933017] iwlwifi 0000:02:00.0: Current read_ptr 0 write_ptr 3
[  293.933019] iwlwifi 0000:02:00.0: On demand firmware reload
[  294.136749] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  294.137187] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  294.137337] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  302.186326] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  302.186330] iwlwifi 0000:02:00.0: Current read_ptr 0 write_ptr 3
[  302.186333] iwlwifi 0000:02:00.0: On demand firmware reload
[  302.426055] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  302.426686] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  302.426843] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  310.471645] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  310.471664] iwlwifi 0000:02:00.0: Current read_ptr 0 write_ptr 3
[  310.471670] iwlwifi 0000:02:00.0: On demand firmware reload
[  310.711373] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  310.712021] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  310.712185] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  330.741408] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  330.741423] iwlwifi 0000:02:00.0: Current read_ptr 3 write_ptr 6
[  330.741430] iwlwifi 0000:02:00.0: On demand firmware reload
[  331.001145] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  331.001915] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  331.002073] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  638.159589] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  638.159608] iwlwifi 0000:02:00.0: Current read_ptr 0 write_ptr 3
[  638.159616] iwlwifi 0000:02:00.0: On demand firmware reload
[  638.515116] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  638.515780] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  638.515936] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  658.545192] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  658.545203] iwlwifi 0000:02:00.0: Current read_ptr 3 write_ptr 6
[  658.545209] iwlwifi 0000:02:00.0: On demand firmware reload
[  658.717017] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  658.717659] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  658.717824] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  666.762555] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  666.762568] iwlwifi 0000:02:00.0: Current read_ptr 0 write_ptr 3
[  666.762575] iwlwifi 0000:02:00.0: On demand firmware reload
[  667.058200] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  667.058749] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  667.058917] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  675.103750] iwlwifi 0000:02:00.0: Queue 0 stuck for 2000 ms.
[  675.103765] iwlwifi 0000:02:00.0: Current read_ptr 0 write_ptr 3
[  675.103773] iwlwifi 0000:02:00.0: On demand firmware reload
[  675.259601] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  675.260270] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[  675.260426] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0

kandj@kandj-U56E:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wimax: WiMAX
    Soft blocked: yes
    Hard blocked: no

kandj@kandj-U56E:~$ lsmod | grep asus 
asus_nb_wmi            12710  0 
asus_wmi               24456  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
wmi                    19256  1 asus_wmi

kandj@kandj-U56E:~$ sudo modprobe -r asus_wmi 
[sudo] password for kandj: 
FATAL: Module asus_wmi is in use.

I didn't read anything about that message, so I figured I'd try to get some help with this. Thanks!

---

### Post by jwx330 on 2012-11-07
Anybody?

---

### Post by wildmanne39 on 2012-11-26
Thread closed. Please do not post duplicates, it dilutes community effort.

---

