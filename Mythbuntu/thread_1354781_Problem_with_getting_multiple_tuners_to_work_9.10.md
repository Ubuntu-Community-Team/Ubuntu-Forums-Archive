---
title: "Problem with getting multiple tuners to work 9.10"
date: 2009-12-14
forum: Mythbuntu
---

### Post by tdcarlo on 2009-12-14
Hello,

I recently found a couple of PCI-express hauppenpauge 1250 tuners half-off at best buy and wanted to add them to my backend.  I was running 8.10 and to get them to work in combination with my hdPVR 5500 I had to load v4l-dvb.  Everything was fine for about two weeks.  After the initial grace period, a tuner would be dropped every day or two and I would have to delete and readd it.  Finally, I'm guessing the database became corrupt and only the HDPVR was being recognized.  So I decided to do a fresh install and upgrade to 9.10.  

After the install, I cannot add a second tuner.  I install one tuner fine.  But when I try to install a second tuner it always finds the first tuner again and says warning DVB:0 "already in use".  I've tried a fresh install with all three tuners, one 1250 and the 5500, and two 1250's....all give the same results.  I do load v4l-dvb as my 1250's come up as 1270's.  Everything else seems to be fine.

Any advise?  I'm at work so won't be able to post logs for about 8 hours but will immediately when I get home.

---

### Post by NightStorm on 2009-12-14
If you go to where the device is selected and right arrow, do you get another choice?
If not, maybe you can do a "dmesg" and look to see if both tuners are being recognized, loading firmware, etc?

   - Bruce

---

### Post by tdcarlo on 2009-12-14
Hi Bruce,

Thanks for the help.

Here is dmesg for Hauppenpage
```
[   11.905005] CORE cx23885[0]: subsystem: 0070:2211, board: Hauppauge WinTV-HVR1270 [card=18,autodetected]
[   12.052724] tveeprom 1-0050: Hauppauge model 22111, rev C2F5, serial# 6316673
[   12.052741] cx23885[0]: hauppauge eeprom: model=22111
[   12.489484] CORE cx23885[1]: subsystem: 0070:2211, board: Hauppauge WinTV-HVR1270 [card=18,autodetected]
[   12.645539] tveeprom 5-0050: Hauppauge model 22111, rev C2F5, serial# 6314286
[   12.645557] cx23885[1]: hauppauge eeprom: model=22111

```

So it appears that they are both being recognized

and here is the HDPVR 5500

```
[   11.983787] cx88[0]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47,autodetected], frontend(s): 1
[   12.261826] input: cx88 IR (pcHDTV HD5500 HDTV) as /devices/pci0000:00/0000:00:08.0/0000:01:09.0/input/input6
[   12.339249] cx88[0]/2: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47
```

Tonight, I did a fresh install was able to install two of the three tuners.  One 1250 (adapter 0)and the 5500 (adapter 1).  When I try to install the second 1250, I do not get offered adapter 2. 

I'm wondering if something along these lines is appropriate?  [http://ubuntuforums.org/showthread.php?t=753434](http://ubuntuforums.org/showthread.php?t=753434)

thanks,
Troy

---

### Post by tdcarlo on 2009-12-14
I also noticed that when I went to /dev/v4l/by-path.  I only saw two files

pci-0000:01:09.0-video-index0  pci-0000:01:09.0-video-index1

---

### Post by nickrout on 2009-12-14
one card may be faulty. strange things also go on on the pci bus - try swapping some of the card's pci slots.

---

### Post by NightStorm on 2009-12-14
> **tdcarlo said:**
> I also noticed that when I went to /dev/v4l/by-path.  I only saw two files

pci-0000:01:09.0-video-index0  pci-0000:01:09.0-video-index1

It does look like your cards are all being detected.  I don't know the 1250, I have a 2250 and I think that is just the duo of the 1250.  Mine shows up under /dev/dvb/ like this:

# ls -l /dev/dvb
drwxr-xr-x 2 root root 120 2009-12-14 22:15 adapter0
drwxr-xr-x 2 root root 120 2009-12-14 22:15 adapter1

And beneath each of the adapter? directories I have something similar to:
crw-rw----+ 1 root video 212, 5 2009-12-14 22:15 demux0
crw-rw----+ 1 root video 212, 6 2009-12-14 22:15 dvr0
crw-rw----+ 1 root video 212, 4 2009-12-14 22:15 frontend0
crw-rw----+ 1 root video 212, 7 2009-12-14 22:15 net0

So for the "DVB Device Number" I have to enter:
  /dev/dvb/adapter0/frontend0
and
  /dev/dvb/adapter1/frontend0

for the two tuners on that card.

One other problem I had when first first trying to get the HVR-2250s to work was that they were not showing up on the DVB DTV Capture card(v3.x) page at all.  This was because the firmware was not loading.  You can see the firmware load in my dmesg here:
# dmesg | egrep saa                         
[   12.404403] saa7164 driver loaded
[   12.404520] saa7164 0000:04:00.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18
[   12.404841] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   12.404847] saa7164[0]/0: found at 0000:04:00.0, rev: 129, irq: 18, latency: 0, mmio: 0xfdc00000
[   12.404852] saa7164 0000:04:00.0: setting latency timer to 64
[   12.404856] IRQ 18/saa7164[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   12.660027] saa7164_downloadfirmware() no first image
[   12.660036] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   12.660040] saa7164 0000:04:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[   12.916844] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   12.916847] saa7164_downloadfirmware() firmware loaded.
[   12.916855] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   12.916861] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   12.916862] saa7164_downloadfirmware() BSLSize = 0x0
[   12.916864] saa7164_downloadfirmware() Reserved = 0x0
[   12.916865] saa7164_downloadfirmware() Version = 0x51cc1
[   19.950015] saa7164_downloadimage() Image downloaded, booting...
[   20.060016] saa7164_downloadimage() Image booted successfully.
[   22.410014] saa7164_downloadimage() Image downloaded, booting...
[   23.840013] saa7164_downloadimage() Image booted successfully.
[   23.880957] saa7164[0]: Hauppauge eeprom: model=88061
[   24.624832] DVB: registering new adapter (saa7164)
[   28.397421] DVB: registering new adapter (saa7164)

That is the only other thing I can think of that you might check.  Otherwise (as nickrout said) .. maybe a card has problems?  You did start to have issues under 8.10 after a "burn-in" period, right?

    - Bruce

---

### Post by SiHa on 2009-12-15
Maybe [[COLOR="Blue"]_this_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1311795) will help? Specifically Neon Dusk's post.

Your problem is subtly different, being that you don't seem to be getting all adaptors created. Perhaps they are both ending up as adapter0?. Maybe you could force it to allocate adapter 0&1 to the two 1250's?

---

### Post by tdcarlo on 2009-12-15
Thanks all,

I forgot to mention that if I install each card alone, they all work.  

I'm going to try to force the order of allocation tonight when I get home and I'll post the results then.

thanks again,
Troy

---

### Post by tdcarlo on 2009-12-15
> **SiHa said:**
> Maybe [[COLOR="Blue"]_this_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1311795) will help? Specifically Neon Dusk's post.

Your problem is subtly different, being that you don't seem to be getting all adaptors created. Perhaps they are both ending up as adapter0?. Maybe you could force it to allocate adapter 0&1 to the two 1250's?

So this kinda did.

```
#set 1 1250 
options CORE_cx23885[0]_dvb adapter_nr=0

#set 2 1250
options CORE-cx23885[1]_dvb adapter_nr=1

#set 3 5500
options cx88_dvb adapter_nr=2
```

When I go to the backend, I still cant add a third card.  If I try to create a new card, it replies with  "warning already in use" for adapters 0 and 2.  Adapter 1 is never offered.  But, when I view tuner status via the front end, it shows three tuners.  All of them seem to work.

I'm not sure if this is solved or not.

Thanks for the help everybody.

Troy

---

### Post by SiHa on 2009-12-16
What does
```
 
options CORE_cx23885_dvb adapter_nr=0,1
```do? Rather than have them on separate lines.

To be sure the line is actually doing anything (ie, the adapter name is correct) have you tried changing it to, say:```
options CORE_cx23885_dvb adapter_nr=3,4
``` I had to play around with the name a bit until I got something it liked.

---

### Post by tdcarlo on 2009-12-16
> **SiHa said:**
> What does
```
 
options CORE_cx23885_dvb adapter_nr=0,1
```do? Rather than have them on separate lines.

To be sure the line is actually doing anything (ie, the adapter name is correct) have you tried changing it to, say:```
options CORE_cx23885_dvb adapter_nr=3,4
``` I had to play around with the name a bit until I got something it liked.

The first thing I tried was ```
#set 1 1250 
options CORE_cx23885_dvb adapter_nr=0

#set 2 1250
options CORE-cx23885_dvb adapter_nr=1

#set 3 5500
options cx88_dvb adapter_nr=2
```

And after a reboot, I only got one 1250 as adapter 0 but the 5500 was now recognized as adapter 2.  So the file changed the 5500's adapter number from 1 to 2, suggesting that it was altering the way the cards were being seen by mythbuntu.

Next I tried.

```
#set 1 1250 
options CORE_cx23885[0]_dvb adapter_nr=0

#set 2 1250
options CORE-cx23885[1]_dvb adapter_nr=1

#set 3 5500
options cx88_dvb adapter_nr=2
```

Adding the [0] and [1] allowed for the second 1250 to be recognized.  I couldn't add a third card in the backend but the frontend reported two 1250's.  ```
 
options CORE_cx23885_dvb adapter_nr=0,1
```I don't know this for sure but my suspicion is that you'd use the above code if they were on the same card, a dual tuner.  If you want me to, I'll put in your code tonight and report but I my guess is only one 1250 will be recognized.

Troy

---

### Post by SiHa on 2009-12-16
> Adding the [0] and [1] allowed for the second 1250 to be recognized. 
Sorry, that wasn't clear from the post.
> I don't know this for sure but my suspicion is that you'd use the above code if they were on the same card, a dual tuner. If you want me to, I'll put in your code tonight and report but I my guess is only one 1250 will be recognized.
Possibly, hadn't considered that, to be honest.
> And after a reboot, I only got one 1250 as adapter 0 but the 5500 was now recognized as adapter 2. So the file changed the 5500's adapter number from 1 to 2, suggesting that it was altering the way the cards were being seen by mythbuntu.
I was suggesting that perhaps **CORE_cx23885_dvb** was not being recognized, but the above shows that's not right.

Anyway, I've exhausted my slim knowledge of this facet of MythTV setup, sorry.

---

