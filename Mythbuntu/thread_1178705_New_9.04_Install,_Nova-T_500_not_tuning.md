---
title: "New 9.04 Install, Nova-T 500 not tuning"
date: 2009-06-04
forum: Mythbuntu
---

### Post by GyroTech on 2009-06-04
I'm just trying to install MythBuntu 9.04 on my shiny new MSI Media Live with a Nova-T 500 in there. I've been following the guide [here]("http://parker1.co.uk/mythtv_ubuntu.php").
The system seems to have picked up both the tuners properly:
```
# grep -i dvb /var/log/messages
Jun  4 21:15:09 mythtv-lounge kernel: [   10.729900] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
Jun  4 21:15:09 mythtv-lounge kernel: [   10.729944] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Jun  4 21:15:09 mythtv-lounge kernel: [   10.730221] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
Jun  4 21:15:09 mythtv-lounge kernel: [   10.847209] DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
Jun  4 21:15:09 mythtv-lounge kernel: [   11.467809] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Jun  4 21:15:09 mythtv-lounge kernel: [   11.468095] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
Jun  4 21:15:09 mythtv-lounge kernel: [   11.473943] DVB: registering adapter 1 frontend 0 (DiBcom 3000MC/P)...
Jun  4 21:15:09 mythtv-lounge kernel: [   12.026190] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:10.0/0000:04:06.2/usb2/2-1/input/input7
Jun  4 21:15:09 mythtv-lounge kernel: [   12.028842] dvb-usb: schedule remote query interval to 50 msecs.
Jun  4 21:15:09 mythtv-lounge kernel: [   12.028846] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
Jun  4 21:15:09 mythtv-lounge kernel: [   12.029060] usbcore: registered new interface driver dvb_usb_dib0700
```
but trying to scan any of my local transmitters (as discovered [here]("http://www.dtg.org.uk/industry/coverage.html") to be Crystal Palace > Sandy Heath > Luton) just results in either turning failure or timeout like this:
```
# scan /usr/share/dvb/dvb-t/uk-CrystalPalace > /root/.tzap/channels.conf
scanning /usr/share/dvb/dvb-t/uk-CrystalPalace
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 505833000 0 3 9 1 0 0 0
initial transponder 481833000 0 2 9 3 0 0 0
initial transponder 561833000 0 2 9 3 0 0 0
initial transponder 529833000 0 3 9 1 0 0 0
initial transponder 578167000 0 3 9 1 0 0 0
initial transponder 537833000 0 3 9 1 0 0 0
>>> tune to: 505833000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
<<cut repeat of above>>
dumping lists (0 services)
Done.

```
or
```
# scan /usr/share/dvb/dvb-t/uk-SandyHeath > /root/.tzap/channels.conf
scanning /usr/share/dvb/dvb-t/uk-SandyHeath
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 641833000 0 3 9 1 0 0 0
initial transponder 665833000 0 2 9 3 0 0 0
initial transponder 650167000 0 2 9 3 0 0 0
initial transponder 842000000 0 3 9 1 0 0 0
initial transponder 626167000 0 3 9 1 0 0 0
initial transponder 674167000 0 3 9 1 0 0 0
>>> tune to: 641833000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 641833000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
<<cut repeat of above>>
dumping lists (0 services)
Done.

```
though there wasn't a transponder file for the Luton transmitter so I couldn't test that.

I know the tuner works because this box previously had Mythbuntu 8.04 on and (mostly) working before it had to be requisitioned for something else for a bit. Plus I'm also watching freeview on the main TV directly so I am getting a signal.

Anyone have any ideas for me?? Many thanks,

---

### Post by Lem on 2009-06-06
You sure you've done this step?;

Turn on the onboard amplifier or you will get very poor signal strength. It is possible that this will cause you to receive no signal at all due to the amplification of signal noise regardless of signal quality. 

sudo gedit /etc/modprobe.d/options
Add: options dvb-usb-dib0700 force_lna_activation=1 

I rebuilt my box recently and forgot this snippet of code and spent a couple of hours wondering why it wouldn't pick up any channels.

---

### Post by Neon Dusk on 2009-06-06
In 9.04 modprobe now needs .conf filenames

---

### Post by GyroTech on 2009-06-14
Sorry it's been so long to reply, I've been very busy lately.

So, the tuning problem is actually to do with the updated firmware as I later found [here]("http://ubuntuforums.org/showthread.php?t=1140411"). Once I copied the old firmware over the new one, scanning worked just fine.

---

