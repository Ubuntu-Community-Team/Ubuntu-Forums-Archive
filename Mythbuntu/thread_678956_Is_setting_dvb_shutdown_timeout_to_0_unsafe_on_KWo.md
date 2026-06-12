---
title: "Is setting dvb_shutdown_timeout to 0 unsafe on KWorld ATSC 115 card?"
date: 2008-01-26
forum: Mythbuntu
---

### Post by thecoolcat on 2008-01-26
Hello,

I'm using KWorld ATSC 115. I've got both digital ATSC and analog NTSC to work successfully. However, I had trouble switching between ATSC to NTSC and the channel not tuning without switching to another analog station and then back. Almost as if the dvb dev isn't releasing the tuner.

After setting dvb_core dvb_shutdown_timeout=0 in ine of my files inside /etc/modprobe.d, this problem has gone away!

My question is this: Is it okay to set this option? I believe setting this option turns off the power management feature when the DVB card is not in use. So will this harm my card or will this produce excessive heat and damage (fry!) my PC hardware.

Thanks.

---

### Post by Offoffoff on 2008-07-10
Maybe in Your internet start script it is better to do:
modprobe dvb-core dvb_shutdown_timeout=0
And in internet stop script:
modprobe dvb-core dvb_shutdown_timeout=5

Thus Your hardware will be more heat protected...

---

### Post by kwisher on 2008-07-26
> **thecoolcat said:**
> Hello,

I'm using KWorld ATSC 115. I've got both digital ATSC and analog NTSC to work successfully. However, I had trouble switching between ATSC to NTSC and the channel not tuning without switching to another analog station and then back. Almost as if the dvb dev isn't releasing the tuner.

After setting dvb_core dvb_shutdown_timeout=0 in ine of my files inside /etc/modprobe.d, this problem has gone away!

My question is this: Is it okay to set this option? I believe setting this option turns off the power management feature when the DVB card is not in use. So will this harm my card or will this produce excessive heat and damage (fry!) my PC hardware.

Thanks.

coolcat,

I have a pair of 115's and I'm having touble getting the digital tuners to pick up any signals from my comcast cable. Could you please explain any extra steps you had to do to get these cards to work?

TIA,

kwisher

---

