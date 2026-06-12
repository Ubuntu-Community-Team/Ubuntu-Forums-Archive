---
title: "Got Nova-T stick recognised, but still won't work"
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by Digital Spaghetti on 2007-05-24
I know the mystery of the Hauppage Nova-T stick has been going on for a while - but today I managed with some success to get Feisty to recognise it.  Here are some results:

```

digitalspaghetti@tane-laptop:~$ dmesg|grep -i dvb
[   18.004000] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[   18.055000] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-01.fw'
[   18.744000] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   18.744000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   18.744000] DVB: registering new adapter (Hauppauge Nova-T Stick)
[   18.948000] DVB: registering frontend 0 (DiBcom 7000PC)...
[   19.425000] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[   19.425000] usbcore: registered new interface driver dvb_usb_dib0700

```

So I've installed Kaffine and it recognizes the card.  I've tried 3 scan types (Auto, UK-Craigkelly and UK-Blackhill).  The problem with Kaffine is it would not let me tune into the stations it foun.

Running some dvb-utils gives me these results:

```

digitalspaghetti@tane-laptop:~$ femon
using '/dev/dvb/adapter0/frontend0'
FE: DiBcom 7000PC (TERRESTRIAL)
status 01 | signal 1d2f | snr 0000 | ber 001fffff | unc 00000000 |
status 01 | signal 1d2f | snr 0000 | ber 001fffff | unc 00000000 |
status 01 | signal 1d2f | snr 0000 | ber 001fffff | unc 00000000 |
status 01 | signal 1d2f | snr 0000 | ber 001fffff | unc 00000000 |
status 01 | signal 1d2f | snr 0000 | ber 001fffff | unc 00000000 |
status 01 | signal 1d2f | snr 0000 | ber 001fffff | unc 00000000 |
status 01 | signal 1d2f | snr 0000 | ber 001fffff | unc 00000000 |
status 01 | signal 1d2f | snr 0000 | ber 001fffff | unc 00000000 |

```

However, when I run scan I get this error:

```

digitalspaghetti@tane-laptop:~$ scan -c
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
dumping lists (0 services)
Done.

```

When i restart it does seem to work, sometimes, but then it has ongoing problems.  I'm using the latest v4l-experimental drivers, and I have the latest firmware.  Running on 7.04 on a Advent 7111 Laptop.

---

### Post by manicminer on 2007-05-28
There seem to be various known problems with this hardware and the latest drivers, I remember reading somewhere that the support was broken recently for scanning and auto-detect :( but I cannot find a reference.

There have been lots of posts of the linux-dvb mailing list, the maintainer knows there are issues but it seems to be taking a while to fix. There are fairly regular posts on the dvb mailing list about problems but no solutions as yet.

I have a "just about working" based on the 2.6.19 kernel on my system. I was thinking of upgrading to fiesty but given this report I don't think I will!

I just about get support from xine / mplayer, most other apps fail for me.

Sorry this isn't a more positve reply :(

---

### Post by SoberKing on 2007-05-28
I have a Nova-T stick running fine under Feisty (and using the Blackhill transmitter being only 20 miles from Edinburgh..). Having a look at my dmesg output I notice one difference between yours and mine:

```
stuart@alice:/lib/firmware$ dmesg|grep -i dvb
[   28.520000] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[   29.192000] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-01.fw'
[   29.884000] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   29.884000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   29.884000] DVB: registering new adapter (Hauppauge Nova-T Stick).
[   30.120000] DVB: registering frontend 0 **(DiBcom 7000MA/MB/PA/PB/MC)**...
[   30.644000] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[   30.644000] usbcore: registered new interface driver dvb_usb_dib0700

```

What I did to setup was copy the firmware (which you obviously have) and compile whatever version of the V4L drivers that were latest at the time of the Feisty release. Don't really understand how all this works, but it may be due to the line above being different (and therefore possibly wrong at your end).

---

