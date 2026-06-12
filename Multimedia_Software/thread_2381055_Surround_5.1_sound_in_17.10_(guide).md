---
title: "Surround 5.1 sound in 17.10 (guide)"
date: 2017-12-26
forum: Multimedia Software
---

### Post by User-007 on 2017-12-26
Hi,

I found that instructions [here]("https://ubuntuforums.org/showthread.php?t=1608804&page=11") and thus [here]("https://help.ubuntu.com/community/DigitalAC-3Pulseaudio") are outdated since they totally broke my 17.10 system. After complete reinstallation, found that the process to get the surround sound working is in fact simplier.

So what I did:
```
sudo apt-get install libasound2-plugins-extra
```
```
sudo nano ~/.asoundrc
```

Copied following text there:```
pcm.a52 {
  @args [CARD]
  @args.CARD {
    type string
  }
  type rate
  slave {
    pcm {
      type a52
      bitrate 448
      channels 6
      card $CARD
    }
    rate 48000
  }
}

```

```
sudo nano /etc/pulse/daemon.conf
```

Then added a line ```
default-sample-rate = 48000
``` under the line ```
; default-sample-rate = 44100
```
 
And finally, after running ```
pulseaudio -k
``` the surround option is available in pavucontrol. And after selecting it, the surround is working properly in Google Chrome, VLC, Kaffeine, Totem...

---

