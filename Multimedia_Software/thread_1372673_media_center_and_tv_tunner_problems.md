---
title: "media center and tv tunner problems"
date: 2010-01-04
forum: Multimedia Software
---

### Post by Just_Edd on 2010-01-04
hello, i am using ubuntu karmic(9.10) in my PC and everthing works great but i dont know how to make works the tv tunner, audio and video inputs and the S-video connectors. 

My pc model is, HP Media Center PC m7630la, here are the spects:

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=es&cc=mx&prodNameId=3284319&prodTypeId=12454&prodSeriesId=3220014&swLang=34&taskId=135&swEnvOID=1099](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=es&cc=mx&prodNameId=3284319&prodTypeId=12454&prodSeriesId=3220014&swLang=34&taskId=135&swEnvOID=1099)

sorry about my grammar, i am a spanish speaker, i appreciate alot the help.

please help me, i really like ubuntu, and i would like to keep using it!!.

when i use lspc i see thisi:

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: ATI Technologies Inc RV505 [Radeon X1550 64-bit]
01:00.1 Display controller: ATI Technologies Inc Device 7167
02:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:02.0 Multimedia video controller: Internext Compression Inc Device 0006 (rev 01)
02:03.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

---

### Post by lovinglinux on 2010-01-04
I'm not sure it will help you, since we have different TV card models, but I configured mine [this way](http://ubuntuforums.org/showpost.php?p=5971890&postcount=2). 

Anyway, there are [several threads in the forums about Hauppauge TV card](http://www.google.com/search?q=Hauppauge++site%3Aubuntuforums.org).

---

### Post by Just_Edd on 2010-01-07
yes, but i dont know how to use it for my card!!

---

### Post by Just_Edd on 2010-01-12
i think i fixed!!, i used IVTV Drivers!! i had to open the case to see the card!!, i don't know why i didn't do that before!!. The card is a WinTV pvr-150. 

Thanx for the information!!, but now i can't watch tv through xawtv or tvtime. The only way to watch tv is using VLC, and XawTV at the same time. I use VLC for watch and XawTV for changing the chanels, so i need to have both programs opened, i dont know why.

Thanx for the help!!

---

