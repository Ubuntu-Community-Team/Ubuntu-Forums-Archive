---
title: "DVB tunes in windows but not Ubuntu"
date: 2010-05-03
forum: Multimedia Software
---

### Post by prju68 on 2010-05-03
HI

I am running Karmic, and have two DVB-T tuners which are insight of the Crystal Palace transmitter in London.

If I tune the DVB sticks in Windows 7 I get all the channels on all the frequencies that Crystal pallace is transmitting on.  If I tune on Ubuntu only a few of the frequencies actually work. Which means I am missing good channels like the BBC and Film 4.

What am I doing to tune:

> scan /usr/share/dvb/dvb-t/uk-CrystalPalaceI have checked the CrytalPlace frequencies and these seem to be correct, but the tuning fails like this..

> >>> tune to: 505833000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!This should be MUX1. 

 I have confirmed this by scanning in windows which works fine.

> Frequency (As Locked) = 506000kHz

Frequency of Parent Transmitter  = 505833kHz

Network/Region Name = London.
Freeview Multiplex  = Mux 1
#Relay transmitter frequencies
#Network_2("London.", 697833, 8, 1)
#Network_2("London.", 690166, 8, 1)
#Network_2("London.", 554000, 8, 1)


Channel Name           LCN   SID    Vid   Aud   PMT
-------------------------------------------------------------------
CBBC Channel        ,   70, 4671,  620,   621, 4671    #
CBBC Channel        ,     , 4671,  620,   622, 4671    #
BBC NEWS            ,   80, 4415,  640,   641, 4415    #
BBC TWO             ,    2, 4228,  610,   611, 4228    #
BBC TWO             ,     , 4228,  610,   612, 4228    #
BBC ONE             ,    1, 4164,  600,   601, 4164    #
BBC ONE             ,     , 4164,  600,   602, 4164    #


# Signal Strength = 22
# Signal Quality  = 100%If I run w_scan in attempt to get a list of frequencies this pulls up the following:

> # T[2] <freq> <bw> <fec_hi> <fec_lo> <mod> <tm> <guard> <hi> [# comment]
#------------------------------------------------------------------------------
T 481833330 8MHz  2/3 NONE    QAM64   2k 1/32 NONE      # London.
T 697833330 8MHz  3/4 NONE    QAM16   2k 1/32 NONE
T 634166670 8MHz  2/3 NONE    QAM64   2k 1/32 NONE
T 714166670 8MHz  3/4 NONE    QAM16   2k 1/32 NONE
T 578166670 8MHz  3/4 NONE    QAM16   2k 1/32 NONE      # London.
T 738000000 8MHz  3/4 NONE    QAM16   2k 1/32 NONE
T 697833330 8MHz  3/4 NONE    QAM16   2k 1/32 NONE
T 634166670 8MHz  2/3 NONE    QAM64   2k 1/32 NONE
T 714166670 8MHz  3/4 NONE    QAM16   2k 1/32 NONEWhich does not give me the all the CrystalPalace frequencies. I'm guessing the extra ones are from another transmitter.

So my Uk-CrystalPalace file is correct, but I cannot tune and generate the Channels.conf. I know my DVB sticks are fine because they work in windows.
So what am I missing? Surely there are plenty of other people in london where it is working fine.

My DVB sticks are a Compro U80. Which is a bit of pain under linux as its a combination of a RTL2831u and QT1010 for which I had to compile the drivers the other is a cheapo afatech job that works without any effort.

Any suggestions would be gratefully received.

Peter

---

### Post by ugnius40 on 2010-10-27
Hi,

Sorry to bump old thread, but I'm also having same exact problem, did anyone had any success with Compro U80? I've tried Jan Hoogenraads driver [http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2]("http://linuxtv.org/hg/%7Ejhoogenraad/rtl2831-r2") it does compile, but does not seem to tune, I've been explained U80 uses QT1010 tuner and needs this [http://linuxtv.org/hg/~anttip/qt1010/]("http://linuxtv.org/hg/%7Eanttip/qt1010/") branch. But it does not compile for me. 
I've also tried [http://linuxtv.org/hg/~anttip/rtl2831u/]("http://linuxtv.org/hg/%7Eanttip/rtl2831u/") driver, which failed to compile with same error as qt1010 branch (something about missing linux/autoconf.h).

Any Ideas what to try next, apart from waiting another year?

---

### Post by Elfantin on 2011-05-19
Better late than never?

I think the problem is with the QT1010, which is the tuner. I have a KWorld DVB-T KW-D-395U, which has a QT1010 as a tuner and a AF9013/15 as a USB bridge/demodulator. I was all happy until with the DSO they have changed the frequency for BBC and [I haven't been able to tune]("http://ubuntuforums.org/showthread.php?p=10769738#post10769738") to the SandyHeath transmitter.
My personal impression is that there is no solution (except fixing the drivers).
So, well, this is not a solution. Alas, I now have two USB sticks that don't work...

---

### Post by sosasami on 2011-12-05
Anyone found a solution to this?

I have a Kworld 395U and I am unable to find any channels whatsoever.

any help would be much appreciated.

---

### Post by BicyclerBoy on 2011-12-05
KWorld 395U is the same as one of..
[http://linuxtv.org/wiki/index.php/Afatech_AF9015](http://linuxtv.org/wiki/index.php/Afatech_AF9015)

kernel 2.6.29 or later needed. (Lucid or later).

Do you have linux-firmware (& non-free firmware) package installed ?
Use synaptic package manager & check/install.

in terminal
dmesg | grep firmware
dmesg | grep dvb

---

