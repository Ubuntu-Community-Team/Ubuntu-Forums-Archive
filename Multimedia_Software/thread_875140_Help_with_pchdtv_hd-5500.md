---
title: "Help with pchdtv hd-5500"
date: 2008-07-30
forum: Multimedia Software
---

### Post by jacoody on 2008-07-30
I'm running Mythbuntu 8.04 (kernel 2.6.24-19 i think).  When I have a clean image with clean modules, I get the following for cat /proc/asound/cards (from memory)
 
         0    M1010LT
         1    Conextant cx88
         2    Conextant cx88_1
 
Under this configuration, the analog tuner of the card shows nothing but static on every channel but the sound works and is captured in the backend under /dev/dsp1 and /dev/dsp2.
 
When I upgrade the v4l-dvb drivers using the following method
 
     sudo apt-get install gcc linux-headers-2.6.24-19-generic mercurial
     hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
     cd v4l-dvb
     make && sudo make install && sudo reboot
 
the analog portion of the card works but cat /proc/asound/cards shows only
 
      0  M1010LT
 
and the sound is not captured because /dev/dsp1 and /dev/dsp2 does not exist.  This is because module cx88_alsa is not loading.    When I try and sudo modprobe cx88_alsa I get a FATAL error complaining about version not agreeing.  Apparently the update to v4l-dvd does not also update the cx88_alsa module.
 
I am not a linux guru and really need some help with this.  Does anyone have an idea of how to fix this?
 
Thank you,
JA

---

### Post by jacoody on 2008-07-30
I went back to the clean distribution modules and now my dmesg looks like this

[  208.122698] cx88/2: unregistering cx8802 driver, type: dvb access: shared
[  208.122709] cx88[0]/2: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47]
[  208.126593] cx88[1]/2: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47]
[  208.153775] ACPI: PCI interrupt for device 0000:02:06.2 disabled
[  208.154310] ACPI: PCI interrupt for device 0000:02:05.2 disabled
[  214.924689] ACPI: PCI interrupt for device 0000:02:06.0 disabled
[  215.604474] ACPI: PCI interrupt for device 0000:02:05.0 disabled
[  231.939444] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[  231.940035] cx88[0]/2: cx2388x 8802 Driver Manager
[  231.940056] ACPI: PCI Interrupt 0000:02:05.2[A] -> GSI 16 (level, low) -> IRQ 21
[  231.940069] cx88[0]/2: found at 0000:02:05.2, rev: 5, irq: 21, latency: 32, mmio: 0xf7000000
[  231.963593] cx88[1]/2: cx2388x 8802 Driver Manager
[  231.963616] ACPI: PCI Interrupt 0000:02:06.2[A] -> GSI 17 (level, low) -> IRQ 22
[  231.963629] cx88[1]/2: found at 0000:02:06.2, rev: 5, irq: 22, latency: 32, mmio: 0xfb000000
[  231.971720] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[  231.971728] cx88/2: registering cx8802 driver, type: dvb access: shared
[  231.971734] cx88[0]/2: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47]
[  231.971739] cx88[0]/2: cx2388x based DVB/ATSC card
[  232.377639] DVB: registering new adapter (cx88[0])
[  232.378061] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[  232.381185] cx88[1]/2: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47]
[  232.381195] cx88[1]/2: cx2388x based DVB/ATSC card
[  233.213781] DVB: registering new adapter (cx88[1])
[  233.214227] DVB: registering frontend 1 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[  238.245779] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[  238.246308] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 16 (level, low) -> IRQ 21
[  238.248303] cx88[0]/0: found at 0000:02:05.0, rev: 5, irq: 21, latency: 32, mmio: 0xf9000000
[  238.268239] tuner: disagrees about version of symbol tea5767_attach
[  238.268249] tuner: Unknown symbol tea5767_attach
[  238.268435] tuner: Unknown symbol tda8290_probe
[  238.268516] tuner: Unknown symbol tda8290_attach
[  238.268874] tuner: disagrees about version of symbol simple_tuner_attach
[  238.268878] tuner: Unknown symbol simple_tuner_attach
[  238.268935] tuner: disagrees about version of symbol microtune_attach
[  238.268939] tuner: Unknown symbol microtune_attach
[  238.269162] tuner: disagrees about version of symbol tea5761_attach
[  238.269165] tuner: Unknown symbol tea5761_attach
[  238.279474] cx88[0]/0: registered device video0 [v4l2]
[  238.279939] cx88[0]/0: registered device vbi0
[  238.287622] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 17 (level, low) -> IRQ 22
[  238.288174] cx88[1]/0: found at 0000:02:06.0, rev: 5, irq: 22, latency: 32, mmio: 0xf5000000
[  238.338832] tuner: disagrees about version of symbol tea5767_attach
[  238.338842] tuner: Unknown symbol tea5767_attach
[  238.339029] tuner: Unknown symbol tda8290_probe
[  238.339110] tuner: Unknown symbol tda8290_attach
[  238.339488] tuner: disagrees about version of symbol simple_tuner_attach
[  238.339492] tuner: Unknown symbol simple_tuner_attach
[  238.339550] tuner: disagrees about version of symbol microtune_attach
[  238.339553] tuner: Unknown symbol microtune_attach
[  238.339777] tuner: disagrees about version of symbol tea5761_attach
[  238.339780] tuner: Unknown symbol tea5761_attach
[  238.346166] cx88[1]/0: registered device video1 [v4l2]
[  238.346204] cx88[1]/0: registered device vbi1
:confused:

---

### Post by Afkpuz on 2008-07-30
You need to add this to your /etc/modules/ file.

```
cx88-dvb
```



Then reboot.
Then, when setting up your card, choose "DVB TV", not the "pchdtv" cards.

Detail [here]("http://wiki.linuxmce.org/index.php/PcHDTV_HD5500")

the only difference on that page is that you'll need to use a different text editor than kate.

P.S. I used to have this card and I'm not sure how well it works in mythbuntu, but I can verify that it works well in an ubuntu+mythtv install

---

### Post by jacoody on 2008-07-30
Thank you for the response.  I have that in my file already.  I can't use the dvb option in mythtv-setup because I'm trying to watch analog cable so I'm using the v4l driver.

JA

---

### Post by Afkpuz on 2008-07-31
The way it worked for me was to only add the dvb part.  Then, it picks up that it is a hybrid card and adds the appropriate analog inputs.  I never had to choose v4l as a card.  So, after adding only a dvb card, I had the analog input listed in the input section.  Does that make sense?  Also, there a place when adding the dvb card to set the sample rate for analog audio.  Did you check that link I sent?  Also note that I used this procedure in a previous version of mythtv+ubuntu. Long story short is you need to tell it that your card is a dvb card and then it should pick up on the analog tuner automatically.  At least, that's what it did for me.

---

### Post by jacoody on 2008-07-31
hmm, I'll try it again this afternoon.  Last time I added the dvb driver I looked all over for the analog options and it didn't have any.  I'll check the input screen this time.  Are you running 8.04?

Thanks!

---

### Post by jacoody on 2008-07-31
I set it up with the DVB driver but there are no anolog options for it in my version of mythtv.  I used cable as my input but when it scans for channels the only option is dvb input.  The analog side of the tuner doesn't kick in.

JA

---

### Post by Afkpuz on 2008-08-01
When I had the card, I used both 7.10 and 8.04.  I think where the diffence came in was in the latest version of mythtv.  I remember noticing that once I upgraded mythtv, the analog part was gone.  That's right around the time that I sold that card and went for a dual analog tuner.  Sorry, I should have mentioned that earlier.

---

### Post by jacoody on 2008-08-02
I got the sound working.  I had to reinstall mythbuntu completely.  There is an update that ruins the sound drivers so I haven't installed any updates.

The problem now is that the sound is tinny.  I've set it to 48000 under the analog driver but not sure what to do next.

JA

---

