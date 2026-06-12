---
title: "DVB-T Tuners not scanning in MythTV but OK in w_scan"
date: 2013-03-10
forum: Mythbuntu
---

### Post by ShonkyCH on 2013-03-10
Hi

I just "ported" over to Mythbuntu from Mythdora. I'm going for a clean install though. There's a lot of cruft in my old system that I'd like to let go so whilst I'll port in some things like recordings I want to leave the rest out.

So I installed 12.04.2 64 bit with little hassle. My Lifeview USB dual DVB-T tuners are both detected (4 tuners all up). w_scan works fine and finds all the expected channels/frequencies. tzap has no problem then tuning to them and gets a lock almost instantly.

However dvbscan cannot find anything and gives "unable to query frontend status". MythTV also appears to scan but finds nothing. When scanning in MythTV, the signal strength jumps all over the place. I increased the timeouts significantly but that just makes MythTV wait longer on each step.

Can anyone suggest what I might do here? The tuners worked fine previously on MythTV 0.26-2/3 version (I think) I had with Mythdora. It was fairly up to date at least.

Thanks
Christian

---

### Post by klc5555 on 2013-03-11
> **ShonkyCH said:**
> Hi

I just "ported" over to Mythbuntu from Mythdora. I'm going for a clean install though. There's a lot of cruft in my old system that I'd like to let go so whilst I'll port in some things like recordings I want to leave the rest out.

So I installed 12.04.2 64 bit with little hassle. My Lifeview USB dual DVB-T tuners are both detected (4 tuners all up). w_scan works fine and finds all the expected channels/frequencies. tzap has no problem then tuning to them and gets a lock almost instantly.

However dvbscan cannot find anything and gives "unable to query frontend status". MythTV also appears to scan but finds nothing. When scanning in MythTV, the signal strength jumps all over the place. I increased the timeouts significantly but that just makes MythTV wait longer on each step.

Can anyone suggest what I might do here? The tuners worked fine previously on MythTV 0.26-2/3 version (I think) I had with Mythdora. It was fairly up to date at least.

Thanks
Christian


Assuming that the detected tuners were also set up correctly in the "input cards" section of the mythbackend setup, have you been able to import the  channels.conf file that w_scan prepared for you into the backend setup via "mythtv-setup -> Input Connections -> Scan Channels -> *Scan Type: Import Channels.conf*" ?  This is the traditional workaround when mythtv scanning is broken, as it frequently is. Unfortunately, in some versions of mythtv, the import function also is reported to be broken or missing. The data may be added manually from the channels.conf into the "channel editor", channel-by-channel, using the workform provided by the "add channel" option. Doable if you have, say, 10 or 15 channels --a heck of a slog if you're receiving 50-ish. You could try just one channel as a test.

---

### Post by ShonkyCH on 2013-03-11
> **klc5555 said:**
> Assuming that the detected tuners were also set up correctly in the "input cards" section of the mythbackend setup, have you been able to import the  channels.conf file that w_scan prepared for you into the backend setup via "mythtv-setup -> Input Connections -> Scan Channels -> *Scan Type: Import Channels.conf*" ?  This is the traditional workaround when mythtv scanning is broken, as it frequently is. Unfortunately, in some versions of mythtv, the import function also is reported to be broken or missing. The data may be added manually from the channels.conf into the "channel editor", channel-by-channel, using the workform provided by the "add channel" option. Doable if you have, say, 10 or 15 channels --a heck of a slog if you're receiving 50-ish. You could try just one channel as a test.

Thanks for the reply. Was just coming back to post. I couldn't get it to work at all scanning. Importing from the w_scan channels.conf file didn't work either and gave some error like "Couldn't open file %1" which seems like a bug as you mention - I found a few references to that.

In the end I just imported the channels, dtv_multiplex etc tables from a backup (about 30 channels). Not ideal since I'll still have to manually create some new channels that were added since I last scanned. Fine since I had a backup but not so fine for someone new to MythTV...

After that MythTV seems to work perfectly changing channels. Haven't got the guide up and running yet, but if Live TV works, recording should be fine.

---

### Post by ShonkyCH on 2013-03-14
For the benefit of anyone who comes across this post, I was using the original packages that came with the 12.04.2 release  i.e. 0.25.2+fixes.20120802.46cab93-0ubuntu1

After an upgrade to the latest 0.25 version (currently 0.25.3+fixes.20130309.1e200d3-0ubuntu0mythbuntu2) channel scanning is working fine.

---

### Post by ShonkyCH on 2013-03-14
Sigh... Not as perfect as I had thought... The multiplexes where only populated in the channelscan_dtv_multiplex table. They were numbered differently and were not loaded into the dtv_multiplex table...

---

