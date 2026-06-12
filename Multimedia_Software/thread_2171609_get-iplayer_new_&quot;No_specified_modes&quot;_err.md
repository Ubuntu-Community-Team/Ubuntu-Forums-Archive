---
title: "get-iplayer new &quot;No specified modes&quot; error. Diff versions &amp; modes &amp; debug don't help."
date: 2013-08-31
forum: Multimedia Software
---

### Post by chris94 on 2013-08-31
I've had no problems for years, now suddenly get-iplayer reports "No specified modes (flashhigh,flashstd,flashnormal) available for this programme with version 'default'" for my radio show.

The stream works, it is not UK only (and anyway I have checked the debug output for this error), I have tried all the modes ( iphone, flashhd, flashvhigh, flashhigh, flashstd, flashnormal, flashlow, n95_wifi, flashaac, flashaachigh, flashaacstd, flashaaclow, flashaudio, realaudio, wma) and versions (signed, audiodescribed, default), but it cannot find the stream whatever I try.

Oddly, at the top of the debug output it does claim to find three streams - version default, services iplayer_intl_stream_wma_lo_concrete, iplayer_intl_stream_aac_rtmp_concrete and iplayer_intl_stream_wma_lo_concrete, but when it tries to download the stream it cannot find any modes.

I've tried using flvstreamer but to no avail, with: get_iplayer --get --pid=b039hlzb --flvstreamer=/usr/bin/flvstreamer

(This pid will be valid for one week.)

Any ideas? I've attached the debug output as a zipped text file to this post. Huge thanks.

---

### Post by carl4926 on 2013-08-31
[https://github.com/dinkypumpkin/get_iplayer/wiki](https://github.com/dinkypumpkin/get_iplayer/wiki)

---

### Post by ajgreeny on 2013-08-31
I don't think the repo version works any more so I believe you have to use the get_iPlayer version from the ppa nowadays for it to work at all.  Do a quick search for the ppa for your Ubuntu and you may find it works again.

---

### Post by chris94 on 2013-09-01
I reinstalled from Jon Hedgerow's repo (instructions here  [https://github.com/dinkypumpkin/get_iplayer/wiki/ubuntu](https://github.com/dinkypumpkin/get_iplayer/wiki/ubuntu) - from Carl's  link).

My problem is now solved, thanks. There were a few extra steps I don't  need to understand but would love any enlightenment on, and include for  any other newbies out there.

I think my RTMPdump install was also broken somehow - in the output to my first attempt after installing the PPA version I got:

...
INFO: File name prefix = Gilles_Peterson_-_Mount_Kimbie_in_session_b039hlzb_default
RTMPDump v2.4-n78-git3a1e20c-ppa8~precise
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
**ERROR: RTMP_Connect0, failed to connect socket. 111 (Connection refused)**
INFO: Command exit code 3 (raw code = 768)
WARNING: Failed to stream file /home/ubuntu/Gilles_Peterson_-_Mount_Kimbie_in_session_b039hlzb_default.partial.m4a.flv via RTMP
INFO: skipping flashaaclow1 mode
[B]INFO: Trying wma1 mode to record radio: Gilles Peterson - Mount Kimbie in session

WARNING: Required mplayer does not exist
[/B]INFO: skipping wma1 mode
ERROR: Failed to record 'Gilles Peterson - Mount Kimbie in session (b039hlzb)'

I got something similar with other RTMP streams. Running "get-iplayer  --info ..." revealed a wma stream, so I installed mplayer, specified  --mode-wma1, and was able to get the show. (Although wma takes 3 hours  as it records at live rate, whereas RTMPDump takes a few seconds.)

I wanted RTMPdump back though. I checked and my RTMPDump was the latest  version. I ran apt-get upgrade etc. It wouldn't work until I restarted  the server. On restarting the server, get-iplayer could get the flash  version again. (And thanks to the PPA install now uses avconv to  convert.)

RTMPdump and get-iplayer problems started around the same time, so the  original problem might have been related to RTMPdump needing a server  restart. Although I can see that RTMPdump is no longer using outdated  libraries but avconv, which seems more capable, and I'm now getting  sensible error messages, so the PPA upgrade was necessary. Huge thanks  to you both.

---

### Post by dinkypumpkin on 2013-09-04
What extra steps do you need enlightenment on?  It appears you have done everything necessary for the PPA install.

Your initial post (and the attached log) indicate a few things:

1) You were trying to download a radio programme without either --type=radio or --modes=flashaaclow.  That will fail in the latest version as well, though it appears from your later post you've corrected that.  Without seeing your preferences or other permutations, it's impossible to say whether more was going on.  As a rule, use --type=radio when downloading radio programmes.

2) That particular problem was unrelated to rtmdump.  The log shows you didn't get that far in the download process.

3) It's harmless, but you don't need --get with --pid

But that's rather academic.  You were well-advised to upgrade from the PPA since 2.80 is obsolete for radio downloads and completely broken for TV downloads.

If you encounter that "connection refused" error from rtmpdump again, try first deleting the ~/.swfinfo file (used for SWF verification) so that rtmpdump will be forced to regenerate it.  There have been a couple of reports in the past that this was a solution (and it worked once for me).  However, I couldn't reproduce that behaviour with current 12.04 repo and PPA builds.  Still worth a punt before restarting a server.

---

