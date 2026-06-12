---
title: "Digital TV card for Feisty??"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by Goodson1974 on 2007-04-26
Hi all
 
I'm about to invest in a new DVB tv card for my PC and i'm hoping that there are some out there that require no (or simple) tinkering to get working with Ubuntu Feisty in the UK (using the Tacolneston transmitter if that makes a difference?!).
 
I was thinking of getting a Hauppauge Win TV Nova-T PCI but then read that it's not working too well with Feisty even though it was fine with Dapper and Edgy.
 
If someone could point me in the right direction i'd be eternally grateful :)

---

### Post by daverave999 on 2007-04-26
I have that very card. I've not finished setting MythTV up completely yet (only non-TV-card things like getting listings from the Radio Times site and channel names sorted) but I have been able to watch TV fine so far.

I used the guide at [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) for Edgy, and didn't encounter any more problems than last time using it for Feisty again.

I haven't been looking around these parts recently-what problems have people been having?

---

### Post by jtreach on 2007-04-26
I'd like to know the answer to this question too......

Basically I need someone to say get x card it's pretty cheap and runs prefectly with feisty out of the box.

Anybody know what my x would be?

Is there a list of supported DVB cards anywhere?

---

### Post by Goodson1974 on 2007-04-26
There are problems mentioned in the following thread: -

[http://ubuntuforums.org/showthread.php?t=415790](http://ubuntuforums.org/showthread.php?t=415790)

Not sure what's going on there as my knowledge ain't great!

---

### Post by GREG1292 on 2007-04-26
I am new to the forum but with all the great help I was able to get Mythtv up in running in no time. The PCHDTV 5500 has a great picture for DVB and the HDTV is stunning and drivers support is good.

Greg

---

### Post by puppy on 2007-04-26
I'm using the Nebula Electronics DigiTV PCI card in my machine - it's not particularly cheap however. It does work perfectly using Kaffeine from the KDE repositories with 2 simple commands in the console and setting it up appropriately in the application, which takes all of 1 or 2 minutes before you can watch all the Freeview channels :) 

I have to say I gave up on MythTV, which seems to be a very dark art indeed #-o   

If you do select a particular card that you want, please check the forums here and elsewhere to ensure that other people have got it to work, before taking the plunge and taking the cash out of your pocket- it might just be an expensive doorstop otherwise, not all TV cards are currently supported (and don't get me started on the Creative X-Fi soundcard!)

---

### Post by mtron on 2007-04-30
i have a [Hauppauge Nova - s]("http://www.hauppauge.com/PAGES/products/data_novas.html") card, which was detected by ubuntu right out of the box.

 No setup, no drivers needed to be loaded - ubuntu style ;)

You can get these budget cards for 50 Euro (~ 60 US$)

---

### Post by tonym on 2007-05-04
I've got the DigiTV card and it used to work fine but won't under Feisty.  Could you give us a hint what the 2 simple commands are?

Regards

Tony

---

### Post by PhatBoy on 2007-06-19
I have a Nova-T working fine under Feisty. Only slightly more problematic than under Edgy - had to add cx88_dvb to /etc/modules to get it to be recognised in Feisty.

---

### Post by david_2001 on 2007-06-19
2 x Kworld DVB-T 100s here, working fine under feisty.  Just be aware that the dvb kernel modules do not load automatically for any card in the 2.6.20 kernel.

---

### Post by jazzgossen on 2007-07-02
> **PhatBoy said:**
> I have a Nova-T working fine under Feisty. Only slightly more problematic than under Edgy - had to add cx88_dvb to /etc/modules to get it to be recognised in Feisty.

What kind of Nova-T? I'm also on the lookout for a DVB-T card, and most preferably a dual-tuner card. The wiki at linuxtv.org says that both dual cards that are listed (both the Hauppauge and the Pinnacle) have problems. Has anybody used a dual-tuner DVB-T card with Linux/Ubuntu?

---

