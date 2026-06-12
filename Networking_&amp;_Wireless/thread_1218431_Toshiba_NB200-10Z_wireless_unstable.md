---
title: "Toshiba NB200-10Z wireless unstable"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by ikkefc3 on 2009-07-20
Hello,
I have a Toshiba NB200-10Z (also known as NB200 or NB205).
The wifi driver it uses is ath9k and the wifi connection is very unstable. Sometimes the connection just falls away and the signal strenght changes a lot. I'm using it about 4 metres from  router with no walls between it, so it should be no problem. The signal is stable while using Windows XP.

How can I improve the stability of the connection?

---

### Post by dimeotane on 2009-07-21
Does the problem occur for you right after a fresh reboot?

Or have you noticed if this problem occurs after the netbook has been put into suspend and then you resume?

I have the same issue with my NB200,  after a a little while and some downloading, the net signal becomes unusable and eventually the signal drops.  The wifi manager shows device not ready or something like that.
The only option left is to reboot. 

It seems to be working fine after a fresh reboot.  I have a feeling the problem might be after I've put the netbook into suspend and then resume?  I think the keyboard was not working after I resumed one time as well.  

Can anyone confirm if this is the case?

---

### Post by superprash2003 on 2009-07-21
take a look at this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by dimeotane on 2009-07-23
Just to confirm on my NB200 (running 9.10 Netbook Remix)
the wireless seems to be working well on a fresh boot (although the meter shows lower quality link 40% than my Dell at 80%, the NB200 connection is actually equally fast pings and faster download speed)

However on closing the lid where the netbook sleeps and then I open it again
the (google.com) pings have doubled to 200ms and I can't even complete a download speed test it is so slow with a router connection of 24Mb/s.  Pages only load a few lines and then stall. 

The command I found to get it working again is:
> $ sudo ifconfig wlan0 down
Then in a moment the netbook automatically reconnected to my wireless router back at 54MB/s and the normal ping of 99ms.  However the Rioplex downloads speed test was again fast at 900kbps.  It appears this solves the problem, but it would be annoying to have to enter this command each time I open the notebook.   At least I don't need to reboot each time though.

---

