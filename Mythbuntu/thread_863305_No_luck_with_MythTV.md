---
title: "No luck with MythTV"
date: 2008-07-18
forum: Mythbuntu
---

### Post by riknos on 2008-07-18
I have been trying on and off for several months to get to grips with MythTV and Mythbuntu on 8.10 but still I can't get TV channels input. I've tried a 'straightforward' scan for channels but I always get the error "Error Parsing Parameters". Very helpful. I've tried entering an individual channel but that doesn't do anything. I've also produced a channels.conf file and specified it for channels but to no avail. It is not clear if you just need to enter fields in Setup amnd then just exit. The data fields don't get retained.    

I've looked at all the howtos and docs I can find but I have come to the conclusion there is nothing really out there that documents the Backend in detail, i.e. What all the setup fields mean which ones apply to DVB-S and how they relate. If you supply a channels.conf file what is the field "europe-west" doing? I have a WinTV Nova S card, which is recognised amnd that is as far as I've managed to get. I've specified EIT for Video source but when I run mythfilldatabase I see the app is trying to locate web based programme guide - without success. Mythfilldatabase also always reports that the channels table is set to start on a non-existent channel and would I like it to fix it or No, I know h=waht I am doing! If I say yes fix it it doesn't seem to work and just returns to the same two choices each time.

It is just MythTV that I am totally stuck with as I have been able to scan channels and watch satellite TV using Kaffeine.

Can anyone out there help this very frustrated newbie - please.

---

### Post by theophile on 2008-07-18
What is your hardware configuration? You mentioned watching satellite. ASAIK, you can only get feed from a satellite through a converter box or STB. This being the case, the channel scanner will not work. 

It will help to know what exactly it is you are trying to make work.

---

### Post by riknos on 2008-07-18
Thanks for the response theophile. I am running an AMD 64 x 2 4200, kernal 2.6.24-19, Mythbuntu/ubuntu 8.04, Hauppauge WinTV-Nova-S-Plus pci card, Astra28.2E satellite input. MythTV 0.21.0.

---

### Post by theophile on 2008-07-18
I am not familiar with satellite systems, but have you seen this?
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-S_Plus_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-S_Plus_PCI)

It might help narrow things down.

How is your satellite receiver connected to the tuner?

---

### Post by nickrout on 2008-07-18
> **theophile said:**
> What is your hardware configuration? You mentioned watching satellite. ASAIK, you can only get feed from a satellite through a converter box or STB. This being the case, the channel scanner will not work. 

It will help to know what exactly it is you are trying to make work.

Total ********. unencrypted channels work fine straight off the satellite into a DVB-S card.

---

### Post by nickrout on 2008-07-18
Take a look at these guides

[http://support.openmedia.co.nz/mypvr/support/how-to-set-up-a-dvb-s-card-for-freeview-dth/](http://support.openmedia.co.nz/mypvr/support/how-to-set-up-a-dvb-s-card-for-freeview-dth/)

[http://support.openmedia.co.nz/mypvr/support/how-to-set-up-freeview-dth-channels/](http://support.openmedia.co.nz/mypvr/support/how-to-set-up-freeview-dth-channels/)

They are obviously for a different satellite, but they'll give you an idea of what to put in the various fields.

---

### Post by Trollslayer on 2008-07-19
If you want to know what satellite channels are available on East 28 visit [http://www.lyngsat.com/28east.html](http://www.lyngsat.com/28east.html)
That will show clear and encrypted channels.

---

