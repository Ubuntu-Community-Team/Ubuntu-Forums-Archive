---
title: "PulseAudio dies and sinks/sources won't reconnect"
date: 2008-10-03
forum: Multimedia Software
---

### Post by clconway on 2008-10-03
Recently, my PulseAudio daemon has taken to periodically dying. I haven't nailed down exactly what's happening, but it started happening after I began using a pair of USB headphones and seems to have something to do with plugging/unplugging the headphones and suspend resume. It would be great if I could fix this problem (though I'm not especially hopeful), but that's not why I'm posting. (I've posted the output of [FONT="Courier New"]grep pulseaudio /var/log/messages[/FONT] below, in case it holds any clues.)

I've figured out how to restart the daemon, by running "[FONT="Courier New"]pulseaudio -D[/FONT]". But it seems that sources and sinks have a problem connecting with the new instance of the daemon: I have to restart Firefox and Amarok to get any sound out of them; right now, I can't get any sound out of my built-in speakers or speaker output.

Restarting apps and rebooting the system when PulseAudio craps out is a big pain. Is there any way to get sinks and sources to attach themselves to the new daemon without going through all that?

```
Oct  2 16:13:32 wagstaff kernel: [ 3652.907114] pulseaudio[12018]: segfault at b56cb0e0 eip b56cb0e0 esp bfeed86c error 4
Oct  2 16:28:52 wagstaff pulseaudio[15158]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Oct  2 16:28:52 wagstaff pulseaudio[15158]: alsa-util.c: Cannot find fallback mixer control "PCM".
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: 4 sink(s) available.
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:   * index: 0
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <alsa_output.usb_device_ffffffff_ffffffff_noserial_sound_card_0_alsa_playback_0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <modules/module-alsa-sink.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iflags: LATENCY HARDWARE 
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Istate: RUNNING
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ivolume: <0: 100% 1: 100%>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imute: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilatency: <97959 usec>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imonitor source: <1>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isample spec: <s16le 2ch 44100Hz>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ichannel map: <front-left,front-right>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused by: <2>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilinked by: <2>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imodule: <1>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idescription: <ALSA PCM on front:1 (USB Audio) via DMA>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <modules/module-alsa-sink.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iflags: HW_VOLUME_CTRL LATENCY HARDWARE 
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Istate: SUSPENDED
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ivolume: <0:   0% 1:   0%>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imute: <1>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilatency: <0 usec>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imonitor source: <2>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isample spec: <s16le 2ch 44100Hz>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ichannel map: <front-left,front-right>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilinked by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imodule: <2>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idescription: <ALSA PCM on front:0 (STAC92xx Analog) via DMA>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 2
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <rtp>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <modules/module-null-sink.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iflags: LATENCY 
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Istate: SUSPENDED
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ivolume: <0: 100% 1: 100%>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imute: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilatency: <0 usec>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imonitor source: <4>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isample spec: <s16be 2ch 44100Hz>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ichannel map: <front-left,front-right>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilinked by: <1>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imodule: <11>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idescription: <RTP Multicast Sink>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 3
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <combined>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <modules/module-combine.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iflags: LATENCY 
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Istate: SUSPENDED
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ivolume: <0: 100% 1: 100%>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imute: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilatency: <0 usec>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imonitor source: <5>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isample spec: <s16le 2ch 44100Hz>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ichannel map: <front-left,front-right>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilinked by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imodule: <13>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idescription: <Simultaneous output to ALSA PCM on front:1 (USB Audio) via DMA, ALSA PCM on front:0 (STAC92xx Analog) via DMA>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: 6 source(s) available.
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:   * index: 0
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <alsa_input.usb_device_ffffffff_ffffffff_noserial_alsa_capture_0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <modules/module-alsa-source.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iflags: HW_VOLUME_CTRL LATENCY HARDWARE 
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Istate: SUSPENDED
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ivolume: <0:   0%>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imute: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilatency: <0 usec>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isample spec: <s16le 1ch 44100Hz>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ichannel map: <mono>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilinked by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imodule: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idescription: <ALSA PCM on hw:1 (USB Audio) via DMA>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <alsa_output.usb_device_ffffffff_ffffffff_noserial_sound_card_0_alsa_playback_0.monitor>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <modules/module-alsa-sink.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iflags: 
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Istate: SUSPENDED
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ivolume: <0: 100% 1: 100%>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imute: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilatency: <0 usec>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isample spec: <s16le 2ch 44100Hz>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ichannel map: <front-left,front-right>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilinked by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imonitor_of: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imodule: <1>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idescription: <Monitor Source of ALSA PCM on front:1 (USB Audio) via DMA>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 2
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0.monitor>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <modules/module-alsa-sink.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iflags: 
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Istate: SUSPENDED
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ivolume: <0: 100% 1: 100%>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imute: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilatency: <0 usec>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isample spec: <s16le 2ch 44100Hz>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ichannel map: <front-left,front-right>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilinked by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imonitor_of: <1>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imodule: <2>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idescription: <Monitor Source of ALSA PCM on front:0 (STAC92xx Analog) via DMA>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 3
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <modules/module-alsa-source.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iflags: HW_VOLUME_CTRL LATENCY HARDWARE 
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Istate: SUSPENDED
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ivolume: <0:  53% 1:  53%>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imute: <1>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilatency: <0 usec>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isample spec: <s16le 2ch 44100Hz>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ichannel map: <front-left,front-right>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilinked by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imodule: <3>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idescription: <ALSA PCM on front:0 (STAC92xx Analog) via DMA>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 4
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <rtp.monitor>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <modules/module-null-sink.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iflags: 
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Istate: RUNNING
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ivolume: <0: 100% 1: 100%>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imute: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilatency: <0 usec>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isample spec: <s16be 2ch 44100Hz>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ichannel map: <front-left,front-right>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused by: <1>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilinked by: <1>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imonitor_of: <2>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imodule: <11>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idescription: <Monitor Source of RTP Multicast Sink>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 5
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <combined.monitor>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <modules/module-combine.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iflags: 
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Istate: SUSPENDED
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ivolume: <0: 100% 1: 100%>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imute: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilatency: <0 usec>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isample spec: <s16le 2ch 44100Hz>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ichannel map: <front-left,front-right>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilinked by: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imonitor_of: <3>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imodule: <13>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idescription: <Monitor Source of Simultaneous output to ALSA PCM on front:1 (USB Audio) via DMA, ALSA PCM on front:0 (STAC92xx Analog) via DMA>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: 2 sink input(s) available.
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 2
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <RTP Stream (PulseAudio RTP Stream on localhost)>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <modules/rtp/module-rtp-recv.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iflags: 
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Istate: DRAINED
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isink: <0> 'alsa_output.usb_device_ffffffff_ffffffff_noserial_sound_card_0_alsa_playback_0'
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ivolume: <0: 100% 1: 100%>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imute: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilatency: <0 usec>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isample spec: <s16be 2ch 44100Hz>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ichannel map: <front-left,front-right>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iresample method: copy
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imodule: <14>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 5
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <Audio Stream>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <pulsecore/protocol-native.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iflags: 
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Istate: RUNNING
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isink: <0> 'alsa_output.usb_device_ffffffff_ffffffff_noserial_sound_card_0_alsa_playback_0'
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ivolume: <0:  80% 1:  80%>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imute: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilatency: <490997 usec>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isample spec: <s16le 2ch 44100Hz>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ichannel map: <front-left,front-right>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iresample method: auto
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Imodule: <6>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iclient: <4> 'amarokapp'
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: 1 source outputs(s) available.
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 0
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: 'RTP Monitor Stream'
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <modules/rtp/module-rtp-send.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iflags: 
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Istate: RUNNING
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isource: <4> 'rtp.monitor'
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilatency: <0 usec>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isample spec: <s16be 2ch 44100Hz>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ichannel map: <front-left,front-right>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iresample method: auto
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iowner module: <12>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: 2 client(s) logged in.
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 0
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <PulseAudio Volume Control>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <pulsecore/protocol-native.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iowner module: <6>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 4
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <amarokapp>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Idriver: <pulsecore/protocol-native.c>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iowner module: <6>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: 17 module(s) loaded.
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 0
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-alsa-source>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <device_id=1 source_name=alsa_input.usb_device_ffffffff_ffffffff_noserial_alsa_capture_0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-alsa-sink>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <device_id=1 sink_name=alsa_output.usb_device_ffffffff_ffffffff_noserial_sound_card_0_alsa_playback_0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 2
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-alsa-sink>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <device_id=0 sink_name=alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 3
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-alsa-source>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <device_id=0 source_name=alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 4
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-hal-detect>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 5
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-esound-protocol-unix>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 6
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-native-protocol-unix>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 7
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-volume-restore>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 8
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-default-device-restore>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 9
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-rescue-streams>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 10
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-suspend-on-idle>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 11
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-null-sink>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink">
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 12
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-rtp-send>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <source=rtp.monitor loop=1>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 13
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-combine>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 14
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-rtp-recv>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 15
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-gconf>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     index: 16
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iname: <module-x11-publish>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iargument: <>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iused: -1
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iauto unload: no
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: 1 cache entries available.
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c:     name: <pulse-hotplug>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iindex: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Isample spec: <n/a>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ichannel map: <n/a>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilength: <0>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Iduration: <0.0s>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ivolume: <0: 100% 1: 100% 2: 100% 3: 100% 4: 100% 5: 100% 6: 100% 7: 100%>
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ilazy: yes
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: ^Ifilename: /usr/share/sounds/startup3.wav
Oct  2 16:30:42 wagstaff pulseaudio[15158]: main.c: 0 autoload entries available.
Oct  2 19:10:34 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  2 23:06:41 wagstaff pulseaudio[15158]: module-alsa-sink.c: Got POLLERR from ALSA
Oct  2 23:06:41 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  2 23:06:41 wagstaff pulseaudio[15158]: module-alsa-sink.c: Could not recover from POLLERR|POLLNVAL|POLLHUP and XRUN: No such device
Oct  2 23:06:46 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  2 23:07:01 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  2 23:07:06 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  3 00:04:32 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  3 09:08:42 wagstaff pulseaudio[15158]: module-alsa-sink.c: Got POLLERR from ALSA
Oct  3 09:08:42 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  3 09:08:47 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  3 09:09:27 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  3 09:09:32 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  3 09:36:28 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  3 10:31:53 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  3 12:55:35 wagstaff pulseaudio[15158]: module-alsa-sink.c: Got POLLERR from ALSA
Oct  3 12:55:35 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  3 12:55:40 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  3 12:57:20 wagstaff pulseaudio[15158]: module-alsa-sink.c: Got POLLERR from ALSA
Oct  3 12:57:20 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  3 12:57:25 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  3 12:57:30 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  3 12:57:35 wagstaff pulseaudio[15158]: sap.c: sendmsg() failed: Invalid argument
Oct  3 13:01:49 wagstaff pulseaudio[15158]: alsa-util.c: Cannot find fallback mixer control "PCM".
Oct  3 13:01:49 wagstaff pulseaudio[15158]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Oct  3 13:03:35 wagstaff pulseaudio[24764]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Oct  3 13:03:35 wagstaff pulseaudio[24764]: alsa-util.c: Cannot find fallback mixer control "PCM".

```

---

### Post by erikthedrink on 2009-09-08
Maybe yes.  I've got logitech usb speakers.  In Xubuntu, go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:KS
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

