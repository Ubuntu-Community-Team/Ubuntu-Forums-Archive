---
title: "Problems with card Hauppauge WINTV-PVR-150 MCE"
date: 2012-10-31
forum: Mythbuntu
---

### Post by ogogon on 2012-10-31
Good day!
I have a problem with the card Hauppauge WINTV-PVR-150 MCE.

For receive analogue television signal of city cable network, I bought PCI-card Hauppauge WINTV-PVR-150 MCE.

Then I run the configurator Mythtv ba&#1089;kend and installed it this card. Configurator has found a file in the /dev and identified the card type.

Unfortunately, further ba&#1089;kend stopped running. When start directly, he writes that he can not set the channel in tuner and stopped.
After removing tuner card in configurator backend run properly.

I install Mythbuntu from mythbuntu-12.04.1-desktop-amd64.iso

**How do I solve**[B] this problem?
How can test the tuner in Linux?[/B]

Ogogon.

---

### Post by klc5555 on 2012-10-31
> **ogogon said:**
> ...

 Configurator has found a file in the /dev and identified the card type.

...

Ogogon.

The PVR-150 is a very old card, and has worked well in Linux for a long time.

1) Mythbackend Setup may have identified the card wrong. The PVR-150 card is a MPEG card. Setup usually thinks this card is v4l-analog. If you don't change the setting for this card from v4l-analog to MPEG, then the card certainly will not work and mythbackend may not start.

2) You can also test if your particular PVR-150 card works at all in your particular Linux installation, from a command line on your desktop (without any Mythtv running) by using the old utility ivtv-tune (in the Ubuntu package ivtv-utils). You can tune the PVR-150 to a particular channel or frequency, capture what the card is receiving, and play back what it receives using any video player. If the card can't do this, something is wrong outside of Mythtv.

I don't know where you are or what country's analog frequency table you use. But the PVR-150 card and utility will tell you what it knows as follows:
```
ivtv-tune --list-freqtable
```

It will list frequency tables. One of these frequency tables should be yours. Let's say it's "us-cable". And let's say you know that your cable has a station on channel 4.
```
ivtv-tune --freqtable=us-cable --channel=4
```will tune the PVR150 to channel 4.

The PVR-150 should now already be capturing everything on channel 4. Did Linux put the card on /dev/video0? If it did, you can now do the command```
cat /dev/video0 > test.mpg
``` This will start making a recording file "test.mpg" of the program being captured on channel 4. You can view (and listen to) this file with any video player you wish to use: mplayer, or xine, or VLC, for example. Either while the file is still recording, or after you have killed the recording process with the key combination "ctrl c"

If this video capture has worked, then at least you know that your PVR-150 card physically works, and works in your Linux installation. If the card has passed this test, but there is still a problem, then it must be in the Mythtv setup alone.

---

### Post by nickrout on 2012-10-31
> **klc5555 said:**
> The PVR-150 is a very old card, and has worked well in Linux for a long time.

1) Mythbackend Setup may have identified the card wrong. The PVR-150 card is a MPEG card. Setup usually thinks this card is v4l-analog.no it doesn't, v4l is just the forst choice of many>  If you don't change the setting for this card from v4l-analog to MPEG, then the card certainly will not work and mythbackend may not start.

2) You can also test if your particular PVR-150 card works at all in your particular Linux installation, from a command line on your desktop (without any Mythtv running) by using the old utility ivtv-tune (in the Ubuntu package ivtv-utils). You can tune the PVR-150 to a particular channel or frequency, capture what the card is receiving, and play back what it receives using any video player. If the card can't do this, something is wrong outside of Mythtv.

I don't know where you are or what country's analog frequency table you use. But the PVR-150 card and utility will tell you what it knows as follows:
```
ivtv-tune --list-freqtable
```

It will list frequency tables. One of these frequency tables should be yours. Let's say it's "us-cable". And let's say you know that your cable has a station on channel 4.
```
ivtv-tune --freqtable=us-cable --channel=4
```will tune the PVR150 to channel 4.

The PVR-150 should now already be capturing everything on channel 4. Did Linux put the card on /dev/video0? If it did, you can now do the command```
cat /dev/video0 > test.mpg
``` This will start making a recording file "test.mpg" of the program being captured on channel 4. You can view (and listen to) this file with any video player you wish to use: mplayer, or xine, or VLC, for example. Either while the file is still recording, or after you have killed the recording process with the key combination "ctrl c"

If this video capture has worked, then at least you know that your PVR-150 card physically works, and works in your Linux installation. If the card has passed this test, but there is still a problem, then it must be in the Mythtv setup alone.

---

### Post by SAKeeler on 2012-11-01
It comes down to the card not being compatible with 64 bit.  try 32 bit and it should work.  I have one of those cards as well, there is something in regard to the actuall hardware that limits it to 32 bit systems.  ( been to long to recall exactly what the issue is, and i've moved on to a Ceton digital tuner anyway )

---

### Post by klc5555 on 2012-11-01
I'm aware of a bug in the Windows drivers for this card that prevent it from working on 64-bit Windows systems with more than 2 Gigs memory. But I'm not aware that 64-bit Linux is a problem for this card beyond the IR frequently not working in those models that have it.

Has anyone else had a problem with this card in 64-bit Ubuntu? Is this a real, known bug for this card?

It would be good if the original poster would report back on whether he has made any additional attempt to operate the card on his system.

---

### Post by SAKeeler on 2012-11-04
I could be mistaken in my understanding of the issue, as i said, I moved on from this card a while back.  but at the time i was trying to get it working under my 64 bit based Ubuntu box, most of what i was reading stated it would only work under 32 bit systems due to a limitation of the chip used.  I'll try to find some documentation on it.

---

### Post by klc5555 on 2012-11-04
OK.

I still use this card frequently, but not in 64 bit and not in Mythtv, so I haven't kept up with this particular subset of problems.

On the other hand, the original poster seems to have vanished, so the issue we were trying to solve may well be moot.

---

### Post by ogogon on 2012-11-04
I've done the recommended command and got the following:
> ogogon@myth:~$ ivtv-tune --list-freqtable
Frequency Maps:
us-bcast
us-cable
us-cable-hrc
us-cable-irc
japan-bcast
japan-cable
europe-west
europe-east
italy
newzealand
australia
ireland
france
china-bcast
southafrica
argentina
australia-optus
ogogon@myth:~$ ivtv-tune --freqtable=us-cable --channel=4
/dev/video0: 67.250 MHz
ogogon@myth:~$ cat /dev/video0 > test.mpg
^C
ogogon@myth:~$ ls -alg test.mpg 
-rw-rw-r-- 1 ogogon 15138816 &#1087;&#9579;&#1087;&#9580;&#1103;&#9616;&#1087;&#9568;.  5 03:58 test.mpg
ogogon@myth:~$ 
While viewing a file test.mgp seen "snow" screen TV.
However, the program mythbatskend does not want to run.

> ogogon@myth:~$ mythbackend
2012-11-05 04:02:53.746820 C  mythbackend version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org]("http://www.mythtv.org")
2012-11-05 04:02:53.746861 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2012-11-05 04:02:53.746868 N  Enabled verbose msgs:  general
2012-11-05 04:02:53.746895 N  Setting Log Level to LOG_INFO
2012-11-05 04:02:53.746961 I  Added logging to the console
2012-11-05 04:02:53.746972 I  Added database logging to table logging
2012-11-05 04:02:53.747129 N  Setting up SIGHUP handler
2012-11-05 04:02:53.747208 N  Using runtime prefix = /usr
2012-11-05 04:02:53.747229 N  Using configuration directory = /home/ogogon/.mythtv
2012-11-05 04:02:53.747387 I  Assumed character encoding: ru_RU.UTF-8
2012-11-05 04:02:53.747911 N  Empty LocalHostName.
2012-11-05 04:02:53.747925 I  Using localhost value of myth
2012-11-05 04:02:53.778354 N  Setting QT default locale to ru_US
2012-11-05 04:02:53.778434 I  Current locale ru_US
2012-11-05 04:02:53.778491 E  No locale defaults file for ru_US, skipping
2012-11-05 04:02:53.780858 I  Current MythTV Schema Version (DBSchemaVer): 1299
2012-11-05 04:02:53.781331 I  Loading ru translation for module mythfrontend
2012-11-05 04:02:53.782082 N  MythBackend: Starting up as the master server.
2012-11-05 04:02:53.784989 E  TVRec(1): Problem finding starting channel, setting to default of '3'.
2012-11-05 04:02:53.785603 E  InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2012-11-05 04:02:53.785684 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/video0
2012-11-05 04:02:53.785719 E  Problem with capture cardsCard 1failed init
2012-11-05 04:02:53.785756 W  MythBackend: No valid capture cards are defined in the database.
2012-11-05 04:02:53.786564 E  Scheduler: No channel sources defined in the database
ogogon@myth:~$ 
Antenna cable, I connected to the video card's tv-input.
With the command 'chmod' I allow the group 'other' to read and write devices /dev/video*.
> ogogon@myth:/dev$ ls -alg video*
crw-rw-rw-+ 1 video 81, 0 &#1087;&#9579;&#1087;&#9580;&#1103;&#9616;&#1087;&#9568;.  5 03:25 video0
crw-rw-rw-+ 1 video 81, 3 &#1087;&#9579;&#1087;&#9580;&#1103;&#9616;&#1087;&#9568;.  5 03:25 video24
crw-rw-rw-+ 1 video 81, 1 &#1087;&#9579;&#1087;&#9580;&#1103;&#9616;&#1087;&#9568;.  5 03:25 video32
ogogon@myth:/dev$ **That I have configured not correctly?**

Ogogon.

---

### Post by nickrout on 2012-11-04
> **ogogon said:**
> I've done the recommended command and got the following:
While viewing a file test.mgp seen "snow" screen TV.
However, the program mythbatskend does not want to run.

Antenna cable, I connected to the video card's tv-input.
With the command 'chmod' I allow the group 'other' to read and write devices /dev/video*.
**That I have configured not correctly?**

Ogogon.you are starting mythbackend wrong. It is a system service and is started by running ```
sudo service mythtv-backend start
```To do otherwise will run things as the wrong user with wrong permissions.

No need to run chmod, mythbuntu sets up all the permissions properly for you.

---

### Post by klc5555 on 2012-11-05
Well, at least by tuning and getting "snow" it appears that the hardware is not locking up, and that the kernel drivers and firmware are loaded and may be working. 

If your particular area's analog frequency table is in fact "us-cable", you may wish to try the test again on some other channels in the range of channels 2-99 that you suspect may have an analog signal on them, to see whether you can get a real signal and not just "snow". If you can do this, then you will know for certain that your PVR-150 is OK and performing correctly, and your only remaining challenge will be to configure Mythtv.

Do not bother to run the test on channels 5 or 6, however. Experience has shown that these two particular analog channels tend to get wiped out by RF interference from your PC's power supply and are not really usable by onboard analog tuner cards.

---

### Post by Panhead Bill on 2012-11-07
FWIW; I have 3 150 cards on my master backend, it has an A8E-SLI delux Motherboard (64 bit), AMD-64 cpu and copy of 64 bit Mythbuntu.  (Yes it works)

---

### Post by nickrout on 2012-11-07
> **Panhead Bill said:**
> FWIW; I have 3 150 cards on my master backend, it has an A8E-SLI delux Motherboard (64 bit), AMD-64 cpu and copy of 64 bit Mythbuntu.  (Yes it works)What version of mythbuntu?

---

### Post by klc5555 on 2012-11-08
> **Panhead Bill said:**
> FWIW; I have 3 150 cards on my master backend, it has an A8E-SLI delux Motherboard (64 bit), AMD-64 cpu and copy of 64 bit Mythbuntu.  (Yes it works)

Thanks! --that's the main answer to it then. Broadly by type, the hardware and software are known to all work together.

Accordingly, the OP's issues are limited to 1) hardware, only to the extent that his individual PVR 150 may in theory be defective; or 2) software, to the extent that drivers and firmware may not be installed properly or, more likely, 2a) mythbackend is not configured correctly to access his card.

If the OP manages to get a real, live video signal of any sort from the card via the command line, using the methods described earlier, possibilities 1) and 2) are eliminated, and he only needs to worry about properly configuring mythbackend.

---

### Post by nickrout on 2012-11-08
> **klc5555 said:**
> Thanks! --that's the main answer to it then. Broadly by type, the hardware and software are known to all work together.

Accordingly, the OP's issues are limited to 1) hardware, only to the extent that his individual PVR 150 may in theory be defective; or 2) software, to the extent that drivers and firmware may not be installed properly or, more likely, 2a) mythbackend is not configured correctly to access his card.

If the OP manages to get a real, live video signal of any sort from the card via the command line, using the methods described earlier, possibilities 1) and 2) are eliminated, and he only needs to worry about properly configuring mythbackend.Other factors may be:

[LIST=1]
[*]Motherboard chipset and it's interaction with the (now quite old) PVR cards.
[*]Possibility of the cards themselves being damaged or broken - again they are quite old and it definitely pays to check the capacitors. They are apparently easy to replace if you have some electronics skills.
[/LIST]

---

### Post by Panhead Bill on 2012-11-08
10.04 through 12.04

---

### Post by dannyboy79 on 2012-11-08
I use Mythbuntu 10.04 which has 0.23.1-fixes I believe. I have heard bad things about the latest MythTV not playing nice with the old analog Haugpauge cards like the PVR-150, -350, and -500.

---

### Post by Panhead Bill on 2012-11-08
Maybe so, My primary backend started with 10.04 and has been dist. upgraded to 12.04. it runs the old cards.  My newer secondary backend/frontend unit (with a Hauppague 150)only would accept 10.04 and upgrades to 12.04, it stalled when I tried to load 11.10 or 12.04 on clean installs.

---

### Post by westlandnick on 2012-11-27
I have what I believe is this card, and I did I fresh install of mythbuntu 12.04 and I can capture good video on channels 2-13, anything above 13 is static, and I am having a similar problem setting up the mythbackend.  I went through and installed the ivtv drivers, and I even reinstalled kubuntu, command line installed the mytv and mysql/server and same thing, capture video on command line.  Anyway, i also have a windows 7 install, booted into media center, and same thing i can get channels 2-13, but very choppy, but nothing above.  I'm thinking my card is shot.  i thought I would see if anyone has any insight.

---

### Post by anonymousdog on 2012-11-27
There are unresolved tickets on these Hauppauge MPEG2 cards under 0.25 on 32- or 64-bit systems.  The most confounding and irritating issue by far is whatever leads to zero-byte recordings and LiveTV tuning failures (both issues are failure to successfully tune the card).  These issues are unique to MythTV, and I have been unable to reproduce them with torture tests on the cards and system using a variety of other software (on the same distro/hardware combos).

The bug most at issue is [10732]("http://code.mythtv.org/trac/ticket/10732") and is being treated as a nuisance as far as I can tell; it's been reported since the 0.25 release, affects multiple users, is repeatable, and impacts very widely-used cards...still marked as "minor"...and has been closed at least once for "too much talk".  Yeah, whatever.  This is a MythTV issue, but I really doubt it will EVER be fixed as the developers pretty much view these cards as "legacy" devices (thus, the "minor" designation on a show stopper issue).

I've tried I/O priority hacks (both deadline and cfq schedulers) as well as the "remove/add" tuner approaches...even a clean install on different base hardware and PVR-500...same issue.  These MAY reduce symptom severity but fail to evince reliability.  There is now a patch posted on the ticket -- it may work, but will make the system a PITA to update (since it'll have to be re-patched every time the affected module gets rewritten).

Stay away from the ivtv MPEG2 cards if you're going to use any MythTV past 0.23...they worked flawlessly for years until I upgraded beyond 0.23 (no matter on what distro)!

---

### Post by klc5555 on 2012-11-28
> **westlandnick said:**
> I have what I believe is this card, and I did I fresh install of mythbuntu 12.04 and I can capture good video on channels 2-13, anything above 13 is static, and I am having a similar problem setting up the mythbackend.  I went through and installed the ivtv drivers, and I even reinstalled kubuntu, command line installed the mytv and mysql/server and same thing, capture video on command line.  Anyway, i also have a windows 7 install, booted into media center, and same thing i can get channels 2-13, but very choppy, but nothing above.  I'm thinking my card is shot.  i thought I would see if anyone has any insight.

Are you sure anything is actually being transmitted in analog above ch. 13 where you are? Most US cable companies that still transmit any analog at all stop at 13 (en route to eliminating analog entirely), while OTA analog shouldn't exist any longer (much less UHF analog).

---

### Post by dannyboy79 on 2012-11-28
I live in Milwaukee, WI and TWC still transmits all analog stations (2 thru 99) over the coax line I have for internet service. Pretty awesome IMO. Once they get rid of the analog signal over the internet line, I'll finally pull the trigger on some digital tuners. Probably go with HD Homerun's, see if TWC has any unencrypted QAM channels or just go OTA totally.

---

### Post by westlandnick on 2012-11-28
> **klc5555 said:**
> Are you sure anything is actually being transmitted in analog above ch. 13 where you are? Most US cable companies that still transmit any analog at all stop at 13 (en route to eliminating analog entirely), while OTA analog shouldn't exist any longer (much less UHF analog).

Honestly no, I have no idea... Another friend of mine believes that anything above channel 13 is digital.. Which very well could be why I'm getting static on those channels.  So that was part of my question, do I need a digital tuner in order to capture those channels?  

The other part to my question stems from the OP, my mythtv backend is my biggest problem.  When I get to setting up the channels, it "searches for channels" and gets nothing.  But I can capture 2-13 just fine manually, so why isn't it at least seeing those channels?  both linux distros I installed are 64 bit.  When I read that this card doesn't work in 64 bit I thought great, that is my issue, but then someone else said that it should work fine..  So my first install was mythbuntu 12.04 64bit.  my second/current is kubuntu 12.04LTS 64bit.  I have 4 hard drives to work with so it wouldn't be a big deal for me to try mythbuntu 32bit, but with my other issues I'm wondering if I'm wasting my time with this capture card.  If I have to buy a digital card to get all my channels, so be it, I'll just do that.. But I got this card for free so I figured I would at least see if I can get this to work as a secondary card...  Thanks for the help

---

### Post by klc5555 on 2012-11-28
> **dannyboy79 said:**
> I live in Milwaukee, WI and TWC still transmits all analog stations (2 thru 99) over the coax line I have for internet service. Pretty awesome IMO. Once they get rid of the analog signal over the internet line, I'll finally pull the trigger on some digital tuners. Probably go with HD Homerun's, see if TWC has any unencrypted QAM channels or just go OTA totally.

Wow. Makes me nostalgic for the good old pre-2009 days. Where I am, Comcast nuked everything analog above above ch. 20 within 5 months of the digital switchover, then station by station down to 13, then finally all analog about a year ago. Clear QAM stations were steadily purged of old standbys like the History Channel down to exactly what was available locally OTA.

Now, since the rules governing the encryption of basic cable change on Dec. 10, like almost everybody else I fully expect Comcast to begin to encrypt everything fairly soon. So in preparation I've got one backend already on OTA digital, the other two still on QAM.

---

### Post by klc5555 on 2012-11-28
> **westlandnick said:**
> Honestly no, I have no idea... Another friend of mine believes that anything above channel 13 is digital.. Which very well could be why I'm getting static on those channels.  So that was part of my question, do I need a digital tuner in order to capture those channels?  

The other part to my question stems from the OP, my mythtv backend is my biggest problem.  When I get to setting up the channels, it "searches for channels" and gets nothing.  But I can capture 2-13 just fine manually, so why isn't it at least seeing those channels?  both linux distros I installed are 64 bit.  When I read that this card doesn't work in 64 bit I thought great, that is my issue, but then someone else said that it should work fine..  So my first install was mythbuntu 12.04 64bit.  my second/current is kubuntu 12.04LTS 64bit.  I have 4 hard drives to work with so it wouldn't be a big deal for me to try mythbuntu 32bit, but with my other issues I'm wondering if I'm wasting my time with this capture card.  If I have to buy a digital card to get all my channels, so be it, I'll just do that.. But I got this card for free so I figured I would at least see if I can get this to work as a secondary card...  Thanks for the help

You need to know if your stations beyond 13 are in fact digital. You have not mentioned whether you are on cable or not; I assume you are. A bit of web research ought to give you your digital vs. analog answer for your particular area and your particular provider.

If your stations above 13 are digital, to receive them you will need either a QAM capable digital tuner, which will tune in the unencrypted digital channels (clear QAM), or a cable box or digital transport adapter provided by your cable company, which will tune the authorized digital stations (including encrypted ones) and convert them to an analog form that your PVR 150 understands: coax on ch.3 or 4, or input into a composite video or S-Video port. 

That you can tune anything at all with your PVR 150 proves that it is functioning with your version of Kubuntu. One problem is that analog scanning in many versions of Mythtv above around 0.22 is broken. This has never been a big problem for the PVR 150 and other analog tuners --they already know how to tune channels 2-99 and so analog channels are very easy to add individually using "add channel" in the Channel Editor. Even when mythtv-setup's analog scanning worked, it didn't actually scan anything. It just set up a bunch of database entries for chs. 2-99 similar to "add channel" without determining whether any receivable signal was on that channel.

So whatever analog stations you may have, you will be able to set them up in mythbackend whether you can scan for them or not.

---

### Post by dannyboy79 on 2012-11-28
> **klc5555 said:**
> Wow. Makes me nostalgic for the good old pre-2009 days. Where I am, Comcast nuked everything analog above above ch. 20 within 5 months of the digital switchover, then station by station down to 13, then finally all analog about a year ago. Clear QAM stations were steadily purged of old standbys like the History Channel down to exactly what was available locally OTA.

Now, since the rules governing the encryption of basic cable change on Dec. 10, like almost everybody else I fully expect Comcast to begin to encrypt everything fairly soon. So in preparation I've got one backend already on OTA digital, the other two still on QAM.

what rules are changing for encrypting basic cable?

---

### Post by klc5555 on 2012-11-28
> **dannyboy79 said:**
> what rules are changing for encrypting basic cable?

The FCC lifted the rule preventing the cable companies encrypting local channels. Beginning next month, the cable providers will (after appropriate notice) be free to encrypt everything they offer. Likely no more clear QAM; a box will be needed for everything.

---

### Post by westlandnick on 2012-11-28
> **klc5555 said:**
> You need to know if your stations beyond 13 are in fact digital. You have not mentioned whether you are on cable or not; I assume you are. A bit of web research ought to give you your digital vs. analog answer for your particular area and your particular provider.

If your stations above 13 are digital, to receive them you will need either a QAM capable digital tuner, which will tune in the unencrypted digital channels (clear QAM), or a cable box or digital transport adapter provided by your cable company, which will tune the authorized digital stations (including encrypted ones) and convert them to an analog form that your PVR 150 understands: coax on ch.3 or 4, or input into a composite video or S-Video port. 

That you can tune anything at all with your PVR 150 proves that it is functioning with your version of Kubuntu. One problem is that analog scanning in many versions of Mythtv above around 0.22 is broken. This has never been a big problem for the PVR 150 and other analog tuners --they already know how to tune channels 2-99 and so analog channels are very easy to add individually using "add channel" in the Channel Editor. Even when mythtv-setup's analog scanning worked, it didn't actually scan anything. It just set up a bunch of database entries for chs. 2-99 similar to "add channel" without determining whether any receivable signal was on that channel.

So whatever analog stations you may have, you will be able to set them up in mythbackend whether you can scan for them or not.

Great, thanks for all this info.  I forgot to mention the cable part, yes I am on Comcast/Xfinity cable in Ogden Utah.  I didn't try the add channels manually, I will check that out.  This helps me a lot, I wondered if I needed to use my cable box before my card, I didn't see anywhere that specified..  I'm assuming having the cable box in line before my pvr would mean in order to capture a digital channel I would actually have to change it to that channel on the comcast box first?  Or is my pvr smart enough to take do that on its own?  Again, thanks for the help.  This has been kind of a headache, but it will be worth it in the long run.

---

### Post by klc5555 on 2012-11-28
> **westlandnick said:**
> Great, thanks for all this info.  I forgot to mention the cable part, yes I am on Comcast/Xfinity cable in Ogden Utah.  I didn't try the add channels manually, I will check that out.  This helps me a lot, I wondered if I needed to use my cable box before my card, I didn't see anywhere that specified..  I'm assuming having the cable box in line before my pvr would mean in order to capture a digital channel I would actually have to change it to that channel on the comcast box first?  Or is my pvr smart enough to take do that on its own?  Again, thanks for the help.  This has been kind of a headache, but it will be worth it in the long run.

Yes, your cable will feed into your cable box; your cable box will feed into your PVR 150. The PVR 150 itself will not be tuned after startup; the cable box will tune the channels and will output the result (by whatever output it has) to your PVR 150. For the full use of Mythtv, this means that you will need to configure LIRC and use some sort of IR blaster. When Mythtv needs to change the channel, instead of changing channels directly on the PVR 150, it will use LIRC to send the IR signal through the IR blaster to the Comcast box, which then changes its channel. 

All the ch.2-13 analog stations you now get directly on the PVR 150 are also available through the Comcast box. In my area, when Comcast cut the analogs down to ch. 2-20, they also cut the analog signal strength way down, so the quality on these surviving analog stations was terrible. The quality was much better on the versions through the box; and I suspect this will be true for you as well.

Also, for the time being at least, all your "local" stations (however that may be defined) are additionally available over your cable in clear QAM digital, SD and probably HD. You just need a digital tuner to pick them up. Since your cable box will occupy some sort of analog tuner input, but will just get in the way of getting clear QAM, to receive everything Comcast is currently throwing at you you need either two tuner cards--one analog and one digital --or a "hybrid dual tuner" card that has separate analog and digital inputs into it and accordingly supports simultaneous reception of analog and digital signals. Such cards include PCI cards like the Hauppauge PVR 1600, or PCIe cards like the Hauppage 1250 or several other similar cards. You'd run your cable to a splitter, with one side out of the splitter going to your cable box for the encrypted stuff, and the other side going straight to your digital tuner input for your clear QAM.

Good luck!

---

### Post by dannyboy79 on 2012-11-28
> **klc5555 said:**
> The FCC lifted the rule preventing the cable companies encrypting local channels. Beginning next month, the cable providers will (after appropriate notice) be free to encrypt everything they offer. Likely no more clear QAM; a box will be needed for everything.
I don't see why cable providers would want to do that. smart customers will just drop them and go with OTA since those are required by the FCC to be transmitted.

---

### Post by westlandnick on 2012-11-28
So I went home on my lunch, went into the channel editor and manually added channels 2-13.  It ran the mythfilldatabase, that took a few minutes, it downloaded program guides from schedulesdirect and back to the kde desktop.  I don't have a frontend setup, I just have a mythbuntu live usb stick.  So I booted my laptop on the live usb, and loaded mythfrontend, it has you test the connection, which said it was a success, then when I click the start frontend, nothing happens..  I let it sit for a few minutes, nothing... I close it out, relaunch, same.  I rebooted both my backend and frontend, same.  I didn't have anymore time to mess with it I had to head back to work.  I should be able to figure it out when I get home, just thought I would throw this out there and see if anyone has any suggestions..

---

### Post by westlandnick on 2012-11-28
I assumed it would be something similar to that..  I also wondered what the hell a ir blaster was..  This is all starting to make sense though.  I appreciate the help to the noob.  Thanks again

---

