---
title: "ndiswrapper:"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by DeltaFee on 2009-03-07
I have a dell Inspiron 5000e laptop, the only network connection is my **Linksys** **WPC54GS**. On this laptop I have installed Ubuntu 8.10; I have also configure the **NDSIWRAPPER** until I get to **mprobing NDSIWRAPPER**. Where the command terminal does not give any output form the mprobe command.:eek: Even after I restart the laptop I try to connect to the internet through the adapter and it won't connect. :frown: I am not sure what I am doing wrong. Thxs! DF

---

### Post by Skripka on 2009-03-07
Presuming you prior work is correct, when you type:

```

sudo modprobe ndiswrapper

```

You shouldn't get a response from the terminal, apart from a new prompt.  In linux, "no news is good news", ifTerminal does not spit errors back at you-then it should have worked.

after modprobe, you probably need to type:

```

iwconfig

```

to see if it worked...there should be a "wlan0" listed in there if it did.

I'm not on Ubunut, and stopped using wireless a while back, so I'm doing tthis by memory.

---

### Post by kevdog on 2009-03-08
Im just wondering why you are choosing ndiswrapper over b43 or another native variant (STA(wl))?  Could you list
lspci -nnm

Its probably locking since the windows driver you want to use is incorrect.

---

### Post by DeltaFee on 2009-03-11
Here are those two things:

LSPCI:
> 
00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "440BX/ZX/DX - 82443BX/ZX/DX Host bridge [7190]" -r03 "" ""
00:01.0 "PCI bridge [0604]" "Intel Corporation [8086]" "440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [7191]" -r03 "" ""
00:04.0 "CardBus bridge [0607]" "Texas Instruments [104c]" "PCI1225 [ac1c]" -r01 "Dell [1028]" "Device [00cc]"
00:04.1 "CardBus bridge [0607]" "Texas Instruments [104c]" "PCI1225 [ac1c]" -r01 "Dell [1028]" "Device [00cc]"
00:07.0 "Bridge [0680]" "Intel Corporation [8086]" "82371AB/EB/MB PIIX4 ISA [7110]" -r02 "" ""
00:07.1 "IDE interface [0101]" "Intel Corporation [8086]" "82371AB/EB/MB PIIX4 IDE [7111]" -r01 -p80 "" ""
00:07.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82371AB/EB/MB PIIX4 USB [7112]" -r01 "" ""
00:07.3 "Bridge [0680]" "Intel Corporation [8086]" "82371AB/EB/MB PIIX4 ACPI [7113]" -r03 "" ""
00:08.0 "Multimedia audio controller [0401]" "ESS Technology [125d]" "ES1978 Maestro 2E [1978]" -r10 "Dell [1028]" "Device [00cc]"
00:10.0 "Communication controller [0780]" "Agere Systems [11c1]" "WinModem 56k [0448]" -r01 "Actiontec Electronics Inc [1668]" "Device [2000]"
01:00.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "Rage Mobility M3 AGP 2x [4c46]" -r02 "Dell [1028]" "Device [00cc]"
**06:00.0 "Network controller [0280]" "Broadcom Corporation [B][14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r03 "Linksys [1737]" "Device [4320]"**[/B]


IWCONFIG:
> 
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by Skripka on 2009-03-11
> **DeltaFee said:**
> 


IWCONFIG:

IIRC, you iwconfig looks good for continuing.  You'll need to designate ESSID and encryption-but you're on your way it looks like.  You can do all this fun from the commandline, or use GUI utilities to do the rest-following whatever tutorial got you thus far.

I always did it in Terminal...but then again I use Arch. ;)

---

### Post by DeltaFee on 2009-03-13
> 
IIRC, you iwconfig looks good for continuing. You'll need to designate ESSID and encryption-but you're on your way it looks like. You can do all this fun from the commandline, or use GUI utilities to do the rest-following whatever tutorial got you thus far.

I always did it in Terminal...but then again I use Arch.


I am not sure how to configure the wireless, where is the tutorial I need to get it working? THX

---

### Post by Skripka on 2009-03-13
> **DeltaFee said:**
> I am not sure how to configure the wireless, where is the tutorial I need to get it working? THX

BAM:

[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

You should be ready for step 7....although it might not hurt to go back to step 5 to make sure things have worked.

---

