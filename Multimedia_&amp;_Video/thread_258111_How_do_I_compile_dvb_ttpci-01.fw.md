---
title: "How do I compile dvb_ttpci-01.fw?"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by wwuster on 2006-09-15
I'm running Ubuntu 6.06 LTS and trying to get a nexus-s dvb-s card running
in NTSC mode.

Here's what I've done so far:

1. wget [http://www.linuxtv.org/download/dvb/firmware/dvb-ttpci-01.fw-2622](http://www.linuxtv.org/download/dvb/firmware/dvb-ttpci-01.fw-2622)
2. copied dvb-ttpci-01.fw-2622 to /lib/firmware/2.6.15-26-386/dvb-ttpci-01.fw
3. rmmod dvb_ttpci
4. modprobe dvb_ttpci
5. ls /dev/dvb/'. This showed /dev/dvb/adapter0
6. I downloaded Thoraz's DVB stuff: 
	wget [http://www.phobos.ca/dvb/files/linuxtv-dvb-apps-na-1.1.2.tar.bz2](http://www.phobos.ca/dvb/files/linuxtv-dvb-apps-na-1.1.2.tar.bz2)
7. tar xfj linuxtv-dvb-apps-na-1.1.2.tar.bz2
8. cd linuxtv-dvb-apps-na-1.1.2/util/scan
	
9.Scan echostar 119W on diseqc port 1:
./dvbscan -G -lDBS -o vdr -e 3 -s 1 -x 0 -p dvb-s/echostar-119w > channels.conf

10. copied channels.conf to $HOME/.szap/channels.conf

11. szap -l DBS -x angel
        I got a lock (FE_HAS_LOCK)
	But I'm still in pal mode.

			
What is the easiest way to get NTSC working? I've heard that you can just
rebuild dvb-ttpci-01.fw using newer source code and can pass a parameter to
it telling it to go into NTSC mode but I can't find instructions on how to do this. I'm trying to avoid having to rebuild the kernel.

thanks,
William

---

