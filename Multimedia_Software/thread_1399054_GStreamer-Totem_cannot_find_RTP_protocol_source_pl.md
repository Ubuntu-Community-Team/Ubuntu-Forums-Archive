---
title: "GStreamer-Totem cannot find RTP protocol source plugin"
date: 2010-02-05
forum: Multimedia Software
---

### Post by medo007 on 2010-02-05
Hi,

_here the scenario:_

A Video is being streamed by VLC-Player (no problem here):
- Streaming method: RTP
- Destination: 127.0.0.1:1234

I'm trying to open the video with GStreamer-Totem Player: 
- Movie->Open Location->Enter the address of the file you would like to open: "rtp://127.0.0.1:1234"

_The response from Totem is:_[I]
** Message: Error: A RTP protocol source plugin is required to play this stream, but not installed.
gstplaybasebin.c(1673): gen_source_element (): /GstPlayBin:play:
No URI handler for rtp

** Message: Missing plugin: gstreamer|0.10|totem|RTP protocol source|urisource-rtp (RTP protocol source)
** Message: No installation candidate for missing plugins found.
** Message: Error: A RTP protocol source plugin is required to play this stream, but not installed.
gstplaybasebin.c(1673): gen_source_element (): /GstPlayBin:play:
No URI handler for rtp

** Message: Missing plugin: gstreamer|0.10|totem|RTP protocol source|urisource-rtp (ignoring)
** Message: All missing plugins are blacklisted, doing nothing

[/I]**Can someone tell me where I can find the RTP protocol source plugin?** 
I'm not able to find it on my own (tried Synaptic and Google). And I have to use GStreamer for my project, so I cannot switch to VLC or some other player.

_Here is what gst-inspect tells me I already have:_
[I]$ gst-inspect | grep rtp
asf:  rtpasfdepay: RTP ASF packet depayloader
ffmpeg:  ffmux_rtp: FFMPEG rtp Muxer
rtppayloads:  msgsmpayloader: RTP MSGSM Audio Payloader
rtppayloads:  msgsmdepayloader: MSGSM RTP Depayloader
rtppayloads:  rtpcnpay: RTP Confort Noise Payloader
rtppayloads:  rtpcndepay: RTP Confort Noise Depayloader
rtpjitterbuffer:  rtpjitterbuffer: RTP packet jitter-buffer
jrtp:  rtpsend: JRTP Session
jrtp:  rtprecv: JRTP Session
jrtp:  rtpbin: RTP Bin
rtpdemux:  rtpdemux: RTP Demux
rtpmuxer:  rtpmux: RTP muxer
rtpmuxer:  rtpdtmfmux: RTP muxer
gstrtpmanager:  gstrtpssrcdemux: RTP SSRC Demux
gstrtpmanager:  gstrtpsession: RTP Session
gstrtpmanager:  gstrtpptdemux: RTP Demux
gstrtpmanager:  gstrtpjitterbuffer: RTP packet jitter-buffer
gstrtpmanager:  gstrtpclient: RTP Client
gstrtpmanager:  gstrtpbin: RTP Bin
dtmf:  rtpdtmfdepay: RTP DTMF packet depayloader
dtmf:  rtpdtmfsrc: RTP DTMF packet generator
bluetooth:  rtpsbcpay: RTP packet payloader
quicktime:  rtpxqtdepay: RTP packet depayloader
rtsp:  rtpdec: RTP Decoder
rtp:  rtpdepay: Dummy RTP session manager
rtp:  rtpac3depay: RTP AC3 depayloader
rtp:  rtpdvdepay: RTP DV Depayloader
rtp:  rtpdvpay: RTP DV Payloader
rtp:  rtpilbcpay: RTP iLBC Payloader
rtp:  rtpilbcdepay: RTP iLBC depayloader
rtp:  rtpg726depay: RTP G.726 depayloader
rtp:  rtpg726pay: RTP G.726 payloader
rtp:  rtpg729depay: RTP G.729 depayloader
rtp:  rtpg729pay: RTP G.729 payloader
rtp:  rtpgsmdepay: RTP GSM depayloader
rtp:  rtpgsmpay: RTP GSM payloader
rtp:  rtpamrdepay: RTP AMR depayloader
rtp:  rtpamrpay: RTP AMR payloader
rtp:  rtppcmadepay: RTP PCMA depayloader
rtp:  rtppcmudepay: RTP PCMU depayloader
rtp:  rtppcmupay: RTP PCMU payloader
rtp:  rtppcmapay: RTP PCMA payloader
rtp:  rtpmpadepay: RTP MPEG audio depayloader
rtp:  rtpmpapay: RTP MPEG audio payloader
rtp:  rtpmpvdepay: RTP MPEG video depayloader
rtp:  rtpmpvpay: RTP MPEG2 ES video payloader
rtp:  rtph263ppay: RTP H263 payloader
rtp:  rtph263pdepay: RTP H263 depayloader
rtp:  rtph263depay: RTP H263 depayloader
rtp:  rtph263pay: RTP H263 payloader
rtp:  rtph264depay: RTP H264 depayloader
rtp:  rtph264pay: RTP H264 payloader
rtp:  rtpjpegdepay: RTP JPEG depayloader
rtp:  rtpjpegpay: RTP JPEG payloader
rtp:  rtpL16pay: RTP audio payloader
rtp:  rtpL16depay: RTP audio depayloader
rtp:  asteriskh263: RTP Asterisk H263 depayloader
rtp:  rtpmp1sdepay: RTP MPEG1 System Stream depayloader
rtp:  rtpmp2tdepay: RTP MPEG Transport Stream depayloader
rtp:  rtpmp2tpay: RTP MPEG2 Transport Stream payloader
rtp:  rtpmp4vpay: RTP MPEG4 Video payloader
rtp:  rtpmp4vdepay: RTP MPEG4 video depayloader
rtp:  rtpmp4apay: RTP MPEG4 audio payloader
rtp:  rtpmp4adepay: RTP MPEG4 audio depayloader
rtp:  rtpmp4gdepay: RTP MPEG4 ES depayloader
rtp:  rtpmp4gpay: RTP MPEG4 ES payloader
rtp:  rtpspeexpay: RTP Speex payloader
rtp:  rtpspeexdepay: RTP Speex depayloader
rtp:  rtpsv3vdepay: RTP SVQ3 depayloader
rtp:  rtptheoradepay: RTP Theora depayloader
rtp:  rtptheorapay: RTP Theora depayloader
rtp:  rtpvorbisdepay: RTP Vorbis depayloader
rtp:  rtpvorbispay: RTP Vorbis depayloader
rtp:  rtpvrawdepay: RTP Raw Video depayloader
rtp:  rtpvrawpay: RTP Raw Video payloader

[/I]
What am I missing?
Thanks for the help! :)

---

