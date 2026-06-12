---
title: "Anyone get Mythbuntu 9.10 working with ATI TV-Wonder?"
date: 2009-11-13
forum: Mythbuntu
---

### Post by rayto on 2009-11-13
I had my ATI TV-Wonder card working fine with Mythbuntu 8.04.1, but after the upgrade to 9.10, I cannot change channel.  Since then, I reinstalled 9.10 from scratch. (I formated the whole disk). Now when I get to setup the TV card (backend configuration, it recognized that it is a TV-Wonder card, but the scan button is not enabled.  I search on the net and found the following suggestion:     cd /etc/modprobe.d     echo "options cx88xx card=4 tuner=44" > cx88xx     modprobe -r cx8800     modprobe cx8800  It was for a TV-Wonder-Pro card. Mine is just a TV-Wonder. I tried it anyway. It doesn't work.  Anyone get 9.10 working with ATI TV-Wonder card? Any suggestion as what to try?  Thanks, Raymond

---

