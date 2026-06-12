---
title: "How do I use the serial MIDI driver?"
date: 2009-11-29
forum: Multimedia Software
---

### Post by Blimix on 2009-11-29
Hey, all.  I hate bothering people with noob-ish questions, but after lots of time RTFMing, Googling and searching the Ubuntu Forums, I'm still stuck.

My Roland SC-7 sound module receives MIDI signals through the serial port, with a special cable.  Ubuntu has the driver to support this (snd-serial-u16550).  I can get the driver loaded into the kernel with modprobe (though for some reason it requires sudo, and sometimes requires setserial first).  But I have no clue how to tell the system to *use* the driver:  To actually output MIDI signals to the serial port.

The hardware is okay:  It works when I boot from my Windows partition.  I've been wrestling with aconnect, jackd, TiMidity, modprobe and alsa-base.conf, all to no avail.  Because I'm relatively new to Ubuntu, I'm in "try everything because I don't know what to do" mode (which is taxing).  Playing MIDI files in TiMidity generates sound internally (I installed fluidsynth), but sends nothing to the Roland.

I would be grateful for any advice.  Thanks!

[Just in case it's helpful:]

$ aconnect -i -l
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
	Connecting To: 15:0
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 20: 'Serial MIDI (UART16550A)' [type=kernel]
    0 'Serial MIDI 1   '

$ aconnect -o -l
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 20: 'Serial MIDI (UART16550A)' [type=kernel]
    0 'Serial MIDI 1   '
client 128: 'TiMidity' [type=user]
    0 'TiMidity port 0 '
    1 'TiMidity port 1 '
    2 'TiMidity port 2 '
    3 'TiMidity port 3 '


$ aconnect 128:0 20:0
Connection failed (Operation not permitted)

---

