---
title: "Can't get DVB USB tv tuner happening"
date: 2012-07-27
forum: Multimedia Software
---

### Post by Bucky Ball on 2012-07-27
Hi all,
 
*** Please head for the second post. ****Read below in this post for background info only. **** Original prob was couldn't get missing channels, AND couldn't get picture. Have changed the thread title. ;) **[B]I have gotten the tuner working but still can't find missing stations. 
[/B]
*** Original Problem and background:**

Just bought an EZCap 646 USB TV tuner. DVB-T and DAB/DAB+ also. There's even a Linux driver on the install disk! How quaint (although not well explained). The dongle is recognised, can even scan, but not see, some channels. Here goes:
 
This is from the end of dmesg after I plug the dongle in:
 
 ```
[ 6728.852025] usb 1-7: new high speed USB device using ehci_hcd and address 4 
 [ 6729.195283] IR NEC protocol handler initialized 
 [ 6729.235715] IR RC5(x) protocol handler initialized 
 [ 6729.285064] IR RC6 protocol handler initialized 
 [ 6729.298766] IR JVC protocol handler initialized 
 [ 6729.417675] IR Sony protocol handler initialized 
 [ 6729.421629] dvb-usb: found a 'RTL2832U DVB-T USB DEVICE' in warm state. 
 [ 6729.421641] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer. 
 [ 6729.424175] DVB: registering new adapter (RTL2832U DVB-T USB DEVICE) 
 [ 6729.430876] DVB: registering adapter 0 frontend 0 (Realtek RTL2832 DVB-T  RTL2836 DTMB)... 
 [ 6729.431425] dvb-usb: RTL2832U DVB-T USB DEVICE successfully initialized and connected. 
 [ 6729.431453] dvb-usb: found a 'RTL2832U DVB-T USB DEVICE' in warm state. 
 [ 6729.431464] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer. 
 [ 6729.437254] lirc_dev: IR Remote Control driver registered, major 250  
 [ 6729.441648] DVB: registering new adapter (RTL2832U DVB-T USB DEVICE) 
 [ 6729.443631] DVB: registering adapter 1 frontend 0 (Realtek RTL2832 DVB-T  RTL2836 DTMB)... 
 [ 6729.444507] dvb-usb: RTL2832U DVB-T USB DEVICE successfully initialized and connected. 
 [ 6729.444936] usbcore: registered new interface driver dvb_usb_rtl2832u 
 [ 6729.518258] IR LIRC bridge handler initialized 
 [ 6827.051886] ISO 9660 Extensions: Microsoft Joliet Level 3 
  [ 6827.067938] ISOFS: changing to secondary root 
``` femon:
 
```
Problem retrieving frontend information: Operation not permitted  
 status       | signal fff4 | snr 002a | ber 009818f8 | unc 0025fcf9 | 
``` w_scan: This is from the end of the output of w_scan:
 
  ```
Info: SDT(actual) filter timeout  
 Info: NIT(actual) filter timeout  
 tune to: QAM_AUTO f = 219500 kHz I999B7C999D999T999G999Y999  
 (time: 08:38) Info: PAT filter timeout  
 Info: SDT(actual) filter timeout  
 Info: NIT(actual) filter timeout  
 tune to: QAM_AUTO f = 226500 kHz I999B7C999D999T999G999Y999  
 (time: 08:53) Info: PAT filter timeout  
 Info: SDT(actual) filter timeout  
 Info: NIT(actual) filter timeout  
 tune to: QAM_AUTO f = 564500 kHz I999B7C999D999T999G999Y999  
 (time: 09:07) Info: PAT filter timeout  
 Info: SDT(actual) filter timeout  
 Info: NIT(actual) filter timeout  
 dumping lists (0 services) 
``` Done.  
 
The scan does work but only picks up one station. I would really like to know how  to make a channels.conf when I do a w_scan. I can't find one. I start Me-TV and 'Failed to lock to channel'. I've also done a scan with that and picks up the same channel as w_scan (and it's related stations). I used the 'au-Adelaide' scan file (which seems to be provided in a vast selection by Me-TV) to do the scan. Channels it finds (SBS for those in Australia) are right but no picture in Me-TV, although I can see the program guide for one channel, even though the others are visible. Can't select (can't lock to channel). Tried VLC and a heap of others to no avail.
 
 DVB-T all new to me me, so any help handy. I've seen a lot of advice, but confused. Just want and app that can show me tv and play the DAB. Cool. ;)  
 
 All advice welcome and, as usual, tnx in advance. BB

---

### Post by Bucky Ball on 2012-07-28
Good news is:

I installed Freevo and that installed a heap of lib*** files. Freevo didn't work, didn't see the dongle at all. Closed that, tweaked around a bit (not much), but whatever I did or Freevo installed worked for Me-TV; even though I've only got about eight of a possible 31 channels (and no DAB), they do now indeed appear to be working faultlessly with a pretty good picture (the resolution tweak is at the computer end). 

So, my problem is now how do I scan for the other channels? In the scan file I used with Me-TV all the channels are listed if I open the file in a text editor:

                         > # Australia / Adelaide / Mt Lofty
    [LEFT]**# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy**[/LEFT]
    [LEFT]# ABC[/LEFT]
    [LEFT]T 226500000 7MHz 3/4 NONE QAM64 8k 1/16 NONE[/LEFT]
    [LEFT]# Seven[/LEFT]
    [LEFT]T 177500000 7MHz 3/4 NONE QAM64 8k 1/16 NONE[/LEFT]
    [LEFT]# Nine[/LEFT]
    [LEFT]T 191625000 7MHz 3/4 NONE QAM64 8k 1/16 NONE[/LEFT]
    [LEFT]# Ten[/LEFT]
    [LEFT]T 219500000 7MHz 3/4 NONE QAM64 8k 1/16 NONE[/LEFT]
    [LEFT]# SBS[/LEFT]
    [LEFT]T 564500000 7MHz 2/3 NONE QAM64 8k 1/8 NONE[/LEFT]
 These are all correct re the right stations. But only SBS channels are found with scan. I have made the first line bold as I'm wondering if what's in there has something to do with my problem. The others appear to be getting found when I w_scan but the scan stops for awhile then I get:

```
tune to: QAM_AUTO f = 177500 kHz I999B7C999D999T999G999Y999 
(time: 08:04) Info: PAT filter timeout
Info: SDT(actual) filter timeout
Info: NIT(actual) filter timeout

```

BTW: The device seems to be happening at: /dev/dvb/adapter1/frontend0

---

### Post by Bucky Ball on 2012-07-28
Ah, just had another thought. I ran dvbsnoop -s feinfo and got this:

```
dvbsnoop V1.4.50 -- [http://dvbsnoop.sourceforge.net/](http://dvbsnoop.sourceforge.net/) 

---------------------------------------------------------
FrontEnd Info...
---------------------------------------------------------

Device: /dev/dvb/adapter0/frontend0

Basic capabilities:
    Name: "Realtek RTL2832 DVB-T  RTL2836 DTMB"
    Frontend-type:       OFDM (DVB-T)
    [B]Frequency (min):     174000.000 kHz
    Frequency (max):     862000.000 kHz[/B]
    Frequency stepsiz:   166.667 kHz
    Frequency tolerance: 0.000 kHz
    Symbol rate (min):     0.000000 MSym/s
    Symbol rate (max):     0.000000 MSym/s
    Symbol rate tolerance: 0 ppm
    Notifier delay: 0 ms
    Frontend capabilities:
        auto inversion
        FEC 1/2
        FEC 2/3
        FEC 3/4
        FEC 5/6
        FEC 7/8
        FEC AUTO
        QPSK
        QAM 16
        QAM 64
        QAM AUTO
        auto transmission mode
        auto guard interval
        auto hierarchy

Current parameters:
    Frequency:  564500.000 kHz
    Inversion:  ON
    Bandwidth:  7 MHz
    Stream code rate (hi prio):  FEC 2/3
    Stream code rate (lo prio):  FEC AUTO
    Modulation:  QAM 64
    Transmission mode:  8k mode
    Guard interval:  1/8
    Hierarchy:  none
```The RTL2832 is correct (actually should be RTL2832U but machine sees it and working). Wondering if the frequency range, which I've put in bold, is too small and that's why it's only picking up one station. How do I change that or find what it's supposed to be? I figure that scan file I've been using in Me-TV is probly right after all.

---

### Post by Bucky Ball on 2012-07-28
Well, just got VLC to do a scan (I wasn't expecting it) but found no  channels. Can't get it to scan again, though. Just gives me the same error it was giving before:

 >  [COLOR=#000000]VLC is unable to open the MRL 'dvb://frequency=0000'. Check the log for details.[/COLOR]
 [COLOR=#000000][... *and with the channel frequency*:][/COLOR]
  [COLOR=#000000]VLC is unable to open the MRL 'dvb://frequency=226500000000'. Check the log for details.[/COLOR]
 Have tried other frequencies from the au-Adelaide file. Same as above. Can't find vlc log but will persevere.

---

### Post by errrn on 2012-07-28
I'd suggest trying tvtime. the scanner is more "agressive" and will do a sweep through every frequency your tuner can handle.

it's in the software center.

---

### Post by Bucky Ball on 2012-07-28
> **errrn said:**
> I'd suggest trying tvtime. the scanner is more "agressive" and will do a sweep through every frequency your tuner can handle.

it's in the software center.

Thanks, but launches then immediately closes when I launch it, throwing this error when run from the terminal:

```
:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/bucky/.tvtime/tvtime.xml
videoinput: Cannot open capture device **/dev/video0**: No such file or directory
mixer: Can't open device /dev/mixer, mixer volume and mute unavailable.
Segmentation fault
```The capture device is **/dev/adapter1** so do you know where the config file for TVTime is so I can change that? I've had a sniff but didn't see much promising. How do you get TV? Remember; I am using a DVB-T USB TV tuner, not a capture card. This seems to be for capture cards but I'd like to be enlightened ... ;)

Meanwhile, this is where I'm at this morning. This is what happens when I plug in the TV tuner now:
 
```
[ 3461.568022] usb 1-7: new high speed USB device using ehci_hcd and address 4 
 [ 3461.771788] IR NEC protocol handler initialized 
 [ 3461.788224] dvb-usb: found a 'RTL2832U DVB-T USB DEVICE' in warm state. 
 [ 3461.788237] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer. 
 [ 3461.790418] IR RC5(x) protocol handler initialized 
 [ 3461.792323] DVB: registering new adapter (RTL2832U DVB-T USB DEVICE) 
 [ 3461.795967] DVB: registering adapter 0 frontend 0 (Realtek RTL2832 DVB-T  RTL2836 DTMB)... 
 [ 3461.799670] dvb-usb: RTL2832U DVB-T USB DEVICE successfully initialized and connected. 
 [ 3461.799703] dvb-usb: found a 'RTL2832U DVB-T USB DEVICE' in warm state. 
 [ 3461.799713] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer. 
 [ 3461.807083] IR RC6 protocol handler initialized 
 [ 3461.813092] DVB: registering new adapter (RTL2832U DVB-T USB DEVICE) 
 [ 3461.815503] DVB: registering adapter 1 frontend 0 (Realtek RTL2832 DVB-T  RTL2836 DTMB)... 
 [ 3461.816039] dvb-usb: RTL2832U DVB-T USB DEVICE successfully initialized and connected. 
 [ 3461.816477] usbcore: registered new interface driver dvb_usb_rtl2832u 
 [ 3461.830393] IR JVC protocol handler initialized 
 [ 3461.909895] IR Sony protocol handler initialized 
 [ 3461.924099] lirc_dev: IR Remote Control driver registered, major 250  
 [ 3461.929522] IR LIRC bridge handler initialized 
``` All looks good and the remote is even registered. I also got xine working, but that only gets one channel; a totally different channel than Me-TV &#8211; Channel 44, which is a community channel. I also managed to generate a channels.conf file in /xine/.tzap/channels.conf and, yes, that has the one channel xine is picking up in it. I tried to be tricky and grabbed the scan file:
 
 > # Australia / Adelaide / Mt Lofty
 # T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
 # ABC
 T 226500000 7MHz 3/4 NONE QAM64 8k 1/16 NONE
 # Seven
 T 177500000 7MHz 3/4 NONE QAM64 8k 1/16 NONE
 # Nine
 T 191625000 7MHz 3/4 NONE QAM64 8k 1/16 NONE
 # Ten
 T 219500000 7MHz 3/4 NONE QAM64 8k 1/16 NONE
 # SBS
  T 564500000 7MHz 2/3 NONE QAM64 8k 1/8 NONE &#8230; and attempted to turn it into something for the channel.conf by using the details above and changing the format. Didn't work. Below is what I did:
 
> 44 Adelaide(44Adelaide):543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_NONE:QPSK:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:100:101:3585
 # T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
 ABC
  (ABC):226500000:INVERSION_AUTO:BANDWIDTH_7_MHz:FEC_3_4:FEC_NONE:QPSK:TRANSMISSION_MODE_8k:GUARD_INTERVAL_1_16:HIERACHY_NONE:100:101:3585 I did the scan using this command: ```
w_scan -ft -c AU -X | tee .xine/channels.conf
``` First error:
 
> (there is a bit here I missed)settings for AUSTRALIA 
 DVB aerial 
 DVB-T AU 
 frontend_type DVB-T, channellist 3 
 output format czap/tzap/szap/xine 
 Info: using DVB adapter auto detection. 
     /dev/dvb/adapter0/frontend0 -> DVB-T "Realtek RTL2832 DVB-T  RTL2836 DTMB": good :-) 
     /dev/dvb/adapter1/frontend0 -> DVB-T "Realtek RTL2832 DVB-T  RTL2836 DTMB": good :-) 
 Using DVB-T frontend (adapter /dev/dvb/adapter0/frontend0) 
 -_-_-_-_ Getting frontend capabilities-_-_-_-_  
 Using DVB API 5.2 
 frontend Realtek RTL2832 DVB-T  RTL2836 DTMB supports 
 INVERSION_AUTO 
 QAM_AUTO 
 TRANSMISSION_MODE_AUTO 
 GUARD_INTERVAL_AUTO 
 HIERARCHY_AUTO 
 FEC_AUTO 
 -_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_  
 Scanning 7MHz frequencies... 
 177500: (time: 00:01) (time: 00:04) __tune_to_transponder:1733: ERROR: FE_READ_STATUS failed: 1 Operation not permitted  Can't think of anything else right now but feel free to chime in &#8230; attempting to crack a nut here which is no doubt a lot easier than my lack of experience with anything DVB is dragging me through. Still, I'm learning something (which I don't really have time to learn right now!). ;)
 
All ideas appreciated.

** UPDATE: I deleted all the channels in Me-TV, rescanned, and this time it picked up another channel, not SBS but 7! Who knows. That is coming through loud and clear (well, little jumpy, but think that's another tweak, perhaps not Me-TV). My next step is to create files with just one channel in them, scan each separately with Me-TV and see how that goes. Long winded but if it works ... Onward and upward!!!

---

### Post by Bucky Ball on 2012-07-29
Not so fast ...

Was checking channel 7, everything looked stable. Suddenly starts getting real pixelated then dies. Haven't managed to get anything back since. Wonder what I tweaked? (Think I did do something in an attempt to get the other channels). I am doing a scan with this command:

```
w_scan -c AU -a 1 -x > au-Adelaide
```Goes ok but get this when it finds the *correct* frequencies:

```
Info: NIT(actual) filter timeout

```Hunted high and low but can't find anything that tells me how to fix. Fingers crossed someone who knows what they're doing rolls along ... ;)

---

### Post by Bucky Ball on 2012-07-29
Well, finally fixed, enough to watch the Olympics anyway. I checked and one of the connecting aerial cables was dodgy (there are three to get here) so I was doing some things right all along and that was throwing me. Wondered why I had a perfect channel then it went pixie and died.

I discovered on my laptop with Win7 (where it was working) that the connection was dodgy, AND that the dongle only works in the eSATA/USB combo slot! Weak signal and kills the signal eventually in any other.  
 
 I had a short USB extension cable attached from dongle to computer so I took that off and plugged the dongle directly into a USB 2.0 slot on the desktop so I knew I was getting signal. Recognised by dmesg.

I did successfully change an entry from the scan file to the channels.conf syntax and it worked a treat! So, to save some work, thought I'd look for a channels.conf file for Adelaide, Australia, and sure enough, I found a couple. Trouble is, both quite old and missing a couple of channels (29, now 32 I think). I'll keep digging for that.
 
 So I have a channels.conf file that works with gxine and xine, but Me-TV still finds nothing when I scan using that channels.conf and nothing at all when I scan using the original scan file (au-Adelaide) which originally gave me a random channel (I now presume the dongle may have been cutting in and out; scans regardless of signal). Don't know what upset Me-TV's. I'll keep digging around for a more up-to-date channels.conf for Adelaide or attempt to cobble one together myself.  
 
 Well, thanks to the poster and myself for all my help. As happens with some of my threads, they are like a therapy to help me work it out, and I eventually solve the issue myself. I'll write a condensed how-to and post a link right HERE later. Hopefully that will save someone a couple of days or at least get them on their way.
 
Now where was I? Oh, that's right; working on the laptop (on what I was supposed to be doing for two days) and poolside at the Olympics on the desktop. Sweet. ;)

---

### Post by Bucky Ball on 2014-06-20
Just a quick note before closing this ancient thread: If you are in Australia and having trouble getting SBS, Channel 10, or any other channels, don't bother with the 'au-Adelaide', or whatever your state may be, go for the 'auto-Australia' channels.conf in the dvb-t database. I was setting Me-TV up again just the other day and took me an age to figure out how to get all channels. I found 'auto-Australia' by accident as I was scrolling through the list of channels.conf files in dvb-t! Work a charm and picked up everything! ;)

Have fun, and before myself or anyone else accuses me of necromancy:

*Thread Closed. ;)*

---

