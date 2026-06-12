---
title: "How to stop Pulseaudio from resampling for bit perfect playback"
date: 2014-07-02
forum: Multimedia Software
---

### Post by reddeadresolve2 on 2014-07-02
Hey I need help stopping PulseAudio from resampling my audio. My DAC is capable of 44100, 48000, 88200, 96000 playback. How can I set pulse to give me the best possible audio? 

Using Xubuntu 14.04 with a Schiit Modi DAC, DAC is 100% Ubuntu/Linux compatible. 

```
Schiit Schiit USB Audio Device at usb-0000:06:01.2-4, high speed : USB Audio

Playback:
  Status: Stop
  Interface 1
    Altset 1
    Format: S16_LE
    Channels: 2
    Endpoint: 5 OUT (ASYNC)
    Rates: 44100, 48000, 88200, 96000
    Data packet interval: 1000 us
  Interface 1
    Altset 2
    Format: S24_3LE
    Channels: 2
    Endpoint: 5 OUT (ASYNC)
    Rates: 44100, 48000, 88200, 96000
    Data packet interval: 1000 us


```

---

### Post by Yellow Pasque on 2014-07-02
Pulseaudio uses the settings in /etc/pulse/daemon.conf
```
gksu gedit /etc/pulse/daemon.conf
```

Try enabling the following option by removing the semicolon in front:
```
; alternate-sample-rate=48000
```
Save. Quit. Log out (or kill pulseaudio to make it restart).

[http://arunraghavan.net/2011/10/alternate-sample-rates/](http://arunraghavan.net/2011/10/alternate-sample-rates/)

---

### Post by reddeadresolve2 on 2014-07-02
> **Temüjin said:**
> Pulseaudio uses the settings in /etc/pulse/daemon.conf
```
gksu gedit /etc/pulse/daemon.conf
```

Try enabling the following option by removing the semicolon in front:
```
; alternate-sample-rate=48000
```
Save. Quit. Log out (or kill pulseaudio to make it restart).

[http://arunraghavan.net/2011/10/alternate-sample-rates/](http://arunraghavan.net/2011/10/alternate-sample-rates/)

Thanks for the info, seems like bit perfect playback with Pulse is getting better, but it still leaves my 96000 streams being down sampled.

---

### Post by Yellow Pasque on 2014-07-03
If you change it to "alternate-sample-rate=96000" then it should use 96 kHz (assuming no other streams are using pulseaudio at that time)

---

