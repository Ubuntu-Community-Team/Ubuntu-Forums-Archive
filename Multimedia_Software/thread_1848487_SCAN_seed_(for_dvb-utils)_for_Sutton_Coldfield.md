---
title: "SCAN seed (for dvb-utils) for Sutton Coldfield"
date: 2011-09-22
forum: Multimedia Software
---

### Post by macey on 2011-09-22
Hello,
since digital cutover on S/C transmitter (21st Sep), the seed file supplied with DVB-UTILS is out of date. 

Current file:-

[I]/usr/share/dvb/dvb-t/uk-SuttonColdfield

# UK, Sutton Coldfield
# Auto-generated from [http://www.dtg.org.uk/retailer/dtt_channels.html](http://www.dtg.org.uk/retailer/dtt_channels.html)
# and [http://www.ofcom.org.uk/static/reception_advice/index.asp.html](http://www.ofcom.org.uk/static/reception_advice/index.asp.html)
# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
T 634167000 8MHz 3/4 NONE QAM16 2k 1/32 NONE
T 658167000 8MHz 2/3 NONE QAM64 2k 1/32 NONE
T 682167000 8MHz 2/3 NONE QAM64 2k 1/32 NONE
T 714167000 8MHz 3/4 NONE QAM16 2k 1/32 NONE
T 722167000 8MHz 3/4 NONE QAM16 2k 1/32 NONE
T 746000000 8MHz 3/4 NONE QAM16 2k 1/32 NONE

[/I]

I have looked at [http://www.dtg.org.uk/retailer/dtt_channels.html]("http://www.dtg.org.uk/retailer/dtt_channels.html")

but can't find info on generating new list.

Help much appreciated.
Richard

---

### Post by sboot on 2011-10-14
Try replacing the contents of your seed file with this... 

```
# Sutton Coldfield, Central West
# Author: Stephen Boot
# Created with info from http://www.ukfree.tv/txdetail.php?a=SK113003

# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
#PSB1 BBCA
T 650000000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
#PSB2 D3+4
T 674000000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
#PSB3 BBCB (Freeview HD)
#T 626166670 8MHz 2/3 NONE QAM256 32k 1/32 NONE
#COM4 SDN
T 642000000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
#COM5 ArqA
T 666000000 8MHz 2/3 NONE QAM64 8k 1/32 NONE
#COM6 ArqB
T 618166670 8MHz 2/3 NONE QAM64 8k 1/32 NONE

```...worked for me :)

BTW, if you have a Freeview HD card, this is untested and have no idea if it works... but if the driver is supported, try uncommenting the line below "#PSB3 BBCB (Freeview HD)" and post your failure/success below.

---

### Post by Graham17655 on 2011-11-05
For a HD card the line needs to read as follows:
T 626166670 8MHz 2/3 NONE QAM256 AUTO 1/32 NONE
then it works fine (or at least it would if I had a signal).

---

