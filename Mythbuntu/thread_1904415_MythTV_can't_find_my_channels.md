---
title: "MythTV can't find my channels"
date: 2012-01-04
forum: Mythbuntu
---

### Post by squaregoldfish on 2012-01-04
Hi all,

This may well be a FAQ, but I'm afraid a lot of searching round the net and reading has only confused me.

After a new install of Ubuntu and MythTV, a channel scan turns up nothing. This isn't really surprising as I'm in the UK and my transmitter has just done the digital switchover meaning all the frequencies have changed. Running dvb's scan tool with a custom-built frequency table finds all the TV channels, and they're all watchable. (I have a channels.conf file from that.)

What I can't seem to do is tell MythTV what frequencies to scan so it will find the channels, or how exactly I'm supposed to get channels.conf into MythTV. What's the simplest/definitive way to do either of these? 

Everything I've read so far either didn't work or made vague hints about digging around in MythTV's database with no real explanation of what exactly I was meant to be doing. Some clear guidance would be very useful!

Thanks in advance,
Steve.

---

### Post by wyliecoyoteuk on 2012-01-04
Some more detailed information might help.

What version of :
Mythtv?
Ubuntu?
Model of DVBTV card?

For example:
I am running Mythbuntu 11.10 (Mythtv 0.24) with a Hauppuage WinTV nova-T500, and have no problems.

---

### Post by squaregoldfish on 2012-01-05
Ha! I knew I meant to add something to the bottom of the post....

Ubuntu 11.10
MythTV 2:0.24.0+fixes20110908.1de0431-0ubuntu1 (from Synaptic)
2x Hauppage Nova-T BVB-T [cx8800] (reported by MythTV)

Steve.

---

### Post by klc5555 on 2012-01-05
Traditionally you import a known working channels.conf file for a tuner card in  Mythtv by going into Input Connections for your tuner and hitting the Scan Channels button. Set the scan type to "import" and provide the path to your channels.conf file. 

Once the backend has been restarted, the channels supplied by your channels.conf should all be tunable as they were outside mythtv, but you will eventually need to edit the pertinent information (name, callsign, assigned channel in mythtv, and xmltvid) in the backend's Channel Editor to clean things up and to allow your grabber to supply the correct program scheduling information.

---

### Post by squaregoldfish on 2012-01-06
Hmm. I can't import my channels.conf.

After selecting Import, there's a drop-down box labelled Scan to Import, but there's nothing in the list and I can't type anything into the box.

:confused:

Steve.

---

### Post by wyliecoyoteuk on 2012-01-06
Are you selecting "import channels.conf" or "Import existing scan"?
If the first and you can't enter anything, it sounds like you have file permissions set wrong somewhere.
Are you a member of the mythtv group?

---

### Post by squaregoldfish on 2012-01-07
I only have two option - Full Scan or Import Existing Scan. No mention of importing channels.conf anywhere....

Steve.

PS I am a member of the mythtv group.

---

### Post by wyliecoyoteuk on 2012-01-07
I am using a standard install of Mythbuntu 11.10, and I get the import channels.conf option in the backend setup.

If you are using MythTV on top of a Ubuntu full install, it should be the same, but Obviously it is not The usual cause is a permissions error.

---

### Post by RoboJ1M on 2012-02-02
I got this working on uk-Rowridge and MythTV 0.24 with the following:

use "w_scan" to create a new custom initial tuning data file for your transmitter. You'll see w_scan pick up all the transports from the first one it finds, and it will correct the first one using data from itself.

Use this site: [http://www.digitaluk.co.uk/postcodechecker/main/index/dummy/NA/yes](http://www.digitaluk.co.uk/postcodechecker/main/index/dummy/NA/yes)

To check they correct six muxes are in that file, comment out the duff ones (you'll pick up every transmitter you can see)

In Myth:

Delete all channels and transports.
Manually add one transport from your file
Do a Scan Existing Transports and make sure you select the option to automatically add other transports.

After doing that, all my channels appeared.

I'm currently trying to find out how to get those files updated before 12.04 is released but I don't see how I can contact the powers that be. Anybody?

J.

---

### Post by squaregoldfish on 2012-02-02
OK, so after a bit of back and forth on IRC, I've discovered that I'd set up my tuner card as analog instead of digital. Since the Add Card screen came up with the card name straight away, I assumed it at figured everything out for me.

I am a dumbass.

---

