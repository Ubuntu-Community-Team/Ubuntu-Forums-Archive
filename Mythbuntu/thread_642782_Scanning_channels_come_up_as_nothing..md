---
title: "Scanning channels come up as nothing."
date: 2007-12-17
forum: Mythbuntu
---

### Post by Scrier on 2007-12-17
Hi, 

I have been struggling this weekend to set up frontend and backend storage system with little success.

First I had issues with the Nova T-500 card but that I solved with a great guide on the mythtv site. Although now I can't get passed the 3:rd and 4:th point of the installation. 
Setting up XMLTV from sweden stalls at 50% and if I force a shutdown it is there the next time I startup the config. So that makes it possible to go on to the next step although it probably isn't the right way to go.
At the Scanning for channel I tried all kinds of scan but never found any channels and signal strength didn't pass the 50% barrier. 

My backend had some issues as well so I had to use a special install cd for ubuntu then add mythtv on it. But I have tried to install the following kinds:
[LIST]
[*]**Backend** comp as Primary Backend, No Frontend, Ubuntu Desktop & **Frontend** comp as Frontend with Secondary Backend
[*]**Backend** comp as Secondary Backend, No Frontend, Ubuntu Desktop & **Frontend** comp as Frontend with Primary Backend
[*]**Frontend** as standard install
[*]**Frontend** as Primary Backend, Frontend
[/LIST]

With little success. I't feels sad but i'm on the verge of going to an xp solution :(

---

### Post by Scrier on 2007-12-18
Any suggestion on what I can try from here to get past the scanning of channels and / or get past the XMLTV for this system located in sweden?

---

### Post by WaggonerW on 2007-12-18
I have used dvb-utils when I was unable to find channels in Myth, but I'm not sure if this will also work on DVB-T cards. You can generate a channels.conf with a command-line scanner (I believe I used cscan). Shut down mythbacked before using dvb-utils, and after you have generated channels.conf, it can be imported into the mythbackend setup.

---

### Post by tohc1 on 2007-12-19
For your xmltv problem try alt-tab - the configuration window might come up as a text console.

For the scanning problem have you tried slowing down the tuning - (myth-setup > capture cards > recording options button) I have a nova-t 500 and got strange results when scanning without a delay of 25ms here. Also make sure you've turned the onboard amplifier on - i think its in the guide you used.

Don't worry too much about the signal strength indicators as I'm not convinced they work - I've never seen much change even between stronger/weaker channels.

---

### Post by Nikas on 2007-12-19
Yep. For the swedish source you have to press alt+tab to switch to the console window when it stalls at 50%. Swedb works great!

About signal strength... have you added "options dvb-usb-dib0700 force_lna_activation=1" to /etc/modprobe.d/options?

If not:

```

sudo gedit /etc/modprobe.d/options
Add this line to the file and reboot: options dvb-usb-dib0700 force_lna_activation=1

```

---

### Post by Scrier on 2007-12-20
I have added that config line and got xmltv to get information now about the channels I have, although the scanning still fails. I tried this
> sudo apt-get update
sudo apt-get install dvb-utils dvbstream
sudo -s -H
mkdir /root/.tzap
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/se-Skovde > /root/.tzap/channels.conf
And to run the scanner with XMLTV channels in it, channel strength came up to 60-70% now but still only timeouts. maybe im doing it right alkthough not knowing it, not sure how I can test it in a pure backend.

Also the SQL database couldn't be connected to from my backend and checking netstat shows that the channels is run on ip 0.0.0.0. Any ideas where to go from here would be appreciated.

---

### Post by smbm on 2007-12-20
Im having the same problem! Same hardware.

Tried the solution detailed in the post above only pointing to uk-Rowridge (our local transmitter) and am getting the following message. Can anyone decode it for me?

WARNING: filter timeout pid 0x0010

---

### Post by Scrier on 2007-12-21
This is the output I get when scanning channels:

> root@Backend:/home/scrier# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/se-Karlstad > /root/.tzap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/se-Karlstad
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 546000000 0 3 9 3 1 3 0
initial transponder 522000000 0 3 9 3 1 3 0
initial transponder 642000000 0 3 9 3 1 3 0
initial transponder 626000000 0 3 9 3 1 3 0
>>> tune to: 546000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 546000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 522000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 522000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 642000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 642000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 626000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 626000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

---

### Post by Nikas on 2007-12-21
> **Scrier said:**
> This is the output I get when scanning channels:

You can set the right frequency by your self. You can find which you should use at [http://www.teracom.se/?page=5835](http://www.teracom.se/?page=5835) (it's like 5 or 6 channels)

Check your channels and get the right "mhz" from "Omvandlingstabell (Digital tv)"

In Mythtv-setup.
```
Go to "5. Kanaleditor"
Select "Transporteditor"
Add your transports as follow:
Frekvens: Fyll i frekvensen i omvanlingstabellen som passar din sändare/kanal. Lägg till SEX nollor efter frekvensen.

```
For "Karlstad Sörmon" your frequencys should be:
650000000
674000000
546000000
642000000

```
Bandbredd: 8 Mhz
Inversion: Auto
Modulering: QAM 64
LP kodhastighet: 1/2
HP kodhastighet: 2/3
Överföringsläge: 8K
Skyddsintervall: 1/8
Hierarki: Ingen
```

Save all the transports and do a new channel search. Select "Söktyp: Full sökning av existerande transporter"


I can help you more in swedish if you contact me by pm.

**Edit:**
As you can see here:
INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:F EC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL _1_4:HIERARCHY_NONE
The "settings" are wrong. :) When the analog net in sweden was turned off the frequencys changed for digitaltv. Dont think the new ones exist in the files that comes with Myth.
I think that "se-Karlstad" are outdated.

**Edit2:**
Change se-Karlstad to:
```
# Sweden - Karlstad UPDATED
# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
T 650000000 8MHz 2/3 1/2 QAM64 8k 1/8 NONE
T 674000000 8MHz 2/3 1/2 QAM64 8k 1/8 NONE
T 546000000 8MHz 2/3 1/2 QAM64 8k 1/8 NONE
T 642000000 8MHz 2/3 1/2 QAM64 8k 1/8 NONE

```
and try that scan again if you want but you dont need it when it works from mythtv directly.

---

### Post by Nikas on 2007-12-28
Ok. The problem was that "Scrier" was trying to use a Nova T-500 with cable. (analog or DVB-C). The Nova T-500 card = DVB-T. (digital terrestrial)

---

