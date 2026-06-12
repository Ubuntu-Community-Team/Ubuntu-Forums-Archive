---
title: "Kaffein suddenly cannot stream/scan DVB-S channels"
date: 2015-08-10
forum: Multimedia Software
---

### Post by tarekeldeeb on 2015-08-10
Hi,

I installed ubuntu 15.04 x64 on a box with DVB-S card. Then I installed Kaffeine, with all KDE dependencies.
I was able to scan channels, view, record and timeshift. This went great for weeks.

Then I installed mythtv, which seems to have ruined everything.

Now I cannot even scan for channels.

```
$ sudo scan /usr/share/dvb/dvb-s/Nilesat101+102-7.0W 
scanning /usr/share/dvb/dvb-s/Nilesat101+102-7.0W
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: cannot parse'[CHANNEL]
'
ERROR: cannot parse'	DELIVERY_SYSTEM = DVBS
'
ERROR: cannot parse'	FREQUENCY = 10719000
'
ERROR: cannot parse'	POLARIZATION = VERTICAL
'
ERROR: cannot parse'	SYMBOL_RATE = 27500000
'
ERROR: cannot parse'	INNER_FEC = 3/4
'
ERROR: cannot parse'	INVERSION = AUTO
'
ERROR: cannot parse'[CHANNEL]
'
ERROR: cannot parse'	DELIVERY_SYSTEM = DVBS
'
ERROR: cannot parse'	FREQUENCY = 10723000
'
ERROR: cannot parse'	POLARIZATION = HORIZONTAL
'
ERROR: cannot parse'	SYMBOL_RATE = 27500000
'
ERROR: cannot parse'	INNER_FEC = 3/4
'
ERROR: cannot parse'	INVERSION = AUTO
'
ERROR: cannot parse'[CHANNEL]
'
ERROR: cannot parse'	DELIVERY_SYSTEM = DVBS
...

```

All transponders report such error.

Now I removed all mythtv packages, reboot, but with no luck with Kaffeine. How can I possible return back to the state without mythtv or whatever that ruined the kaffeine DVB-s playback and stream?

Support me, please.

---

### Post by masand2 on 2015-10-29
Hi [**[COLOR=#000000]tarekeldeeb[/COLOR]**]("http://ubuntuforums.org/member.php?u=235451"),

I had the same issue today. It helped to use the files below /usr/share/dvb/dvb-legacy/dvb-c in my case instead of those in /usr/share/dvb/dvb-c/ (mind the "dvb-legacy").

So you might want to try /usr/share/dvb/dvb-legacy/dvb-s/... for your case.

The next step was to try mplayer with the /dev/dvb/adapter0/dvr0 device, but mplayer always crashes before showing a picture. I will try other players tomorrow, but if anyone has some hints - they´re surely welcome :-)
(Ubuntu 15.10 on a Raspberry Pi2 and a Sundtek MediaTV Pro III)

Regards,
masand

---

### Post by tarekeldeeb on 2015-10-30
I fixed the problem, finally. Checking the dmesg showed the tuner needed to load a firmware file on demand, but the file was not found and got timeout. I googled the missing file and copied it to /lib/firmware and everything got back working.

---

