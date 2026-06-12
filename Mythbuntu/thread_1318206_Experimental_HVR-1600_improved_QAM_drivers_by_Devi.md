---
title: "Experimental HVR-1600 improved QAM drivers by Devin Heitmueller"
date: 2009-11-07
forum: Mythbuntu
---

### Post by epi 1:10,000 on 2009-11-07
Devin Heitmueller at Kernel Labs was kind enough to do some reverse engineering to improve the reception of the Hauppauge HVR-1600.
 

 [http://www.kernellabs.com/blog/?p=1027](http://www.kernellabs.com/blog/?p=1027)
 

 If anyone is willing to test/try these drivers you may do so by:
 

 

 hg clone [http://kernellabs.com/hg/~dheitmueller/hvr-1600-perf-2]("http://kernellabs.com/hg/%7Edheitmueller/hvr-1600-perf-2")
 
cd hvr*-1600*-perf-*2
 
make
 
sudo make install
 
reboot


This installs new drivers for many cards so beware that you may have to restore/reconfigure the settings of some of your other cards.

---

