---
title: "midi sound problems"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by monkblah on 2007-10-03
Hi, I'm using Fiesty with an SB Live soundcard and AMD64 processor. Trying to get midi sound working.

First, I can play regular sound files, no problem. When I tried to play a midi file using kmid, however (or aplaymidi), no sound comes out. Kmid does display the words but no sound.

I installed timidity, and it is able to play the midi files successfully -- i.e., "timidty [midi_file]" plays sound.

I tried running Timidity as a server, it seemed like that might be necessary for kmid and other programs to work. I added it to my /etc/default/timidity to run automatically on startup, using:

```
timidity -iA -B2,8 -Os1l -s 44100
```

This seems to work, because now I have extra devices:
```

aplaymidi -l
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 16:0    SB Live 5.1 [SB0220]             EMU10K1 MPU-401 (UART)
 17:0    Emu10k1 WaveTable                Emu10k1 Port 0
 17:1    Emu10k1 WaveTable                Emu10k1 Port 1
 17:2    Emu10k1 WaveTable                Emu10k1 Port 2
 17:3    Emu10k1 WaveTable                Emu10k1 Port 3
128:0    TiMidity                         TiMidity port 0
128:1    TiMidity                         TiMidity port 1
128:2    TiMidity                         TiMidity port 2
128:3    TiMidity                         TiMidity port 3
```

They are visible in kmid as well.

However, selecting these devices in kmid doesn't seem to make a difference. No sound plays from kmid, though timidity can play sound successfully. In the konsole window I run kmid from it just keeps saying

```
AlsaOut::eventInit : no source
```

Can't play midi files using other apps either, like aplaymidi, just with timidity.

It seems like somehow the timidity server is not talking to the midi apps successfully? Since timidity can play itself, it seems like the soundcard is not the problem.

I have reached a dead end at this point, can't find any further info (though other people seem to be having similar problems).

Does anyone have any ideas?

---

### Post by mosestruong on 2008-01-27
I'm also having this problem on HP Pavilion dv2308tx running amd64 kernel. Has anyone found a solution to this?

---

