---
title: "Acer Aspire Revo R3700 says Wireless Device Not Ready"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by StevieRG on 2012-02-07
Hi, I have an Acer Aspire Revo R3700 on which I installed 10.04LTS, everything is great except the wireless connection. Wired connection works fine.

In the main menu bar under "Wireless Networks" it says "Device Not Ready". Looking at some previous posts of similar problems, I think the following info might be useful for diagnosis to start with. Could you help please? Many thanks.


revo@revo-aspire:~$ lsmod | grep -e rt2 -e rt3
rt3090sta             674536  0 


revo@revo-aspire:~$ dmesg | grep -i rt2
[   17.527113] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   17.527120] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[   17.532259] !!! rt28xx Initialized fail !!!
[   17.582539] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   17.582548] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[   17.587853] !!! rt28xx Initialized fail !!!
[   23.132062] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   23.132071] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[   23.137318] !!! rt28xx Initialized fail !!!
[   23.189861] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   23.189871] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[   23.195108] !!! rt28xx Initialized fail !!!
[  257.116854] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[  257.116860] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[  257.122003] !!! rt28xx Initialized fail !!!
[  257.131417] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[  257.131424] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[  257.136611] !!! rt28xx Initialized fail !!!
[28470.521922] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[28470.521929] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[28470.527280] !!! rt28xx Initialized fail !!!
[28472.492711] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[28472.492720] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[28472.497856] !!! rt28xx Initialized fail !!!
[29315.874763] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[29315.874769] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[29315.879905] !!! rt28xx Initialized fail !!!
[29315.889681] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[29315.889689] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[29315.894920] !!! rt28xx Initialized fail !!!
[32447.095487] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[32447.095493] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[32447.100792] !!! rt28xx Initialized fail !!!
[32447.542680] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[32447.542686] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[32447.547839] !!! rt28xx Initialized fail !!!


revo@revo-aspire:~$ dmesg | grep -i rt3
[   14.309079] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned.
[   14.392774] rt3090 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.392823] rt3090 0000:02:00.0: setting latency timer to 64
[  252.187368] rt3090 0000:02:00.0: PCI INT A disabled
[  253.867458] rt3090 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[28442.651153] rt3090 0000:02:00.0: PCI INT A disabled
[28443.843864] rt3090 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[29305.732334] rt3090 0000:02:00.0: PCI INT A disabled
[29306.952589] rt3090 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[32420.093004] rt3090 0000:02:00.0: PCI INT A disabled
[32421.281150] rt3090 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18


revo@revo-aspire:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:18 memory:febf0000-febfffff

---

### Post by chili555 on 2012-02-07
Please try this:```
sudo gedit /etc/Wireless/RT2860STA/RT2860STA.dat
```Is the file already there? If so, you have a permissions problem and need to do:```
sudo chmod +r /etc/Wireless/RT2860STA/RT2860STA.dat
```If the file is not there at all, for now add a single word:```
Default
```Proofread, save and close gedit. Unload and reload the driver:```
sudo modprobe -r rt3090sta
sudo modprobe rt3090sta
```Now check:```
dmesg | grep -i rt2
```Is there any improvement after this timestamp?> [[COLOR="Red"]32447.547839[/COLOR]] !!! rt28xx Initialized fail !!!


---

### Post by StevieRG on 2012-02-07
That's just excellent - problem solved!

Neither the file or the directories path existed, I created the directories and file as you suggested. Then I did the chmod, then the unload and reload, and it sprang into life. In fact I'm using the wireless connection to write this reply. Thank you so much for your quick and useful help.

---

