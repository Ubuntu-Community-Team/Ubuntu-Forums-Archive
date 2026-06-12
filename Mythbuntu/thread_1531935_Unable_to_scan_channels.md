---
title: "Unable to scan channels"
date: 2010-07-15
forum: Mythbuntu
---

### Post by Joey5337 on 2010-07-15
I have problems filling the channel list.
In MythTV Backend Setup, Point 4 and 5, I try to do a channel scan. 
I enter the following values:
Input: [DVB:/dev/dvb/adapter0/frontend0] (DVBInput)
Desired Services: TV, [X] Only Free, [ ] Test Decryptability, Scan-Type Full Scan (Tuned),
frequency 12551500, Polarity Vertical, Symbol Rate 22000000, Mod Sys DVB-S, 
FEC Auto, Modulation QPSK, Inversion Auto, Rolloff 0.35

When I press Next, I get the error message "Failed to find any channels".


Second try: import the channels.conf-File, I got from the scan-Utility. 
Inputs: Scan-Type: Import channels.conf, File Location /tmp/channels.conf
Same error message.


Third try: I started "/usr/bin/mythtv-setup.real" from a terminal. Attempting to scan, the console shows the following messages:

2010-07-15 23:48:53.866 DiSEqCDevTree, Warning: No device tree for cardid 1
2010-07-15 23:48:55.012 DVBSM(/dev/dvb/adapter0/frontend0), Warning: Can not count Uncorrected Blocks
                        eno: Operation not supported (95)
2010-07-15 23:48:55.057 DiSEqCDevTree, Error: No root device tree node!
2010-07-15 23:48:55.058 DVBChan(1:/dev/dvb/adapter0/frontend0) Error: Tune(): Failed to setup DiSEqC devices
2010-07-15 23:48:55.284 ChanImport: No channels to process..

What does this mean? Do I need DiSeq? How can I disable it?

What can I do?

Joey


Background Info:

My box is a Via C7 with 1,5 GHz, using a TechnoTrend Budget S2-3200 and I installed the current Mythbuntu 10.04 from CD
The box is intended as headless Backend but is currently also running a frontend. Im' living in Germany and want to receive Astra 19.2
I'm new to Mythtv, Videocards, satellite TV etc., but I have general Linux-Experience.
The Videocard ist working. "scan /usr/share/dvb/dvb-s/Astra-19.2E | tee channels.conf" finds some channels and I can watch them with mplayer.

---

### Post by bance on 2010-07-15
It is important to set dseq to LMB, myth needs a setting here to allow a scan. it can be a bit flaky so try to do it a few times.......... eventually it will work...... I hope ths helps!

---

### Post by Joey5337 on 2010-07-16
Thanks! Solved.

Even if you don't have digital satellite Equipment, you have to config DiSEqC as "LNB".
DiSEqC is a digital protocol for controlling Switches or Motors at your dish.
If you use the traditional, analog LNB or Multiplexer, your Tuner uses a Voltage and a 20kHz signal to switch between Hi-/Lowband and Hor/Vert Polarisation. Although not beeing a DiSEqC-Device, MythTV must control this switch and the configuration Options are at the same place as for DiSEqC-Devices.

Step-By-Step:
1. Start the Mythtv Backend Setup
2. Select Option 2 (TV-Cards)
3. Select your card and open it with Enter
4. Open the DiSEqC-Options and Select Devive-Type "LNB"
5. Go Back, Save your settings.

After this, my channel scan worked.

Thanks, Joey

---

### Post by bance on 2010-07-17
No prob's.... maybe mark your thread solved?

(edit original post, thread tools> button top right)

---

