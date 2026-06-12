---
title: "DVB-T SCAN seed for Gippsland, Australia"
date: 2011-11-07
forum: Multimedia Software
---

### Post by sepius on 2011-11-07
Hi all
If any one knows where to send this please let me know.

I have just set up my USB DVB-T dongle and found that the SCAN seed for Gippsland Mt Tassie Transmitters was non existent.

I have got the frequencies and checked it and this works for the Mt Tassie transmitter.

Below is the details for au-Gippsland-MtTassie

```
# Australia / Gippsland (Mt Tassie Transmitters)
# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
# ABC
T 627500000 7MHz 3/4 NONE QAM64 8k 1/16 NONE
# Seven
T 564500000 7MHz 3/4 NONE QAM64 8k 1/16 NONE
# Nine
T 585500000 7MHz 3/4 NONE QAM64 8k 1/16 NONE
# Ten
T 606500000 7MHz 3/4 NONE QAM64 8k 1/16 NONE
# SBS
T 543500000 7MHz 2/3 NONE QAM64 8k 1/8 NONE
```

If you wish to use it, just create a file called au-Gippsland-MtTassie and insert the code, then copy file to /usr/share/dvb/dvb-t/ and use scan to get you Gippsland, Australia channels.

Again, if someone knows where I should send this for inclusion into the general repositories, can you please let me know.

Thanks.

---

