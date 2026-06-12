---
title: "I cant start Bristol either -b3 or -jack option"
date: 2014-11-16
forum: Multimedia Software
---

### Post by i12 on 2014-11-16
I installed jack.

```

~$ startBristol -jack
checking availability of TCP port 26684
using port 26684
starting logging thread [@1416122652.469488]
Copyright (c) by Nick Copeland <nickycopeland@hotmail.com> 1996,2012
This program comes with ABSOLUTELY NO WARRANTY; for details type `<Ctrl> w'.
This is free software, and you are welcome to redistribute it
under certain conditions; type `<Ctrl> g' for details of GPL terms.
starting logging thread [@1416122652.517204]
Nov 16 10:24:12 bristol  [0.100099] starting console logging [@1416122652.469488]
Nov 16 10:24:12 bristol  [0.100420] bristol version 0.60.11
Nov 16 10:24:12 bristol  [0.100463] bristol
Nov 16 10:24:12 bristol  [0.100504]     -rate 44100
Nov 16 10:24:12 bristol  [0.100544]     -count 1024
Nov 16 10:24:12 bristol  [0.100584]     -jack
Nov 16 10:24:12 bristol  [0.100623]     -port 26684
Nov 16 10:24:12 bristol  [0.100662] jsm will use 'startBristol -jack'
Nov 16 10:24:12 bristol  [0.100703] generate bandlimited waveforms(31, 12, 84, 1.50, 0.80, 44100)
Nov 16 10:24:12 bristol  [0.100936] could not reschedule thread
Nov 16 10:24:12 bristol  [0.100978] Fixing samplerate at 44100
Nov 16 10:24:12 bristol  [0.103156] midi jack: 128.1
Nov 16 10:24:12 bristol  [0.103251] Opened listening control socket: 26684
Nov 16 10:24:12 bristol  [0.103261] returning handle 0, flags 80000020, fd 4
Nov 16 10:24:12 bristol  [0.103272] opened control socket
Nov 16 10:24:12 bristol  [0.103282] midiOpen: 26684(100)
Nov 16 10:24:12 bristol  [0.103291] opened midi device 128.1
Nov 16 10:24:12 brighton [0.100054] starting console logging [@1416122652.517204]
Nov 16 10:24:12 brighton [0.100310] emulation defaults:
Nov 16 10:24:12 brighton [0.100323]     -voices  32
Nov 16 10:24:12 brighton [0.100333]     -detune  0
Nov 16 10:24:12 brighton [0.100342]     -gain    2
Nov 16 10:24:12 brighton [0.100353]     -pwd     2
Nov 16 10:24:12 brighton [0.100361]     -glide   5
Nov 16 10:24:12 brighton [0.100370]     -curve   175
Nov 16 10:24:12 brighton [0.100380] brighton version 0.60.11
Nov 16 10:24:13 brighton [1.100373]   brighton
Nov 16 10:24:13 brighton [1.100553]     -jack
Nov 16 10:24:13 brighton [1.100565]     -port 26684
Nov 16 10:24:13 brighton [1.101219] starting event management thread
Nov 16 10:24:13 brighton [1.102382] connected to :0.0
Nov 16 10:24:13 brighton [1.102526] brighton 0x6f8700 765 400
Nov 16 10:24:13 brighton [1.102569] display is 1280 by 1024 pixels (0, 0)
Nov 16 10:24:13 brighton [1.102608] Window is w 1280, h 1024, d 24, 0 0 0
Nov 16 10:24:13 brighton [1.103112] Using DirectColor display
Nov 16 10:24:13 brighton [1.176409] Initialise the hammondB3 link to bristol: 0x1d7bf40
Nov 16 10:24:13 brighton [1.176564] hostname is localhost, bristol
Nov 16 10:24:13 brighton [1.176861] TCP port: 26684
Nov 16 10:24:13 bristol  [1.224694] Accepted connection from 0 (4) onto 1 (6)
Nov 16 10:24:13 brighton [1.177034] Connected to the bristol control socket: 6 (dev=0)
Nov 16 10:24:13 brighton [1.177076] returning handle 0, flags 20, fd 6
Nov 16 10:24:13 brighton [1.177110] bristolengine already active (0)
Nov 16 10:24:13 brighton [1.201795] opened GUI midi handles: 0, 0
Nov 16 10:24:13 bristol  [1.482248] could not reschedule thread
Nov 16 10:24:13 bristol  [1.482404] registering jack interface: bristol
Nov 16 10:24:13 bristol  [1.483650] Cannot connect to server socket err = No such file or directory
Nov 16 10:24:13 bristol  [1.483723] Cannot connect to server request channel
Nov 16 10:24:13 bristol  [1.486614] exec of JACK server (command = "/usr/bin/jackd") failed: No such file or directory
Nov 16 10:24:14 bristol  [2.486785] Cannot connect to server socket err = No such file or directory
Nov 16 10:24:14 bristol  [2.486859] Cannot connect to server request channel
Nov 16 10:24:15 bristol  [3.489073] Cannot connect to server socket err = No such file or directory
Nov 16 10:24:15 bristol  [3.489143] Cannot connect to server request channel
Nov 16 10:24:16 bristol  [4.491363] Cannot connect to server socket err = No such file or directory
Nov 16 10:24:16 bristol  [4.491437] Cannot connect to server request channel
Nov 16 10:24:17 bristol  [5.493654] Cannot connect to server socket err = No such file or directory
Nov 16 10:24:17 bristol  [5.493728] Cannot connect to server request channel
Nov 16 10:24:18 brighton [6.382065] closing down TCP sockets
Nov 16 10:24:18 brighton [6.382142] unacknowledged request on 0
Nov 16 10:24:18 bristol  [6.495944] Cannot connect to server socket err = No such file or directory
Nov 16 10:24:18 bristol  [6.496017] Cannot connect to server request channel
Nov 16 10:24:19 bristol  [6.734196] failed to receive audio thread OK, exiting

```

May be something wrong with jack? I cant start it too.

```
 sudo jack
This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
 *warning* You have no standard location set, putting files into the current
           directory. Please consider setting base_dir in ~/.jack3rc.
 *error* Access of CD device /dev/cdrom resulted in error: &#1053;&#1086;&#1089;&#1080;&#1090;&#1077;&#1083;&#1100;
         &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;


```

---

### Post by i12 on 2014-11-16
Ah. I tuned it myself. Invoke jack, then invoke startBristol -jack, then in jack communication assign bristol out to system input, start jack play button. Zynaddsubfx sinth - the same.

---

