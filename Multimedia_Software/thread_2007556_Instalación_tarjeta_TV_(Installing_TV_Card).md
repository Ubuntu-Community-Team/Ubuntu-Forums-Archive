---
title: "Instalación tarjeta TV (Installing TV Card)"
date: 2012-06-20
forum: Multimedia Software
---

### Post by falarconj on 2012-06-20
Hola a tod@s (hi everyone):

Mi nombre es Felipe y soy nuevo en Ubuntu,  hasta ahora todo bien, pero no puedo instalar (o configurar) mi tarjeta de TV, es  una PCTronic 7130. Al escribir el comando lspci me aparece lo siguiente

(My name is Philip and I'm new to Ubuntu, so far so good, but I can not install (or set) my TV card is a PCTronic 7130. When you type the command lspci I get the following):

00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
**00:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)**
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)

¿Alguien podría ayudarme con los pasos a seguir para poder disfrutar del tv cable en mi compu? De antemano, muchas gracias

(Could anyone help me with the steps to enjoy the cable TV in my computer? In advance, thank you very much). :wink:

---

### Post by sinombre5 on 2012-10-14
entra en la terminal
y pon esto
dmesg | grep saa
Ke te dice??

---

