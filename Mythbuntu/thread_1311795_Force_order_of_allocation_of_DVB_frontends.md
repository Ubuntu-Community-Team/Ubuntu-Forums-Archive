---
title: "Force order of allocation of DVB frontends"
date: 2009-11-02
forum: Mythbuntu
---

### Post by stureid on 2009-11-02
I am running Karmic with a dual DVB-T adaptor and a DVB-S2 adaptor.  My problem is that the DVB hardware is not allocated the same frontend ID each time the system boots.

Sometimes the DVB-T card is allocated frontends 0 and 1 with the DVB-S2 card being frontend 2, and sometimes the DVB-T card is frontends 0 and 2, with the DVB-S2 card being frontend 1.

Is there a way to force adaptors to be allocated fixed frontend IDs?  Failing that, could I delay the DVB-S2 card from being allocated until the DVB-T card has been done?

Hope this makes sense - I'm getting better with linux troubleshooting but I'm still quite new to it.

My DVB-T card is an Afatech AF9013 and the DVB-S2 card is a Hauppauge 4000.

Thanks in advance.

---

### Post by Neon Dusk on 2009-11-02
The module for your DVB card should have a parameter to set the adapter number. 
i.e. I've got a Nova-T 500 (dual DVB-T), NOVA HD S2 (DVB-S2), and Twinhan (DVB-T) cards so I've created a /etc/modprobe.d/options-dvb.conf file containing :-
```

#set nova 500 adapter
options dvb_usb_dib0700 adapter_nr=0,1

#set Nova HD S2 adpater
options cx88_dvb adapter_nr=2

#set Twinhan adapter
options dvb_usb_vp7045 adapter_nr=3


```

---

### Post by pootle1 on 2009-11-03
Ooh! just been trying to make this work, the strange thing is adapter_nr for the Nova-T seems to have no effect, but turning on LNA is working OK.  since the DVB-S card behaves though I'm now getting consistent numbers:
```
# turn on the low noise amp in the nova-t tuner
options dvb-usb-dib0700 force_lna_activation=1

# turn off autosuspend on the card as well
options usbcore autosuspend=-1

# try to force nova-t numbers up high to get consistent names
options dvb_usb_dib0700 adapter_nr=8,9

#try to force dvb-s card to higher number
options cx88_dvb adapter_nr=6

```and after reboot I get:

```
ls /dev/dvb
adapter0  adapter1  adapter6

```

---

### Post by Neon Dusk on 2009-11-03
> 
options dvb_usb_dib0700 adapter_nr=8,9

From doing a bit testing it seems that the max allowed value for adapter_nr is 7

---

### Post by pootle1 on 2009-11-04
> **Neon Dusk said:**
> From doing a bit testing it seems that the max allowed value for adapter_nr is 7

That seems to be it, changed the numbers to 4,5 and all is well, thanks.

---

### Post by SiHa on 2009-11-16
> **Neon Dusk said:**
> The module for your DVB card should have a parameter to set the adapter number. 
i.e. I've got a Nova-T 500 (dual DVB-T), NOVA HD S2 (DVB-S2), and Twinhan (DVB-T) cards so I've created a /etc/modprobe.d/options-dvb.conf file containing :-
```

#set Nova 500 adapter
options dvb_usb_dib0700 adapter_nr=0,1

#set Nova HD S2 adpater
options cx88_dvb adapter_nr=2

#set Twinhan adapter
options dvb_usb_vp7045 adapter_nr=3
```

Thanks, that fized it for me as well:
```
#set Nova-T 500 adapter
options dvb_usb_dib0700 adapter_nr=1,2

#set Nova-S adpater
options budget_ci adapter_nr=0
```

---

### Post by stureid on 2009-11-21
> **Neon Dusk said:**
> The module for your DVB card should have a parameter to set the adapter number. 
i.e. I've got a Nova-T 500 (dual DVB-T), NOVA HD S2 (DVB-S2), and Twinhan (DVB-T) cards so I've created a /etc/modprobe.d/options-dvb.conf file containing :-
```

#set nova 500 adapter
options dvb_usb_dib0700 adapter_nr=0,1

#set Nova HD S2 adpater
options cx88_dvb adapter_nr=2

#set Twinhan adapter
options dvb_usb_vp7045 adapter_nr=3


```

Thanks Neon, that did the trick!

---

### Post by My Name on 2010-02-14
How do you know what ubuntu calls your DVB cards?

I need to stop my DVB-s and DVB-t cards from wondering.

---

### Post by Neon Dusk on 2010-02-14
What cards do you have?

'dmesg | grep dvb' should show useful info along with 'lsmod' & 'modinfo NAME_OF_MODULE'

---

### Post by My Name on 2010-02-14
i have found the id of the other cards using a little trial and error but the card i am strugglinh with is the nova-t 909.

---

### Post by Neon Dusk on 2010-02-14
There's a number of different nova-t [versions](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T_PCI)

'dmesg | grep dvb' should show what driver your card is using.

---

### Post by rbsdude on 2010-05-31
Hello ,

I have two cards , one a dvbt other a dvbs2 , both conexant chipsets but different manufacturers ,that use cx88_dvb driver . How to make sure that dvbs2 is adapter 0 and dvbt adapter 1 ?


Best Regards
RD

---

### Post by Neon Dusk on 2010-05-31
You'll need to use udev see [thread=1334173]dvb card order[/thread]

---

