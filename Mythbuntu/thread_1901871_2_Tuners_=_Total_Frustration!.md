---
title: "2 Tuners = Total Frustration!"
date: 2011-12-29
forum: Mythbuntu
---

### Post by MickSulley on 2011-12-29
I have two tuner cards - 
KWorld DVBT PC160-2T PCI for Freeview
TBS Dual DVB-S2 (TBS6981) for FreeSat

Both are dual channel.

I had some problems getting them both to work but a few days ago I deleted them and started again and they both worked - fine!  I had -
/dev/dvb/adapter0/frontend0 as Freeview0
/dev/dvb/adapter0/frontend1 as Freeview1
/dev/dvb/adapter0/frontend2 as FreeSat0
/dev/dvb/adapter0/frontend3 as FreeSat1

Yesterday Freeview stopped working, couldn't receive anything on either channel, I tried scanning and there was zero signal strength on both channels so I power cycled it and tried to scan Freeview again.  Freeview0 scanned OK, but when I tried Freeview1 it showed a satelite setup screen.  When I investigated it has changed the assignments, I now have Freeview on 0 and 2 and FreeSat on 1 and 3.  How does that happen???? Does this mean that after a power cycle it randomly assigns tuner cards?

I am getting so frustrated with Myth that I am seriously considering defecting to Windows, and I never thought I would say that.

Can anyone help please?  How do I stop it randomly assigning cards?  How do I stop my KWorld card loosing its channels?

Running Ubuntu 11.10 64 bit.

Thanks
Mick

---

### Post by ian dobson on 2011-12-29
Hi,

Yes the order of tuners can change.

Have a search here in the forums for tuner + udev, there you'll find a script that allows you to create a hardwired name for each tuner that doesn't change.

you need something along the lines of :-
KERNEL=="video*", SYSFS{vendor}=="0x109e", SYSFS{device}=="0x036e", SYMLINK+="video/bttv"
KERNEL=="video*", SYSFS{vendor}=="0x046d", SYSFS{device}=="0x092e", SYMLINK+="video/webcam"

in a udev rules file.

or if the module support device number then you could force one driver to number 0 and the other to 1 (check what the module drivers support)


Regards
Ian Dobson

---

### Post by MickSulley on 2011-12-29
OK I have tried that, after a fair bit of trial and error I got it to work, the code i have used is 
```
# /etc/udev/rules.d/10-local.rules
#
# To Identify serial nos etc for a Device call
#
#

# Create symlinks for both tuners of afatech device KWorld DVBT PC160-2T
SUBSYSTEM=="dvb", ATTRS{manufacturer}=="Afatech", ENV{afatech}!="two", ENV{afatech}="two", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter_kw1/%%s $${K#*.}'", SYMLINK+="%c"
SUBSYSTEM=="dvb", ATTRS{manufacturer}=="Afatech", ENV{afatech}=="two", ENV{afatech}="one", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter_kw2/%%s $${K#*.}'", SYMLINK+="%c"

# Create symlinks for both tuners of TBS device TBS Dual DVB-S2 (TBS6981) High Definition Digital Satellite Tuner PCI Express Card HD (DVB-S2/DVB-S) Receiver

SUBSYSTEM=="dvb", ATTRS{vendor}=="0x14f1", ATTRS{device}=="0x8852", ENV{tbs}!="two", ENV{tbs}="two", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter_tbs1/%%s $${K#*.}'", SYMLINK+="%c"
SUBSYSTEM=="dvb", ATTRS{vendor}=="0x14f1", ATTRS{device}=="0x8852", ENV{tbs}=="two", ENV{tbs}="one", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter_tbs2/%%s $${K#*.}'", SYMLINK+="%c"

```
But I now see -
adapter0
adapter1
adapter2
adapter3
adapter_kw1
adapter_kw2
adapter_tbs1
adapter_tbs2

Do I need to do something else to stop the original assignments happening?

I did try to scan adapter_kw1 and got nothing, but adapter0 still works.  I also noted that the original adapters directories have a timestamp a second earlier that the new ones.

---

### Post by ian dobson on 2011-12-30
Hi,

The original devices should remain as they are/want to be. You just need to tell mythbackend to use the "linked" names (adapter_kw1/adapter_tbs1). So no matter what device name linux creates mythtv always uses the correct device for the correct source.

By the way, there's no point threatening to go back to windows, no one cares.

Regards
Ian Dobson

---

### Post by MickSulley on 2011-12-30
Thanks for your help Ian, I do appreciate it.  The satellite channels worked OK but I had to power cycle the machine to get the Freeview to work with the new links.  

Just in case anyone else comes across this thread, when looking for details for the rules I thought I had found an attribute to distinguish between the two channels on the KWorld tuner, ATTRS{urbnum}, but could get the rule to work and then discovered that this attribute has a different value each time you boot, so not useful at all:)

---

### Post by ian dobson on 2011-12-30
Hi,

So the problem is solved? If yes mark the thread as SOLVED.

Regards, and a happy new year
Ian Dobson

---

