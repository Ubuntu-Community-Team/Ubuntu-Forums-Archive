---
title: "Yamaha S-08 Usb Midi ?"
date: 2006-04-07
forum: Multimedia &amp; Video
---

### Post by vyruss on 2006-04-07
Hi there, is there any way to use my S-08 with the USB MIDI port? That's the way I used it when I had Windows, because I no longer have a proper MIDI interface. 

Please make my day! ;)

Cheers
Jimmy

---

### Post by christhemonkey on 2006-04-07
do you have the snd-usb-audio module loaded?
To find out if it is:
```
lsmod | grep snd
```
and there should be a line with snd-usb-audio.
if not:
```
sudo modprobe snd-usb-audio
```

Though i am unsure whether this is all you need to do!

---

### Post by dolson on 2006-04-07
Plug it in and turn it on, and then run dmesg and see if there is any output. Paste it here, and we might be able to tell you if it should/could work or not.

As I understand it, most compliant USB MIDI devices are supposed to work, but not all do. That's what I was told anyhow, when I discovered my E-MU Xboard49 worked.

---

### Post by vyruss on 2006-07-11
> **dolson said:**
> Plug it in and turn it on, and then run dmesg and see if there is any output. Paste it here, and we might be able to tell you if it should/could work or not.

As I understand it, most compliant USB MIDI devices are supposed to work, but not all do. That's what I was told anyhow, when I discovered my E-MU Xboard49 worked.

I know this is an old thread, but I've just tried doing this. The results:

**dmesg:**```
Jul 11 22:58:53 gremlin kernel: [17216665.876000] usb 2-2: new full speed USB device using uhci_hcd and address 3
```**lsusb:**```
Bus 002 Device 003: ID 0499:100e Yamaha Corp.
```

---

### Post by christhemonkey on 2006-07-11
Did you try the lsmod | grep snd ?

Also, what is the result of typing:
```
aplaymidi -l

```

---

### Post by vyruss on 2006-07-11
(deleted)

---

### Post by vyruss on 2006-07-11
OK, that was silly of me. Results after loading the **snd-seq module** (which I hadn't):```
vyruss@gremlin:~$ **lsmod | grep snd**
snd_rtctimer            3660  1
snd_seq_dummy           4164  1
snd_seq_oss            37632  0
snd_seq_midi            9888  2
snd_seq_midi_event      8064  2 snd_seq_oss,snd_seq_midi
snd_seq                58832  12 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_usb_audio          83520  3
snd_pcm_oss            56352  0
snd_mixer_oss          20800  2 snd_pcm_oss
snd_pcm                96772  2 snd_usb_audio,snd_pcm_oss
snd_timer              27204  3 snd_rtctimer,snd_seq,snd_pcm
snd_page_alloc         11592  1 snd_pcm
snd_usb_lib            18432  1 snd_usb_audio
snd_hwdep              10272  1 snd_usb_audio
snd_mpu401              7112  0
snd_mpu401_uart         8896  1 snd_mpu401
snd_rawmidi            27552  3 snd_seq_midi,snd_usb_lib,snd_mpu401_uart
snd_seq_device          9548  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    60068  15 snd_seq_oss,snd_seq,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              11040  1 snd
usbcore               138948  8 hci_usb,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd

```**aplaymidi -l:**```
vyruss@gremlin:~$ **aplaymidi -l**
 Port    Client name                      Port name
 62:0    Midi Through                     Midi Through Port-0
 72:0    MPU-401 UART MIDI                MPU-401 UART MIDI
 80:0    S08                              S08 MIDI 1
 80:1    S08                              S08 MIDI 2
```

---

### Post by christhemonkey on 2006-07-11
Well its their, so just try:
```
aplaymidi -p=80:0 /path/to/a/midi/file/file.mid 
```

Obviously replacing /path/to/a/midi/file/file.mid with a real midi file and path.

---

### Post by vyruss on 2006-07-12
> **christhemonkey said:**
> Well its their, so just try:
```
aplaymidi -p=80:0 /path/to/a/midi/file/file.mid 
```

Obviously replacing /path/to/a/midi/file/file.mid with a real midi file and path.

Well, it worked... sorta.

I played 2 midi files OK, on the third I got a hard system lockup.

Also the system locks up completely when I try to load rosegarden.

This doesn't look good, does it? Could it be usb-related?

---

