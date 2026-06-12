---
title: "Can not scan TBS 6891 cards"
date: 2012-09-01
forum: Mythbuntu
---

### Post by Billsputters on 2012-09-01
Following my earlier problems wirth kernel updates etc. I now have a working set of cards

except

I can not for the life of me get the the backend to scan for channels

scan -x0 works and pulls in the expected list of channels, so I guess it is safe to assume the card works and has a signal

I have the LNB set (used the <Alt F> <esc> <Alt F> sequence to make it stick

Starting with the usual suspect of 10714000 freq, etc as per the norm. It goes to the next scan page, get 74% signal strength, 92% s/n and locks to the channel. After 5 secs or so, it informs me it can't find any new channels! Yet I have none defined for that card. 

Really stuck now and grasping at straws.

---

### Post by nickrout on 2012-09-01
> **Billsputters said:**
> Following my earlier problems wirth kernel updates etc. I now have a working set of cards

except

I can not for the life of me get the the backend to scan for channels

scan -x0 works and pulls in the expected list of channels, so I guess it is safe to assume the card works and has a signal

I have the LNB set (used the <Alt F> <esc> <Alt F> sequence to make it stick

Starting with the usual suspect of 10714000 freq, etc as per the norm. It goes to the next scan page, get 74% signal strength, 92% s/n and locks to the channel. After 5 secs or so, it informs me it can't find any new channels! Yet I have none defined for that card. 

Really stuck now and grasping at straws.

What is wrong with your previous scan? (I assume from your posts you are upgrading in some way, so you will still have your database intact).

---

### Post by Billsputters on 2012-09-01
I deleted all input cards, for some reason I could not scan on second TBS channel. This was traced to the problem of cards coming up in different orders upon bootup. 

Having been through the process many many times before, I was not worried about taking all inputs away and adding them again in the correct order. I never learn!

Never had this trouble before.

If I try and add a previous scan, it say it found 400+ new channels, similar of unused transports. I add them, but they never appear.

Looking directly at the db there is nothing added channelwise for these cards. 

Is it possible for the LNB to not be switched on in the Diseq section even though it claims it is?

---

### Post by nickrout on 2012-09-01
> **Billsputters said:**
> I deleted all input cards, for some reason I could not scan on second TBS channel. This was traced to the problem of cards coming up in different orders upon bootup. 

Having been through the process many many times before, I was not worried about taking all inputs away and adding them again in the correct order. I never learn!

Never had this trouble before.

If I try and add a previous scan, it say it found 400+ new channels, similar of unused transports. I add them, but they never appear.

Looking directly at the db there is nothing added channelwise for these cards. 

Is it possible for the LNB to not be switched on in the Diseq section even though it claims it is?

I have found that to be the case at times. Look in the logs too.

---

### Post by Billsputters on 2012-09-01
OK, had a look at the logs. I get this

DVBChan(117:/dev/dvb/adapter_tbs1/frontend0): Opening DVB frontend device failed. eno: Device or resource busy (16)

---

### Post by nickrout on 2012-09-02
> **Billsputters said:**
> OK, had a look at the logs. I get this

DVBChan(117:/dev/dvb/adapter_tbs1/frontend0): Opening DVB frontend device failed. eno: Device or resource busy (16)

permissions perhaps?

---

### Post by Pantera116 on 2012-09-02
I am succesfully using a TBS 6981 card as well as a TBS 6280 DVB-T2 card.
It is neccessary, with this combination of cards, to set up entries in 
/etc/modprobe.d/dvb.conf to define fixed adapter numbers.

options cx23885 adapter_nr2,3

this entry fixes the 6981 card to adaptors 2 and 3.

If i dont do this it attempts to tune a sat card to uhf frequecies ( and vice versa) if the cards are given different adaptor numbers on boot.

I often block kernel updates as it means reinstalling the proprieary tbs driver. 

How up to date is your kernel and driver?

---

### Post by Billsputters on 2012-09-02
Ok set me thinking the permissions route.

Have set up udev rules for the two input cards, to stop the problem of them moving around upon a reboot

```
# /etc/udev/rules.d/10-dvb.rules
#
# To Ientify serial nos etc for a Device call
# udevadm info -a -p $(udevadm info -q path -n /dev/dvb/adapter0/frontend0)
#
                                    
# Create a symlinks for both tuners of TBS device
SUBSYSTEM=="dvb", ATTRS{vendor}=="0x14f1", ATTRS{subsystem_vendor}=="0x6981", ENV{tbs}!="two", ENV{tbs}="two", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter_tbs1/%%s $${K#*.}'", SYMLINK+="%c"
SUBSYSTEM=="dvb", ATTRS{vendor}=="0x14f1", ATTRS{subsystem_vendor}=="0x6981", ENV{tbs}=="two", ENV{tbs}="one", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter_tbs2/%%s $${K#*.}'", SYMLINK+="%c"

# Create a symlinks for both tuners of Hauppauge Nova-T device
SUBSYSTEM=="dvb", ATTRS{idVendor}=="2040", ATTRS{idProduct}=="8400", ENV{nova}!="two", ENV{nova}="two", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter_hp1/%%s $${K#*.}'", SYMLINK+="%c"
SUBSYSTEM=="dvb", ATTRS{idVendor}=="2040", ATTRS{idProduct}=="8400", ENV{nova}=="two", ENV{nova}="one", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter_hp2/%%s $${K#*.}'", SYMLINK+="%c"

```

Which then gives me this lineup
```
/dev/dvb/adapter_hp1:
total 0
drwxr-xr-x  2 root root 120 Sep  2 18:12 .
drwxr-xr-x 10 root root 200 Sep  2 18:12 ..
lrwxrwxrwx  1 root root  18 Sep  2 18:12 demux0 -> ../adapter2/demux0
lrwxrwxrwx  1 root root  16 Sep  2 18:12 dvr0 -> ../adapter2/dvr0
lrwxrwxrwx  1 root root  21 Sep  2 18:12 frontend0 -> ../adapter2/frontend0
lrwxrwxrwx  1 root root  16 Sep  2 18:12 net0 -> ../adapter2/net0

/dev/dvb/adapter_hp2:
total 0
drwxr-xr-x  2 root root 120 Sep  2 18:12 .
drwxr-xr-x 10 root root 200 Sep  2 18:12 ..
lrwxrwxrwx  1 root root  18 Sep  2 18:12 demux0 -> ../adapter2/demux0
lrwxrwxrwx  1 root root  16 Sep  2 18:12 dvr0 -> ../adapter2/dvr0
lrwxrwxrwx  1 root root  21 Sep  2 18:12 frontend0 -> ../adapter2/frontend0
lrwxrwxrwx  1 root root  16 Sep  2 18:12 net0 -> ../adapter2/net0

/dev/dvb/adapter_tbs1:
total 0
drwxr-xr-x  2 root root 120 Sep  2 18:12 .
drwxr-xr-x 10 root root 200 Sep  2 18:12 ..
lrwxrwxrwx  1 root root  18 Sep  2 18:12 demux0 -> ../adapter3/demux0
lrwxrwxrwx  1 root root  16 Sep  2 18:12 dvr0 -> ../adapter3/dvr0
lrwxrwxrwx  1 root root  21 Sep  2 18:12 frontend0 -> ../adapter3/frontend0
lrwxrwxrwx  1 root root  16 Sep  2 18:12 net0 -> ../adapter1/net0

/dev/dvb/adapter_tbs2:
total 0
drwxr-xr-x  2 root root 120 Sep  2 18:12 .
drwxr-xr-x 10 root root 200 Sep  2 18:12 ..
lrwxrwxrwx  1 root root  18 Sep  2 18:12 demux0 -> ../adapter3/demux0
lrwxrwxrwx  1 root root  16 Sep  2 18:12 dvr0 -> ../adapter3/dvr0
lrwxrwxrwx  1 root root  21 Sep  2 18:12 frontend0 -> ../adapter3/frontend0
lrwxrwxrwx  1 root root  16 Sep  2 18:12 net0 -> ../adapter1/net0


```

Two errors evident here.

The DVB-T card (hp1 & hp2) point to the same adapter, which on this present boot is not a problem, but may change with the next boot.

And the DVB-S card (tbs1 & tbs2) are exactly the same, pointing to the same card, except the net0 link points to a different card! 

So that would seem to be where the error lies (I did manage a scan using the target of the links adapter1, and that worked, so sort of backs up my theory.

---

