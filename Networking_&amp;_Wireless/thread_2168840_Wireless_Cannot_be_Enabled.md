---
title: "Wireless Cannot be Enabled"
date: 2013-08-19
forum: Networking &amp; Wireless
---

### Post by scojopa on 2013-08-19
[COLOR=#333333][FONT=Lucida Grande]I have been troubleshooting this today and cannot get the card enabled. I am starting to think it is hardware but wanted to get some feedback first.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Thinkpad T430s, ubuntu 12.10  x64[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I have been running this distro for months and did not perform any upgrades recently. I was not having any issues until this morning - walked away from machine and when I came back it was offline. [/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Toggled the Hardware switch[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Toggled FnF5[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]reset bios (bios does not show any Wireless - could that be from resetting to default while it is hard blocked?)[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]reset network interface[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]pulled out battery[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]dmesg : ilwwifi [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]**RF_Kill bit toggled to disable radio**[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]rfklist: phy0:Wireless LAN Soft blocked: no [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]**Hard blocked: yes**[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]ifconfig -a [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]_does _[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]list wlan0[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]lshw -C network shows network *Disabled Centrino Ultimate-N 6300 WLAN0[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Does anyone have any suggestions - really stuck here. Thank you in advance. ScoPA[/FONT][/COLOR]

---

### Post by zealibib slaughter on 2013-08-19
I use to know exactly how to fix this issue.  I believe answer #2 is what you are needing but I'm not sure anymore [http://askubuntu.com/questions/9816/wireless-shows-up-as-disabled-how-can-i-get-it-working](http://askubuntu.com/questions/9816/wireless-shows-up-as-disabled-how-can-i-get-it-working)  I have had problems with some wifi cards just locking out anywhere from minutes to years after install.  Its for 10.04 but I used one of these solutions as recently as 12.10 (i have it bookmarked for this very reason)

---

### Post by scojopa on 2013-08-19
all the values in NetworkManager.state are set to true

---

### Post by praseodym on 2013-08-19
Check these:

[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

---

### Post by scojopa on 2013-08-19
tried those already - listed in OP

in dmesg:

thinkpad_acpi: radio switch found; radios are disabled

...and a bit later....

iwlwifi : Detected Intel(R) Centrino(R) Ulitimate - N 6300 AGN. REV=0x74
iwlwifi : L1 Enabled; Disabling L0S
microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
iwlwifi: RF_KILL it toggled to disable radio
iwlwifi: device EEPROM VER-0x43a, CALIB=0x6
iwlwifi: Valid TX ant: 0x7 RX ant: 0x7
iwlwifi: Tunable channels: 13 802.11bg, 23 802.11a channels
Registered LED device: phy0-led
cfg80211: Ignoring Regulatory request Set by core since the driver users its own custom regulatory domain
ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
.....

I did have a Virtual Desktop guest open  - Wifi was working and when I came back (10minutes) it was disabled.

---

### Post by Karlchen on 2013-08-19
Hello, scojopa.

Stumbled across a German thread which holds an approch which worked at minimum for one person.
The thread is here: [WLAN einschalten]("http://www.linuxmintusers.de/index.php?topic=13721.msg145248#msg145248") (Switch on WLAN)
The person who reports the problem and reports that one of the offered solution actually has solved his problem is n8user.
As I do not assume that you do read and understand German, here is the summary:

The reported symptoms are pretty similar to yours, though the notebook is a Lenovo.
The steps which solved the problem are [these]("http://www.linuxmintusers.de/index.php?topic=13721.msg145226#msg145226"):

[LIST]
[*]Enter the BIOS setup. 
[*]Reset everything to BIOS defaults 
[/LIST]

The problem reporting person at first was a little bit loathe to accept this advice. Yet, as everything else had failed he did. And much to his amazement, this did solve his problem. The wifi card was no longer hard blocked.
The explanation was that the Windows system (dual boot system, Windows and Linux) had somehow changed the state of the wifi adapter.
Resetting the BIOS setup to default values somehow made the machine recognize the actual state of the wifi adapter.
As a consequence Linux could use it (again).

I cannot promise that the same steps will solve your case, too. Yet, it might be worth a try.

Kind regards,
Karl

---

### Post by scojopa on 2013-08-19
Karl thanks for the replies.  I did reset the bios as per my Op. Again there is no wireless appearing now in the bios. Might actually be hardware?

---

### Post by scojopa on 2013-08-21
Spoke to Lenovo - Wireless does not appear in the bios when it is working. So back to the drawing board. 

Any good tools to troubleshoot. In short I cannot get Hard Blocked to YES when I run rklist unblock all

---

### Post by praseodym on 2013-08-21
Please show
```

lsmod
```

---

