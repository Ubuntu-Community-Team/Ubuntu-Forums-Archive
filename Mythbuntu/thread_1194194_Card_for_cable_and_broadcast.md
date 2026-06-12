---
title: "Card for cable and broadcast?"
date: 2009-06-22
forum: Mythbuntu
---

### Post by embolalia1187 on 2009-06-22
I'm looking into making a box that will move with me to college. I'm not sure, though, what type of signals I get at each. So my question is, which type of signal am I getting, and can I use the same card to record both?

Home is SD digital broadcast, in New York State. HD is available, but since I don't have an HDTV, it wouldn't make much of a difference.

At college in Ohio, there is analogue basic cable in the dorms. A few channels also have free digital and HD, in addition to analogue.

Thanks in advance for your help.

---

### Post by AboveTheLogic on 2009-06-22
a ATSC/NTSC tuner sounds like the best option for you

that will let you get analog cable and digital terrestrial signals, but will not let you get digital cable

you could always run more than one tuner...

---

### Post by LowSky on 2009-06-22
Also get a card that does decoding, otherwise its going to tax your computer's processor. They cost a bit more but worth it.
best option is to check newegg for prices and features. I have the Haupauge HVR-2250, its great under Windows 7, but was a pain to get semi working under linux. Just keep that in mind, heck I wrote a how to just  help others on this forum (enough of me gloating..lol). If linux is a must check the MythTV website for choices, the best for linux use is the  HD-5500
[http://www.pchdtv.com/](http://www.pchdtv.com/)

---

### Post by newlinux on 2009-06-22
I'd get a QAM/ATSC/NTSC tuner... some digital cable stations may be available via unencrypted QAM. Although most of the time what is available are you local stations. In my area it has changed, but right now pretty much all extended basic cable stations are available via unencrypted QAM (only the locals are available in HD, however). A card that does QAM/ATSC/NTSC will get you everything you can get that doesn't require a set top box.

And with modern processors, encoding analog SD signals is not very taxing on the CPU, so depending on your processor I wouldn't worry much about that. Decoding is not usually performed by the tuner card buy by the CPU and/or GPU.

There are a number of tuners that fit the profile. You'll want to narrow them down by type of slot (PCI or PCIe - or maybe even a USB stick, cost, and configuration headache :). Lots of options in the hardware thread.

---

### Post by AboveTheLogic on 2009-06-22
> **newlinux said:**
> I'd get a QAM/ATSC/NTSC tuner...

I guess I assumed that these don't exist when I made my post, I dont recall seeing one during my searches, but I wasn't searching for a QAM tuner at the time.

I agree if you can get an all-in-one tuner it is the best way to go.

---

### Post by newlinux on 2009-06-22
Many of them exist.

I have 2, but they are older. Kworld ATSC 110/115 and Dvico Fusion 5... which both do QAM/ATSC/NTSC. the pchdtv 3000/5500 do as well (I used to have a pchdt 5500). of course you can only tune one signal at a time (these aren't dual tuners) but they can be setup to switch back and forth between signal types on the fly in myth. Those are all PCI. The HVR-1800 is a PCIe card that I believe does all 3. Plenty others...

PCI:   [http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards](http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards)
PCIe:  [http://www.linuxtv.org/wiki/index.php/ATSC_PCIe_Cards](http://www.linuxtv.org/wiki/index.php/ATSC_PCIe_Cards)
USB:   [http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices](http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices)

---

### Post by embolalia1187 on 2009-06-22
Wow. Thanks for all the quick responses. I have a P4, 64-bit, @2.93GHz. Is that enough to do software encoding easily?

Also, a lot of the FAQs make it seem as though watching and recording is not possible at the same time without at least two tuners. What if I'm watching the same channel I'm recording? If I can find a splitter or something (which I understand you need for more than one tuner anyway), can I just split the cable so one line goes directly to the TV, and the other to Myth (which then connects by component or w/e to the TV), would I then be able to watch and record different channels at the same time?

Thanks again.

---

### Post by newlinux on 2009-06-22
> **embolalia1187 said:**
> Wow. Thanks for all the quick responses. I have a P4, 64-bit, @2.93GHz. Is that enough to do software encoding easily? (Part of the reason I'm doing it with Linux is the budget)


Yes. A PIII 700Mhz could do software encoding. It really would only be an issue depending on what else your box is doing at the same time.
> 

Also, a lot of the FAQs make it seem as though watching and recording is not possible at the same time without at least two tuners. What if I'm watching the same channel I'm recording? If I can find a splitter or something (which I understand you need for more than one tuner anyway), can I just split the cable so one line goes directly to the TV, and the other to Myth (which then connects by component or w/e to the TV), would I then be able to watch and record different channels at the same time?

Thanks again.

You can watch in progress recordings, so effectively you can watch the same channel you are recording.

With a splitter going to your tV and myth tuner you can watch one station on your TV while recording another in myth (this is effectively using 2 tuners, although one is only available from the TV). Those FAQs are probably talking about watching liveTV while recording without leaving myth (i.e. having myth do all of it, not using your TV's tuner).

---

### Post by embolalia1187 on 2009-06-22
Awesome. Thanks again!

---

