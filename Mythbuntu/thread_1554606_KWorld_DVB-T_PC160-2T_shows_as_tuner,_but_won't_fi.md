---
title: "KWorld DVB-T PC160-2T shows as tuner, but won't find channels"
date: 2010-08-16
forum: Mythbuntu
---

### Post by Rage10898 on 2010-08-16
Hi all, I have a KWorld DVB-T PC160-2T that shows up as an available DVB in Myth 0.23, on 10.04, using Auto Builds, but will not lock/insert any channel information.

When scanning, it is showing that it receiving a weak signal (~63-70% tops) from my antenna, from which an old AverMedia Bt878 based card is receiving ~93-97% signal strength.

Thinking that it may have been receiving a weak signal off the splitter (currently running the Bt878 card and my TV) I went and got a signal amplifier today, with no change.

I am not sure if it is a fault with this particular card or firmware (which I am assuming is the newest) but I would like to see some use out of my investment!:lolflag:

Can anybody advise me if there is a way to make this card work.  

Attached is dmesg | grep dvb and lspci and lsusb outputs. 

Thanks.

---

### Post by klc5555 on 2010-08-17
You may just be bleeped with this card for the time being pending a driver rewrite, though using newer firmware is reported to make things a bit better. Check the mythtv wiki article on this card to see the current unsatisfactory state of affairs. [http://www.mythtv.org/wiki/Kworld_DVB-T_PC160-2T](http://www.mythtv.org/wiki/Kworld_DVB-T_PC160-2T)

---

### Post by bance on 2010-08-19
[SIZE=3]I've got this card and it worked out of the box. The only thing I did was up the tuning time-out to 250 ms, as recommended on the wiki.

how did you get on?[/SIZE] [SIZE=3]

Steve,[/SIZE]

---

### Post by Rage10898 on 2010-08-19
Hi to you both.

I have tried setting the tuning time-out to 250ms, with no success.  I have also tried setting it at varying times, up to about 1000ms, but no joy.  I will try the new firmware from the wiki entry and see how that goes.

Cheers,

Jason

Edit:  I have seen over here [http://guide.ubuntuforums.org/showthread.php?t=1457615](http://guide.ubuntuforums.org/showthread.php?t=1457615) that some people have managed to get it working on 32 bit systems.  Does anybody know if that would be worth a shot?  Starting to get a little frustrated. ](*,)

---

