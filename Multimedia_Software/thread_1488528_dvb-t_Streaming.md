---
title: "dvb-t Streaming"
date: 2010-05-20
forum: Multimedia Software
---

### Post by slice16 on 2010-05-20
Hello All,

I have been tasked with setting up a video streaming server to stream the world cup to a number of machines in our office. I would prefer to use a ubuntu solution as we don't want to worry about software licensing. At present, I only have a dvb-t Nova-t 700xxx and it doesnt show up with lsusb.

Is there a list of supported dvb cards?

Thanks in advance,

Paul

---

### Post by xc3RnbFO8P on 2010-05-20
> Is there a list of supported dvb cards?
[http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices]("http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices")
> I only have a dvb-t Nova-t 700xxx and it doesnt show up with lsusb.
If you can plugit in to Windows computer and warm it up, then plug it in to Ubuntu and show the output of:
> dmesg

---

### Post by slice16 on 2010-05-20
Thanks Ringi, my card shows on there, so this could be interesting. I will let you know how it goes. 

Thanks,

Paul

---

### Post by slice16 on 2010-06-02
Hi Ringi,

I have now installed the firmware and dvb-t utils and an output of dmesg shows my nova-t card is initiated and working. I am now using dvbt tools to scan for all my channels and output them to ~/channels.conf. I use the following command:

```

sudo scan /usr/share/dvb/dvb-t/uk-WinterHill -o zap tee ~/channels.conf

```

This starts the scan, but on each channel, I get the following error:

```

tune to: 626000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

At first I thought it was something to do with signal, but have tried the card on a fixed aerial to no avail.

Do you have any ideas how I can tune in the channels?

Thanks

---

### Post by slice16 on 2010-06-02
Sorted :) the uk-WinterHill file that comes with dvb-apps has the wrong frequencies as they changed back in december. To fix, I needed to delete all freqencies in uk-WinterHill so that it now reads:

```
# UK, Winter Hill
# Auto-generated from http://www.dtg.org.uk/retailer/dtt_channels.html
# and http://www.ofcom.org.uk/static/reception_advice/index.asp.html
# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
T 746000000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
T 770000000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
T 778000000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
T 794000000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
T 801833000 8MHz 2/3 NONE QAM64 8k 1/32 NONE

```

One that is edited, simply run:

```

scan /usr/share/dvd/dvb-t/uk-WinterHill > ~/channels.conf

```

After a short time, that will populate all tuning information in /home/<username>/channels.conf. To play these in vlc, simple run:

```

vlc ~/channels.conf

```

Jobs a gooden :)

Now all I have to do is work out streaming :)

---

### Post by momist on 2010-08-03
> **slice16 said:**
> Sorted :) the uk-WinterHill file that comes with dvb-apps has the wrong frequencies as they changed back in december. To fix, I needed to delete all freqencies in uk-WinterHill so that it now reads:

Hmmm,  This didn't work for me, in the South Ribble area for Winter Hill.  I've constructed my own as follows:

```
# UK, Winter Hill
# created from http://igorfuna.com/dvb-t/digital/tv-channel-frequencies
# by ims 3-Aug-2010

T 802167000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
T 778167000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
T 770167000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
T 794167000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
T 746167000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
```

I hope that helps someone else ;)

---

