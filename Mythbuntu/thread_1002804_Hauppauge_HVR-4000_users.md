---
title: "Hauppauge HVR-4000 users?"
date: 2008-12-05
forum: Mythbuntu
---

### Post by IntuitiveNipple on 2008-12-05
I need some assistance in finalising the configuration of an HVR-4000. In particular I'm having problems with it detecting a DVB-S signal.

There doesn't appear to be a DC voltage output on the DVB-S connector (expecting close to 15 volts but seeing 0.2V). Having spoke to Hauppauge technical support there should be a voltage on the connector (to power the LNB) when it is using it.
It could be faulty, but possibly related to this is the IR remote control stopped working after a system restart and whilst investigating I noticed the kernel log is now showing that the tveeprom isn't being found - earlier it was logged correctly.

**[COLOR="DarkRed"]Could someone with an HVR-4000 and a multimeter measure and report the DC voltage on the DVB-S connector? [/COLOR]**

Also, can you describe how you begin channel scanning for the DVB-S tuner since it requires a frequency and data-rate to be entered - I've been using 10714000/22000000 so far.

Finally, is the input on /dev/videoX the UHF tuner? Mythbuntu reports it as the DVB-S/S2 but I suspect it is just displaying the adapter name.

**Background**

I've just installed Mythbuntu 8.10 on Intrepid. The system has the Hauppauge HVR-4000 DVB-S/S2, DVB-T, UHF and FM quad receiver.

I've built the v4lb trunk and created symlinks for /dev/dvb/adapter1/* so that Mythbuntu can 'see' both tuner front-ends:
```

sudo mkdir -p /dev/dvb/adapter1
for src in /dev/dvb/adapter0/*1; do  dest="$(echo $src | sed -e 's/adapter0/adapter1/' -e 's/\(\/[a-z]*\)1$/\10/')"; sudo ln -s $src $dest; done

```
I'm going to add **udev** rules to do this automatically.

I set up an EIT video source and paired that with both DVB:0 (the DVB-S/S2 input) and DVB:1 (the DVB-T input).

Mythbuntu correctly scans and receives the DVB-T EPG.

Separately, I've successfully configured and tested lirc with the HVR-4000 remote control.

---

### Post by IntuitiveNipple on 2008-12-05
After a 'cold' restart the tveeprom is being logged correctly as:
```

grep tveeprom /var/log/dmesg
[   33.302745] tveeprom 1-0050: Hauppauge model 69009, rev B2A0, serial# 1241516
[   33.302828] tveeprom 1-0050: MAC address is 00-0D-FE-12-F1-AC
[   33.302977] tveeprom 1-0050: tuner model is Philips FMD1216ME (idx 100, type 63)
[   33.303054] tveeprom 1-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   33.303134] tveeprom 1-0050: audio processor is CX882 (idx 33)
[   33.303196] tveeprom 1-0050: decoder processor is CX882 (idx 25)
[   33.303257] tveeprom 1-0050: has radio, has IR receiver, has no IR transmitter

```
and the Infra Red receiver is also working correctly.

However, trying to tune the DVB-S is still failing to find anything and there is still no significant DC voltage on the DVB-S connection.

---

### Post by IntuitiveNipple on 2008-12-05
Using Kaffeine I've been able to prove that DVB-S and DVB-T are working. It successfully scans all channels at Astra 28.2E ( more than 650 TV) and the DVB-T channels too.

That proves that the v4l-dvb drivers built from trunk are working okay.

So it seems as if MythTV is having problems. I've not been that impressed with it so far, not least the inconsistent configuration interfaces and descriptive terms (different menus/options describe the tuner inputs differently, e.g. some start numbering at zero, others at one, or 'video source' as a description for the electronic program guides).

How are other HVR-4000 users doing?

---

### Post by IntuitiveNipple on 2008-12-24
Returned to this issue today after using Kaffeine for a while and finally made some progress. The key problem is the lack of clear up-to-date documentation on the MythTV 0.21 DVB-S set-up procedure and confusing menus and options buried deep in the configuration.

I discovered, through messing with the back-end configuration, that to achieve a scan the LNB option needs setting for the tuner. This is non-intuitively found behind the DiSEqC button.

So, when setting up the tuner (Capture Card -> DVB DTV Capture Card), press the **DiSEqC** button, select LNB and then the LNB Preset (I used "Universal (Europe)").

Now it is possible to do a scan, but again there are hidden caveats.

By default the Scan option selects "Full Scan (Tuned)" and expects a transponder frequency, polarity, symbol rate and FEC (Forward Error Correction) value.

It turns out these can be found in **/usr/share/doc/dvb-utils/examples/scan/dvb-s/**. I needed the Astra-28.2E settings file, which contains:
```

# Astra 28.2E SDT info service transponder
# freq pol sr fec
S 10773000 H 22000000 5/6
S 11778000 V 27500000 2/3

```
Entering these values into two sessions with the Scan option found *some* channels, but not all.

The fact that a scan now shows a progress dialog in front of the full-screen found-channels list indicates things are working, but it still seemed to end very quickly - compared to the several minutes Kaffeine took to scan.

I tried an alternative Scan option, "**Full Scan of Existing Transports**". This time the scan took several minutes and the resulting channel list looks very similar to the one Kaffeiene found (more than 500 channels).

After the scan I downloaded the channel icons, set the starting channel number (found in the channel editor's list), then closed out of the set-up and allowed it to update the database (mythfill).

Starting the front-end and doing "Watch TV" it finally brought up a picture.

---

