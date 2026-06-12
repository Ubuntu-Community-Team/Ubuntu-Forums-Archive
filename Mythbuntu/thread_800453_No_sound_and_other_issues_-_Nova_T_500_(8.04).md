---
title: "No sound and other issues - Nova T 500 (8.04)"
date: 2008-05-19
forum: Mythbuntu
---

### Post by amphibem on 2008-05-19
OK so I have just installed my new Nova-T 500 (took an age to get here), and have some pressing issues.

1) No sound with the digital channels, works on the one analog channel through my PVR-150.

2) Cannot get mythfilldatabase to poplulate the guide from the digital channels. The data is coming from an external file ([xmlTVNZ]("http://www.reven.co.nz") and that is fine. Have tried different source numbers with no luck.

3) It has crashed a couple of times, havn't tested much on this though

Other (less important stuff) is:

- LiveTV very sluggish but probably can't fix that. I have set channel tuning delay to 75ms, but the digital TV here is HD on the main channels, and as you can see in my sig I am lacking in the required grunt. As the TV is 800x600 I will look for ways to reduce the proccessing load (80%+ it seems). But not for now

The card is configured as a 'DVB DTV capture card (v3.x)', signal timeout and tuning as default. I have turned off 'active EIT scan' and 'open card on demand'. The second of these fixed the complete crashes when opening LiveTV I initially had.

Also added these to /etc/modprobe.d/options

```

options dvb_usb disable_rc_polling=1
options dvb-usb-dib0700 force_lna_activation=1

```

Obviously I have googled, and read heaps on this site. At this stage I would love to get this usable (ie guide and sound), then I will spend time on the other stuff.

---

### Post by amphibem on 2008-05-20
OK hopefully someone will have an idea for me, but in the meantime here is some more info:

I suspect (hope!) that all/some of the crashes where caused by the digital channels adding themselves to the digital source. The only reason I can think for this is the option in tuner setup to get channels from the listing source. I did click that at one stage. Anyway something to investigate when I get the chance.

Part of mythbackend.log:

```
2008-05-20 13:57:46.924 AFD: Opened codec 0x8c9090, id(MPEG2VIDEO) type(Video)
2008-05-20 13:57:46.937 AFD: codec MP2 has 2 channels
2008-05-20 13:57:46.938 AFD: Opened codec 0x8ca4c0, id(MP2) type(Audio)
2008-05-20 13:57:47.038 Preview: Grabbed preview '/var/lib/mythtv/recordings/1000_20080520135738.mpg' 720x576@200s
2008-05-20 13:57:48.977 GetChannelData() failed because it could not
			find channel number 'NextChannel 0' in DB for source '1'.
2008-05-20 13:57:48.987 ChannelBase(1): IsTunable(Tuner 1,NextChannel 0) Failed to find channel in DB on input '1' 
2008-05-20 13:57:48.987 ChannelBase(1) Error: Setting start channel 'NextChannel 0' failed, 
			and we failed to find any suitible channels on any input.
2008-05-20 13:57:49.334 Finished recording Supernanny: channel 1001
2008-05-20 13:57:49.339 scheduler: Last message repeated 2 times: Finished recording: Days Of Our Lives: channel 1000
2008-05-20 13:57:49.345 scheduler: Finished recording: Supernanny: channel 1001
2008-05-20 13:57:50.375 Finished recording Supernanny: channel 1001
2008-05-20 13:57:50.455 TVRec(1): RingBufferChanged()
2008-05-20 13:57:50.466 Finished recording Supernanny: channel 1001

```

Equivalent mythfrontend.log:

```
2008-05-20 13:57:42.915 NVP: prebuffering pause
2008-05-20 13:57:42.982 WriteAudio: buffer underrun
2008-05-20 13:57:45.039 NVP: Prebuffer wait timed out 10 times.
2008-05-20 13:57:49.574 NVP: prebuffering pause
2008-05-20 13:57:51.642 NVP: Prebuffer wait timed out 10 times.
2008-05-20 13:57:53.939 TV: Attempting to change from WatchingLiveTV to None
2008-05-20 13:57:54.389 TV: Changing from WatchingLiveTV to None
2008-05-20 13:57:54.405 DPMS Reactivated.
2008-05-20 13:58:13.303 Received a remote 'Clear Cache' request

```

OK so if I am right, it has tried to tune to a channel that isn't on the input it wants?
Also, I am sure I didn't set it to record 'Supernanny' so I don't know whats happened there. It isn't in the recorded TV and at that stage my guide was screwed. I have a few of these throughout the time I was fiddling.

I cannot find any mention of failed audio, really lost on that. Any hints as to what to search for?

Edit:

If it helps, here is "dmesg | grep -i dvb"

```

[   23.189502] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   23.189591] dvb-usb: will pass the complete MPEG2 transport stream to the sof                                             tware demuxer.
[   23.190368] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   23.307413] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[   23.823848] dvb-usb: will pass the complete MPEG2 transport stream to the sof                                             tware demuxer.
[   23.824056] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   23.829844] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   24.392691] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized                                              and connected.
[   24.392836] usbcore: registered new interface driver dvb_usb_dib0700

```

---

### Post by KillerKiwi on 2008-05-20
The sound issue is a codec one in NZ dvb-t uses an acc codec that there is no version of for mythtv... yet

---

### Post by amphibem on 2008-05-20
Great! :( Any idea how it will be before that codec is added?

In the meantime I was planning a re-install this weekend, maybe I will try something else out for a while.

---

