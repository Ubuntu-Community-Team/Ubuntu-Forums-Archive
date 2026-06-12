---
title: "DTVMux, Error: Invalid S2 modulation system parameter '1', aborting"
date: 2009-11-17
forum: Mythbuntu
---

### Post by gahrens on 2009-11-17
Dear folks,

after my upgrade to 9.10 tv is gone. My Dates:
BACKEND
Library API      : 0.22.20091023-1
QT Version       : 4.5.2
FRONTEND
MythTV Version   : 22594
MythTV Branch    : branches/release-0-22-fixes
Network Protocol : 50
Library API      : 0.22.20091023-1
TV-CARD TECHNISAT SKYSTAR HD 2
01:06.0 Multimedia controller: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] (rev 01)
GRAPHICS CARD
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8300] (rev a2)

OUTPUT MYTHTV BACKEND (ERROR MESSGE)
2009-11-16 19:08:19.150 DTVMux, Error: Invalid S2 modulation system parameter '1', aborting.
2009-11-16 19:08:19.150 DVBChan(1:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(3): Failed to initialize multiplex options
2009-11-16 19:08:19.151 TVRec(1) Error: Failed to set channel to 3. Reverting to kState_None
2009-11-16 19:08:19.155 TVRec(1): Request: Program(no) channel() input() flags(KillRec,)
2009-11-16 19:08:19.155 TVRec(1): ClearFlags(EITScannerRunning,) -> RunMainLoop,CancelNextRecording,
2009-11-16 19:08:19.156 TVRec(1): ClearFlags(PENDINGACTIONS,) -> RunMainLoop,CancelNextRecording,
2009-11-16 19:08:19.157 TVRec(1): SetChannel(3) -- end

KAFFEINE plays tv correct.
If I start tv the screen goes black, I see ...waiting and after approx 6 seconds the menu comes back. A rescan of channels don't bring success.
Had anybody an idea how to debug this. 

Thanks for any support.

Best regards
Gert

---

### Post by SiHa on 2009-11-17
Not sure I'll be able to help much, other than to maybe point you in the right direction. I had a similar isssue:```
Error: SetChannelByString(3): Failed to initialize multiplex options
```Turned out it was because my DVB-S and DVB-T carts had swapped ID's. You've only got the one tuner, but it does look as if Myth is treating it as the wrong type. Maybe it thinks it's DVB-S instead of DVB-S2??

---

### Post by gahrens on 2009-11-18
Hi SiHa,

first thanks for your support. Three days ago I deleted all my channels and tryed a manually channel scan. Without success. Channel scan begins an my Desk freezes after  approx 30.Seconds. Before I used the channels from my 9.4 Installation which works till today. I think ist a difficulty between the hardware driver an the new mythtv 0.22versin. My mythtv fronend id stb0899. I use the s2-liplianin driver source to compile my card driver.

---

### Post by ianhaycox on 2009-11-23
I had this, with different hardware, after upgrading to 9.10.

I deleted all cards, inputs, channels etc, but it would not scan.

Eventually I found that the DB table - dtv_multiplex had been corrupted or not updated correctly by the upgrade.

```

$ mysql -uuser -ppass mythconverg
mysql> update dtv_multiplex set mod_sys = 'DVB-S';

```

fixed it.  I haven't tried DVB-S2

Make sure you have a Db backup beforehand.

---

### Post by gahrens on 2009-11-24
Hi Ian,

thanks a lot. That's it. But how do you insert new channels, scan for new if mythtv uses a false DTVMux parameter 1 instead of 'DVB-S' ?

Best regards Gert

---

