---
title: "Atheros networking card"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by cab_bae on 2010-02-14
Hi my name is Abraham and I have the Acer Aspire One 532h-2594 and it has the network card: atheros AR9285 wireless network adapter and I was wondering if I was the only one experiencing frequent disconnects? Also if there is a fix on this if any?

Thanks in advance!

---

### Post by bkratz on 2010-02-14
This will probably help ( At least it will probably give you more signal strength )

[http://ubuntuforums.org/showpost.php?p=8787144&postcount=4](http://ubuntuforums.org/showpost.php?p=8787144&postcount=4)

---

### Post by cab_bae on 2010-02-15
Well basically I have the new Acer Aspire One Model: AO532h which has the new intel atom n450 & 6 cell battery. I will try what you have stated above in the link but I was reading that there are some kernels specific for these machines that fixed the problems or something like that... :)

---

### Post by sur4ed on 2010-02-15
I have the same setup with the same issue.  I followed similar instruction about installing the karmic-generics and blacklisting the ath9k.  I also tried commenting out the ath_pci.conf. All combinations of this fix resulted in worse connectivity than before.  I also read a thread about this chip pointing to an issue with the bluetooth and wireless on the same chip conflicting.  Since UNR currently doesn't recognize any bluetooth on this laptop, this may be part of the problem.  Hopefully there's a solid fix.

---

### Post by cab_bae on 2010-02-15
Actually the thread that bkratz pointed to is working for me right now and I have better signal. Though you kind of make me think about the bluetooth a bit because I thought it didn't have any. When you look at the box it comes in, it says that it doesn't have bluetooth. So basically to me there is none to begin with... maybe I'm wrong and it does have bluetooth. As for the UNR I did try it out on this netbook but I ended up switching to Ubuntu 9.10 desktop edition because of the wireless issues, but coming to think of it I could revert back and try the wireless fix on it. I also want to state that I was able to install and use Ubuntu Netbook Remix(UNR) without any problems except for the wifi, but that can be fixed with [this thread]("http://ubuntuforums.org/showpost.php?p=8787144&postcount=4").

---

### Post by cab_bae on 2010-02-15
Yup the AO532h does not have bluetooth at all... just confirmed it when I tried to install the windows 7 driver on the Windows 7 Starter Edition...

---

### Post by sur4ed on 2010-02-15
I double checked my box and found the same to be true regarding bluetooth (between that post I had read and the bluetooth function key, I had just kinda wrote it off as a given).  I also used this fix with UNR and its made a significant increase in signal strength detected, but I have yet to load the connection.  I'll test it for a few days and see how it goes.  There wasn't much difference in this fix then the post I had followed previously, but I'm glad to have any improvement.  Thanks for posting the question.  I saw a slew of other questions about this card in different forums while I was looking for a fix.

---

### Post by sur4ed on 2010-02-15
Heavier Traffic doesn't seem to drop the connection, though it's slightly flaky as far as speed is concerned.  Additionally I'm not seeing anything higher than 54g even though my router and the card are n capable.  Have you seen anything faster?

---

### Post by cab_bae on 2010-02-16
Yeah the problem that I would get without the fix is that when I would have heavy traffic I think it would overload and disable the network card and restart it I guess, but after the fix I have better signals and it doesn't disconnect at all. The top speeds that I have seen on this machine with transmission is 625kb maybe 700kb.

---

