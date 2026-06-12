---
title: "Tv Card ++"
date: 2008-05-05
forum: Multimedia Software
---

### Post by OpenFish on 2008-05-05
i have a tv card wich used to be in a very old box with a brocken win98OS and a 15" monitor but happaly ran knoppix but the tv program left huge amounts of black on the screen around the picture and the vlc on it wouldnt play off the card

having a pc in the same room with a 22" monitor i though it would be sencably to use that in stead of the 15" with a huge black boarder 
we also have sitting room with the famly pc but no tv as there is no ariel cable (a must, portable arials dont work in ramsey)
and having a very under used file sever siting next to my main pc i thought would be good to get a dual tune and put it in the file server so both pc could use the one card

i setup a prouf of conseped test and with the help of vlc my 22" monitor is full of colorfully tv with no boarder at all perfect! i am now going to get a new tuner card when i have sorted the cash

but when i plugged my PS2 in to the composite the picture is several second behind the action this is not helped by my converting it to mp4v but without this the culor is v blue (the tv card is very old) 
the top command gives 1.6% mem and 10% cup witch due to tops unic way of meashering dual prosesors is atualy 5%

the PS2 is a very important tool for bribing my little bro and i dont want to have to have my main pc on all the time as the 8600 nvidi card and AMD 6000+ eats power (not as good as when it was new but still fare beter than most of my frends and u should see there faces when beryl comes on lol)

in sort how do i get the time delay to a negligible/unnoticeable point ??
any idears??


brws@brws:~$  vlc -vvv v4l:/dev/video0:norm=pal:size=720×480:channel=1 -I dummy --sout '#transcode{vcodec=mp4v,acodec=mpga,vb=800,ab=128,deinterlace}:std{access=mmsh,dst=:9090}'
VLC media player 0.8.6a Janus
[00000001] main private debug: checking builtin modules
[00000001] main private debug: checking plugin modules
[00000001] main private debug: loading plugins cache file /home/brws/.vlc/cache/plugins-04081e.dat
[00000001] main private debug: recursively browsing `modules'
[00000001] main private debug: recursively browsing `/usr/lib/vlc'
[00000001] main private debug: recursively browsing `plugins'
[00000001] main private debug: module bank initialized, found 221 modules
[00000001] main private debug: opening config file /home/brws/.vlc/vlcrc
[00000001] main private warning: config file /home/brws/.vlc/vlcrc does not exist yet
[00000001] main private debug: CPU has capabilities 486 586 MMX 3DNow! MMXEXT SSE SSE2 FPU
[00000001] main private debug: looking for memcpy module: 4 candidates
[00000001] main private debug: using memcpy module "memcpymmxext"
[00000285] main playlist debug: waiting for thread completion
[00000285] main playlist debug: thread 1082132832 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000286] main private debug: waiting for thread completion
[00000286] main private debug: thread 1090525536 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000287] main interface debug: looking for interface module: 1 candidate
[00000287] main interface debug: using interface module "hotkeys"
[00000287] main interface debug: thread 1098918240 (interface) created at priority 0 (interface/interface.c:231)
[00000289] main interface debug: looking for interface module: 1 candidate
[00000289] main interface debug: using interface module "screensaver"
[00000289] main interface debug: thread 1107310944 (interface) created at priority 0 (interface/interface.c:231)
[00000285] main playlist debug: adding playlist item `v4l:/dev/video0:norm=pal:size=720×480:channel=1' ( v4l:/dev/video0:norm=pal:size=720×480:channel=1 )
[00000291] main interface debug: looking for interface module: 6 candidates
[00000291] dummy interface: using the dummy interface module...
[00000291] main interface debug: using interface module "dummy"
[00000291] main interface debug: thread 1115703648 (manager) created at priority 0 (interface/interface.c:216)
[00000285] main playlist debug: creating new input thread
[00000300] main input debug: waiting for thread completion
[00000300] main input debug: creating statistics handler
[00000302] main stream output debug: stream=`transcode'
[00000303] main private debug: looking for sout stream module: 1 candidate
[00000302] main stream output debug: stream=`std'
[00000306] main private debug: looking for sout stream module: 1 candidate
[00000306] main private debug: set sout option: sout-standard-access to mmsh
[00000306] main private debug: set sout option: sout-standard-dst to :9090
[00000306] stream_out_standard private debug: creating `mmsh/(null)://:9090'
[00000306] stream_out_standard private debug: using `mmsh/asfh://:9090'
[00000308] main private debug: looking for sout access module: 1 candidate
[00000300] main input debug: thread 1124096352 (input) created at priority 0 (input/input.c:266)
[00000308] main private: creating httpd
[00000308] main private debug: net: listening to  port 9090
[00000311] main http server debug: thread 1132489056 (httpd host thread) created at priority 0 (network/httpd.c:1078)
[00000308] main private debug: using sout access module "access_output_http"
[00000306] stream_out_standard private debug: access opened
[00000312] main private debug: looking for sout mux module: 1 candidate
[00000312] mux_asf private debug: asf muxer opened
[00000312] mux_asf private debug: creating asf stream to be used with mmsh
[00000312] mux_asf private debug: Packet size 4096
[00000312] mux_asf private debug: meta data: title='', author='', copyright='', comment='', rating=''
[00000312] main private debug: using sout mux module "mux_asf"
[00000302] main stream output debug: muxer support adding stream at any time
[00000302] main stream output debug: muxer prefers to wait for all ES before starting to mux
[00000306] stream_out_standard private debug: mux opened
[00000306] main private debug: using sout stream module "stream_out_standard"
[00000303] main private debug: set sout option: sout-transcode-vcodec to mp4v
[00000303] main private debug: set sout option: sout-transcode-acodec to mpga
[00000303] main private debug: set sout option: sout-transcode-vb to 800
[00000303] main private debug: set sout option: sout-transcode-ab to 128
[00000303] main private debug: set sout option: sout-transcode-deinterlace to (null)
[00000303] stream_out_transcode private debug: codec audio=mpga 0Hz 0 channels 128Kb/s
[00000303] stream_out_transcode private debug: codec video=mp4v 0x0 scaling: 1.000000 800kb/s
[00000303] main private debug: using sout stream module "stream_out_transcode"
[00000300] main input debug: `v4l:/dev/video0:norm=pal:size=720×480:channel=1' gives access `v4l' demux `' path `/dev/video0:norm=pal:size=720×480:channel=1'
[00000300] main input debug: creating demux: access='v4l' demux='' path='/dev/video0:norm=pal:size=720×480:channel=1'
[00000314] main demuxer debug: looking for access_demux module: 1 candidate
[00000314] v4l demuxer debug: WxH 720x0
[00000314] v4l demuxer debug: main device=`/dev/video0'
[00000314] v4l demuxer debug: V4L device BT848A video (Hauppauge (bt848) 4 channels 1 audios 48 < w < 924 32 < h < 576
[00000314] v4l demuxer debug: invalid height 0
[00000314] v4l demuxer debug: setting channel Composite1(1) 0 tuners flags=0x2 type=0x2 norm=0x0
[00000314] v4l demuxer debug: will use 320x240
[00000314] v4l demuxer debug: v4l device uses brightness: 32768
[00000314] v4l demuxer debug: v4l device uses colour: 32768
[00000314] v4l demuxer debug: v4l device uses hue: 32768
[00000314] v4l demuxer debug: v4l device uses contrast: 32768
[00000314] v4l demuxer debug: v4l device uses frame size: 230400
[00000314] v4l demuxer debug: v4l device uses chroma: RV24
[00000314] v4l demuxer error: cannot open audio device (No such file or directory)
[00000314] v4l demuxer debug: v4l grabbing started
[00000314] v4l demuxer debug: added new video es RV24 320x240
[00000300] main input debug: selecting program id=0
[00000314] main demuxer debug: using access_demux module "v4l"
[00000316] main packetizer debug: looking for packetizer module: 17 candidates
[00000316] main packetizer debug: using packetizer module "rawvideo"
[00000316] main packetizer debug: thread 1140881760 (decoder) created at priority 0 (input/decoder.c:159)
[00000300] main input debug: starting in sync mode
[00000300] main input debug: `v4l:/dev/video0:norm=pal:size=720×480:channel=1' successfully opened
[00000302] main stream output debug: adding a new input
[00000303] stream_out_transcode private debug: creating video transcoding from fcc=`RV24' to fcc=`mp4v'
[00000319] main decoder debug: looking for decoder module: 24 candidates
[00000319] main decoder debug: using decoder module "rawvideo"
[00000320] main encoder debug: looking for encoder module: 9 candidates
[00000320] ffmpeg encoder debug: libavcodec initialized (interface 3345152 )
[00000320] ffmpeg encoder debug: found encoder MPEG-4 Video
[00000320] main encoder debug: using encoder module "ffmpeg"
[00000320] main encoder debug: removing module "ffmpeg"
[00000303] stream_out_transcode private debug: decoder aspect is 576000:432000
[00000303] stream_out_transcode private debug: source pixel aspect is 1.000000:1[00000303] stream_out_transcode private debug: scaled pixel aspect is 1.000000:1[00000303] stream_out_transcode private debug: source 320x240, crop 320x240, destination 320x240, padding 320x240
[00000303] stream_out_transcode private debug: encoder aspect is 576000:432000
[00000320] main encoder debug: looking for encoder module: 9 candidates
[00000320] ffmpeg encoder debug: libavcodec already initialized
[00000320] ffmpeg encoder debug: found encoder MPEG-4 Video
[00000320] main encoder debug: using encoder module "ffmpeg"
[00000312] main private debug: adding a new input
[00000312] mux_asf private debug: adding input
[00000356] main private debug: looking for video filter2 module: 4 candidates
[00000356] main private warning: no video filter2 module matching "deinterlace" could be loaded
[00000303] stream_out_transcode private debug: no video filter found
[00000361] main private debug: looking for crop padd module: 1 candidate
[00000361] ffmpeg private debug: input: 320x240 RV24 -> 320x240 I420
[00000361] ffmpeg private debug: libavcodec already initialized
[00000361] main private debug: using crop padd module "ffmpeg"
[00000311] main http server debug: Connection from 192.168.1.105
[00000311] main http server debug: Connection from 192.168.1.105
[00000311] main http server debug: Connection from 192.168.1.105
[00000312] mux_asf private debug: Asf muxer creating header
[00000312] mux_asf private debug: pixel aspect-ratio: 1/1
[00000311] main http server debug: Connection from 192.168.1.105
[00000311] main http server debug: Connection from 192.168.1.105


vlc mmsh://192.168.1.120:9090 --loop

thank u very much

---

