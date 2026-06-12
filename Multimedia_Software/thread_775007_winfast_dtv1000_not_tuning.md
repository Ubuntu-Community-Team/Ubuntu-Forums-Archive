---
title: "winfast dtv1000 not tuning"
date: 2008-04-29
forum: Multimedia Software
---

### Post by funkdaddy on 2008-04-29
Hi guys,

Im new to both linux and ubuntu and am trying to get my winfast dtv1000 working under ubuntu 8.04 i386 desktop edition.
I run a tri boot and the card is working perfectly under XP and Vista with all the channels tuned correctly.

lspci returns:

05:01.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:01.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

On some forums I've noticed people reporting the card wont work without various modules loaded. I've added
cx88-dvb
dvb-core
cx88-alsa

to /etc/modules then rebooted

Heres what happens in some programs:

=============me-tv=================

[email]ahassell@ahassell-desktop:~/.me[/email]-tv$ me-tv
Me TV-Message: 30/04/08 09:45:33 - Me TV Version: 0.5.17
Me TV-Message: 30/04/08 09:45:33 - Loading glade file '/usr/share/me-tv/glade/me-tv.glade'
Me TV-Message: 30/04/08 09:45:34 - Creating EPG file at '/home/ahassell/.me-tv/epg.xml'
Me TV-Message: 30/04/08 09:45:34 - EPG file loaded
initial transponder 226500000 1 3 9 3 1 1 0
initial transponder 177500000 1 2 9 3 1 1 0
initial transponder 191625000 1 3 9 3 1 1 0
initial transponder 219500000 1 3 9 3 1 1 0
initial transponder 536625000 1 2 9 3 1 2 0
>>> tune to:
WARNING: >>> tuning failed!!!
>>> tune to: (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to:
WARNING: >>> tuning failed!!!
>>> tune to: (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to:
WARNING: >>> tuning failed!!!
>>> tune to: (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to:
WARNING: >>> tuning failed!!!
>>> tune to: (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to:
WARNING: >>> tuning failed!!!
>>> tune to: (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Me TV-Message: 30/04/08 09:46:03 - Done.
Me TV-Message: 30/04/08 09:46:04 - Channel file loaded

(me-tv:7538): Me TV-CRITICAL **: Exception message: 'There are no usable channels in the channels.conf file.'
Me TV-Message: 30/04/08 09:46:04 - Exception in void Application::init(): There are no usable channels in the channels.conf file.
Me TV-Message: 30/04/08 09:46:06 - Terminating application normally


=========tvtime===========

[email]ahassell@ahassell-desktop:~/.tvti[/email]me$ tvtime-scanner --input=0
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/ahassell/.tvtime/tvtime.xml
Scanning using TV standard PAL.
/home/ahassell/.tvtime/stationlist.xml: No existing PAL station list "Custom".

No tuner found on input 0. If you have a tuner, please
select a different input using --input=<num>.

[email]ahassell@ahassell-desktop:~/.tvti[/email]me$ tvtime-scanner --input=1
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/ahassell/.tvtime/tvtime.xml
Scanning using TV standard PAL.
/home/ahassell/.tvtime/stationlist.xml: No existing PAL station list "Custom".

No tuner found on input 1. If you have a tuner, please
select a different input using --input=<num>.

[email]ahassell@ahassell-desktop:~/.tvti[/email]me$ tvtime-scanner --input=2
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/ahassell/.tvtime/tvtime.xml
Scanning using TV standard PAL.
/home/ahassell/.tvtime/stationlist.xml: No existing PAL station list "Custom".

No tuner found on input 2. If you have a tuner, please
select a different input using --input=<num>.

==========xawtv===========

this actually runs and gets to the gui but when you set the frequency table to australia and scan it doesn't find any channels

==========kaffeine========

this was most promising as in the device settings it detected the
card as Conexant CX22702 DVB-T (although this number differs slightly from what is returned by the lspci command _shrug_). As with xawtv however it doesn't find any channels when tuning.

Any ideas gurus?

Thanks,
Adam

---

