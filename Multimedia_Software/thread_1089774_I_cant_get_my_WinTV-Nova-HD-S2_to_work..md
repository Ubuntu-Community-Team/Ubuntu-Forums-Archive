---
title: "I cant get my WinTV-Nova-HD-S2 to work."
date: 2009-03-07
forum: Multimedia Software
---

### Post by sam667 on 2009-03-07
Hi,

I hope someone can help me with this.
I've had a Mythbuntu installation working on my machine for some time but with the HDD crashing I decided to take the opportunity to upgrade the machine with a WinTV-Nova-HD-S2 card along with the budget card.

It seems the machine is seeing the card alright:
```

root@loke:~/scan-s2# dmesg | grep -i dvb
[    8.551470] saa7146: register extension 'budget_ci dvb'.
[    8.551522] budget_ci dvb 0000:02:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    8.551576] DVB: registering new adapter (TT-Budget/WinTV-NOVA-CI PCI)
[    8.593701] input: Budget-CI dvb ir receiver saa7146 (0) as /devices/pci0000:00/0000:00:1e.0/0000:02:05.0/input/input6
[    9.304236] DVB: registering frontend 0 (ST STV0299 DVB-S)...
[    9.305544] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected]
[    9.561359] tveeprom 1-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[    9.806498] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[    9.806506] cx88/2: registering cx8802 driver, type: dvb access: shared
[    9.806513] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]
[    9.806521] cx88[0]/2: cx2388x based DVB/ATSC card
[    9.935965] DVB: registering new adapter (cx88[0])
[    9.935974] DVB: registering frontend 1 (Conexant CX24116/CX24118)...
[  226.006675] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  226.006686] firmware: requesting dvb-fe-cx24116.fw

```

and 

```
root@loke:~/scan-s2# dmesg | grep -i firm
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[  226.006675] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  226.006686] firmware: requesting dvb-fe-cx24116.fw
[  226.050825] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[  229.726923] cx24116_load_firmware: FW version 1.23.86.1
[  229.726963] cx24116_firmware_ondemand: Firmware upload complete

```

Now the problem is MythTV wont scan any channels on the new card, and I havent managed to (having looked at posts on this forum) to make mplayer or Kaffeine to work with the card.

If I use scan-s2 I get nothing:
```
root@loke:~/scan-s2# scan-s2 -a 1 dvb-s/Astra-28.2E 
API major 5, minor 0
scanning dvb-s/Astra-28.2E
using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
initial transponder DVB-S  10773000 H 22000000 5/6 AUTO AUTO
initial transponder DVB-S2 10773000 H 22000000 5/6 AUTO AUTO
initial transponder DVB-S  11778000 V 27500000 2/3 AUTO AUTO
initial transponder DVB-S2 11778000 V 27500000 2/3 AUTO AUTO
----------------------------------> Using DVB-S
FE_SET_PROPERTY DTV_CLEAR failed: Operation not supported
FE_SET_PROPERTY DTV_CLEAR failed: Operation not supported
----------------------------------> Using DVB-S2
FE_SET_PROPERTY DTV_CLEAR failed: Operation not supported
FE_SET_PROPERTY DTV_CLEAR failed: Operation not supported
----------------------------------> Using DVB-S
FE_SET_PROPERTY DTV_CLEAR failed: Operation not supported
FE_SET_PROPERTY DTV_CLEAR failed: Operation not supported
----------------------------------> Using DVB-S2
FE_SET_PROPERTY DTV_CLEAR failed: Operation not supported
FE_SET_PROPERTY DTV_CLEAR failed: Operation not supported
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

Can anyone see anything thats standing out? Or help me get this card to work? I miss my mythtv :(

---

### Post by spicemuseum on 2009-03-10
The instructions here worked for me...

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000)

---

### Post by sam667 on 2009-03-12
Thanks, I got it to work... well it did, and now its not anymore :S

I cant scan a frequency through MythTV, the signal strength is 85% byt snr is 0... it then fails saying "No signal".

I managed to get it working but after a reboot it seems to have lost everything.

---

### Post by RuthlessK on 2009-07-21
Lo,

Did you ever get it working?

I've just bought the card and it works fine on my vista (dirty word I know) Install it on ubuntu 9.04 machine all seams well apart from I don't get any signal or lock. Is this a driver error or firmware? I'm new to linux so not sure what to do next :(

I've read a few of the thread and have tried most but still no joy :confused:

---

### Post by Neon Dusk on 2009-07-21
The firmware supplied with 9.04 is corrupt - [launchpad link](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/363682).

---

### Post by RuthlessK on 2009-07-21
I noticed this when I ran dmesg

```
[  654.184011] cx24116_cmd_execute() Firmware not responding
[  654.184017] cx24116_firmware_ondemand: Writing firmware to device failed
[  654.184037] cx24116_firmware_ondemand: Firmware upload failed
[  654.184040] cx24116_cmd_execute(): Unable initialise the firmware
[  658.671218] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  658.671226] cx88-mpeg driver manager 0000:03:01.2: firmware: requesting dvb-fe-cx24116.fw
[  658.679362] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
```

I take it thats why it's not working? ](*,)

---

### Post by Neon Dusk on 2009-07-22
Yes, it looks like you've got the corrupt firmware.

If you follow the launchpad link you'll see how to download working firmware.

---

### Post by RuthlessK on 2009-07-22
I've now installed the Firmware and no longer get the error message :) But I still cannot get a signal when scanning. If I remove the card and stick it in my Vista Machine it works so that eliminates the Card and Cable.

Any Suggestions? I'm so close now, must be ?

---

### Post by Neon Dusk on 2009-07-23
What are using to scan for channels and what satelleties are you scanning?

---

### Post by RuthlessK on 2009-07-23
The Satelite dish I have is a minidish with quad LNB, the satelite i'm trying to scan is the Astra 28 etc (the default one that sky uses) I'm using the mythubuntu software to scan for channels. 

At present I have a sky+ box using two of the connections and a FreeSat box in the bed room on the 3rd and last but least the PCI card in my PC room on the 4th.

As far as I can tell all is working apart from the scanning bit. 

Cheers

Ruthless

---

### Post by Neon Dusk on 2009-07-23
It may be worthwhile trying a scan out with Mythtv.
First stop the mythbackend '/etc/init.d/mythbackend stop'
Then run 'scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf'

---

### Post by RuthlessK on 2009-07-23
I ran the scan and got loads of channels :D copied them into my channels.conf and am now in the process of scanning with mythtv. 

Signal @ 89%
Signal/noise @ 74%
Scan: =========> @ 67% so far

Scan finished and all looks well, apart from when I start the frontend and click on Watch TV the screen goes blank and then returns to the same main screen again.

my channels.conf is in /home/mythtv/channels.conf 

by the way cheers for your help Neon I really appreciate it :)

---

### Post by Neon Dusk on 2009-07-24
Can you double check your backend settings against [http://parker1.co.uk/mythtv_freesat.php](http://parker1.co.uk/mythtv_freesat.php).

If they look fine then you'll need to have a look at /var/log/mythtv/mythfrontend.log to see why Watch TV doesn't work.

Edit: 

It may be that you haven't configured DisEqC. In Mythbackend -> Capture Card Setup -> DiSEqC -> Create LNB and set to (Universal (Europe)

---

### Post by RuthlessK on 2009-07-25
Almost their now :)

Got pictures now and lots of channels, just one problem now the live TV looks like is not buffering properly, it's like it lags or something. Audio is out of sink as well :confused:

---

### Post by Neon Dusk on 2009-07-26
Have you tried a different [playback profile](http://www.mythtv.org/wiki/Playback_profiles) in 'Setup->TV Settings->Playback -> Playback Profiles' ?

---

### Post by RuthlessK on 2009-07-27
> **ruthlessk said:**
> almost their now :)

got pictures now and lots of channels, just one problem now the live tv looks like is not buffering properly, it's like it lags or something. Audio is out of sink as well :confused:lol silly me I didn't install the drivers for my Nvidia gts8800 card, all of the channels are smooth except BBC HD which is a little bit laggy. Which is my next thing to sort. 

_todo list_
BBC HD laggy
remove Unknown channels
rename channels
sort out remote as not working properly
read up on why it records all the channels I watch?

I was also looking at the mythweb, what plugins would you recommend?

---

### Post by RuthlessK on 2010-01-10
Not going well :(

Mythtv work well on 9.04, decidied to try 9.10 but can I get it to work :( keep getting **0 -- Found 15 probable channels** when scanning channels. at the end of the scan it states **Found 130 new conflicting channels**.

My channels.conf file is fine.

Any help would be great!

---

### Post by hibit on 2010-02-07
I'm afraid I have the same issue on upgrading 9.04 to 9.10 with my WinTV Nova-HD-S2. Channel scan in backend setup results apparently in hundreds of conflicting channels. Even after manually adding those, trying to view them fails with messages in the logs about missing PID table entries. Thus far no combination of reinstall, trying to avoid conflicts by not configuring my other DVB-T card, deleting all channels etc. seems to fix the issue. Is it possible that the software is trying to scan S2 but using S settings?

---

### Post by RuthlessK on 2011-05-15
Hi,

I used to have mythtv working and it was great, a few pc's later and I thought I'd slap it back on, but I'm having problems.

Got firmware working,
Ran a scan - 'scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf' no issues all went well. 

But for some strange reason it won't import into mythv - **failed to find any channels**

I tried the:
mkdir ~/.mplayer
cp channels.conf ~/.mplayer
mplayer dvb://"BBC THREE" 

Thats works fine! When I do get it to scan I just keep getting - Timed out, **4 possible channels etc**

Any suggestions?

---

