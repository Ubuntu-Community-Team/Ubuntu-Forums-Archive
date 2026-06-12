---
title: "How to download streaming from MIT World"
date: 2009-04-21
forum: Multimedia Software
---

### Post by bellani on 2009-04-21
Hello there. 

I'm looking for a script to download videos from mitworld.
Usually I was using this algorithm
access this url:
[http://cp58255.edgefcs.net/fcs/ident](http://cp58255.edgefcs.net/fcs/ident)
will produce a IP
this IP I would use to replace the xs in the following rtmpdump command ([http://rtmpdump.sourceforge.net/](http://rtmpdump.sourceforge.net/))

./rtmpdump --host "x.x.x.x" --port 1935 --protocol rtmp --playpath "mitworldflash/name-of-the-video --swfUrl "http://mitworld.mit.edu/flash/player/Main.swf?host=cp58255.edgefcs.net&flv=name-of-video" --tcUrl "rtmp://x.x.x.x:1935/ondemand?_fcs_vhost=cp58255.edgefcs.net" --pageUrl="http://mitworld.mit.edu/video/url" --app "ondemand?_fcs_vhost=cp58255.edgefcs.net" --flashVer "LNX 9,0,124,0" --flv "name_of_stream.flv"

This script don't work anymore, likely because they change the playpath.
Does anyone know how to fix it?

---

### Post by miguelsvieira on 2010-02-15
You might wanna try [get-flash-videos]("https://code.google.com/p/get-flash-videos/"). The stable release 1.20 did not work with mitworld, but starting from [rev. 330]("https://code.google.com/p/get-flash-videos/source/detail?r=330") it does.

It took me quite an effort to get it to work (compiling, and it requires either flvstreamer or rtmpdump -- which for some reason I couldn't apt-get to Ubuntu; had to download a pre-compiled binary at [http://savannah.nongnu.org/projects/flvstreamer](http://savannah.nongnu.org/projects/flvstreamer) and copy/chmod it to usr/bin), and I'm still testing it, but apparently it does the job.

---

### Post by puppetslave on 2010-02-18
Hi,

you can try this -

flvstreamer -o outputfile -r [FONT=monospace]"[/FONT]rtmp://<HOST>/ondemand/ampsflash/<FLV_NAME>?_fcs_vhost=<HOST>"

Substitute <HOST> and <FLV_NAME> with the corresponding values for "host:" and "flv:" from the page source. E.g. -
flvstreamer -o Turing.flv -r "rtmp://cp58255.edgefcs.net/ondemand/ampsflash/mitw-00813-csail-creativity-pt2-copeland-turing-30nov2006?_fcs_vhost=cp58255.edgefcs.net"

Works for me with FLVStreamer v1.8e.

i figured out from the source code of the perl module, Mitworld.pm [https://code.google.com/p/get-flash-videos/source/browse/trunk/FlashVideo/Site/Mitworld.pm?spec=svn330&r=330](https://code.google.com/p/get-flash-videos/source/browse/trunk/FlashVideo/Site/Mitworld.pm?spec=svn330&r=330)
, that you mentioned.

i wonder why they do not provide direct download for videos released to public?

---

