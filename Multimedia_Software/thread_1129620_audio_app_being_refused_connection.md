---
title: "audio app being refused connection"
date: 2009-04-18
forum: Multimedia Software
---

### Post by Richard-g8jvm on 2009-04-18
Sorry Guys I have cross posted this on the X64 forum as well

 audio device connection refused
I have pulseaudio disabled as I have multiple sound cards.
I'm using an application which is dependent on portaudio, mainly running python scripts.Easiest to show the example of whats happening:-

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

Audio Input Output Device Name
Device Channels Channels
------------------------------------------------------------------
0 12 10 M Audio Delta 66: ICE1712 multi (hw:0,0)
1 2 8 PnP Audio Device : USB Audio (hw:1,0)
2 0 10 front
3 0 10 surround40
4 0 10 surround51
5 0 128 iec958
6 128 128 spdif
7 128 128 default
8 0 10 dmix
9 16 16 /dev/dsp
10 16 2 /dev/dsp1

User requested devices: Input = 0 Output = 0
Default devices: Input = 7 Output = 7
Will open devices: Input = 7 Output = 7
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)



Other audio apps run OK, I've run the app as root and the same happens.
Anyone any idea as to why the ALSA backend would be refusing connection

I'm running ubuntu9.04 amd64

TIA

Richard
Richard-g8jvm is online now Report Post   	Edit/Delete Message

---

### Post by markbuntu on 2009-04-19
bluetooth is not so easy. Alsa will refuse the connection if bluetooth is not paired first. Also, it would be a good idea to have the latest bluez.

btw, I have multiple sound cards and I could never get them to work without pulseaudio.

---

### Post by delcypher on 2009-11-02
I believe this is to do with bluetooth being enabled in ALSA's configuration but the module isn't actually loaded [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/423410]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/423410")

Apparently you can try fixing it by running (WARNING I HAVEN'T TRIED THIS):
```
sudo apt-get purge bluez-alsa
```

However I just modified the configuration file myself and restarted ALSA.

I fixed this by editing /usr/share/alsa/alsa.conf and then by commenting the bluetooth line like so
```

#
#  ALSA library configuration file
#

# pre-load the configuration files

@hooks [
        {
                func load
                files [
                        "/usr/share/alsa/pulse.conf"
#COMMENT-OUT            "/usr/share/alsa/bluetooth.conf"
                        "/etc/asound.conf"
                        "~/.asoundrc"
                ]
                errors false
        }
]

```

and then by running
```
sudo /etc/init.d/alsa-utils reset
```

---

