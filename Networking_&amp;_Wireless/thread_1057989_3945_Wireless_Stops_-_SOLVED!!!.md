---
title: "3945 Wireless Stops - SOLVED!!!"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by MarkAfterDark on 2009-02-02
Ever since updating to 8.10 I and many others have been plagued with a Kernel bug in regards to the "Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)" connection stopping and dropping due to a microcode error.

I can't take credit for this solution as I found it while digging on one of the dozens of threads about this issue.  This may not solve all WPA Enterprise issues but it solved mine.  

The original link can be found here:  [http://www.linuxtent.com/?p=118]("http://www.linuxtent.com/?p=118")

```
lspci -vvnn

For my laptop:

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4227] (rev 02)
Subsystem: Intel Corporation PRO/Wireless 3945BG Network Connection [8086:1014]
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0, Cache Line Size: 64 bytes
Interrupt: pin A routed to IRQ 217
Region 0: Memory at df6ff000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>

running
iwlist scanning
gives me
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.

digging for the source of the error i got this message in the log

dmesg | grep iwl

[ 68.062145] iwl3945: Microcode SW error detected. Restarting 0×82000008.
[ 68.062169] iwl3945: Error Reply type 0×00000005 cmd REPLY_SCAN_CMD (0×80) seq 0×4414 ser 0×0000004B
[ 69.064840] iwl3945: Can’t stop Rx DMA.
[ 69.196238] Registered led device: iwl-phy0:RX
[ 69.196280] Registered led device: iwl-phy0:TX

I tried this trick, to solve the problem

   1. sudo modprobe -r iwl3945
   2. create a file named iwl3945 in /etc/modprobe.d
   3. in that file enter the following entries
      alias wlan0 iwl3945
      options iwl3945 disable_hw_scan=1
   4. sudo modprobe iwl3945
   5. sudo ifconfig wlan0 up

after that i got my wireless card working, but not the wireless LED. For me that is enough :)
```

---

