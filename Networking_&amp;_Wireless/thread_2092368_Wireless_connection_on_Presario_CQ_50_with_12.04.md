---
title: "Wireless connection on Presario CQ 50 with 12.04"
date: 2012-12-07
forum: Networking &amp; Wireless
---

### Post by spenbeck on 2012-12-07
Compaq Presario CQ 50 110 (2009), 2 ghz AMD Turion x2 RM70 Dual Core.
Wireless Connector: Atheros 243x / AR542x.

Hi everyone, I'm a newbie to Ubuntu, but managed to install 12.04 on to the above laptop a couple of weeks ago, of which I am very happy. But, after trying to connect to my brothers wireless network, which failed, I am now unable to re-connect to my wireless network at home. I can still connect using an ethernet cable though. 

Is wireless connection a common problem with pc laptops and ubuntu or is it down to specific machines?

To re-connect, is it a simple fix like something switched off in the BIOS which I can turn back on in Terminal or is it more complicated?

Do I have to download an driver update or use something like 'ndiswrapper' and download a windows update?

I have checked other threads with similar problems, but I can't find a decisive answer yet. I will keep looking.

Any info or pointers to other threads greatly received. :-)

- - - -

P.S. I also have a matching CQ 50 with 12.04 installed along side Vista. This also dropped connection to the wireless network, but I managed to re-connect it in Vista using the HP Wireless Assistant. Is this a clue to the problem above?

P.P.S. FYI - I have noticed that since the laptop has dropped wireless connection the fan does not run like a train and the battery lasts much, much longer now!

---

### Post by spenbeck on 2012-12-08
Hi again,

I have progressed a little further with this problem. I have managed to download and install ndiswrapper so I can try and use the original windows driver (Atheros AR 242x). I can download the 'driver' from the atheros website, but it comes down as an '.exe' file. 

I can not run it or open it to find the .inf file I require.

Any pointers of what to do next are welcome, but in the mean time I'll plod on.

---

### Post by spenbeck on 2012-12-10
Hi again,

I think I've moved on a bit further with this problem. I managed to download ndiswrapper and installed it OK. It took me some time but I finally managed to get the correct Atheros driver from the atheros.cz website. I opened Windows Wireless Drivers (ndiswrapper?) found the driver, which it recognised as OK and installed it. I thought YES!, but........ now I can't find a wireless network in the system settings>network.

One of the threads which helped me get this far mentioned typing 'sudo iwgonfig' in the Terminal, but it now says 'lo no wireless extensions and etho no wireless extensions'.

I've got so far on my own, but now I think I'm getting out of my depth.

I could really do with some help from an expert who could give me some pointers to see if I've got everything installed correctly and in the right order please.

best regards, Ian Bradley (spenbeck)

---

### Post by spenbeck on 2012-12-12
Hi everyone,

With no help coming I think I am going to have to back everything up and re-install 12.04 again from scratch.

---

