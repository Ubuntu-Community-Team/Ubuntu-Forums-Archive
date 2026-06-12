---
title: "A Plea For A Basic, Simple to Setup Media Server"
date: 2013-05-09
forum: Multimedia Software
---

### Post by Mark_in_Hollywood on 2013-05-09
I have a (50") TV with an ethernet port for an input. I have a computer with one (1) ethernet port for an input or an output. I have a five (5) port ethernet switch (unmanaged). I have a SiliconDust HDHomeRun Dual TV tuner. I have MythTV. My OS is ver. 12.04.

Over time I have tried multiple servers and got each and every one of them screwed up and would like to be pointed to a URL or .pdf that makes an easier job of installing the "server" software application, configuring same and running (enjoying) "it". Can you point me to a "How To"?

I tried MediaTomb. No luck. I tried Cherokee. No luck. I am trying XBMC. And not much luck here either.

The computer's ethernet port is plugged into the switch. Also plugged into the switch are the Silicon Dust HDHomeRun (Dual) Tuner and the cable from the switch to the 50" TV.

My computer sends the video signal to the monitor (actually a TV set with computer monitor capability) via a VGA cable. To simplify the details of this post, I'll call the TV set that doubles as a computer monitor, the **monitor**. I can see/hear media from live tv via MythTV, so the switch is sending or allowing the computer (and MythTV) to access the HomeRun's signal.

Between the MythTv and the HDHomeRun tuner, I can watch live TV, or record and playback TV on the monitor. The TV is another matter. I believe it sees the HomeRun tuner as the "server".  But no signal from it gets through and in any event, I'm not sure the TV could "play" or "stream" what came from the HomeRun tuner anyway. How can I configure my various devices (components) to allow me to send media from the computer, through the switch to the TV (50")??? By from the computer I mean, either Hulu or MythTV's .mpg files?

All I want to do is send the video (whether it is a live TV channel, a recorded .mpg, or Hulu to the TV, that is the 50" TV. I thought that's what a "media server" does. But time after time, I am not understanding what is what.

Lastly, I tried using Netgear's WNDA-3100 wifi adapter with the 50" TV. It could not hold onto the Netflix' signal from the modem-router-wifi. (I run the signal power at 6, bumped it up to 10 (which is max) and the adapter could not hold the signal, even though the modem-router-wifi is 20 feet from the Netgear adapter. So, I'm trying a wired (ethernet cable) approach. And returned the Netgear adapter.

The 50" TV had in it menus, a "Connection Test". When the "Ethernet Cable" is set to "Manual" this is what the 50" TV "sees".

IP Address: 169.254.58.123
Subnet mask: 255.255.0.0
Default Gateway is blank
DNS is blank

Proxy address is blank
Proxy port is: 0 (number) zero

If the TV (50") is set to Ethernet "Automatic", it can find the cable but cannot find an IP Address. I have a spare router (actually a router-wifi) and can attach it, but LORDY! is there no simple way to achieve this?

Ubuntu's Network Manager shows:

eth0 - IPv4

IP Address: 169.254.4.60
B'cast Address: 169.254.255.255
Subnet mask: 255.255.0.0

Some technical info:

Nvidia 9500GT graphics card and driver version 304.88.

Ubuntu Precise Pangolin ver. 12.04 LTS

MythTV version: fixes/0.26 (v0.26.0-119-gc0419cd)

Rosewill 5 port ethernet switch RC-409LX

Silicon Dust Dual tuner with firmware revision 101A799A


2WIRE000 wifi base station

IPv4

IP Address: 192.168.1.72
B'cast Address: 192.168.1.255
Subnet Mask: 255.255.255.0
Default Route: 192.168.1.254
Primary DNS: 192.168.1.254

---

