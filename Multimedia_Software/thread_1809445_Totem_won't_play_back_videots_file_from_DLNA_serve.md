---
title: "Totem won't play back video/ts file from DLNA server"
date: 2011-07-21
forum: Multimedia Software
---

### Post by andy.stevens on 2011-07-21
Hi,

I'm having trouble playing back videos from a DLNA device in Ubuntu 11.04, and I'm not sure where the problem lies.

Using the software manager I've installed the extra plugins package for Totem, and enabled the Coherence DLNA/UPNP plugin.  I can see the device (Humax Freeview HD recorder) in the MediaServers list, and can browse through the programmes I've recorded on it.  However, trying to play any of the has no effect, the main part of the window still shows the "clapperboard" graphic.

I noticed that the "recent files" filenames that were appearing on the Movie menu didn't match the ones that were listed in the sidebar - they're of the form e.g. 313.TS rather than the original descriptive name with a .ts extension.  Running Totem from a shell prompt, I can see the following console output:
request to play: Man on Earth_20110622_0508.ts 0\1\3\311\314 http://192.168.254.1:9000/web/media/313.TS
I tried entering that URL into Firefox, and it started downloading okay; according to the LiveHTTPHeaders addon the response headers are
HTTP/1.1 200 OK 
Transfer-Encoding: chunked 
Server: HUMAX / MicroMediaServer 
Accept-Range: bytes 
Content-Type: video/ts 
Content-Length: 1799258112 
Pragma: no-cache 
Cache-Control: no-cache 

Why can't Totem play the file?  Some other codec needed for video/ts files that I've not got installed? (it hasn't prompted me to install any extra packages)  Does it just not like the fact the file extension is upper case?  Or something else entirely?

On a separate machine, also running Ubuntu 11.04, I installed the VideoLan client; VLC can browse to the files and play them without any problem.  So why can't Totem?


Andy

---

### Post by spych102 on 2011-08-06
I have a Humax PVR as well and had the same problem with Totem. VLC does open and play the .ts files albeit with an audio sync issue.

The next step I took was to transfer the files to a usb drive. I found that the .ts files still wouldn't open locally with Totem, reporting no error just as with your experience. I renamed the file extension to .mpg and all of a sudden the files open and play. Totem does a strange thing where it asks me to install extra codecs but then reports that it can't find them. It seems to be able to play the file back perfectly well without the extra codecs.

I also tried opening the .ts files with Avidemux, another gstreamer  based program and I had precisely the same experience, the .ts extension didn't work but an .mpg extension did and it asked me to install codecs that it couldn't find and doesn't need for reading the file back.

It's definitely something to do with the .ts extension and it only seems to affect gstreamer based media programs.

---

### Post by Blingin2Mingin on 2011-11-06
Same problem here, I installed xbmc to play back the ts files from the Humax dlna server. Nice media centre that it is, having to use xbmc to playback ts files is overkill.

---

### Post by BicyclerBoy on 2011-11-06
Using 11.04, Totem/coherence works with MythTV DLNA server (mpeg2-ts).
But the files are named with suffix mpg..
Does sound like the wrong demuxer is used because of the file extension.
MythTV (& XBMC) play .ts files without problem possibly because they are ffmpeg based.

The DLNA client coherence does not work in 11.10 Totem.

But the 11.04 Totem plugins, gstreamer, does not yet support LATM AAC which has been common place in broadcast/OTA/dvb mpeg4/10 (H264AVC).
This support has recently been added to the latest packages (not in 11.04).

Do you have installed the gstreamer packages:
- base
- good
- bad
- bad-multiverse (prob not necessary)
- bad
- ugly-multiverse (prob not necessary)
- ffmpeg
gnome-codec-install

---

