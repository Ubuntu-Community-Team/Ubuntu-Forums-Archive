---
title: "no auto connection to wired ethernet on restarts"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by rawlins02 on 2010-11-30
Just noticed that auto connection to my wired ethernet is not being established after restarts I'm making.  Never recall this in the past. I do get an auto connect when I shutdown and restart. I'm using 10.04 LTS Lucid Lynx.

Also have noticed that nearly every upgrade over the past week or so is calling for restart to complete the upgrade. Can there be any unwanted problems in doing several upgrades over a period of several days before doing the restart?  I'd like to think not.

As you can imagine these two issues together are causing some lost time.

---

### Post by s_raiguel on 2010-11-30
What kind of NIC do you have? I've had a similar problem with the Intel PCIe NIC on my Dell motherboard. Had it with the first release of 10.10, and then again when the new kernel was released earlier today. In both instances, I was able to download Intel's driver from their website, compile/install it as was up and going again in a matter of minutes. If you download the .tar.gz file, there's a readme with clear instructions how to install it- just a matter of un-tarring the file and then typing "sudo make install"

---

### Post by rawlins02 on 2010-11-30
Can't seem to find where network card information is located.  Given time I'm sure I will.  Suggestions?  Thanks.

---

### Post by rawlins02 on 2010-11-30
I have a Dell Studio XPS 1645.  Think it's a Notebook Broadcom BCM5784M card.  Still looking to confirm that.

---

### Post by E=MCC on 2010-11-30
I have the same no re-connection problem with a 64-bit Gigabye motherboard, integrated NC, AMD Phenom 3-core CPU, and cat5-wired to DSL (AT&T).  Can restore connection by taking otermachines off of DSL modem, turning off Ubuntu machine, turning off DSL modem, then starting DSL modem, then starting Ubuntu machine(10.10).  All that is a big pain and doesn't always work.  Any ideas would be appreciated.  Thanks!
E=MCC

---

### Post by E=MCC on 2010-11-30
typos:  NC should be NIC
          otermachines should be other machines (particularly Dell running Windows 7)

---

