---
title: "[SOLVED] One channel won't work in MythTV"
date: 2008-07-11
forum: Mythbuntu
---

### Post by tqft on 2008-07-11
Hardy x86_32, Fusion HDTV Pro tuner card, onboard intel graphics chip

Am in Brisbane Australia.

All channels except channel 7 work fine in MythTV.
Using vlc 0.8.6h channel 7 (all including HD) work.

Myth doesn't appear to be getting a channel lock on any of the channel 7 signals.

Nothing obvious in the log, signal strength on all the other channels appears fine and like I said channel 7 works fine in vlc. 

I have gone into the backend and deleted and rescanned all the channels already twice and imported the working channels.conf that use vlc uses - everything except channel 7 in myth is fine.

Nothing obvious in the logs (frontend or backend).

Any ideas?

---

### Post by Lindsay.Mathieson on 2008-07-11
Well that's weird :) What part of Brisbane? I'm in Camp Hill (southside) and get Seven/Seven HD fine.

When trying to view the channel do a Ctrl-F7 (or is it Alt-F7 ?) this brings up the signal strength box. Check the strength and BE (Bit Error) values.


One thing - what case and Power supply do you have? I had a Antec NSK2480 with the built in Earthwatts 380W PSU - it was interfering badly with Channel Seven. Once I replaced the PSU reception was much better.

---

### Post by tqft on 2008-07-12
Looks like you were right about the interference - deleted all the transports and that took the channels with them and rescanned and am getting a signal strength of 1% or 2 % on Seven HD - most HD channels I get 60+%.

I will open the case and vacuum it out and see if that helps.

Thanks

BTW - am in Runcorn

---

### Post by Lindsay.Mathieson on 2008-07-12
I presume Seven SD is only 1-2% as well.

---

### Post by ian dobson on 2008-07-12
Hi,

Only 1-2% signal quality, I'm suprised you get anything. On my system with 2 DVB-C cards I get problems when the signal strength is under about 45%.

Try using tzap to tune to one of your bad channels and see what ber/unc  (bit rate error/uncorrected block rate).

Have a look here [http://www.mythtv.org/wiki/index.php/Tzap](http://www.mythtv.org/wiki/index.php/Tzap)

Regards
Ian Dobson

---

### Post by tqft on 2008-07-12
[email]ian@tqft:~/.tzap[/email]$ tzap "7 HD Digital"
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 177500000 Hz
video pid 0x0441, audio pid 0x0000
status 00 | signal 0000 | snr 0000 | ber 00000000 | unc 00000000 | 
status 1e | signal 0000 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 00a0 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr fcfc | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr f4f4 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr e4e4 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr f1f1 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr f4f4 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr f6f6 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr fcfc | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr eeee | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr f2f2 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr f2f2 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr f6f6 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr fdfd | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr fefe | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr fcfc | ber 00000000 | unc 00000000 | FE_HAS_LOCK



[email]ian@tqft:~/.tzap[/email]$ tzap "7 Digital"
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 177500000 Hz
video pid 0x0401, audio pid 0x0402
status 00 | signal 0000 | snr 0000 | ber 00000000 | unc 00000000 | 
status 1e | signal 0000 | snr f6f6 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr f4f4 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr eded | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 01fc | snr f0f0 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr f2f2 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr fafa | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr f9f9 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr f2f2 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal 0000 | snr f5f5 | ber 00000000 | unc 00000000 | FE_HAS_LOCK


When opening Myth front end - watch tv and switching to 7 Digital or 7 HD only get a partial lock or no lock at at all.

Reading the link about tzap - it notes the snr should be steady and I notice the data above indicates it isn't, whereas TEN HD has a steady signal to noise ratio


[email]ian@tqft:~/.tzap[/email]$ tzap "TEN HD"
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 219500000 Hz
video pid 0x0202, audio pid 0x0000
status 00 | signal 0178 | snr 0000 | ber 00000000 | unc 00000000 | 
status 1e | signal 9fdc | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1e | signal a000 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK


Options?  Vacuum the inside of the machine?  Is there a way to reduce the sensitivity of myth to the snr as vlc plays 7 HD fine?

---

### Post by ian dobson on 2008-07-13
Hi,

Could you try increasing the tuning timouts in mythtv-setup. That might help abit. It looks as if mythtv isn't calculating the signal strength correctly.

Regards
Ian Dobson

---

### Post by Lindsay.Mathieson on 2008-07-13
What's your aerial - rooftop? is it split between many devices?

---

### Post by tqft on 2008-07-13
Thanks all - increasing the timeout in the backend seemed to have done the trick.

A bit slower changing channels in myth but sucj is life.

When I change to any 7 - it shows 0% signal but gets a lock and plays fine now.

On the aerial split - just one split.  When the guy installed the antenna about 3 months ago he checked the readings - about 80dB here in the study at the wall outlet.  We are halfway up the side of a hill and have a reasonably clear line of sight over the houses between us and the TV broadcast towers.

---

### Post by Lindsay.Mathieson on 2008-07-13
> **tqft said:**
> Thanks all - increasing the timeout in the backend seemed to have done the trick.

A bit slower changing channels in myth but sucj is life.

When I change to any 7 - it shows 0% signal but gets a lock and plays fine now.

Weird but good :) Glad things worked out.

---

