---
title: "Mythtv timeout scanning HAUPPAUGE NOVA-T 500 PCI Dual"
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by austway on 2007-07-20
I'm trying to get this card working with Feisty. I have followed a number of guides including:
[http://wiki.efficientpc.co.uk/index.php/Install_Nova-T_500_On_Ubuntu_Linux](http://wiki.efficientpc.co.uk/index.php/Install_Nova-T_500_On_Ubuntu_Linux)

The card seems to be recognized OK when I check with dmesg.

The scan command produces a valid channels.conf file for my area.

The tzap command produces output like this:

[email]ken@ken-desktop:~/.tzap[/email]$ tzap "ABC HDTV"
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 226500000 Hz
video pid 0x090a, audio pid 0x0000
status 03 | signal cdcb | snr 0000 | ber 001fffff | unc 00000000 | 
status 1f | signal cddc | snr 0000 | ber 000000a0 | unc 00000abf | FE_HAS_LOCK
status 1f | signal cdcb | snr 0000 | ber 000000a0 | unc 00000abf | FE_HAS_LOCK
status 1f | signal cdd1 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal cdcc | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal cdcb | snr 0000 | ber 00000220 | unc 00000000 | FE_HAS_LOCK
status 1f | signal cdc8 | snr 0000 | ber 00000000 | unc 00000033 | FE_HAS_LOCK
status 1f | signal cdce | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal cdd2 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal cdcb | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal cdd0 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK

Mythtv recognizes the card in the "Capture Cards" area. However, when I go into "Input Connections" and select "Scan for channels" I get the continuous message "Timeout scanning -- no signal". The Scan Progress indicates a Signal Strength up to 80% at times during this process.

Any suggestions to resolve this would be greatly appreciated.

---

### Post by drifting on 2007-09-02
Sorry to say I have the same problem !

Mine was working fine and two things happened, ITV changed their lineup and I did an update to the backend server. Did notice a kernel update.

I have tried everything, even went so far as to install the latest vlb driver. Tzap works, just Myth cant seem to tune the card. The only way I got my channels back was to import the channel.conf, however on leaving mythbacend setup it moans about starting on channel 3 as it does not exist and offers to correct it. It doesn't do anything just hangs 
:(

Really depressed now, wished I knew what it was, Wifey is driving me nuts as she is missing programs.

Paul.

---

### Post by sygin on 2008-01-05
Hi,

What firmware are you using. Is it 1.10?

I would follow the guide at:
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

You would need to rebuild your linux.tv modules as described in the guide.

Then use MythTV to get channels, if it does not work I would test my tv signal with a freeview box and if the signal is good, try the process again with a fresh Ubuntu Gutsy install.

MythTV should just find channels. 

Cheers
Sygin

---

### Post by zzztownsend on 2008-01-08
my nova-t-500 worked by following SYGINs link above. I changed a setting in mythtv under 'capture cards' then 'recording options' then there is a setting to change the tuning timeout - i changed this from 0 ms to 25 ms and the card tuned in perfectly

sorry if this is a bit vague but I'm at work so I'm going from memory

good luck

cheers

matt

---

### Post by drifting on 2008-01-10
Thanks guys for all the replies, I went back to basics and reinstalled the drivers etc for the card, and reconfigured, now all is well.

Paul.

---

