---
title: "Haupauge PCTV WinGo2"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by scto on 2006-11-10
Any success with this card?

dmesg seems to be ok, only 1 record isn't good, isn't it?
[17179588.824000] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe

so i made in /etc/modprobe.d/tvcard 2 entries

options cx88xx card=1 tuner=56 radio=1
tda9887 debug=0


and in /etc/modules also

tda9887
cx88xx

so no error ins dmesg
but i can only see 1 channel, if i scan (whit zapping, tvtime, xawtv or whatever) arround 60 channel's found.
but i can't switch, i only see 1 channel what do i wrong?

help is welcome and sorry for my englisch
tom

---

### Post by scto on 2006-11-11
hmm, tried different settings, yesterday it worked 1 times, i had all channels in zapping or tvtime, this happened until i unloaded and reloaded some cx88xx/cx8800 bttv video_buf etv modules.

but it worked only 1 time, after a reboot everything like before, i recive a signal but i cant search channels only 1 channel is in my tv app, the picture is not clear und the sound is noisy

my settings:

/etc/modprobe.d/tvtuner

alias char-major-81 videodev
alias char-major-81-0 tveeprom
alias char-major-81-1 cx88xx
options cx88xx card=1 tuner=56 radio=1 #tried different settings 55 or 56 in different forums they told 56 to use
options tda9887 debug=2

#options tuner secam=d pal=d
#options tda9887 port2=0 debug=0


dmesg looks like

CORE cx88[0]: subsystem: 0070:3401, board: Hauppauge WinTV 34xxx models [card=1,insmod option]

kernel: [17179586.228000] TV tuner 55 at 0x1fe, Radio tuner 1 at 0x1fe
kernel: [17179586.440000] tveeprom 0-0050: Hauppauge model 34704, rev J1B3, serial# 8521833
kernel: [17179586.440000] tveeprom 0-0050: tuner model is TCL M2523_3DB_E (idx 113, type 4)
kernel: [17179586.440000] tveeprom 0-0050: TV standards PAL(B/G) PAL(D/D1/K) (eeprom 0x44)
kernel: [17179586.440000] tveeprom 0-0050: audio processor is CX881 (idx 31)
kernel: [17179586.440000] tveeprom 0-0050: has radio
kernel: [17179586.440000] cx88[0]: warning: unknown hauppauge model #34704
kernel: [17179586.440000] cx88[0]: hauppauge eeprom: model=34704
kernel: [17179586.440000] input: cx88 IR (Hauppauge WinTV 34xxx  as /class/input/input3
kernel: [17179586.560000] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
kernel: [17179586.560000] cx88[0]/0: found at 0000:04:01.0, rev: 5, irq: 217, latency: 32, mmio: 0xe5000000
kernel: [17179586.588000] cx88[0]/0: registered device video0 [v4l2]
kernel: [17179586.588000] cx88[0]/0: registered device vbi0
kernel: [17179586.588000] cx88[0]/0: registered device radio0

this is my /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
tda9887
cx88xx


in v4l forums and in the mercury (doesn't know the exactly name) they all write that this model is supportet bx the cx88xx module, once i had all fully functional yesterday i believe it's posible to bring this peace of hardware to work

The model is a Hauppauge WinTV Go2 with FM, i live in Switzerland so it's the same tvnorm as Germany Pal BG/Western Europe

Does nobody have the same Card and could give me some tips?

Or does i miss something here?

maybe lspci?
00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01df (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
04:01.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
04:01.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)


I tried so far, tvtime, xawtv, kdetv, zapping, zapping cvs but all of them did'nt work (as i said before, yesterday the all worked till i rebooted my machine :-( )

best regards
tom

ps please forgive me for my bad english

---

### Post by scto on 2006-11-11
no tips?

---

### Post by scto on 2006-11-11
iv'e found a smal how to do:

[http://jtyr.home.cern.ch/jtyr/wintv_go2.html](http://jtyr.home.cern.ch/jtyr/wintv_go2.html)

but this also doesn't work, i've the same type of card so why this doesn't work?
edgy kernel to old or what could it be?

regards
tom

---

### Post by scto on 2006-11-12
i recived an answer on v4l mailinglist, theres no chance.

only way is hardcoding 2 lines:

core->tuner_type = 56; (of core)
  tun_setup.type = 56; (of i2c)

ok, hmm if i change this i have to recompile my kernel right?
is there a way for only compile the changed module (core/i2c)

thx
tom

---

### Post by scto on 2006-11-12
Filled a launchpad bug:
[https://launchpad.net/distros/ubuntu/+bug/71462](https://launchpad.net/distros/ubuntu/+bug/71462)

---

### Post by scto on 2006-11-13
ok it's solved, i found a solution.

i reported all in launchpad bug number 71462.

downloaded [http://linuxtv.org/hg/](http://linuxtv.org/hg/)

v4l-dvb source tree

made inside the v4l tree a make and a sudo make install

in /etc/modules
tda9887
cx88xx

in /etc/modprobe.d/tvtuner
# i2c
alias char-major-89     i2c-dev
options i2c-algo-bit    bit_test=1
# card
alias char-major-81     videodev
alias char-major-81-0   cx8800


after a reboot my card is regognized and working.
is there a chance that this would be done in standart edgy kernel?

cheers
tom

---

