---
title: "problem with skystar2 on ubuntu 7.10"
date: 2008-04-08
forum: Multimedia &amp; Video
---

### Post by nemanaldin on 2008-04-08
hi
i have problem with my skystar2 2.6d card
on ubntu 
```
Linux  2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```
command: dmesg
```
[ 2643.180000] b2c2-flexcop: i2c master_xfer failed
[ 2643.180000] b2c2-flexcop: i2c master_xfer failed
[ 2643.180000] b2c2-flexcop: i2c master_xfer failed
[ 2643.180000] b2c2-flexcop: i2c master_xfer failed
[ 2643.180000] b2c2-flexcop: i2c master_xfer failed
[ 2643.180000] b2c2-flexcop: i2c master_xfer failed
[ 2644.280000] b2c2-flexcop: i2c master_xfer failed
[ 2644.280000] b2c2-flexcop: i2c master_xfer failed
[ 2644.280000] b2c2-flexcop: i2c master_xfer failed
[ 2644.280000] b2c2-flexcop: i2c master_xfer failed
[ 2644.280000] b2c2-flexcop: i2c master_xfer failed
[ 2644.280000] b2c2-flexcop: i2c master_xfer failed
[ 2644.280000] b2c2-flexcop: i2c master_xfer failed
[ 2644.280000] b2c2-flexcop: i2c master_xfer failed
[ 2644.280000] b2c2-flexcop: i2c master_xfer failed
[ 2644.280000] b2c2-flexcop: i2c master_xfer failed
[ 2644.280000] b2c2-flexcop: i2c master_xfer failed
[ 2644.280000] b2c2-flexcop: i2c master_xfer failed
[ 2644.280000] b2c2-flexcop: i2c master_xfer failed
[ 2644.280000] b2c2-flexcop: i2c master_xfer failed
[ 2645.380000] b2c2-flexcop: i2c master_xfer failed
[ 3240.172000] PPP: VJ decompression error
[ 3692.704000] PPP: VJ decompression error
[ 3703.440000] PPP: VJ decompression error
[ 3703.528000] PPP: VJ decompression error
[ 3703.568000] PPP: VJ decompression error
[ 3703.656000] PPP: VJ decompression error
[ 3703.736000] PPP: VJ decompression error
[ 3703.776000] PPP: VJ decompression error
[ 3703.824000] PPP: VJ decompression error
[ 3703.888000] PPP: VJ decompression error
[ 3703.968000] PPP: VJ decompression error
[ 3704.056000] PPP: VJ decompression error
[ 3704.120000] PPP: VJ decompression error
[ 3704.200000] PPP: VJ decompression error
[ 3716.912000] PPP: VJ decompression error
[ 3716.920000] PPP: VJ decompression error
[ 3722.192000] PPP: VJ decompression error
[ 3726.096000] PPP: VJ decompression error
[ 5265.164000] b2c2-flexcop: i2c master_xfer failed
[ 5265.164000] b2c2-flexcop: i2c master_xfer failed
[ 5265.164000] b2c2-flexcop: i2c master_xfer failed
[ 5265.164000] b2c2-flexcop: i2c master_xfer failed
[ 5265.164000] b2c2-flexcop: i2c master_xfer failed
[ 5265.164000] b2c2-flexcop: i2c master_xfer failed
[ 5265.164000] b2c2-flexcop: i2c master_xfer failed
[ 5265.164000] b2c2-flexcop: i2c master_xfer failed
[ 5265.164000] b2c2-flexcop: i2c master_xfer failed
[ 5265.164000] b2c2-flexcop: i2c master_xfer failed
[ 5265.164000] b2c2-flexcop: i2c master_xfer failed
[ 5265.164000] b2c2-flexcop: i2c master_xfer failed
```
and first when i search channels in kaffeine cant found channels but finally it found 
and when i click on channels kaffeine give error cant tune dvb

when run kaffeine in terminal

```
nemanaldin@nemanaldin:~$ kaffeine
kbuildsycoca running...
0
/dev/dvb/adapter0/frontend0 : opened ( ST STV0299 DVB-S )
/dev/dvb/0/frontend1 : : No such file or directory
Loaded epg data : 0 events (0 msecs)
nemanaldin@nemanaldin:~$ Tuning to: CNBC-e / autocount: 0
DvbCam::probe(): /dev/dvb/adapter0/ca0: : No such file or directory
Using DVB device 0:0 "ST STV0299 DVB-S"
tuning DVB-S to 11892000 h 12800000
inv:2 fecH:5
DiSEqC: switch pos 0, 18V, hiband (index 3)
FE_SET_TONE failed: Connection timed out
DiSEqC: e0 10 38 f3 00 00
FE_DISEQC_SEND_MASTER_CMD failed: Connection timed out
FE_DISEQC_SEND_BURST failed: Connection timed out
FE_SET_TONE failed: Connection timed out
...............

Not able to lock to the signal on the given frequency
Frontend closed
Tuning delay: 3314 ms

``` 
i dont have diseqc 

and when run this command dmesg | grep DVB nothin happen and cant find dvb
but dvb folder in dev exist
how can i fix 
thanks and sorry for my bad english

---

### Post by canadiandude007 on 2008-05-28
Hello,

To resolve the PPP: VJ decompression error, you need to modify the /etc/ppp/options file and add 'novjcomp' to it.

Basically when your system has a high amount of traffic it can lose some frames that will not be decompressed.  So doing the above will switch off the VJ compression so you won't see those errors.  This is internal to the kernel.

---

### Post by canadiandude007 on 2008-05-28
Hello,

To resolve the PPP: VJ decompression error, you need to modify the /etc/ppp/options file and add 'novj' to it.

Basically when your system has a high amount of traffic it can lose some frames that will not be decompressed.  So doing the above will switch off the VJ compression so you won't see those errors.  This is internal to the kernel.

---

