---
title: "Open Source Routers"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by inkrypted on 2011-08-25
I have a Netgear WNR2000 V3 that I have been happy with but recently I have been having some speed and disconnect issues and after having endless discussions with my ISP I decided to get an Asus RT-N16 R and try some open source firmware. I wondered if anyone else here was using open source firmware like DDWRT, OpenWRT, or Tomato and if so has it helped your connection in any way? What has been your experiences? Thanks.

---

### Post by lmarmisa on 2011-08-26
> **inkrypted said:**
> I have a Netgear WNR2000 V3 that I have been happy with but recently I have been having some speed and disconnect issues and after having endless discussions with my ISP I decided to get an Asus RT-N16 R and try some open source firmware. I wondered if anyone else here was using open source firmware like DDWRT, OpenWRT, or Tomato and if so has it helped your connection in any way? What has been your experiences? Thanks.

I have two [Linksys WRT54GL]("http://en.wikipedia.org/wiki/Linksys_WRT54G_series") (one is the main router, the second one is for [WDS]("http://en.wikipedia.org/wiki/Wireless_Distribution_System")) and I love them.

I have used DD-WRT, Tomato and TomatoVPN. All these firmwares are great. I really recommend them.

If your current problem is related to router, I recommend to use a new one with an open source linux based firmware.

Best regards,

Luis

---

### Post by Kernelingus on 2011-08-26
I use (and love) an older Linksys WRT54G with DD-WRT.  I would recommend doing so to anyone.

Here in the US they're really easy to find on craigslist, at swap meets, flea markets, etc.  You can also always find them on Ebay.  (I own several of them, my favorite is a version 4 that I picked up at a yard sale.)

You can learn the hardware requirements for each version of DD-WRT on their website.  There's a nifty chart of the different versions of the WRT54G, explaining which hardware each contains, on Wikipedia.

[http://en.wikipedia.org/wiki/Linksys_WRT54G_series](http://en.wikipedia.org/wiki/Linksys_WRT54G_series)

Happy routing.

---

### Post by inkrypted on 2011-08-26
Thank you very much for sharing your experiences. It all sounds positive so I am really looking forward to Monday. I checked the compatibility list and this router is capable of using alot of different firmwares but after doing some research I think I have decided on Tomato USB. I will report back and post on how this goes (crosses fingers).

---

### Post by lmarmisa on 2011-08-27
> **inkrypted said:**
> Thank you very much for sharing your experiences. It all sounds positive so I am really looking forward to Monday. I checked the compatibility list and this router is capable of using alot of different firmwares but after doing some research I think I have decided on Tomato USB. I will report back and post on how this goes (crosses fingers).

Hi Chris,

I think that your router is not able to run open source firmwares at the moment. 

The version of your device is important. Netgear WNR2000 V2 is suppoted, but Netgear WNR2000 V3 not. 

Be very careful with this point. You could brick your router.

Best regards,

Luis

---

### Post by inkrypted on 2011-08-27
Hello Luis I think you misunderstood. I know the Netgear is not capable of running open source firmware that is why I am purchasing the Asus RT-N16 router. I did a bit of research before I made the purchase here are the links I checked. 

[http://patricksheedy.net/blog/simple-tomato-firmware-install-on-asus-rt-n16-router/](http://patricksheedy.net/blog/simple-tomato-firmware-install-on-asus-rt-n16-router/)

[http://dd-wrt.ca/wiki/index.php/Asus_RT-N16](http://dd-wrt.ca/wiki/index.php/Asus_RT-N16)

Let me know if you think I am making a mistake. I value peoples opinions who have been down this road before.
Sorry for any confusion but thank you for your concern.:)

---

### Post by inkrypted on 2011-08-27
I hope this is beneficial for all of us. Nice to meet you gbvehiclehire. My new router won't arrive until Monday. I intend to post back and let everyone know how it went and if it improved anything (fingers still crossed).

---

### Post by lmarmisa on 2011-08-27
> **inkrypted said:**
> Hello Luis I think you misunderstood. I know the Netgear is not capable of running open source firmware that is why I am purchasing the Asus RT-N16 router. I did a bit of research before I made the purchase here are the links I checked. 

[http://patricksheedy.net/blog/simple-tomato-firmware-install-on-asus-rt-n16-router/](http://patricksheedy.net/blog/simple-tomato-firmware-install-on-asus-rt-n16-router/)

[http://dd-wrt.ca/wiki/index.php/Asus_RT-N16](http://dd-wrt.ca/wiki/index.php/Asus_RT-N16)

Let me know if you think I am making a mistake. I value peoples opinions who have been down this road before.
Sorry for any confusion but thank you for your concern.:)

Sorry, Chris. I checked the wrong model!!!. :oops:

You are right. Your new modem, the Asus RT-N16, is compatible with DD-WRT and Tomato USB.

Best regards,

Luis

---

### Post by inkrypted on 2011-08-27
No Problem. That post makes me feel alot better. I have never tried Asus routers before so I am a bit nervous. So that's one part I now know I didn't screw up now for the firmware.

---

### Post by inkrypted on 2011-08-30
Well I can honestly say that changing the firmware did the trick. At first I used the stock firmware for a few hours and it was pretty much the same wireless disconnects, media server stutters, and slow speeds at times. Not holding out much hope I installed the Tomato USB firmware which was smooth as glass using the restoration utility included. After a three hour test run I can say that all wireless connections are super stable. Speed has stabilized and no more stuttering on the media server. Wired devices even seem faster. Tomato has a very simple interface and an amazing set of features especially the QOS. The RT-N16 is nothing to write home about until you pair it with the right firmware.

---

