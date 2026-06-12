---
title: "Problem with Hauppauge Nova 500"
date: 2014-03-12
forum: Mythbuntu
---

### Post by chipdaz on 2014-03-12
I've had a problem with my Hauppauge card for quite a while now and I'd like to know if others with the same card are having similar issues. Similarly if people *aren't* having issues please also reply as it might help me troubleshoot my setup.

The card is a Hauppauge Nova t 500 pci version, but I'd like to know if usb stick users have troubles because the pci card is the same as the usb device but with a usb adapter internally. My motherboard is a H61M/U3S3 and I'm using Mythtv 0.27 in case that matters.

Initially after a cold boot the Nova work fine, however after a few  hours mythtv is no longer able to record reliably from either of the cards  tuners and the entries contain gibberish mpg files from 0-120MB in size. Viewing them in vlc (mythtv fails to play them) they look like random rubbish. If I remove mythtv's lock on the cards then performing a channel  scan using dvbscan or scan also fails. OTOH my satellite tv card (a Tevii S650) continues to work flawlessly. Maybe if I tick "Wait for SEQ start header" in mythtv-setup the gibberish files won't appear at all and mythtv will correctly recognise a failed recording. I'll try that later.

I've set the tuning delay for the capture cards to 500ms and enabled active EIT scanning but to no avail. I also have the following in /etc/modprobe.d/options-dvb.conf:

options dvb_usb_dib0700 force_lna_activation=1 adapter_nr=5,6
options usbcore autosuspend=-1

The mythbackend.log file includes the following example:
Mar 10 08:57:00 darren-desktop mythbackend: mythbackend[1760]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange) TVRec[96]: Changing from None to RecordingOnly
Mar 10 08:57:00 darren-desktop mythbackend: mythbackend[1760]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[96]: HW Tuner: 96->96
Mar 10 08:57:11 darren-desktop mythbackend: mythbackend[1760]: N Scheduler autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 12.0 GB w/freq: 14 min
Mar 10 08:57:11 darren-desktop mythbackend: mythbackend[1760]: I Scheduler scheduler.cpp:2645 (HandleRecordingStatusChange) Tuning recording: "Highway To Heaven": channel 1061 on cardid 96, sourceid 1
Mar 10 09:04:41 darren-desktop mythbackend: mythbackend[1760]: I CoreContext scheduler.cpp:704 (UpdateRecStatus) Updating status for "Highway To Heaven" on cardid 96 (Tuning => Recording)
Mar 10 09:04:41 darren-desktop mythbackend: mythbackend[1760]: I TVRecEvent tv_rec.cpp:4126 (TuningNewRecorder) TVRec[96]: rec->GetPathname(): '/mnt/myth/mythtv-rec/1061_20140310085700.mpg'
Mar 10 09:04:54 darren-desktop mythbackend: mythbackend[1760]: E DVBRead mpeg/mpegstreamdata.cpp:365 (AssemblePSIP) MPEGStream[96](0x7fc630017838): Error: offset>181, pes length & current cannot be queried

I'll post a dmesg when the tuner next goes bad.

---

### Post by blm-ubunet on 2014-03-12
I've been using one of these tuners for > 6 years with mythtv.
This card has been rock solid..
Still on about kernel 2.6.35 with core2duo P45 chipset.

AFAICT you want to:
- use lna (you are)
- disable the IR remote polling (stop log spam)
- not use EIT scanning at all
- different timeout for each tuner (maybe)

I have played with EIT scanning on 1 tuner & that did not seem to cause trouble except removing most of the EPG..

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500)
options dvb_usb disable_rc_polling=1

You should have "Wait for SEQ start header" set. It should never have been an option.
SEQ start is a mpeg2video terminology (H264 starts on SPS).
It is not possible to start decoding the stream until SEQ or SPS are found/seen/obtained.
AFAIK Code changes in master (& 0.27+fixes) make this "setting" redundant.

Next time the cards go bad (after capturing dmesg) ..try to modprobe the driver
sudo modprobe dib07000

---

### Post by chipdaz on 2014-03-13
> **blm-ubunet said:**
> I've been using one of these tuners for > 6 years with mythtv.
This card has been rock solid..
Still on about kernel 2.6.35 with core2duo P45 chipset.

Thank you. I do suspect a kernel issue as in the past I've reinstalled old ubuntus but still used mythtv 0.27. The problem reappeared when I updated the old distro again.

> AFAICT you want to:
- use lna (you are)
- disable the IR remote polling (stop log spam)
- not use EIT scanning at all
- different timeout for each tuner (maybe)

I have played with EIT scanning on 1 tuner & that did not seem to cause trouble except removing most of the EPG..

I'll try these but I use the remote so I don't think stopping polling is an option

Righ now it seems to be a kernel issue to me. Is anyone else using the Nova T 500 either successfully or not with newer ubuntu/mythbuntus?

Or if you're using te 12.04 lts are you brave enough to try the lts-saucy kernel?

---

### Post by philip7 on 2014-03-13
I've also been using this tv tuner for a number of years and never had an issue, until I did a clean reinstall the other week.

The problems I had were different to yours, the tuners weren't available to mythtv so I couldn't use them.

But I updated the kernel to the latest version and the problem was resolved, I had followed all the instructions on the wiki but don't think they really made a difference.

---

### Post by itlarson2 on 2014-03-13
This is a long shot, but could the tuner just be getting too hot?  I thought of this just because you mention it works fine at first.  All the tuner issues i've had latley have been hardware problems with tuners next to the video card- although in both cases they just flat-out died.

---

### Post by chipdaz on 2014-03-22
Doubtful as going back to the 12.04 lts, as a temporary measure, and using the quantal kernel (3.5.0) seems to have solved the issue. Also I'm using a low powered graphics card. I'm going on holiday next week but might experiment when I get back.

---

