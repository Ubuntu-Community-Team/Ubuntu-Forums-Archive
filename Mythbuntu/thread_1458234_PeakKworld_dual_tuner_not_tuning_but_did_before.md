---
title: "Peak/Kworld dual tuner not tuning but did before"
date: 2010-04-19
forum: Mythbuntu
---

### Post by evey on 2010-04-19
Hi
Have a AMD Athlon 64 x2 Dual 3800+ box with 2GB of Ram running the latest Mythbuntu (Combined back/front end) and a Peak DVB-T dual tuner PCI (221544) - same as Kworld DVB-T PC160.

I'm Lancaster UK - and want to use it for Freeview.  I've had the card tuned in previously (Showed 75/76% strength during scan - new TV ariel with booster) - have been able to watch freeview, but at the time couldn't get any sound from the on board sound or from a separate sound blaster card (Did follow several guides to no avail) - tried doing an install of Unbuntu and then pulling mythtv onto it in the hope of being able to resolve but ended up buying a cheap genuis sound card that just worked out of the box.
Tried to get tv card to scan channels but no joy.  
Re-installed Mythbuntu with non free firmware and all codecs enabled, tuner picked up by mythbuntu as /dev/dvb/adapter0/frontend0 and /dev/dvb/adapter1/frontend0.  
Tried setting up with XMLTV from Radio Times Ireland configured through terminal then tried tuning - no signal strength shown during channel scan and no channels found.  Then tried doing tuner scan without xmltv, just eit - again no channels found.
Looking through others attempts at channel scanning tried scan and w_scan - output shown below :
scan -u /usr/share/dvb/dvb-t/uk-Lancaster > channels.conf
scanning /usr/share/dvb/dvb-t/uk-Lancaster
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 530167000 0 3 9 1 0 0 0
initial transponder 482167000 0 2 9 3 0 0 0
initial transponder 506167000 0 2 9 3 0 0 0
initial transponder 562167000 0 3 9 1 0 0 0
initial transponder 578000000 0 3 9 1 0 0 0
initial transponder 545833000 0 3 9 1 0 0 0
>>> tune to: 530167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
__tune_to_transponder:1516: ERROR: FE_READ_STATUS failed: 121 Remote I/O error
>>> tune to: 530167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
__tune_to_transponder:1516: ERROR: FE_READ_STATUS failed: 121 Remote I/O error
...
>>> tune to: 545833000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
__tune_to_transponder:1516: ERROR: FE_READ_STATUS failed: 121 Remote I/O error
ERROR: initial tuning failed
dumping lists (0 services)
Done.

--------------
w_scan -ft -c GB >> channels.conf
w_scan version 20090808 (compiled for DVB API 5.0)
using settings for UNITED KINGDOM
DVB aerial
DVB-T GB
frontend_type DVB-T, channellist 6
output format vdr-1.6
Info: using DVB adapter auto detection.
    /dev/dvb/adapter0/frontend0 -> DVB-T "Afatech AF9013 DVB-T": good :-)
    /dev/dvb/adapter1/frontend0 -> DVB-T "Afatech AF9013 DVB-T": good :-)
Using DVB-T frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.0
frontend Afatech AF9013 DVB-T supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
Scanning 7MHz frequencies...
177500: (time: 01:00) 


857833: (time: 160:04) 

ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!

------------

Just in case it helps :

grep -i dvb /var/log/messages
Apr  8 13:39:32 mythtv kernel: [   13.723472] dvb-usb: found a 'KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T)' in cold state, will try to load a firmware
Apr  8 13:39:32 mythtv kernel: [   13.723479] usb 2-1: firmware: requesting dvb-usb-af9015.fw
Apr  8 13:39:32 mythtv kernel: [   14.075251] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
Apr  8 13:39:32 mythtv kernel: [   14.137299] dvb-usb: found a 'KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T)' in warm state.
Apr  8 13:39:32 mythtv kernel: [   14.137356] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Apr  8 13:39:32 mythtv kernel: [   14.137680] DVB: registering new adapter (KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T))
Apr  8 13:39:33 mythtv kernel: [   14.729777] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
Apr  8 13:39:33 mythtv kernel: [   15.116846] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Apr  8 13:39:33 mythtv kernel: [   15.117229] DVB: registering new adapter (KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T))
Apr  8 13:39:34 mythtv kernel: [   15.770836] af9013: found a 'Afatech AF9013 DVB-T' in warm state.
Apr  8 13:39:34 mythtv kernel: [   15.787468] DVB: registering adapter 1 frontend 0 (Afatech AF9013 DVB-T)...
Apr  8 13:39:34 mythtv kernel: [   16.149405] dvb-usb: KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T) successfully initialized and connected.
Apr  8 13:39:34 mythtv kernel: [   16.157824] usbcore: registered new interface driver dvb_usb_af9015

---------------------------------

The tuner card seems to be being picked up by various different apps and I have had it tuned in previously (How I wish i hadn't even breathed on the setup at that point)0 - so I'm loathed to knock the tuner card - any ideas appreciated.

I've attached some Mythbuntu screen shots in case they help.

---

### Post by JasonEde on 2010-04-24
I'm having a strange problem with the same card, also on Mythbuntu 9.10 that I think might be the same. It used to work fine and I then added a Hauppauge HD-S2 card and again everything was fine.

However, starting this last week its all suddenly gone pear shaped. The peak card only seems to work after a cold boot and for a few hours at a time. After a few hours then I try watching TV and it just can't get a lock. If I try re-tuning then it can't find any channels. A reboot doesn't seem to get it working again. Only a power off and then power on from cold seems to bring the card back to life.

Evey - Try tuning after a cold boot and with the 4.95 firmware.

I got fed up this week with this hanging after a few hours and so I backed up the database, wiped the mythbox and started afresh. Reimported the database and all was fine.

I scanned channels (only on the DVB-T card) and all was happy. Today I then ran a script I used to set up the channels the way I want them and turn off the unused channels and sort the EIT so it only runs on the channels that need it. Then a few hours later it has stopped working again. I suspect something I did setting up the channels upset the card somehow, although that seems odd to me. 

There are errors in the dmesg log which I have attached along with the script I use for the channel setting.

Any ideas?

---

### Post by ian dobson on 2010-04-24
Hi,

When you tell mythtv to use EIT it'll go through tuning to each of the channels one after the other looking for EPG data. I think mythtv uses 1 minute timeout for the channel. 

Maybe try increasing this value to 4-5minutes or so. The setting is called EITTransportTimeout in the settings table (sorry I'm not sure where it is in myth-setup).

Regards
Ian Dobson

---

### Post by evey on 2010-04-24
Interesting Jason - I sure do hope this doesn't turn into hardware failure  - I bought this card because it was one of the few dual tuner dedicated cards recommended for mythbuntu (Couldn't stretch to a Hauppage dual tuner).

In my case I've generally always attempted tuning from a cold boot, including trying the tv aerial with and without booster attached in case the booster was adding interference.  Just to elimate any booster issues - are you running one with this setup and are you switching it on and off in tandem with the machine.  The guy who fitted the new aerials (Has a very good rep) said there were quite a few boosters that added more noise to a signal causing more problems.  If there's anything like that I'd be tempted to try running without the booster in case this is linked to the issue.

I'll check for the firmware side but I've been keeping the box fully updated - checked this every time I go back to attemnpt a retune.  Is 4.95 the latest revision or are you meaning to try older firmware in case?

On that note I did notice the nvidia driver changed for my graphics card during an upgrade and now has stopped being able to get TV out (The old driver also allowed me to set the specific Pal I setting for the TV, so probably will have to revert to the old Nvidia driver too.)  And all I wanted at the time was to put a dvd on for the kids and couldn't even do that - let alone get freeview through the box - this is getting really sad.

Hopefully tomorrow I'll be able to get the box fired up (In the middle of a ton and a half of diy) and put up my dmesg log and see how it compares to your's - this may help both of us.  I haven't got to the stage of messing around with the database for channel matching but I can see where the script is going.

Also, thanks Ian for the reply - I think what you're talking about is on the first screenshot I attached to the post.  I've already tried uping the timeouts values but haven't gone quite as far as you suggest - again will try that tomorrow.

Will get back tomorrow with an update - thanks

Paul

---

### Post by JasonEde on 2010-04-25
I am wondering if my issues are hardware related. I know for my case EIT has been working fine once I'd done a full tuned scan.

I've just noticed that once the card has stopped working and won't tune to any tv channel the messages log is full of this...


Apr 25 07:33:55 jason-desktop kernel: [56240.581822] af9013: I2C read failed reg:9bee
Apr 25 07:33:55 jason-desktop kernel: [56240.632330] af9013: I2C read failed reg:d330
Apr 25 07:33:55 jason-desktop kernel: [56240.682837] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56240.733339] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56240.783850] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56240.834356] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56240.884864] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56240.935368] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56240.985876] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56241.036383] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56241.086887] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56241.137395] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56241.176527] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56241.193276] af9013: I2C write failed reg:ae00 len:1
Apr 25 07:33:56 jason-desktop kernel: [56241.196152] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56241.246659] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56241.297165] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56241.347670] af9013: I2C read failed reg:d330
Apr 25 07:33:56 jason-desktop kernel: [56241.398178] af9013: I2C read failed reg:d330


One thing that intrigues me...

jason@jason-desktop:~$ lsmod | grep dvb
cx88_dvb               21088  1
cx88_vp3054_i2c         2524  1 cx88_dvb
videobuf_dvb            7040  1 cx88_dvb
cx8802                 15264  1 cx88_dvb
cx88xx                 77836  4 cx88_dvb,cx88_alsa,cx8802,cx8800
dvb_usb_af9015         25308  2
dvb_usb                16200  1 dvb_usb_af9015
videobuf_dma_sg        12608  5 cx88_dvb,cx88_alsa,cx8802,cx8800,cx88xx
dvb_core               87364  3 cx88_dvb,videobuf_dvb,dvb_usb
videobuf_core          17952  5 videobuf_dvb,cx8802,cx8800,cx88xx,videobuf_dma_sg


If I look at an lsmod for other systems that are using this card then they all seem to have i2c_core loaded, but that module doesn't seem to exist on my system anywhere that I can find... Could this be the problem?

Jason

---

### Post by JasonEde on 2010-04-25
Evey - The 4.95 firmware, which I believe is the latest for this card is linked from [http://linuxtv.org/wiki/index.php/Afatech_AF9015](http://linuxtv.org/wiki/index.php/Afatech_AF9015). Scroll right to the bottom of this page and see the firmware link.

Can you post end of the dmesg output where it mentions the DVB card?

---

### Post by dabobson on 2010-04-25
Hi all,
I've been wrestling with similar problems  over the last couple of weeks with the same card and mythbuntu. I did have both tuners working but recently only one of them would lock a signal. When I came across your post last night I began to wonder if an update of something in the last few weeks had somehow caused this?

Anway, for me this now seems to have been resolved (it's been working for a couple of hours and counting!) by simply saving the firmware at:
[http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/)
in my /lib/firmware folder. I turned off and on again and both tuners work!
This is the same location that you linked to (indirectly) in your last post so the main reasons I mention it again are:
a) I thought I already had the latest version of the firmware installed, so even if you do too it's worth giving it a go.
b) To restore some hope that there may be light at the end of the tunnel if you're getting as frustrated as I was...

I don't know much about Linux, been learning along the way since I installed mythbuntu a couple of months ago, but if there's anything i can tell you about my setup that may help you resolve your own problems let me know.

Good luck!

Doug

---

### Post by JasonEde on 2010-04-25
I'm using that latest firmware... it's been installed in /lib/firmware since day 1. I've just downloaded the latest copy and done a diff against the version I'm using and its identical.

It could be an update thats caused it as it has only been in the last week... The fact that it needs a cold boot to get it working again though does imply a firmware issue and I hope not a hardware issue.

I've updated the v4l drivers to latest version so lets see if that helps... It seems to be stable for last 4-5 hours, although I currently have the DVB-S card unconfigured right now.  So far it has been up for 6-8 hours before it starts to stop working... I am getting some  'I2C read failed reg:d2e6' in the messages log.

I wonder could it be a selinux problem? 

Jason

---

### Post by JasonEde on 2010-04-26
It's just done it again... I seems like something that has changed probably in an update? means my system is stable for a few hours now before the Peak card just stops working.

---

### Post by JasonEde on 2010-04-26
Have just found out that shortly before I started to experience the problem that work has started at our local transmitter  [http://help.digitaluk.co.uk/display/4/kb/article.aspx?aid=7463](http://help.digitaluk.co.uk/display/4/kb/article.aspx?aid=7463) Emley Moor. On the TV we have noticed one of the multiplexes dropping in and out quite a lot and when it is on we have very poor signal strength. Could this be causing problems for the card?

---

### Post by evey on 2010-04-26
Firstly I'll get the requested console output and dmesg up before doing another reply...

lsmod | grep dvb
dvb_usb_af9015         32964  1 
dvb_usb                19276  1 dvb_usb_af9015
dvb_core              104528  1 dvb_usb

---------------------------

dmesg below towards end concerning card :
--------------------------

[   13.275897] dvb-usb: found a 'KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T)' in cold state, will try to load a firmware
[   13.275905] usb 2-1: firmware: requesting dvb-usb-af9015.fw
[   13.379021] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   13.379028]   alloc irq_desc for 18 on node 0
[   13.379030]   alloc kstat_irqs on node 0
[   13.379040] nvidia 0000:05:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   13.379047] nvidia 0000:05:00.0: setting latency timer to 64
[   13.379262] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[   13.520081] cfg80211: Calling CRDA to update world regulatory domain
[   13.644480] rtl8180 0000:01:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   13.735704] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.959357] cfg80211: World regulatory domain updated:
[   13.959361]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.959365]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.959368]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.959370]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.959373]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.959376]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.129399] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[   14.186696] dvb-usb: found a 'KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T)' in warm state.
[   14.186761] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   14.187076] DVB: registering new adapter (KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T))
[   14.630148] af9013: firmware version:4.65.0
[   14.634152] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   14.700763] tda18271 2-00c0: creating new instance
[   14.706536] TDA18271HD/C2 detected @ 2-00c0
[   14.832043] phy0: Selected rate control algorithm 'minstrel'
[   14.832844] phy0: hwaddr 00:17:3f:d3:ce:3d, RTL8185vD + rtl8225z2
[   15.060605] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.060986] DVB: registering new adapter (KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T))
[   15.138468] C-Media PCI 0000:01:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   17.602589] af9015: bulk message failed:-110 (8/0)
[   17.602595] af9015: firmware copy to 2nd frontend failed, will disable it
[   17.602598] dvb-usb: no frontend was attached by 'KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T)'
[   17.602603] dvb-usb: KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T) successfully initialized and connected.
[   17.846207] type=1505 audit(1272310465.556:11): operation="profile_replace" pid=935 name=/sbin/dhclient3
[   17.846508] type=1505 audit(1272310465.556:12): operation="profile_replace" pid=935 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   17.846681] type=1505 audit(1272310465.556:13): operation="profile_replace" pid=935 name=/usr/lib/connman/scripts/dhclient-script
[   17.851185] type=1505 audit(1272310465.556:14): operation="profile_replace" pid=936 name=/usr/bin/evince
[   17.856237] type=1505 audit(1272310465.566:15): operation="profile_replace" pid=936 name=/usr/bin/evince-previewer
[   17.859204] type=1505 audit(1272310465.566:16): operation="profile_replace" pid=936 name=/usr/bin/evince-thumbnailer
[   17.869066] type=1505 audit(1272310465.576:17): operation="profile_replace" pid=940 name=/usr/sbin/mysqld
[   17.871424] type=1505 audit(1272310465.576:18): operation="profile_replace" pid=941 name=/usr/sbin/ntpd
[   17.873369] type=1505 audit(1272310465.586:19): operation="profile_replace" pid=942 name=/usr/sbin/tcpdump
[   19.602587] af9015: bulk message failed:-110 (8/0)
[   19.602592] af9015: endpoint init failed:-110
[   19.602611] dvb_usb_af9015: probe of 2-1:1.0 failed with error -110
[   19.602649] usbcore: registered new interface driver dvb_usb_af9015
[   20.143022] usplash:380 freeing invalid memtype ffffffffd0000000-ffffffffe0000000

-------------------------

Ij the middle of cooking tea but will post a proper reply soon...:popcorn:

---

### Post by JasonEde on 2010-04-26
Evey - That is using the 4.65 firmware which a lot of people have reported as buggy. Get the latest firmware linked from an earlier post.

Mine is still dropping out randomly with lots of read errors and it is getting to the point where it is not reliable to record anything at all on the box. Has anyone any ideas?

Again from the messages log...

Apr 26 20:31:51 jason-desktop kernel: [ 8416.204447] af9013: I2C read failed reg:d330
Apr 26 20:31:52 jason-desktop kernel: [ 8418.005979] af9013: I2C read failed reg:d330
Apr 26 20:31:54 jason-desktop kernel: [ 8419.805014] af9013: I2C read failed reg:d330
Apr 26 20:31:56 jason-desktop kernel: [ 8421.604922] af9013: I2C read failed reg:d330
Apr 26 20:31:58 jason-desktop kernel: [ 8423.404460] af9013: I2C read failed reg:d330
Apr 26 20:32:00 jason-desktop kernel: [ 8425.204495] af9013: I2C read failed reg:d330
Apr 26 20:32:01 jason-desktop kernel: [ 8427.004531] af9013: I2C read failed reg:d330
Apr 26 20:34:12 jason-desktop kernel: [ 8557.639170] af9013: I2C read failed reg:d417
Apr 26 20:34:12 jason-desktop kernel: [ 8557.639414] af9013: I2C write failed reg:d3c0 len:1

---

### Post by evey on 2010-04-27
Thanks Doug and Jason - firmware from the link seems to be the way to go.  Thought I was keeping the box up-to-date but evidently that dmesg log shows otherwise - wonder if somehow I ended up with the 4.95 firmware during a previous install when the card would scan ok (Can't remember doing anything other than using Ubuntu package manager).  Next job firmware.

Jason - the antenna work might have some bearing but if you have a freeview box that will scan ok it looks a bit remote.  I started off with a Hauppage HVR 1100 before buying the Peak card.  Before I had the knew aerials installed, whether that card was in a Windows XP box or Mythbuntu scanning was very poor, yet freeview box scanned ok.  Tried different boosters in case they would do the trick without the need for new aerials, but they didn't so ended up shelling out for that too.  Came to the conclusion that TV capture cards are not especially robust in terms of scanning and buffering.
Really want the dual tuners on the Peak card so don't want to put the Hauppage back into the mythbuntu box (I'm using it anyway for video capture elsewhere).

I know for me, the last resort if this all doesn't seem to get it going is to whip the Peak card out and put it into an XP box to check the hardware - Jason have you got an XP machine or a mate with one you can try it in to rule out hardware issues - especially overheating as this seems to be a cold boot issue for you.

I'll post back once the new firmware is in place and run a scan with long, long timeouts...

---

### Post by hollo32 on 2010-04-29
I'm having the same problem as Jason with a different tuner using the same chipset. I have a TwinHan AzureWave AD-TU700(704J) which uses the same af9013/5 chipset.

I have only had the card for a few weeks, but it worked perfectly until a couple of days ago. Since then it has been intermittently failing by being unable to get a lock on watching tv, and on recording no file is recorded (although Myth doesn't report any error until you try to watch the recording).

After it stops working the only way to recover seems to be poweroff, wait, poweron. A straight reboot doesn't do the job, which also makes me think it is a hardware/firmware problem in the tuner.

Relevent dmesg bits for the card.
> 
[   15.077591] dvb-usb: found a 'TwinHan AzureWave AD-TU700(704J)' in cold state, will try to load a firmware
[   15.077611] usb 1-6: firmware: requesting dvb-usb-af9015.fw
[   15.141649] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[   15.302600] dvb-usb: found a 'TwinHan AzureWave AD-TU700(704J)' in warm state.
[   15.302704] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.303766] DVB: registering new adapter (TwinHan AzureWave AD-TU700(704J))
[   15.686214] af9013: firmware version:4.95.0
[   15.689294] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   15.707301] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   15.708311] DVB: registering new adapter (TwinHan AzureWave AD-TU700(704J))
[   16.673854] dvb-usb: schedule remote query interval to 150 msecs.
[   16.673867] dvb-usb: TwinHan AzureWave AD-TU700(704J) successfully initialized and connected.
[   16.946262] usbcore: registered new interface driver dvb_usb_af9015
 > 
~$ uname -a 
Linux ion 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
~$ lsmod|egrep 'dvb|af'
af9013                 20608  2 
dvb_usb_af9015         25308  16 
dvb_usb                16200  1 dvb_usb_af9015
dvb_core               87364  1 dvb_usb
Error messages I have noted are:
> mythfilldatabas[3255]: segfault at fefa1183 ip 00146f3c sp b6712c80 error 4 in libmythdb-0.22.so.0.22.0[110000+97000]I seem to get this one quite a bit, even when the card is working.

> Apr 25 07:53:42 ion kernel: [296442.632079] af9013: I2C read failed reg:d330
Apr 25 07:53:44 ion kernel: [296444.628696] af9013: I2C read failed reg:d330
Apr 25 07:53:46 ion kernel: [296446.630748] af9013: I2C write failed reg:ae00 len:1
Apr 25 07:53:48 ion kernel: [296448.632831] af9013: I2C read failed reg:9bee
Apr 25 07:53:50 ion kernel: [296450.632841] af9013: I2C read failed reg:d330
Apr 25 07:53:52 ion kernel: [296452.636655] af9013: I2C write failed reg:ae00 len:1
Apr 25 07:53:54 ion kernel: [296454.637068] af9013: I2C read failed reg:d330
Apr 25 07:53:56 ion kernel: [296456.644067] af9013: I2C read failed reg:d330
Apr 25 07:53:58 ion kernel: [296458.644170] af9013: I2C write failed reg:ae00 len:1
I have a whole string of these in my log from the first couple of occasions it failed, but I think this is from
when I unplugged the USB cable and reattached in the hope of resetting it, not from earlier when it actually failed.

I'm on standard Ubuntu 9.10 with no external sources (apart from the most recent af9015 firmware which I downloaded from the site linked above). No joy fixing this one yet, but it sounds like the same problem others on this thread have.

---

### Post by evey on 2010-04-29
Hi Hollo32
Hopefully I'll get chance to put the new firmware on tonight or tomorrow and see what we get.  If I start experiencing the same issues like yourself and Jason then I'm definitely whipping the card out of the Mythbuntu box and shoving it in a Win XP one to see how it behaves.  If it starts bombing out on that then not so good, but if it behaves itself then can start pointing at the firmware solidly and if necessary request it looking into.

Like my post replying to Jason, have you got an XP box or a mate with an XP box you can try it in and see if it croaks or not?  At least of two of us with appropriate results might help decide on firmware or hopefully not hardware issues.

---

### Post by JasonEde on 2010-04-29
Ok I think I'm getting progress...

I think, from other things I've read, is that the linux firmware doesn't cope too well with low signals. I've turned off EIT scanning (lots of locations in backend config) and made useonairguide=0 for all channels on that source and I've changed the DVB to open on demand. Also I'm not scheduling recordings on signals that are very weak here (due to work on local transmitter - I'm moving those to DVB-S for now)

So far it has been up for well over 24 hours with no signs of any problems. No error messages. I think the problem was the weak signal on some channels that were dropping in and out. I'll feed back after the bank holiday weekend about stability.

Jason

---

### Post by c1ru on 2010-05-03
I have the same problem and i have tested it with 3 or 4 adapters, all with the same af9015 chipset. But differents vendors.

The card work fine, and you can tune and watch channels, but when you stills w/o using the adapters, in about 3 or 4 hours, when you return only can watch a black screen on select mythtv, you can see the info of the channels but nothing more.

With one hauppauge work like a charm.

All devices on usb port.

Tested on alot of pcs, and  motheboards with the same problem.

fimrware used 4.95 from linux restricted drivers.

Apologize about my english.

---

### Post by JasonEde on 2010-05-04
c1ru > Is there anything in your logs /var/log/messages or on the dmesg log about any errors?

Do you use EIT or xmltv guides?

My system has now been stable for over 4 days after completely disabling EIT and using only xmltv.

---

### Post by evey on 2010-05-06
I installed the new firmware, but found after reboot the card wasn't found.  Have now done completely cold boot and the card has picked up 60 odd channels - haven't used EIT.  Will now leave it running for a few days and see if it drops out but Jason's results look quite hopeful.
Interestingly I noticed the scan was showing now 40 - 55% signal strength whereas as when I had running last time it was around 75%; nothing in the aerial side has changed so I guess it could be different firmware that was a tad optimistic.
Will repost after a few days and see if it's kept going.
c1ru - Not using EIT may well help as Jason said; I wouldn't have set it up with EIT first time around because I want the 14 days listings.

---

### Post by JasonEde on 2010-05-06
Evey - I found the same thing with the signal strength after upgrading the firmware. Glad it wasn't just me. I persistently get signal strength of between 40-60% but I can get a lock and a decent picture.

You would need a cold boot to pick up the new firmware as its not unloaded on a warm reboot.

Thing is on xmltv can't get the radio guides so need EIT for radio stations. I'd like to get it working again, but might just periodically enable it to scan radio stations. If that becomes necessary I might see if can script it with a cron job somehow...

---

### Post by evey on 2010-05-07
Soooo glad this is not looking like hardware anymore.  I did think originally from what I read about transmitter location and strengths that the 75% figure suggested that the transmitter was practically in the next street, very optimistic.
I did do a little Java app to pull down channels and listings from Radio times, store it in a serialised object structure, and then write out a list periodically of basic html pages suitable for phone browsing (Got tired of all the bloat of tv guide type websites).  The intention was - given time which I appear to be somewhat lacking as ever - to build on that to provide additional alert stuff and also integrate with mythtv to action recording etc. (Yep no doubt re-inventing the wheel, but it would be my somewhat misshappen wheel at least).

Are there any listing sources like radio times for the radio?(Irony of this question has just hit me)

---

### Post by c1ru on 2010-05-09
I`m testing at this time w/o eit.

I would buy one nova-td-hd, supports hd channels and have dual tuner.
Its more expensive, at least 80&#8364;, but tested with one friend, and working fine w/o have to do nothing, and recording fine for about 10 days w/o shutdown or restart.

---

### Post by JasonEde on 2010-05-09
I wonder if it's a problem with the card or firmware that we have these problems with weak signals/EIT?

---

### Post by evey on 2010-05-10
I've never seen EIT to work that well - have had several set top boxes, and the last time round deliberately went for a more expensive set top box for the guide facilities - hoping that it would be better - but still found the presence of guide information patchy and erratic (before and after new aerials).  Also in the house find the same thing with an LG TV and it's guide.
I would wonder about the firmware handling EIT - that area of it not being so resilient killing the whole party when it doesn't get clear data instead of just returning 'No Information'.

---

### Post by JasonEde on 2010-05-10
I'm thinking that too... We've still a multiplex that is 'out' here that has a very low signal output that the TV cannot even pick up most of the time. I have a feeling that the EIT code isn't robust and is causing an issue in the firmware (maybe where a counter or something buffer overflows....) as only a hard power off that causes the firmware to be reloaded seems to fix it.

I really would like some EIT data as in the UK it is currently the only way to get the radio schedules. I want stability of my backend even more though. Although my system now powers up and shutsdown automatically for recordings it would be nice not to have to worry about it losing lock when it is up.

---

### Post by evey on 2010-05-10
Obviously would be nice for the firmware to be investigated, but in case that's a long way off, perhaps fall-back RSS parsed, populating the DB.  It's only BBC stuff but maybe an approach :

[http://www.iplayerconverter.co.uk/reciva_instructions.aspx](http://www.iplayerconverter.co.uk/reciva_instructions.aspx)

---

### Post by c1ru on 2010-05-11
I have tested it with two modes, eit and xmltv and still having the same problem.
And a poor signal now.

---

### Post by JasonEde on 2010-05-12
When you've tried it on xmltv have you turned off all the EIT settings? There is quite a few of them!

---

### Post by c1ru on 2010-05-12
I think no, only have used xmltv guide, not more. I can test it now. But i think the problem with the poor signal quality dont solved this.

I start to testing that.
I have set now all input to do not use eit for automatic update database and check it yes to open card on demand.
I have anothers options under "general" for how many time use eit before to change the channel and find more info, but only can set the time, not more.
I have testing now, when i do not use mytv, the led stills off, but at this moment, switch to watch one channel, and the led turns green. If i record one channel and swith to another the led turns orange.

At this moment i`m recording two channels and do not have the problem of poor signal.

Recording two channels and 0 pixelation....!!!!!

I have to test it for a long more time.

---

### Post by evey on 2010-05-12
Have you got an aerial booster?  If not, worth getting one of those (Try not to get a really cheap one that just add's noise to the signal).
if you do have an aerial booster connected, try removing it and plugging the aerial directly in- the booster may have started failing.
A couple of days ago I found our set top box was showing 'no signal' (The booster has two outputs - one for the mythbuntu box and another for the set top box).  Despite having the led on, the booster has stopped providing output - so unplugged it and plugged the aerial in directly - now fine.  The booster is probably only 2 months old.

---

### Post by c1ru on 2010-05-12
I dont have this problem. Dont use it.

I have another adapter, one nova-td-hd and never have this problem, all time do very good recordings w/o poor signal.

But all adapters with af9015 are more cheaps. half al least.

---

### Post by ozsliver on 2010-05-22
I'm also getting this problem after upgrading firmware to 4.95 :(

---

### Post by evey on 2010-06-03
After finding BBC channels hadn't tuned in (Others at that point working fine), tried a rescan - and no channels were detected, lost them all.  Tried eliminating everything on the aerial side, but ](*,)so am now about to do a clean reinstall with mythbuntu 10.4 and will use the 4.95 firmware from the outset.  Will post back as to how it's gone.

---

### Post by evey on 2010-06-03
Done a clean install of 10.4 (Looks nice) with the 4.95 firmware installed and cold rebooted before touching any myth backend config.
Did channel scan which did include BBC channels but seemed to omit a number of others (e.g. 5 USA) and noted most of the channel numbers seemed too high like I was picking up weaker signals from another trasnmitter.  When trying to view these channels get a 'no lock' timeout.  
So removed channels and tried another scan - now no channels picked up.  Tried removing the aerial booster - just in case of interference - and plugging aerial in directly and again no channels picked up.
Will ponder overnight what to do, even tempted with just shoving on another distro like Mythdora just in case...
Going to have to find that original posting on Mythbuntu about this dual tuner card 'working out of the box' and amend sharply, I bought the dammned card on that recommendation specifically for the myth box, hope I don't end up heading down the Windows Media Centre route - not what I wanted to end up but the amount of time and messing around this is taking is getting a bit much.
Might try just EIT tuning tomorrow - had enough for one evening.

---

### Post by ozsliver on 2010-06-07
Hi Evey  Unfortunately I think the problem is in firmware 4.95.  My setup worked perfectly with 4.65 until I upgraded to 10.04 and Myth 0.23.  If you can be bothered, try to get Mythbuntu 9.10 and do a clean install, it will probably work.  This problem upset me quite a lot.

---

### Post by evey on 2010-06-07
Thanks Ozliver.  I was starting to knock the card as having a very erratic tuner (And close to viciously amending that hardware posting about 'working out of the box').  What I'll do first is try putting on the 4.65 firmware in the current 10.4 install, and if that doesn't work, then try the 9.10 Mythbuntu with 4.65 firmware.   I'll repost once I get chance to do all that.
If I ever get Mythbuntu working with this card, it's going to be sooo backed up.
Cheers

---

### Post by ozsliver on 2010-06-07
Cool please let me know. 
I'm not sure firmware 4.65 will work with the 10.04 kernel though.

Looking at the changes here:

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/458444](https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/458444)

It looks like they changed stuff in the firmware to fix the bug above.

This may have broken the KWorld card functionality, look at posts #11 and #12. Maybe it would be worth it to notify the firmware's mailing list of the problem many people are having with this card.

I think the card is working fine, I've been running with Windows Media Centre for a couple of weeks with no problems at all.

---

### Post by evey on 2010-06-09
Between each firmware change, deleting of channels and cards, then cold reboot.  Long channel scan timeouts.

4.65 firmware - 13 channels found, very little usable, no main stream but did get price drop tv - 4.65 has a sense of humour; does anyone who takes the effort to build a myth box actually enable that type of channel except for laughs?...
4.71 firmware - it too has a sense of humour, 13 channels and it thinks I should be bidding for an over priced exercise bike.
4.73 firmware - 52 channels but crazy numbering - starting from 4168 and only getting partial lock when trying to view a channel, so can't bid on that medalian on a chain that looked so tasteful...
4.95 firmware - just for consistency reverted - 23 channels found, little main stream (Again no BBC etc.) - crazy numbering - started from 8384.

Now from [https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/458444/comments/19](https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/458444/comments/19) did :

$ sudo add-apt-repository ppa:chasedouglas/linux-firmware-nonfree
$ sudo apt-get update
$ sudo apt-get install linux-firmware-nonfree


Appeared I had the latest non free firmware anyway, cold reboot.

For the hell of it upped the card channel scan timeouts (Signal, channel) from 6000 ms, 12000 ms to 12000 ms, 18000 ms and now gone full circle and back to "No Channels Found".

Will also put a posting up on [https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/458444/](https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/458444/) about this in the hope in future of them getting the firmware to play nicely with this card - I sure hope it does get sorted as 10.4 looks nice and I can see the improvements in responsiveness.

So next, when I get chance, wipe and install the earlier 9.10 Mythbuntu and start the firmware fun again from 4.65 upwards.

---

### Post by evey on 2010-06-09
Further after adding an entry on the bugs.launchpad website, got a reply : [https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/458444/comments/43](https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/458444/comments/43)

I said in the reply to that on launchpad I'd start a new bug entry if the 4.65 firmware worked in 9.10 Mythbuntu, but if it doesn't work, don't hold your breath for any stable firmware for this card...

---

### Post by JasonEde on 2010-06-14
I upgraded to 4.95 after finding the 4.65 flakey for me. It seems that, for me, the card really doesn't like weak signal on any of the channels if you're using dual tuners and EIT. A friend of mine not far from me with a better aerial has no problem at all although he has a high gain digital aerial and mine is just standard gain one.

It also seems it is a bit more stable if only 1 of the tuners is connected. I didn't have a problem tuning channels once I'd dug the frequencies for the tune out of the relevant file in   [FONT=&quot]/usr/share/dvb/dvb-t/ and done a full scaned tune.

I have to say the firmware for this card really doesn't appear that stable at all (any version) of it and it also seems like the firmware upgrading has been abandoned. I'm seriously thinking of ditching this card for a better (more expensive :( ) dual tuner card. Such a shame as when it's working it is really good.

Is the source code for the firmware readily available? Isn't anyone interested in doing any more work on it as this is still a really common chipset.

I'll hold off upgrading to 10.04 by the looks of what posted here... Mine had become quite stable until I'd done some updates on 9.1 that seemed to cause issues with back-end :(
[/FONT]

---

### Post by evey on 2010-06-15
Tried the advice at [https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/458444/](https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/458444/) about unplugging the card completely, all power out for 10 mins and then re plugging - on 10.4 Mythbuntu - checked dmesg log - was showing as 4.95 firmware, did channel scan (As always loooong time outs) - same very patchy results.
Wiped and went back to 9.10 Mythbuntu and put in 4.65 firmware - again confirmed in dmesg log was that firmware version.  Ended up with daft/high channel numbers, anything that was found was either partial lock or breaking up badly when viewing.

Ozsilver - thanks for putting up that launchpad link - helped to illuminate a bit about this.  1.  The hardware page that mythbuntu links to is very unreliable and can lead to you buying incompatible hardware.
2.  From Chase Douglas comments on the launchpad thread :
"Until there's firmware that makes things work right for the card, I  think we should leave things as they are."
and barberio's : "Checking on the V4L wiki, the Peak/K-World PC-160-T is known to be buggy  with the current linux driver. I'm afraid you'll have to wait for  upstream support fixes for this specific hardware from Linux TV and I'll  have to refer you to [http://www.linuxtv.org/"]("http://www.linuxtv.org/")

Out of interest Oz, what version of Media Centre are you running (e.g. is it Windows 7 etc.)

Jason - quite agree, I'm considering either ditching the card or shelling out for Windows Media centre but as always would really like to get Myth going - want to have a lamp stack to play with other stuff.  From having a brief look across at people running Windows Media centre with this card, few report issues which makes me think we're back into pointing to the firmware and a long, long wait if ever someone bothers to fix it.  My true annoyance is at that hardware compatibility page. 

So I noticed this Hauppage Nova -TD 500 dual DVBT [http://www.ebuyer.com/product/113946](http://www.ebuyer.com/product/113946) which seemed a lot cheaper for a hauppage dual card (I went for the Peak because when I was looking at Hauppage dual tuners they where around the £80 mark) but I now don't know who to trust as to whether that card really would be 'compatible'.  Also now seen [http://www.amazon.co.uk/Hauppauge-WinTV-Nova-digital-tuner/dp/tech-data/B000I1RHWA/ref=de_a_smtd](http://www.amazon.co.uk/Hauppauge-WinTV-Nova-digital-tuner/dp/tech-data/B000I1RHWA/ref=de_a_smtd) Hauppage Nova T 500 Dual.  The Nova TD ones have the 'diversity' bit which seems to be very ambiguous about the firmware support, so I think it would be so far the straight Nova T 500.

The only one I know of is [http://www.mythtv.org/wiki/Video_capture_card](http://www.mythtv.org/wiki/Video_capture_card) linked from mythbuntu.org.

Does anyone know of a sound source for hardware advice with Mythbuntu - feel I've been stung already and really, really loathed to shell any more out on the risk of yet another dead end.

---

### Post by evey on 2010-06-15
I've also amended that hardware entry at [http://www.mythtv.org/wiki/Kworld_DVB-T_PC160-2T](http://www.mythtv.org/wiki/Kworld_DVB-T_PC160-2T)

---

### Post by JasonEde on 2010-06-15
> **evey said:**
> 

Jason - quite agree, I'm considering either ditching the card or shelling out for Windows Media centre but as always would really like to get Myth going - want to have a lamp stack to play with other stuff.  From having a brief look across at people running Windows Media centre with this card, few report issues which makes me think we're back into pointing to the firmware and a long, long wait if ever someone bothers to fix it.  My true annoyance is at that hardware compatibility page. 

So I noticed this Hauppage Nova -TD 500 dual DVBT [http://www.ebuyer.com/product/113946](http://www.ebuyer.com/product/113946) which seemed a lot cheaper for a hauppage dual card (I went for the Peak because when I was looking at Hauppage dual tuners they where around the £80 mark) but I now don't know who to trust as to whether that card really would be 'compatible'.  Also now seen [http://www.amazon.co.uk/Hauppauge-WinTV-Nova-digital-tuner/dp/tech-data/B000I1RHWA/ref=de_a_smtd](http://www.amazon.co.uk/Hauppauge-WinTV-Nova-digital-tuner/dp/tech-data/B000I1RHWA/ref=de_a_smtd) Hauppage Nova T 500 Dual.  The Nova TD ones have the 'diversity' bit which seems to be very ambiguous about the firmware support, so I think it would be so far the straight Nova T 500.



My other card is a Hauppauge DVB-S2 card and although its not been used much it has been extremely reliable although it wasn't cheap. As a bonus I managed to get the remote control working quite easily too.

If I change the card I'll be looking at Hauppauge cards. I've only 1 aerial cable that can use for the card and as don't want to split it so I'll need a dual tuner card with 1 aerial input... I'm going to wait until the signal here is back to its normal strength before I decide fully what I'll do with the peak card.

Jason

---

### Post by evey on 2010-06-15
I've ordered the Nova T 500 Dual from Amazon; felt I'd exhausted the search to try to work out the situation with Mythbuntu - it appears to be ok.  I think if anyone ever asked me about building a Myth box I'd suggest trying any kit they may already have but if it came down to buying a new TV tuner, start the research from the point of view of only buying a Hauppage card.

And after that's tuned in (Oh had that card better behave itself) just need to sort out the MS Media centre keyboard and getting that to work...glutton for punishment me thinks.

Good luck Jason with the signal strength - you never know by the time that get's sorted someone might have noticed the firmware and this card and done something about it.

---

### Post by ozsliver on 2010-06-21
Hi Evey

I can feel your pain mate. I spent many days researching which hardware to buy to have a reliable Myth box, as few of my friends got stung. I also spent much more on the motherboard/graphics card combo to have nVidia where an ATI card would have been cheaper if I knew I had to run Media Centre instead. You did well updating the hardware Wiki, I was thinking to do it myself.

So I really really tried hard for a Myth box, but I got fed up after the botched upgrade. As you pointed out, there are not many choices for a dual digital tuner for Myth that do not cost a bomb. I didn't want to shell out for the Hauppauge. I considered the Leadtek DTV2000DS as it had a similar price to the KWorld, but no one had used it yet, and now reading here it seems to have similar problems:

[http://www.xpmediacentre.com.au/community/tuners/41937-leadtek-dtv2000ds.html](http://www.xpmediacentre.com.au/community/tuners/41937-leadtek-dtv2000ds.html)

I'm now running Windows 7 Media Centre, and I must reluctantly admit it is a great software. I just moved in in a weaker signal area but the card is working very very well. Also the UI is simple and great and the TV guide works out of the box for Australia.

All the best, I think choosing the Hauppauge was a wise choice if you want to stick with Linux.

---

### Post by evey on 2010-06-22
Hi Oz

The problem I think too with the sources for hardware compatibility research and them being updated is that you have to go through so much fiddling with the setup that you're not sure if it's something you've missed until maybe a few months down the line when you really start pointing the finger at something and feeling confident about it- in this case the firmware, and I guess people by then are so fed up they don't want anything more to do with it - including updating the hardware compatibility listings, all of this stuff is a time sink.

Anyway - it's been running well for 4 days, gone crazy with the scheduled recording - plenty of times used both tuners to record and then realising when I want to watch something else I've gone silly and 'no more tuners' available.  I'll see if that Hauppage card keeps on coming down in price, or maybe see if there's one on ebay.
Only thing that did happen is the web service went down - haven't had to chance to find out what triggered that but a service httpd start brought it back up.
  
I nearly ended up sending the card back because Amazon sent me a Nova TD (Diversity) instead of the straight Nova T 500.  I'd read some older stuff about issues with the TD but decided yet again to hunt further and it turned out they had sorted out the firmware for it.

Convinced that if anyone is starting out building one of these and already has the kit lying around (Mine was built mostly from stuff that didn't sell on a car boot sale) then give it a go, but to avoid frustration only buy Hauppage tuner cards if they're going to buy a tuner card.

From reading that posting the Leadtek looks like a similar world of pain to the Peak/Kworld, so like you say best avoided for Myth.

Personally I'm not a head banging Linux, Mac, Windows zealot (Worked with a few of them that worship at their respective altars) and I just think go for the 'tool for the job'.  Because I wanted to do some Java development on the media side I really wanted to get the myth box running, but on the practical side for the family to use if it hadn't worked out, it would probably have been a Win7 media centre.

May the signal strength be with you Oz :mrgreen:

---

### Post by JasonEde on 2010-06-22
Evey - Does the Hauppauge TD500 seem to be much more stable? Have you EIT scanning on as well?

---

### Post by evey on 2010-06-23
Hi Jason - haven't EIT scanned it but I did 2 scans and they were consistently stable - same set of complete channels including the BBC ones which I couldn't get with the Peak/KWorld card.  Also signal strength during scans much higher (I know it may be just what the firmware is reporting rather than the absolute truth) and locking is far quicker.
Haven't had any issues with the Hauppauge tuner card, only issues I've had is apache stopping and twice the box being unresponsive (Nothing on the network) as if it has suspended (Probably bios pesky energy saving setting).
I suppose you're thinking about it because of the radio listings; if I was trying to pull that one off then I would go with a Hauppage card, especially as the prices appear to have come down, and who knows they may come down further with HD pushing prices as the top.  I paid £51.58 with the 'free super saver' delivery - it was worth it just to stop the tail chasing.
I only enabled tv channels (And got rid of fair few of them e.g. QVC), I'll have a look at those that I've disabled and see if there are radio ones in that list (I suspect the way I did the XMLTV setup they should still be there).  I'll let you know.

---

### Post by evey on 2010-07-16
Whoops - just looked back at this thread an realised I didn't get back about the radio side of things- sorry Jason had a lot of distractions on.
When I checked through the additional channels where all tv, no radio picked up during a full channel scan.   Don't know if a scan with EIT would pick radio up but as it's taken so long to get this right + hassle from family if something breaks means I don't want to risk breaking the set up at the moment.  So paranoid now about going to sort out a disk image of it this weekend.

---

### Post by JasonEde on 2010-07-16
I've just splashed out on Hauppauge Nova TD500 and upgraded to 10.04 at the same time. All looking good so far although I only installed last night.

---

### Post by evey on 2010-07-17
Fingers crossed for you.  If you do start to have issues I suggest enabling the testing repositories for mythtv (I think you get 2 choices - the bleeding edge version or the current - I stuck with the current).  I had issues with 10.4 playing DVD's (Just locked for a while then spit back into the menu) - this was fixed when I added the testing repositories.

I'm splashing out - a little - on the mythbox; next week should be moving it out of the old recked 'Tiny Computer Systems' case into a media centre case (Full height) - still a cheapie (£27) but have also bought ultra quiet 80mm fans, gel mounts and general quietening gear to make it ok for the front room.

Have been keeping an eye out for another Nova TD 500 but secondhand and cheap (Nothing cheap enough yet on ebay) as I have on occasion been recording on both tuners and wanting to watch something else.  I know I could start to delve into the banding business to record two programs from one tuner but if the card is cheap and just works...

Issue though this weekend - get the setup disk imaged and sort out the very laggy MCE remote (And MS USB IR Reciever) - probably by switching in the Nova TD 500's IR detector and using the Hauppage remote instead.

---

### Post by JasonEde on 2010-07-17
I'm using the Hauppauge remote on the DVB-S card although the remote looks the same as the one for the TD500 card. Just takes a bit of tweaking to get the control as you like it. If get stuck I can post configs. Only thing I added was  a script on startup to make sure I always mapped the correct event id for the remote as the event number changes if have keyboard connected etc...

---

### Post by evey on 2010-07-18
The MCE remote handling driver seems to get flooded with requests  incredibly quickly, so you have a situation where you want to say  scroll up or down a menu, hitting up or down then you'll find it'll seem  to just stop working and you have to then wait several seconds between  pressing a key on the remote to get a response.

Spent hours and hours last night trying to sort out the Hauppauge 500 TD remote - to no avail.  Plugged the IR lead into the card, disconnected the mce USB IR receiver, set in ControlCentre IR setting to be Nova T 500, rebooted for good measure.

Used the arrow keys on the remote and thought - great, no more dreadfully laggy slow MCE remote - response was instant and repeatable...Except the only keys that seemed to work were the arrow keys and as not even the OK button would work rendered the remote useless...so near but so far.

Tried all the different Hauppauge configs in control centre; no change (Checked that the /etc/lirc conf files where pointing to the hauppauge config).  Checked output of lirc on command line with irw - was reacting to all keys except the 'Go' and 'OK' keys, so I set off on a mission to find the correct keycodes for the lirc.conf file.  At first tried using the irrecord app to generate codes for the keys but didn't get along with that because of the amount of key holding and waiting, and waiting for it to get ti's baseline inputs to work.

So scouted round the internet for different Hauppage remote codes for Ok and Go, and tried each of these in the lirc conf file - retarting lirc service each time - and checking irw - no reaction to those keys but was to all the others.  After exhausting thelist or codes I went back to irrecord and percevered more with it and finally got two codes out for the keys 0x60 and 0x62 which again didn't work.

Wondering if there was an issue of a duplicate key mapping file (I knew if I changed the lirc conf file, irw output would show those changes) which was screwing things up when trying to use the remote with myth.  So checked and could only find the single ./lirc/mythtv keymapping file and the key name mappings matched those in the lirc conf file.
Tried modifying the key mapping file so that the Hauppage remote's up arrow mapped to down - the change had no effect and the up arrow still sent the up keystroke in the mythfront end menu.

Then wondered if I had somehow two instance of lirc running - ps aux | grep lirc showed the one.  
This is the wierdest - out of curiosity shut down lirc, fired up myth front end, and the arrow keys on the Hauppage remote were still working - what on earth is doing that if lirc isn't running :shock:???

So would be interested in seeing your lirc config files.  Also, I've got a MCE keyboard - the remote control type keys work but the qwerty side doesn't - as I understand if you enable the keyboard you end up disabling the mce remote.  Have you got this working?

cheers

---

### Post by evey on 2010-07-19
Looked at the MCE keyboard again and noticed - ironically - that the remote parts that do work on it don't have the request flood issue.  Did a bit more hunting around about this and on the remote side it looks either that I've got a version 1 instead of a version 2 or simply the remote has had it.  Seems the the flood issue is more related to when you run the MCE keyboard driver along with continuous keyboard key repeats.
So splashed out a little more for a Philips version 2  MCE remote, I await delivery to see if it's done the trick.

MCE keyboard wise, I'm just going to Ebay it as I don't see any solution for it's issues with lirc on the horizon.  Had a Logitech MX5000 keyboard that I wasn't using so tried plugging that into the Myth box and was surprised to find it popping up with 'enter code' and away it went.  Not quite as nice as the MCE keyboard but the qwerty keys etc. and even the volume slider controls on it work so happy with that.  It's coming together bit by bit.

---

### Post by Edglex on 2010-11-03
Did anybody ever succeed in getting this card to work reliably? I am currently building a myth box, and having spent a few hundred already I was hoping to be able to get this tuner to work as it is pretty cheap (e.g £28.99 here [http://www.advancetec.co.uk/acatalog/Kworld_PlusTV_Dual_DVBT_PC1602T_tv_card.html](http://www.advancetec.co.uk/acatalog/Kworld_PlusTV_Dual_DVBT_PC1602T_tv_card.html))

There is a new 5.10 firmware available I hear. Anyone tried it?

---

### Post by evey on 2010-11-03
I haven't because it was enough getting a reliable card to work.  
Even with Hauppauge I wanted to add an extra digital tuner card but gave up on those (Both were HVR models - one pci, the other pcie) and I've left it with the Nova TD 500 in the mythbox as it works, although it would have been nice to have another tuner to cope with live tv viewing and recording clashes.

If someone's tried the firmware and it really, really works stably - great.  I've still got the Peak card - haven't got round to ebaying it.  But quite frankly as all my family depend on the mythbuntu box don't want to even breathe on it, let alone risk something else.  I'd be intrested too to hear if anyones tried.

But if it isn't right yet I can't recommend strongly enough to go with something that just works as the cost difference is nothing compared to the timesink of trying to sort out issues.

---

### Post by milaebrothers on 2010-11-10
Hi to all, this is my firs post.

I'm italian, and my English isn't perfect.

I solved in this way, with my ubuntu 10.04.1 and firmware 5.10:

```

sudo apt-get install mercurial build-essential linux-image-`uname -r` linux-headers-`uname -r`

hg clone http://linuxtv.org/hg/~anttip/tda18218

gedit tda18218/linux/drivers/media/dvb/frontends/af9013.c


```edit the file af9013.c and modify this part

```

/* TDA18271 uses different sampling freq for every bw */
        if (state->config.tuner == AF9013_TUNER_TDA18271) {
            switch (bw) {
            case BANDWIDTH_6_MHZ:
                if_sample_freq = 3300000; /* 3.3 MHz */
                break;
            case BANDWIDTH_7_MHZ:
                if_sample_freq = 3800000; /* 3.8 MHz */
                break;
            case BANDWIDTH_8_MHZ:
            default:
                if_sample_freq = 4300000; /* 4.3 MHz */
                break;
            }

```in this way (editing the sampling freq for BANDWIDTH_7_MHZ as the TDA1821) :

```

/* TDA18271 uses different sampling freq for every bw */
        if (state->config.tuner == AF9013_TUNER_TDA18271) {
            switch (bw) {
            case BANDWIDTH_6_MHZ:
                if_sample_freq = 3000000; /* 3 MHz */
                break;
            case BANDWIDTH_7_MHZ:
                if_sample_freq = 3500000; /* 3.5 MHz */
                break;
            case BANDWIDTH_8_MHZ:
            default:
                if_sample_freq = 4000000; /* 4.0 MHz */
                break;
            }

```
note: I cannot try if it's better 3 MHz or 3.3 Mhz for the case BANDWIDTH_6_MHZ.  


```

cd tda18218

make

```stop after 10s with CRTL+C

```

sudo sed -i 's/CONFIG_DVB_FIREDTV=m/CONFIG_DVB_FIREDTV=n/' ./v4l/.config

make

sudo make install

sudo rm /lib/firmware/dvb-usb-af9015.fw

cd /lib/firmware

sudo wget http://palosaari.fi/linux/v4ldvb/firmware/af9015/5.1.0.0/dvb-usb-af9015.fw

sudo reboot


```Paolo

---

### Post by Edglex on 2010-11-16
Hi, thanks for that! 
So does it now work reliably - i.e. doesn't crash after a few hours? If so I think it'd be worth me getting this instead of a hauppage card. 

I only have 1 card slot in my system so I need a dual tuner. 

Thanks!

---

### Post by milaebrothers on 2010-11-18
If i use for a long time dvb-s card, sometime it crashs.  
But often it return to work without shutdown!!

---

### Post by gregoryo2013 on 2013-04-15
I've been having similar problems to what's described here with my Leadtek DTV2000DS (af9013 af9015) on Mythbuntu 12.04, using EIT and DVB-T in Perth, Western Australia. Signal strength is reasonable, but perhaps a contributing factor. I'm considering dropping EIT in favour of shepard, but for now I've put this workaround in place:

* Use linscripts logmon [https://code.google.com/p/linscripts/wiki/logmon](https://code.google.com/p/linscripts/wiki/logmon) to monitor syslog for "af9013: I2C (read|write) failed reg" and call a script 'Responder'
* 'Responder' increments a counter in a file, and if a threshold is reached, restarts mythtv-backend and resets the counter

I've only had it going for a week, but I've seen a couple of restarts and the system is still operating fine.
HTH, Greg.

---

### Post by codemaniac on 2013-04-15
Old thread closed. Please feel free to start afresh.

---

