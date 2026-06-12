---
title: "Philips Semiconductors SAA7131 Karmic [Portsmouth UK]"
date: 2010-01-23
forum: Multimedia Software
---

### Post by richardjennings on 2010-01-23
Hello

My experiences with SAA7131 based DVB-T tuner card in Karmic


Firmware is not installed automatically.

```
sudo apt-get install linux-firmware-nonfree
```

(portsmouth uk).. the default rowridge scan file is incorrect. 

/usr/share/dvb/dvb-t/uk-rowridge

I added 1 new line and commented out the others, this magically worked (with this card in these circumstances).

```
sudo gedit /usr/share/dvb/dvb-t/uk-Rowridge
```

> 
# UK, Rowridge
# Auto-generated from [http://www.dtg.org.uk/retailer/dtt_channels.html](http://www.dtg.org.uk/retailer/dtt_channels.html)
# and [http://www.ofcom.org.uk/static/reception_advice/index.asp.html](http://www.ofcom.org.uk/static/reception_advice/index.asp.html)
# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
#T 489833000 8MHz 3/4 NONE QAM16 2k 1/32 NONE
#T 530000000 8MHz 2/3 NONE QAM64 2k 1/32 NONE
#T 545833000 8MHz 2/3 NONE QAM64 2k 1/32 NONE
#T 562167000 8MHz 3/4 NONE QAM16 2k 1/32 NONE
#T 513833000 8MHz 3/4 NONE QAM16 2k 1/32 NONE
#T 570167000 8MHz 3/4 NONE QAM16 2k 1/32 NONE

T 570166670 8MHz 3/4 NONE QAM16 2k 1/32 NONE



Playback with me-tv (apt-get install me-tv) is problamatic. I believe this is entierly due to the useless reception quality I am getting.


Hope this is helpfull to someone.

check out plug for portsmouth linux users group

---

