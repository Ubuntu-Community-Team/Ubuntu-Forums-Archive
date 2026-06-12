---
title: "Edirol UA-25 in advanced mode and Audacity"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by Muffe on 2006-10-28
I have a laptop (Acer Travelmate 3000) with an internal Intel HDA soundcard, and an external Edirol UA-25 soundcard, witch is my preferred audio device.

The UA-25 has two modes: one usb-audio mode (using generic usb-sound drivers) and one advanced-mode. In the USB-audio mode is the sample rate limited to 44,1 kHz, but it can be increased to 96 kHz in the advanced mode.

I want to use my Edirol UA-25 in advanced mode and record audio with Audacity.

It works in usb-audio mode. The device shows up as /dev/dsp1 (the Intel card is /dev/dsp), and both playback and recording is working. When I switch to advanced mode, only /dev/dsp shows up, witch is my internal soundcard. No /dev/dsp1. If I play a sound file, the audio comes from the inetrnal PC speakers, through the Intel HDA card. It is not possible to record from the UA-25 either.

I know the UA-25 is working in advanced mode, because Amarok plays nicely through it, and many other programs too.

How do I get this soundcard working with Audacity in advanced mode, so that I can record sounds in 48 kHz?

Thanks in advance.

---

### Post by tich on 2007-02-07
i am thinking about purchasing the same soundcard,

did you ever find a solution to your problem?
did you have any other difficulties setting it up?

---

### Post by sgx on 2007-02-10
> **Muffe said:**
> I have a laptop (Acer Travelmate 3000) with an internal Intel HDA soundcard, and an external Edirol UA-25 soundcard, witch is my preferred audio device.

The UA-25 has two modes: one usb-audio mode (using generic usb-sound drivers) and one advanced-mode. In the USB-audio mode is the sample rate limited to 44,1 kHz, but it can be increased to 96 kHz in the advanced mode.

I want to use my Edirol UA-25 in advanced mode and record audio with Audacity.

It works in usb-audio mode. The device shows up as /dev/dsp1 (the Intel card is /dev/dsp), and both playback and recording is working. When I switch to advanced mode, only /dev/dsp shows up, witch is my internal soundcard. No /dev/dsp1. If I play a sound file, the audio comes from the inetrnal PC speakers, through the Intel HDA card. It is not possible to record from the UA-25 either.

I know the UA-25 is working in advanced mode, because Amarok plays nicely through it, and many other programs too.

How do I get this soundcard working with Audacity in advanced mode, so that I can record sounds in 48 kHz?

Thanks in advance.
...while I am confident this post about edirol UM2 may not directly help  now, it shows how one did get some success, and it may help you in the future, leading to versatile linux tips...and the link

[http://lalists.stanford.edu/lau/2007/01/0244.html](http://lalists.stanford.edu/lau/2007/01/0244.html)

may be modified by month or year to yield tons of info on many audio topics, and of course, join the list and take part...
Re: [linux-audio-user] midi interface

    * This message: [ Message body ] [ Respond ] [ More options ]
    * Related messages: [ Next message ] [ Previous message ] [ In reply to ]

From: Alexandre Ratchov <alex@email-addr-hidden>
Date: Tue Jan 09 2007 - 00:00:38 EET

On Sun, Jan 07, 2007 at 07:02:35PM +0100, Julien Claassen wrote:
> Hi!
> If I have a midi-interface, one of those externals, to which you can connect
> more than one device (synth, keyboard), how does this look to alsa? Does it
> only see one dvice with a lot of channels or does it see more devices? I think
> about getting one to use it with midish, which uses rawmidi devices and I
> wonder if it will work.

hello!

if your MIDI interface has multiple MIDI ports but they don't
appear in /dev you can use 'modprobe snd-virmidi' to create virtual
MIDI devices (they will appear in /dev). Then you can use
aconnect(1) to connect virtual devices to real devices.

For instance i have an Edirol UM2 USB-MIDI interface (2 input ports
and 2 output ports). According to 'aseqdump -l' devices appear to
ALSA as ports 16:0 and 16:1. Virtual devices appear as ports 24:0
25:0 26:0 27:0.

$ aseqdump -l
 Port Client name Port name
  0:0 System Timer
  0:1 System Announce
 14:0 Midi Through Midi Through Port-0
 16:0 UM-2 UM-2 MIDI 1
 16:1 UM-2 UM-2 MIDI 2
 20:0 MPU-401 MIDI 1-0 MPU-401 MIDI 1-0
 24:0 Virtual Raw MIDI 2-0 VirMIDI 2-0
 25:0 Virtual Raw MIDI 2-1 VirMIDI 2-1
 26:0 Virtual Raw MIDI 2-2 VirMIDI 2-2
 27:0 Virtual Raw MIDI 2-3 VirMIDI 2-3

$ ls -l /dev/snd/midi*
crw-rw---- 1 root audio 116, 8 2007-01-08 21:56 /dev/snd/midiC0D0
crw-rw---- 1 root audio 116, 40 2007-01-08 21:56 /dev/snd/midiC1D0
crw-rw---- 1 root audio 116, 72 2007-01-08 22:06 /dev/snd/midiC2D0
crw-rw---- 1 root audio 116, 73 2007-01-08 22:06 /dev/snd/midiC2D1
crw-rw---- 1 root audio 116, 74 2007-01-08 22:06 /dev/snd/midiC2D2
crw-rw---- 1 root audio 116, 75 2007-01-08 22:06 /dev/snd/midiC2D3

Then, I connect (in both "in" and "out" directions) port 16:0 to
port 24:0 and 16:1 to 25:0, so that both ports of my UM2 will be
usable as /dev/snd/midiC2D0 and /dev/snd/midiC2D1

$ aconnect 16:0 24:0
$ aconnect 24:0 16:0
$ aconnect 16:1 25:0
$ aconnect 25:0 16:1

At this stage, midish is able to use /dev/snd/midiC2D0 and
/dev/snd/midiC2D1. For instance the following will configure
devices and start sending everything from device 1 (my keyboard) to
device 0 (my sound module)

$ rmidish
send EOF character (control-D) to quit
1> devattach 0 "/dev/snd/midiC2D0"
2> devattach 1 "/dev/snd/midiC2D1"
3> filtnew myfilt
4> filtdevmap myfilt 1 0
5> songidle
press control-C to finish

cheers,

-- Alexandre
Received on Tue Jan 9 00:15:06 2007

    * This message: [ Message body ]
    * Next message: sam@email-addr-hidden: "[linux-audio-user] Re: Re: Re: SB450 any good? why does jack fail?"
    * Previous message: Folderol: "Re: [linux-audio-user] OT: Getting rid of entire studio"
    * In reply to: Julien Claassen: "[linux-audio-user] midi interface"

    * Mail actions: [ respond to this message ] [ mail a new topic ]
    * Contemporary messages sorted: [ By Date ] [ By Thread ] [ By Subject ] [ By Author ] [ By messages with attachments ]

This archive was generated by hypermail 2.1.8 : Tue Jan 09 2007 - 00:15:06 EET

---

