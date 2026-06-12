---
title: "No sound on XMMS or runing a clip unde Flash Player"
date: 2008-09-23
forum: Multimedia Software
---

### Post by rralex89 on 2008-09-23
hello everybody, i have this problem with my week-old ubuntu system that i am new to.

when i installed ubuntu, everything worked just fine, i wen ahead and installed xmms by downloading it from it's website (couldn't find it on synaptic) and installed flash player plugin for mozilla firefox. things went just fine until today. 

When i wanted, this morning, to start xmms to listen to some music i could'nt hear a thing, the mp3 played but it didn't give any sound output. Same thing happenes if i run a video clip under flash player (ex. youtube.com). If i try to use rythmbox or movie player to listen it works but i can't use them everytime as i have some .ogg files.

Anybody have any ideas?:confused:

---

### Post by Crafty Kisses on 2008-09-23
I'd like to see the results of this command:
```
lspci
```

---

### Post by wolfen69 on 2008-09-23
seems to be a common ailment. try: ```
sudo apt-get install libflashsupport
``` then restart.

---

### Post by rralex89 on 2008-09-24
i've tunned the lspci command and here's the output:

```
root@allex89:/home/alex# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0e.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)

```

i allready have the libraries for flash player, it worked seemlessley for a couple of days, however i tried the apt-get command and it dosen't work

Thanks!

---

