---
title: "Afatech AF9013 DVB-T timeout?"
date: 2012-04-21
forum: Mythbuntu
---

### Post by Korvar on 2012-04-21
I have a KWorld PlusTV Dual DVB-T Stick (DVB-T 399U) - a dual tuner Freeview DVB-T usb stick.

It works, except that every so often MythTV seems to lose it - it behaves as if there are no tuners for live TV, generates 0-length recordings, etc.  

Sometimes if I remove the stick, reboot the Mythbuntu box and re-attach, it works again, but more often I have to delete the capture cards and re-add them from scratch.  At which point everything works again for a length of time.

I am new at Mythbuntu, although I've been an Ubuntu user for a while, so I'm not sure what information would be useful to provide.  Please let me know if there's anything needed.

**Edit**It's just done it again - the stick was working fine watching live TV, I stopped watching (via MythTV player on Windows) just before a scheduled recording and the stick isn't lighting up, the recording shows as 0bytes, although the backend status on MythWeb claims it is recording.

Dmesg output:

```


  138.552023] usb 1-7: new high speed USB device number 4 using ehci_hcd
[  138.692675] input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.1/input/input4
[  138.692831] generic-usb 0003:1B80:E399.0003: input,hidraw2: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:1d.7-7/input1
[  138.967127] IR NEC protocol handler initialized
[  138.983680] IR RC5(x) protocol handler initialized
[  138.995042] IR RC6 protocol handler initialized
[  139.021510] IR JVC protocol handler initialized
[  139.034318] IR Sony protocol handler initialized
[  139.053338] lirc_dev: IR Remote Control driver registered, major 250 
[  139.056456] IR LIRC bridge handler initialized
[  139.328556] dvb-usb: found a 'KWorld PlusTV Dual DVB-T Stick (DVB-T 399U)' in cold state, will try to load a firmware
[  139.375653] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[  139.444635] dvb-usb: found a 'KWorld PlusTV Dual DVB-T Stick (DVB-T 399U)' in warm state.
[  139.445941] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  139.446301] DVB: registering new adapter (KWorld PlusTV Dual DVB-T Stick (DVB-T 399U))
[  139.475763] af9013: firmware version:4.95.0.0
[  139.481393] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[  139.509674] MXL5005S: Attached at address 0xc6
[  139.509680] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  139.510094] DVB: registering new adapter (KWorld PlusTV Dual DVB-T Stick (DVB-T 399U))
[  140.224812] af9013: found a 'Afatech AF9013 DVB-T' in warm state.
[  140.228187] af9013: firmware version:4.95.0.0
[  140.242197] DVB: registering adapter 1 frontend 0 (Afatech AF9013 DVB-T)...
[  140.242343] MXL5005S: Attached at address 0xc6
[  140.242352] Registered IR keymap rc-empty
[  140.242445] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-7/rc/rc0/input5
[  140.242503] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-7/rc/rc0
[  140.242507] dvb-usb: schedule remote query interval to 500 msecs.
[  140.242512] dvb-usb: KWorld PlusTV Dual DVB-T Stick (DVB-T 399U) successfully initialized and connected.
[  140.255622] usbcore: registered new interface driver dvb_usb_af9015
[  142.092552] audit_printk_skb: 6 callbacks suppressed
[  142.092557] type=1400 audit(1335015680.771:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1804 comm="apparmor_parser"
[  142.096125] type=1400 audit(1335015680.775:15): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1805 comm="apparmor_parser"
[  142.096979] type=1400 audit(1335015680.775:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1805 comm="apparmor_parser"
[  142.097302] type=1400 audit(1335015680.775:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1805 comm="apparmor_parser"
[  142.100683] type=1400 audit(1335015680.779:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1806 comm="apparmor_parser"
[  142.103874] type=1400 audit(1335015680.779:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=1807 comm="apparmor_parser"
[  142.107725] type=1400 audit(1335015680.783:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=1808 comm="apparmor_parser"
[  142.194302] init: apport pre-start process (1835) terminated with status 1
[  142.225964] init: apport post-stop process (1851) terminated with status 1
[  142.308134] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  142.317672] NFSD: starting 90-second grace period
[  142.795165] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  143.036784] init: plymouth-stop pre-start process (2040) terminated with status 1
[  200.489528] init: mythtv-backend main process (1086) killed by TERM signal
[10101.224133] af9015: recv bulk message failed:-71
[10101.224139] af9015: af9015_rc_query: failed:-1
[10101.224142] dvb-usb: error -1 while querying for an remote control event.
[10101.235505] af9015: recv bulk message failed:-75
[10101.235512] af9013: I2C read failed reg:d507
[18382.540173] af9015: recv bulk message failed:-71
[18382.540180] af9015: af9015_rc_query: failed:-1
[18382.540182] dvb-usb: error -1 while querying for an remote control event.
[18382.565548] af9015: recv bulk message failed:-75
[18382.565553] af9013: I2C read failed reg:d507
[23971.592464] af9015: command failed:2
[23971.592472] af9013: I2C read failed reg:d2e5

```

---

### Post by BicyclerBoy on 2012-04-21
How does windows come into this?
Do you have a windows frontend ?

The errors could be caused by IR remote interface..
Do you use the IR remote Rx on the USB tuner stick ?

I am not sure if this option can be applied to your device:
#/etc/modprobe.d/dvb-options.conf
options dvb_usb disable_rc_polling=1

There are later/other f/w versions mentioned here...
[http://www.linuxtv.org/wiki/index.php/KWorld_USB_Dual_DVB-T_TV_Stick_%28DVB-T_399U%29](http://www.linuxtv.org/wiki/index.php/KWorld_USB_Dual_DVB-T_TV_Stick_%28DVB-T_399U%29)

Reads like another tuner support saga..

---

### Post by Korvar on 2012-04-21
> **BicyclerBoy said:**
> How does windows come into this?
Do you have a windows frontend ?


I have no idea what's relevant, so I'm including all the information I can...

I use this: [http://www.sudu.dk/mythtvplayer/](http://www.sudu.dk/mythtvplayer/)

> The errors could be caused by IR remote interface..
Do you use the IR remote Rx on the USB tuner stick ?

Nope.  Don't even know if it has one.

> I am not sure if this option can be applied to your device:
#/etc/modprobe.d/dvb-options.conf
options dvb_usb disable_rc_polling=1

There are later/other f/w versions mentioned here...
[http://www.linuxtv.org/wiki/index.php/KWorld_USB_Dual_DVB-T_TV_Stick_%28DVB-T_399U%29](http://www.linuxtv.org/wiki/index.php/KWorld_USB_Dual_DVB-T_TV_Stick_%28DVB-T_399U%29)

Reads like another tuner support saga..

Ah, I thought the 4.95.0 was the latest... let's take 5.1.0 for a spin.

---

### Post by BicyclerBoy on 2012-04-21
You are right to post all info..

Your dmesg log shows:
- really long boot time...
- at time = 200 mythbackend is killed why ?
- time = 10101 could be IR polling error..

Does your windows "other mythFE" viewer directly connect to/stream from the tuner card for liveTV or does it use mythbackend ?

i.e. do you have to kill the backend server to watch liveTV on that "other" windows viewer
Is your backend & frontend on separate boxes?

Is this windows viewer running in wine or virtual machine on the linux box ?

---

### Post by Korvar on 2012-04-22
> **BicyclerBoy said:**
> You are right to post all info..

Your dmesg log shows:
- really long boot time...
- at time = 200 mythbackend is killed why ?


After each time the recordings stop working, I reboot and re-add the cards via Applications -> System -> MythTV Backed Setup, which closes mythbackend.  I'm presuming that's why mythbackend shows up as being killed.

> - time = 10101 could be IR polling error..

Does your windows "other mythFE" viewer directly connect to/stream from the tuner card for liveTV or does it use mythbackend ?

i.e. do you have to kill the backend server to watch liveTV on that "other" windows viewer


As far as I can tell MythTV Player uses the mythbackend - I certainly don't have to kill the backend server.  Just tested it now - with the backend server down, MythTV Player fails - specifically, complains it can't find a back-end.

> Is your backend & frontend on separate boxes?

Is this windows viewer running in wine or virtual machine on the linux box ?

Backend is a Mythbuntu box, frontend is my Windows desktop.  More precisely, I run MythTV player on my Windows desktop.  

The Mythbuntu box was set up to be both frontend and backend, but I haven't yet put my TV in place, so I don't run the front end at the moment.

---

### Post by Chris Musampa on 2012-04-22
No help but the same occurs with the KWorld PCI card using the Afatech chip.  I did read the problem would go if you avoid switching between the two tuners, not so, I tried only using one in mythtv and the problem still occurs.

[http://francisfisher.me.uk/problem/2012/using-the-kworld-pc160-2t-with-mythtv-on-ubuntu-linux-11-10/](http://francisfisher.me.uk/problem/2012/using-the-kworld-pc160-2t-with-mythtv-on-ubuntu-linux-11-10/)

---

### Post by BicyclerBoy on 2012-04-22
Can you try a complete cold reboot after tuner lock up? So leave powered down for 20 seconds..

The warm start/reboot does not load the firmware etc. AFAIK The firmware is only needed for analogue (mpeg encoder).

If nothing else this may stop you having to delete & re-add the tuner into mythtv-setup..

mythtv-setup must be able to probe/reset the tuner somehow..
Maybe you can use vl4ctl to reset card..
[http://www.linuxtv.org/wiki/index.php/V4L_TV_Viewing](http://www.linuxtv.org/wiki/index.php/V4L_TV_Viewing)

There was a suggestion (on another afatech page) that setting the tuner to be "released when not in use".

---

### Post by Korvar on 2012-04-24
> **Chris Musampa said:**
> No help but the same occurs with the KWorld PCI card using the Afatech chip.  I did read the problem would go if you avoid switching between the two tuners, not so, I tried only using one in mythtv and the problem still occurs.

[http://francisfisher.me.uk/problem/2012/using-the-kworld-pc160-2t-with-mythtv-on-ubuntu-linux-11-10/](http://francisfisher.me.uk/problem/2012/using-the-kworld-pc160-2t-with-mythtv-on-ubuntu-linux-11-10/)

It's not had to switch between tuners for a bit, and it's stayed up for a couple of days, so it looks like that might be the issue.  Today's schedule has a tuner switch, so we will see if that breaks everything...

---

### Post by Korvar on 2012-04-24
> **BicyclerBoy said:**
> Can you try a complete cold reboot after tuner lock up? So leave powered down for 20 seconds..

The warm start/reboot does not load the firmware etc. AFAIK The firmware is only needed for analogue (mpeg encoder).

If nothing else this may stop you having to delete & re-add the tuner into mythtv-setup..


I'll give that a go if/when it goes down again.  It's been behaving itself for a couple of days now, but that may be due to it not trying to switch tuners.

I also did
> **BicyclerBoy said:**
> 
#/etc/modprobe.d/dvb-options.conf
options dvb_usb disable_rc_polling=1

... so we will see.

> 
mythtv-setup must be able to probe/reset the tuner somehow..
Maybe you can use vl4ctl to reset card..
[http://www.linuxtv.org/wiki/index.php/V4L_TV_Viewing](http://www.linuxtv.org/wiki/index.php/V4L_TV_Viewing)

There was a suggestion (on another afatech page) that setting the tuner to be "released when not in use".

I had it set up to be released when not in use, and that didn't seem to help.  I turned that off, and it's been okay for a couple of days.  But the real test will come when it tries to switch tuners :)

---

### Post by Korvar on 2012-04-24
Well, it finally went down again - a bit before it was going to change tuners, or use both, so I'm not sure if that is actually the problem.  Going to do the remove/re-add thing again, see if that helps at all.

```


[   15.780746] dvb-usb: found a 'KWorld PlusTV Dual DVB-T Stick (DVB-T 399U)' in cold state, will try to load a firmware
[   16.144562] IR Sony protocol handler initialized
[   16.699152] lirc_dev: IR Remote Control driver registered, major 250
[   17.044879] IR LIRC bridge handler initialized
[   17.087710] init: failsafe main process (650) killed by TERM signal
[   17.202166] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[   17.282127] dvb-usb: found a 'KWorld PlusTV Dual DVB-T Stick (DVB-T 399U)' in warm state.
[   17.282279] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   17.282941] DVB: registering new adapter (KWorld PlusTV Dual DVB-T Stick (DVB-T 399U))
[   18.292124] af9013: firmware version:5.1.0.0
[   18.297747] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   18.418058] MXL5005S: Attached at address 0xc6
[   18.418063] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   18.418440] DVB: registering new adapter (KWorld PlusTV Dual DVB-T Stick (DVB-T 399U))
[   19.140869] af9013: found a 'Afatech AF9013 DVB-T' in warm state.
[   19.144246] af9013: firmware version:5.1.0.0
[   19.158241] DVB: registering adapter 1 frontend 0 (Afatech AF9013 DVB-T)...
[   19.158399] MXL5005S: Attached at address 0xc6
[   19.158405] dvb-usb: KWorld PlusTV Dual DVB-T Stick (DVB-T 399U) successfully initialized and connected.
[   19.172342] usbcore: registered new interface driver dvb_usb_af9015
[   20.831254] type=1400 audit(1335292972.512:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=780 comm="apparmor_parser"
[   20.835253] type=1400 audit(1335292972.512:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=781 comm="apparmor_parser"
[   20.835833] type=1400 audit(1335292972.512:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=781 comm="apparmor_parser"
[   20.836365] type=1400 audit(1335292972.516:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=781 comm="apparmor_parser"
[   20.881950] type=1400 audit(1335292972.560:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=782 comm="apparmor_parser"
[   20.885962] type=1400 audit(1335292972.564:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=783 comm="apparmor_parser"
[   21.195012] type=1400 audit(1335292972.876:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=784 comm="apparmor_parser"
[   22.744274] init: apport pre-start process (828) terminated with status 1
[   22.764230] type=1400 audit(1335292974.444:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=867 comm="apparmor_parser"
[   22.789395] init: apport post-stop process (871) terminated with status 1
[   23.429915] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.645330] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   23.679623] NFSD: starting 90-second grace period
[   25.265394] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[   25.265400] tg3 0000:02:00.0: eth0: Flow control is on for TX and on for RX
[   25.265546] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   35.816014] eth0: no IPv6 routers present
[   42.445532] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   43.527920] init: plymouth-stop pre-start process (1521) terminated with status 1
[   47.417237] af9015: command failed:1
[   47.417245] af9013: I2C write failed reg:d005 len:1
[   47.418233] af9015: command failed:2
[   47.418238] af9013: I2C read failed reg:d607
[   47.418854] af9015: command failed:2
[   47.418859] af9013: I2C read failed reg:d607
[   47.423937] af9015: command failed:2
[   47.423945] af9013: I2C read failed reg:d607

```

---

### Post by Korvar on 2012-05-04
Well, I changed the tuners cards recording options:

[LIST]
[*]Open DVB card on demand set to **on**
[*]Use DVB card for active EIT scan to **off**
[*]DVB Tuning Delay to 1000ms.
[/LIST]

It's been behaving for days now, even recording two things at one time, which was suggested as being an issue.  So I can only assume one or all of those three fixed things...

---

### Post by superfrank on 2013-01-07
I know this is an old post but I've some useful information as I've struggled with this issue a lot. 

Basically EIT polling confuses the tuner firmware eventually. Turning EIT polling off solves 99% of the occurrences, but it still happens from time to time. Its probably a bug in the firmware and it occurs in both 4.95 and 5.1 (or whatever the last two firmware versions are called).

If the issue ever happens you need to do a cold boot. That probably means switching off at the mains, or if you have the USB version, you can unplug and replug the stick after a while.

The biggest clue that it has happened is that dmesg shows this kind of stuff:

> [18382.565548] af9015: recv bulk message failed:-75 
[18382.565553] af9013: I2C read failed reg:d507 
[23971.592464] af9015: command failed:2 
[23971.592472] af9013: I2C read failed reg:d2e5

---

### Post by Korvar on 2013-01-07
Yeah, it looks like EITS is the key.  Just had to re-do my setup, had the same problems with the card, searched for this thread, and re-applied the solution, and it's been working fine ever since.  Might be time to put a [Solved] on the initial post :)

---

