---
title: "Hauppauge HVR-1600 Digital Scanning"
date: 2010-02-12
forum: Mythbuntu
---

### Post by outleradam on 2010-02-12
My issue is with digital scanning.   For some reason it's got no bars on any channel when I scan my HVR-1600 card on the digital half.   My analog side is working properly (loading channels from presets).  Just the digital side is not.  I am trying to scan in QAM:256 and my card has QAM printed in big letters right on it.  I have upgraded to the most recent kernel a few times.   Any suggestions?

---

### Post by the_pod on 2010-02-12
I haven't found the "signal strength" meter on the digital half of the 1600 to work.  But it's more the meter and not the signal finder.  Mine finds the signals just fine.

If it finds the signals, don't fret it.  Be sure, however, to set the scan as "cable" or "cable-high", and select the ?frequency? QAM-256 instead of the other selections - there's a drop down.

Assuming you've got that setup you should be fine.

---

### Post by klc5555 on 2010-02-12
Acceptable QAM on a 1600 in Linux is frequently a thankless task.  I assume that the version of the driver you have and firmware are loading, since at least the analog half of the card is running. And lspci (and the tuner card setup in the mythtv backend setup) are recognizing by name the Samsung digital tuner in the card, and has reserved a DVB device for it.

But at minimum there are serious QAM signal-strength issues which can currently be fixed only by replacing the supplied cx18 driver with the QAM-optimized one under development by Devin Heitmuller that you'll need to compile yourself. And again after every kernel upgrade. Source available here: [http://www.kernellabs.com/hg/~dheitmueller/hvr-1600-perf-2](http://www.kernellabs.com/hg/~dheitmueller/hvr-1600-perf-2)

Scanning QAM on a 1600 in Mythtv is also sometimes its own issue. The card may actually be getting channel locks despite showing zero signal strength. Or it may not. Sometimes you may have to prepare a channels.conf file with a utility like dvb-apps and load it instead of doing a conventional scan. As described in the mythtv wiki page here: [http://www.mythtv.org/wiki/Adding_QAM_Channels_For_HDTV_Tuner_Cards](http://www.mythtv.org/wiki/Adding_QAM_Channels_For_HDTV_Tuner_Cards)

There may be other difficulties too, depending on mythtv version. All in all, the 1600 may not be as strong a choice for QAM as, say, something like the pchdtv hd-5500 which works close to perfectly out-of-the-box.

---

### Post by devin.heitmueller on 2010-02-18
For the record, the above mentioned driver work I did was not a "new driver", but rather a series of patches against the current driver which address some issues specific to the design of the HVR-1600 hardware.

Further, I would ask that if you are still using the hg tree on kernellabs.com, you should switch over to the mainline tree at [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb).  All of the patches have been merged upstream (and are set for inclusion in 2.6.33), and the tree on kernellabs.com is likely to disappear soon.

Cheers,

Devin

---

### Post by outleradam on 2010-02-21
Thank you david, I am currently compiling these drivers.    I noticed that I have to disable firedtv-1394 or the kernel will not compile the drivers.  it exits out like this:

```
home/adam/mykernel/v4l-dvb/v4l/et61x251_core.c:2500: warning: the frame size of 1256 bytes is larger than 1024 bytes
  CC [M]  /home/adam/mykernel/v4l-dvb/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/adam/mykernel/v4l-dvb/v4l/firedtv-avc.o
  CC [M]  /home/adam/mykernel/v4l-dvb/v4l/firedtv-ci.o
  CC [M]  /home/adam/mykernel/v4l-dvb/v4l/firedtv-dvb.o
  CC [M]  /home/adam/mykernel/v4l-dvb/v4l/firedtv-fe.o
  CC [M]  /home/adam/mykernel/v4l-dvb/v4l/firedtv-1394.o
/home/adam/mykernel/v4l-dvb/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/adam/mykernel/v4l-dvb/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/home/adam/mykernel/v4l-dvb/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/home/adam/mykernel/v4l-dvb/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/home/adam/mykernel/v4l-dvb/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/home/adam/mykernel/v4l-dvb/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/home/adam/mykernel/v4l-dvb/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/home/adam/mykernel/v4l-dvb/v4l/firedtv-1394.c:40: warning: 'struct hpsb_iso' declared inside parameter list
/home/adam/mykernel/v4l-dvb/v4l/firedtv-1394.c:40: warning: its scope is only this definition or declaration, which is probably not what you want
/home/adam/mykernel/v4l-dvb/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':

```after a few pages of errors, it returns an exit status of 2.

so anyways, here's what I did..

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make xconfig
disabled firedtv
save
exit from xconfig 
make -frame size errors  something about does not match expected 1024
sudo make install -sucessful
sudo make unload -I then received lots of errors from cx18 stating that it was in use
modprobe cx18
sudo reboot

 I know the perferred method is menuconfig, but it does not seem to make a difference in the process, xconfig is just easier to use.   It still does not work.  What am I doing wrong?

---

### Post by outleradam on 2010-02-21
this issue is still an issue.  for some reason I am only picking up a single QAM256 physical channel.

According to my HDHomeRun, this single physical channel is 77.  Channel 77 contains the following QAM256 "Programs".  These are the ONLY channels I can pick up on my HVR-1600.  my HdHomeRun gets nearly 110 channels which are on 9 other physical channels.

```
SCANNING: 541750000 (us-hrc:77)
LOCK: none (ss=93 snq=0 seq=0)
SCANNING: 543000000 (us-cable:77, us-irc:77)
LOCK: qam256 (ss=94 snq=100 seq=100)
PROGRAM: 302: 0 (encrypted)
PROGRAM: 600: 0 (encrypted)
PROGRAM: 601: 0 (encrypted)
PROGRAM: 602: 0 (encrypted)
PROGRAM: 901: 0
PROGRAM: 902: 0
PROGRAM: 903: 0
PROGRAM: 904: 0
PROGRAM: 905: 0
PROGRAM: 906: 0
PROGRAM: 907: 0
PROGRAM: 908: 0
PROGRAM: 909: 0
PROGRAM: 910: 0
PROGRAM: 911: 0
PROGRAM: 912: 0
PROGRAM: 913: 0
PROGRAM: 914: 0
PROGRAM: 915: 0
PROGRAM: 916: 0
PROGRAM: 917: 0
PROGRAM: 918: 0
PROGRAM: 919: 0
PROGRAM: 920: 0
PROGRAM: 921: 0
PROGRAM: 922: 0
PROGRAM: 923: 0
PROGRAM: 924: 0
PROGRAM: 925: 0
PROGRAM: 926: 0
PROGRAM: 927: 0
PROGRAM: 928: 0
PROGRAM: 929: 0
PROGRAM: 930: 0
PROGRAM: 931: 0
PROGRAM: 932: 0
PROGRAM: 933: 0
PROGRAM: 934: 0
PROGRAM: 935: 0
PROGRAM: 936: 0
PROGRAM: 937: 0
PROGRAM: 938: 0
PROGRAM: 939: 0
PROGRAM: 940: 0
PROGRAM: 941: 0
PROGRAM: 942: 0
PROGRAM: 943: 0
PROGRAM: 944: 0
PROGRAM: 945: 0
PROGRAM: 946: 0
PROGRAM: tsid=0x82B2
```



This is an example of a few channels I should be receiving

```
SCANNING: 451750000 (us-hrc:62)
LOCK: none (ss=94 snq=0 seq=0)
SCANNING: 453000000 (us-cable:62, us-irc:62)
LOCK: qam256 (ss=96 snq=100 seq=100)
PROGRAM: 25: 0
PROGRAM: 26: 0
PROGRAM: 27: 0
PROGRAM: 28: 0
PROGRAM: 29: 0
PROGRAM: 30: 0
PROGRAM: 31: 0
PROGRAM: 32: 0
PROGRAM: 33: 0
PROGRAM: 34: 0
PROGRAM: tsid=0x82CD
SCANNING: 457750000 (us-hrc:63)
LOCK: none (ss=94 snq=0 seq=0)
SCANNING: 459000000 (us-cable:63, us-irc:63)
LOCK: qam256 (ss=96 snq=100 seq=100)
PROGRAM: 35: 0
PROGRAM: 36: 0
PROGRAM: 37: 0
PROGRAM: 38: 0
PROGRAM: 39: 0
PROGRAM: 40: 0
PROGRAM: 41: 0
PROGRAM: 42: 0
PROGRAM: 43: 0
PROGRAM: 44: 0
PROGRAM: tsid=0x82CE
```

I don't know the technical terminology for the tsid, but I know that it can help me to determine a transport somehow.   

Is there a way I can force my card to recognize these channels, or tune them somehow using this data?

---

### Post by klc5555 on 2010-02-22
> **outleradam said:**
> this issue is still an issue.  for some reason I am only picking up a single QAM256 physical channel.

...  

Is there a way I can force my card to recognize these channels, or tune them somehow using this data?

If you have a functioning digital QAM Video Source already set up in the mythtv backend setup with some QAM tuner, all other QAM tuners in the myth installation ought to be able to use the same tuning information without needing to scan individually and separately. The tuning information is the same. If you connect the functioning QAM Video Source you have set up to the 1600 in Input Connections, mythtv may be able to tune the card properly despite the card's inability to scan.

Or not. Or, a selection of the stations will tune, but not others. Or you may have unacceptable artifacting in the tuned signal. This will mostly tend to be signal strength related. At that point, the only additional suggestions I can make would be to review the coax cabling/splitting you have set up to attempt to simplify it and preserve a stronger signal to the card's digital input, and/or to use a good line-drop amp or a good amplified splitter to help provide a stronger signal to the card.

Or (unless you rely on the 1600 for analog reception, e.g. from a cable box or DTA, for which service it is truly excellent) to take the 1600 out of the machine, pitch it in a high, long arc into the back yard (or alternatively use it in a Windows machine), and replace the card with something much less frustrating for QAM on Linux, like the smoothly-operating pchdtv hd-5500, or even one of the myriad of different cards (like the Avermedia A-180) that use the cheap Phillips digital tuner. These latter Phillips cards have their own infuriating quirks, but signal strength does not happen to be among them.

---

### Post by outleradam on 2010-02-22
I have read contradictory information on that.  A QAM source will only work with cards of the same type.  I've read this over and over.

---

### Post by klc5555 on 2010-02-23
I have my AverMedia 180s, my pchdtv hd-5500s and my one QAM-capable 1600 (before I concluded that it just wasn't as good at QAM as the others and moved it over to full-time DTA capture) on the same QAM-configured video source. Across 2 backends.

But external tuners like your HD-Homerun may have different requirements -- by the umbrella-word "type" you may be referring to QAM vs. analog vs. OTA digital vs. satellite; or to tuners that require things like external channel-change scripts for ir-blaster use, where each such tuner will require an individual Video Source.

But in lieu of using an already-configured QAM source, I can only, as before, recommend measures to improve signal strength, or switching to a better QAM card.

---

### Post by outleradam on 2010-04-29
The 1600 is fine for digital scanning. I think this is a problem with the kernel. It's digital. It's there and it's in the right format, or it's not. Obviously if windows can do it, and Ubuntu cannot, then it's a problem with Linux.

---

### Post by klc5555 on 2010-04-29
> **outleradam said:**
> The 1600 is fine for digital scanning. I think this is a problem with the kernel. It's digital. It's there and it's in the right format, or it's not. Obviously if windows can do it, and Ubuntu cannot, then it's a problem with Linux.

True, but that's no help to the person who wants to add a good digital tuner card to his Mythbuntu backend. Hauppauge can't themselves be bothered with Linux drivers for their cards, and while the 3rd-party drivers for the 1600 may eventually make the card as good for digital on Linux as it is reputed to be on Windows, that is not quite the case yet. Though for some users, QAM on the 1600 on Linux may already be good enough. And that's fine.

So the Mythbuntu or other Myth user has 3 choices regarding the 1600: 1) use it, tweak it and its driver where possible, and be satisfied with the 1600 within its current QAM limitations on Linux, while waiting for driver development to catch up (as it eventually did for, e.g., the analog driver for the pchdtv hd-5500). 2) Dump Mythtv on Linux for some sort of Windows-based solution using the 1600; or 3) Use a different card for QAM on Linux.

I personally chose 3). Though if I manage to get a 2.6.33.3 kernel/modules to compile and boot properly, I'll give the recently merged cx18 driver a fresh look on QAM.

---

### Post by PopaTim on 2010-05-03
Do you have a windows pc that you could test or compare the 1600 to with something else Like your tv or dvd recorder. (I've never found how to display signal strength under myth)

The reason I ask is that My 1600 is the worst digital tuner ever. I get 80-90% signal stength on my tv from an antenna that is connected to it thru a vcr (yes they still exist) and an CECB; yet my 1600 can only sometimes get 3 or 4 of the 15 local channels. I say sometimes because the signal strength is so low that you can't actualy watch anything if the channel gets detected in the first place.

---

