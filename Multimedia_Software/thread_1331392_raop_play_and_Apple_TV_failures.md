---
title: "raop_play and Apple TV failures"
date: 2009-11-19
forum: Multimedia Software
---

### Post by TheGreyGhost on 2009-11-19
Hello!

I have an Apple TV that I would like to use as an Airtunes output device.  We have successfully used it through my wife's Mac and now I dug in to try and get it working on my laptop running Karmic.

I managed to compile the software after some adjustments.  Compilation failed on two occasions (const conversion solved with a cast and data type mismatches in the substitute glib module) but I fixed those with help from others online.

First up, I tried to run aexcl_play and used the GUI to select a track.  Here's the terminal output of that attempt:

```
$ aexcl_play
DBG: mdns_event
DBG: mdns_update:192.168.1.28-Apple TV
DBG: selected num = 1
DBG: selected item = Englishtheme.mp3
ERR: error:get_tcp_nconnect addr=192.168.1.28, port=5000
DBG: received SIGCHLD, pid=20628
DBG: main end

```My assumption is the port isn't listening, so I portscan the device with nmap:

```
$ nmap 192.168.1.28

Starting Nmap 5.00 ( http://nmap.org ) at 2009-11-19 08:58 EST
Interesting ports on AppleTV.westell.com (192.168.1.28):
Not shown: 612 closed ports, 386 filtered ports
PORT      STATE SERVICE
3689/tcp  open  rendezvous
49155/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 2.66 seconds

```Using that information, I go to the raop_play command and enter the following:

```
$ raop_play --port 49155 192.168.1.28 ~/Music/Englishtheme.mp3
DBG: Server: AirTunes/102.2
DBG: CSeq: 1
DBG: Transport: RTP/AVP/TCP;unicast;mode=record;server_port=49333
DBG: Session: 1
DBG: Audio-Jack-Status: connected
DBG: Server: AirTunes/102.2
DBG: CSeq: 2
DBG: Audio-Latency: 322
DBG: Server: AirTunes/102.2
DBG: CSeq: 3
DBG: Server: AirTunes/102.2
DBG: CSeq: 4
connected
DBG: id3 tagsize: 0
DBG: sample rate=22050
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layer 1, 2, and 3.
Version 0.59q (2002/03/23). Written and copyrights by Joe Drew.
Uses code from various people. See 'README' for more!
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!

Directory: /home/carl/Music/
Playing MPEG stream from Englishtheme.mp3 ...
MPEG 1.0 layer III, 32 kbit/s, 22050 Hz mono

[1:42] Decoding of Englishtheme.mp3 finished.
done
INFO: fd_event_callback: read, disconnected on the other end

```No response from the AppleTV.  Yes, my receiver is on and the volume is turned up :)  Additionally I tried installing PulseAudio with its Raop module but no luck there either.  

Any ideas?  I don't quite know what to make of the situation at this point.

-- Carl

---

