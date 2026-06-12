---
title: "Trusty 14.04 upgrade and unable to setup DVB capture cards"
date: 2014-05-03
forum: Mythbuntu
---

### Post by Bob_Gardner on 2014-05-03
Hi,
 I have a kubuntu 14.04 setup, upgraded from 12.04, which did run mythtv flawlessly. On upgrading however, I can't set up the capture cards. I have a Hauppage PCI/USB card, which the kernal sees fine, dmesg produces
```

[   19.125317] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[   19.210924] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   20.260214] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   20.260340] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   20.743138] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   21.176287] dvb-usb: schedule remote query interval to 50 msecs.
[   21.176295] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   21.177784] usbcore: registered new interface driver dvb_usb_dib0700

```

The frontend devices are all present
```

mythtv@cuthred:~$ ls -l /dev/dvb/adapter*
/dev/dvb/adapter0:
total 0
crw-rw----+ 1 root video 212, 0 May  3 04:00 demux0
crw-rw----+ 1 root video 212, 1 May  3 04:00 dvr0
crw-rw----+ 1 root video 212, 3 May  3 04:00 frontend0
crw-rw----+ 1 root video 212, 2 May  3 04:00 net0

/dev/dvb/adapter1:
total 0
crw-rw----+ 1 root video 212, 4 May  3 04:00 demux0
crw-rw----+ 1 root video 212, 5 May  3 04:00 dvr0
crw-rw----+ 1 root video 212, 7 May  3 04:00 frontend0
crw-rw----+ 1 root video 212, 6 May  3 04:00 net0


```

Permissions are as they should be, both my personal account and mythtv are members of the video group, so permissions arn't the problem. Tools such as femon and dvbsnoop work ok

```

mythtv@cuthred:~$ dvbsnoop -s feinfo     
dvbsnoop V1.4.50 -- http://dvbsnoop.sourceforge.net/ 

---------------------------------------------------------
FrontEnd Info...
---------------------------------------------------------

Device: /dev/dvb/adapter0/frontend0

Basic capabilities:
    Name: "DiBcom 7000PC"
    Frontend-type:       OFDM (DVB-T)
    Frequency (min):     45000.000 kHz
    Frequency (max):     860000.000 kHz
    Frequency stepsiz:   62.500 kHz
    Frequency tolerance: 0.000 kHz
    Symbol rate (min):     0.000000 MSym/s
    Symbol rate (max):     0.000000 MSym/s
    Symbol rate tolerance: 0 ppm
    Notifier delay: 0 ms
    Frontend capabilities:
        auto inversion
        FEC 1/2
        FEC 2/3
        FEC 3/4
        FEC 5/6
        FEC 7/8
        FEC AUTO
        QPSK
        QAM 16
        QAM 64
        QAM AUTO
        auto transmission mode
        auto guard interval
        auto hierarchy

Current parameters:
    Frequency:  778000.000 kHz
    Inversion:  AUTO
    Bandwidth:  8 MHz
    Stream code rate (hi prio):  FEC 1/2
    Stream code rate (lo prio):  FEC 1/2
    Modulation:  QPSK
    Transmission mode:  2k mode
    Guard interval:  1/32
    Hierarchy:  none

mythtv@cuthred:~$ femon -H -a0
FE: DiBcom 7000PC (DVBT)
status S     | signal  56% | snr   1% | ber 2097151 | unc 0 | 
status S     | signal  56% | snr   1% | ber 2097151 | unc 0 | 
status S     | signal  56% | snr   1% | ber 2097151 | unc 0 | 
status S     | signal  56% | snr   1% | ber 2097151 | unc 0 |


``` 

But in mythtv backend setup, add capture card it says Frontend ID: Could not get card info for card /dev/dvb/adaptor0/frontend0 Subtype: Unknown error

This appears to have been a common problem, threads on this issue go back many years and a number of solutions have been proposed, none of which work here. Permissions has been sorted, running femon whilst adding a card has been tried, as per

[https://bbs.archlinux.org/viewtopic.php?id=158027](https://bbs.archlinux.org/viewtopic.php?id=158027)

Any ideas? Any thoughts on why this problem has existed for years without mythtv or Ubunto sorting it?

Grateful for any advice,

Thanks.

---

### Post by blm-ubunet on 2014-05-03
Did you try "delete all capture cards on** all hosts**" from the mythtv-setup?
And then try to re-add cards.
Is your BE user (mythtv) a member of the video group?

I thought the femon workaround was just for scanning dvb multiplexes/channels..

Due to local frequency restack & added mux, I had to re-scan (x3) a nova-T-500 by selecting "rescan existing transports" (with find new transports ticked).
 This was successful without using femon hack but using kernel/v4l-dvb from 10.04.

---

### Post by Bob_Gardner on 2014-05-03
Hi blm, thank you, I hadn't tried deleting from all hosts - but I have now, and it made no difference :(, and yes, the mythtv user is a member of video, as my personal account is.

I'm using the latest kernel, 3.13.0-24-generic.

---

### Post by blm-ubunet on 2014-05-03
Are you sure the backend has stopped (before starting mythtv-setup) ?

```
sudo service mythtv-backend [status | stop | start]
```
The [ | ] list means use one.. 

You're not trying to run mythtv-setup as root user ? (very bad thing).
Need to see some log files..

---

### Post by Bob_Gardner on 2014-05-05
Solved - I gace up in the end and uninstalled mythtv's backend and front end, and reinstalled. All worked jusr right after that :p

Thank you for your help.

---

