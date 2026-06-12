---
title: "Streaming DVB-T via VLC on Headless Server"
date: 2012-02-12
forum: Multimedia Software
---

### Post by sgrabowski on 2012-02-12
I'm trying to create a homebrew Slingbox-esq setup for distributing live TV around my home network.

I've got a Ubuntu Server 10.04 (headless) setup on an old Shuttle AMD system and a working Nebula DigiTV DVB-T PCI card [bt878] installed.

I came across [this post](http://forum.videolan.org/viewtopic.php?f=13&t=97607#p325484) which seemed to do precisely what I was after. Unfortunately, even after a lot of digging I was coming to the limits of my cli skills.

Here's what I have tried:
```
cvlc --open=~/channels.conf --http-src=/usr/share/vlc/http -vvv dvb:// :dvb-adapter=0 --sout '#standard{access=htp,mus=ogg,dst=192.168.1.65:8181}'
```

I tried to follow the sets as closely as possible from the post linked above. I already have a correct channels.conf file.

Any help on what I have done wrong would be much appreciated.

---

### Post by ron999 on 2012-02-12
> **sgrabowski said:**
> '#standard{access=htp,mu[COLOR="Red"][COLOR="Red"]s[/COLOR][/COLOR]=ogg,dst=192.168.1.65:8181}'[/code]


Any help on what I have done wrong would be much appreciated.

Hi
Typo mu[COLOR="Red"]x[/COLOR], not mus.

---

### Post by sgrabowski on 2012-02-12
Fixing the typo still doesn't work.

I tried to take out the "--sout '#standard{access=htp,mus=ogg,dst=192.168.1.65:8181}'" section of the command and churned its way through the channels that got stuck working through the EPG data. This is definately going in the right direction, just need that push over the hill ;)

---

### Post by sgrabowski on 2012-02-14
Right,

I have carried on digging and found this command in this thread:

```
vlc -vvv ~/channels.conf --sout '#transcode{vcodec=DIV3,vb=2048,scale=0.25,acodec=mp3,ab=32,channels=2}:std{access=mmsh,mux=asfh,dst=:8080}'
```

And here is the output from the session:

```
[0xca1668] main mux debug: looking for sout mux module: 1 candidate
[0xca1668] mux_asf mux debug: asf muxer opened
[0xca1668] mux_asf mux debug: creating asf stream to be used with mmsh
[0xca1668] mux_asf mux debug: Packet size 4096
[0xca1668] mux_asf mux debug: meta data: title='', author='', copyright='', comment='', rating=''
[0xca1668] main mux debug: using sout mux module "mux_asf"
[0xca1668] main mux debug: TIMER module_need() : 0.812 ms - Total 0.812 ms / 1 intvls (Avg 0.812 ms)
[0xcaf758] main stream output debug: muxer support adding stream at any time
[0xcaf758] main stream output debug: muxer prefers to wait for all ES before starting to mux
[0xcae9a8] stream_out_standard stream out debug: mux opened
[0xcae9a8] main stream out debug: using sout stream module "stream_out_standard"
[0xcae9a8] main stream out debug: TIMER module_need() : 5.074 ms - Total 5.074 ms / 1 intvls (Avg 5.074 ms)
[0xcaa1b8] main stream out debug: set config option: sout-transcode-vcodec to DIV3
[0xcaa1b8] main stream out debug: set config option: sout-transcode-vb to 2048
[0xcaa1b8] main stream out debug: set config option: sout-transcode-scale to 0.25
[0xcaa1b8] main stream out debug: set config option: sout-transcode-acodec to mp3
[0xcaa1b8] main stream out debug: set config option: sout-transcode-ab to 32
[0xcaa1b8] main stream out debug: set config option: sout-transcode-channels to 2
[0xcaa1b8] stream_out_transcode stream out debug: codec audio=mp3  0Hz 2 channels 32Kb/s
[0xcaa1b8] stream_out_transcode stream out debug: codec video=DIV3 0x0 scaling: 0.250000 2048kb/s
[0xcaa1b8] main stream out debug: using sout stream module "stream_out_transcode"
[0xcaa1b8] main stream out debug: TIMER module_need() : 9.867 ms - Total 9.867 ms / 1 intvls (Avg 9.867 ms)
[0xc9daf8] main input debug: using timeshift granularity of 50 MBytes
[0xc9daf8] main input debug: using timeshift path '/tmp'
[0xc9daf8] main input debug: `dvb://' gives access `dvb' demux `' path `'
[0xc9daf8] main input debug: creating demux: access='dvb' demux='' path=''
[0xca1b08] main demux debug: looking for access_demux module: 0 candidates
[0xca1b08] main demux debug: no access_demux module matched "dvb"
[0xca1b08] main demux debug: TIMER module_need() : 0.106 ms - Total 0.106 ms / 1 intvls (Avg 0.106 ms)
[0xc9daf8] main input debug: creating access 'dvb' path=''
[0x1178b08] main access debug: looking for access module: 1 candidate
[0x1178b08] dvb access debug: Opening device /dev/dvb/adapter0/frontend0
[0x1178b08] dvb access debug: Frontend Info:
[0x1178b08] dvb access debug:   name = Zarlink MT352 DVB-T
[0x1178b08] dvb access debug:   type = OFDM (DVB-T)
[0x1178b08] dvb access debug:   frequency_min = 174000000 (kHz)
[0x1178b08] dvb access debug:   frequency_max = 862000000 (kHz)
[0x1178b08] dvb access debug:   frequency_stepsize = 166667
[0x1178b08] dvb access debug:   frequency_tolerance = 0
[0x1178b08] dvb access debug:   symbol_rate_min = 0 (kHz)
[0x1178b08] dvb access debug:   symbol_rate_max = 0 (kHz)
[0x1178b08] dvb access debug:   symbol_rate_tolerance (ppm) = 0
[0x1178b08] dvb access debug:   notifier_delay (ms) = 0
[0x1178b08] dvb access debug: Frontend Info capability list:
[0x1178b08] dvb access debug:   inversion auto
[0x1178b08] dvb access debug:   forward error correction 1/2
[0x1178b08] dvb access debug:   forward error correction 2/3
[0x1178b08] dvb access debug:   forward error correction 3/4
[0x1178b08] dvb access debug:   forward error correction 5/6
[0x1178b08] dvb access debug:   forward error correction 7/8
[0x1178b08] dvb access debug:   forward error correction auto
[0x1178b08] dvb access debug:   card can do QPSK
[0x1178b08] dvb access debug:   card can do QAM 16
[0x1178b08] dvb access debug:   card can do QAM 64
[0x1178b08] dvb access debug:   card can do QAM auto
[0x1178b08] dvb access debug:   transmission mode auto
[0x1178b08] dvb access debug:   guard interval mode auto
[0x1178b08] dvb access debug:   hierarchy mode auto
[0x1178b08] dvb access debug:   card can mute TS
[0x1178b08] dvb access debug:   card can recover from a cable unplug
[0x1178b08] dvb access debug: End of capability list
[0x1178b08] dvb access debug: trying to tune the frontend...
[0x1178b08] dvb access debug: using inversion=2
[0x1178b08] dvb access debug: using bandwidth=8
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using transmission=2
[0x1178b08] dvb access debug: using guard=32
[0x1178b08] dvb access debug: using hierarchy=-1
[0x1178b08] dvb access debug: Opening device /dev/dvb/adapter0/dvr0
[0x1178b08] dvb access debug: setting filter on PAT
[0x1178b08] dvb access debug: Opening device /dev/dvb/adapter0/demux0
[0x1178b08] dvb access debug: DMXSetFilter: DMX_PES_OTHER for PID 0
[0x1178b08] dvb access debug: Opening device /dev/dvb/adapter0/ca0
[0x1178b08] dvb access warning: CAMInit: opening CAM device failed (No such file or directory)
[0x1178b08] main access debug: using access module "dvb"
[0x1178b08] main access debug: TIMER module_need() : 3.846 ms - Total 3.846 ms / 1 intvls (Avg 3.846 ms)
[0x117a778] main stream debug: Using AStream*Block
[0x117a778] main stream debug: pre buffering
[0x1178b08] dvb access warning: no lock, tuning again
[0x1178b08] dvb access debug: using inversion=2
[0x1178b08] dvb access debug: using bandwidth=8
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using transmission=2
[0x1178b08] dvb access debug: using guard=32
[0x1178b08] dvb access debug: using hierarchy=-1
[0x1178b08] dvb access warning: no lock, tuning again
[0x1178b08] dvb access debug: using inversion=2
[0x1178b08] dvb access debug: using bandwidth=8
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using transmission=2
[0x1178b08] dvb access debug: using guard=32
[0x1178b08] dvb access debug: using hierarchy=-1
[0x1178b08] dvb access warning: no lock, tuning again
[0x1178b08] dvb access debug: using inversion=2
[0x1178b08] dvb access debug: using bandwidth=8
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using transmission=2
[0x1178b08] dvb access debug: using guard=32
[0x1178b08] dvb access debug: using hierarchy=-1
[0x1178b08] dvb access warning: no lock, tuning again
[0x1178b08] dvb access debug: using inversion=2
[0x1178b08] dvb access debug: using bandwidth=8
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using transmission=2
[0x1178b08] dvb access debug: using guard=32
[0x1178b08] dvb access debug: using hierarchy=-1
[0x1178b08] dvb access warning: no lock, tuning again
[0x1178b08] dvb access debug: using inversion=2
[0x1178b08] dvb access debug: using bandwidth=8
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using transmission=2
[0x1178b08] dvb access debug: using guard=32
[0x1178b08] dvb access debug: using hierarchy=-1
[0x1178b08] dvb access warning: no lock, tuning again
[0x1178b08] dvb access debug: using inversion=2
[0x1178b08] dvb access debug: using bandwidth=8
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using transmission=2
[0x1178b08] dvb access debug: using guard=32
[0x1178b08] dvb access debug: using hierarchy=-1
[0x1178b08] dvb access warning: no lock, tuning again
[0x1178b08] dvb access debug: using inversion=2
[0x1178b08] dvb access debug: using bandwidth=8
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using transmission=2
[0x1178b08] dvb access debug: using guard=32
[0x1178b08] dvb access debug: using hierarchy=-1
[0x1178b08] dvb access warning: no lock, tuning again
[0x1178b08] dvb access debug: using inversion=2
[0x1178b08] dvb access debug: using bandwidth=8
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using transmission=2
[0x1178b08] dvb access debug: using guard=32
[0x1178b08] dvb access debug: using hierarchy=-1
[0x1178b08] dvb access warning: no lock, tuning again
[0x1178b08] dvb access debug: using inversion=2
[0x1178b08] dvb access debug: using bandwidth=8
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using fec=9
[0x1178b08] dvb access debug: using transmission=2
[0x1178b08] dvb access debug: using guard=32
[0x1178b08] dvb access debug: using hierarchy=-1
^C[0xc7f6e8] signals interface error: Caught Interrupt signal, exiting...
[0xb85888] main libvlc debug: deactivating the playlist
[0xc84cf8] main playlist debug: Deactivate
[0xc84cf8] main playlist debug: incoming request - stopping current input
[0xc84cf8] main playlist debug: dying input
[0x117a778] main stream debug: prebuffering done 0 bytes in 99s - 0 kbytes/s
[0x117a778] main stream error: cannot pre fill buffer
[0xc9daf8] main input warning: cannot create a stream_t from access
[0x1178b08] dvb access debug: DMXUnsetFilter: closing demux 9
[0x1178b08] main access debug: removing module "dvb"
[0xc9daf8] main input debug: thread ended
[0xc84cf8] main playlist debug: dead input
[0xcaf758] main stream output debug: destroying useless sout
[0xcaa1b8] main stream out debug: destroying chain... (name=transcode)
[0xcae9a8] main stream out debug: destroying chain... (name=std)
[0xca1668] mux_asf mux debug: Asf muxer closed
[0x11795e8] access_output_http access out warning: HTTP sout access cannot seek
[0xca1668] main mux debug: removing module "mux_asf"
[0xca1de8] main http server debug: waitpipe: object killed
[0xca1de8] main http server debug: HTTP host removed
[0xcac008] main http server debug: no hosts left, stopping httpd
[0x11795e8] access_output_http access out debug: Close
[0x11795e8] main access out debug: removing module "access_output_http"
[0xcae9a8] main stream out debug: removing module "stream_out_standard"
[0xcae9a8] main stream out debug: destroying chain done
[0xcaa1b8] main stream out debug: removing module "stream_out_transcode"
[0xcaa1b8] main stream out debug: destroying chain done
[0xc9daf8] main input debug: TIMER input launching for 'BBC ONE' : 99118.117 ms - Total 99118.117 ms / 1 intvls (Avg 99118.109 ms)
[0xc84cf8] main playlist debug: saving Media Library to file /home/stefan/.local/share/vlc/ml.xspf
[0xc84cf8] main playlist debug: looking for playlist export module: 1 candidate
[0xc84cf8] main playlist debug: using playlist export module "export"
[0xc84cf8] main playlist debug: TIMER module_need() : 0.761 ms - Total 0.761 ms / 1 intvls (Avg 0.761 ms)
[0xc84cf8] main playlist debug: removing module "export"
[0xc84cf8] main playlist debug: Deactivated
[0xb85888] main libvlc debug: removing all services discovery tasks
[0xb85888] main libvlc debug: removing all interfaces
[0xc80538] main interface debug: removing module "dummy"
[0xc7f6e8] main interface debug: removing module "signals"
[0xc841d8] main interface debug: removing module "screensaver"
[0xc9b918] main interface debug: removing module "hotkeys"
[0xb85888] main libvlc debug: removing playlist
[0xc84cf8] main playlist debug: Destroyed
[0xb85888] main libvlc debug: TIMER ML Load : Total 18.653 ms / 1 intvls (Avg 18.653 ms)
[0xb85888] main libvlc debug: TIMER Items array build : Total 0.138 ms / 3 intvls (Avg 0.046 ms)
[0xb85888] main libvlc debug: TIMER ML Dump : Total 1.270 ms / 1 intvls (Avg 1.270 ms)
[0xb85888] main libvlc debug: removing stats
[0xb85888] main libvlc debug: removing module "memcpymmxext"
[0xb85888] main libvlc debug: opening config file (/home/stefan/.config/vlc/vlcrc)
[0xb85888] main libvlc debug: writing plugins cache /home/stefan/.cache/vlc/plugins-04081e.dat

```

I had to interrupt the process as it just hung there seemingly not making any progress.

---

