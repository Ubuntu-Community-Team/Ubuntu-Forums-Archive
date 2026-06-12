---
title: "Changing Hauppauge Card"
date: 2008-10-27
forum: Mythbuntu
---

### Post by ljbeng on 2008-10-27
I built my PVR a year ago using the current Mythbuntu of the time.. 7 something.

I record over the air channels only and I will need a Digital Tuner come February.

I built my box with a PVR-150.  If I buy a HVR-1250 or HVR-1600 will I be able to swap out the cards, power up, channel search and go?

---

### Post by ljbeng on 2008-10-28
Anyone know this one?  Is Mythbuntu plug and play?  Can I just change tuner cards and go?

---

### Post by SiHa on 2008-10-28
I think the answer is almost certainly 'no', especially as you're changing from Analogue to Digital. You will need to run the backend setup again with the new cards. Shouldn't take too long though, and I don't think you'll need to do much with the frontend setup.

---

### Post by klc5555 on 2008-10-28
> **ljbeng said:**
> I built my PVR a year ago using the current Mythbuntu of the time.. 7 something.

I record over the air channels only and I will need a Digital Tuner come February.

I built my box with a PVR-150.  If I buy a HVR-1250 or HVR-1600 will I be able to swap out the cards, power up, channel search and go?

I can't answer to the 1250, but I have been wrestling for a couple of weeks with a 1600 that I added to a slave backend, and can testify that it can possibly be a real PITA to set up.

Read carefully the wiki document at [http://mythtv.org/wiki/index.php/Hauppauge_HVR-1600](http://mythtv.org/wiki/index.php/Hauppauge_HVR-1600)

Depending on your kernel level, you may have to compile the cx18 driver module yourself from v4l daily snapshots. cx18 support is supposed to have been added to the 2.6.26 and above kernel tree, so perhaps 8.10 will have it supported out-of-the box.

The cx18 driver is beta, and tends not to play nicely with nvidia proprietary drivers. i.e., if cx18 is modprobed, X can't start; if you rmmod the cx18, then the nvidia driver will load, but thereafter you can't load the cx18 driver and initialize the card. The open source nv driver (for what it's worth) works fine with cx18.

In this nvidia proprietary driver conflict, (not mentioned in the wiki doc) the usual recommendation is to expand available virtual memory by passing the append "vmalloc = 256m" to the kernel at boot, but this solution appears not to be effective in all cases. 

The card is also fussy about which PCI slot it's stuck in. It may  work better either in the 1st or 2nd slot after the graphics card; in the 3rd PCI slot or further it may prevent the machine from booting. 

Then there are the various issues described in the wiki doc, which may or may not affect you.

So, the short answer is: the 1600 may work for you, but it certainly won't be just a plug'n'boot replacement process. 

Good luck in your card replacement search! :)

---

### Post by bawilson2 on 2008-10-30
It won't be a plug and play change but I'm using the HVR-1600 and didn't have any problems getting it to run along with the proprietary nvidia drivers.

---

