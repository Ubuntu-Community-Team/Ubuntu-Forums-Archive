---
title: "Sim Card Reader/Memory Card Reader"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by desaivarun_104lts on 2011-04-05
Hi,

Today i bought a sim Card Reader/Memory Card Reader..Ubuntu recognizes my Cannon SD card when i place the card in the reader,and it works perfectly.

The problem is that,when i place M2(Micro MS)card in the card reader,it is not working,also when i kept my mobile SIM in the SIM card Reader,it is also not working.

Any Help will be usefull. Will Sim Card Reader's work in Ubuntu..
Any special driver are needed??

---

### Post by cariboo on 2011-04-05
To do some trouble shooting, open a terminal just after you have inserted one of your and type:

```
dmesg | tail n10
```

the output should look similar to this:

```
dmesg | tail -n10
[ 2884.549721] sd 4:0:0:0: [sdc] Write Protect is off
[ 2884.549726] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 2884.550585] sd 4:0:0:0: [sdc] No Caching mode page present
[ 2884.550590] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 2884.553214] sd 4:0:0:0: [sdc] No Caching mode page present
[ 2884.553219] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 2884.554224]  sdc: **sdc1**
[ 2884.556839] sd 4:0:0:0: [sdc] No Caching mode page present
[ 2884.556846] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 2884.556850] sd 4:0:0:0: [sdc] Attached SCSI removable disk
```

as you can see from the output above my mini memory card is given a device label of /dev/sdc1.

---

### Post by desaivarun_104lts on 2011-04-05
> **cariboo907 said:**
> To do some trouble shooting, open a terminal just after you have inserted one of your and type:

```
dmesg | tail n10
```

the output should look similar to this:

```
dmesg | tail -n10
[ 2884.549721] sd 4:0:0:0: [sdc] Write Protect is off
[ 2884.549726] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 2884.550585] sd 4:0:0:0: [sdc] No Caching mode page present
[ 2884.550590] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 2884.553214] sd 4:0:0:0: [sdc] No Caching mode page present
[ 2884.553219] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 2884.554224]  sdc: **sdc1**
[ 2884.556839] sd 4:0:0:0: [sdc] No Caching mode page present
[ 2884.556846] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 2884.556850] sd 4:0:0:0: [sdc] Attached SCSI removable disk
```

as you can see from the output above my mini memory card is given a device label of /dev/sdc1.
hi @carib00907

I tried the command you given to me.The output is


tail: cannot open `n10' for reading: No such file or directory

Any other commands to check?

---

