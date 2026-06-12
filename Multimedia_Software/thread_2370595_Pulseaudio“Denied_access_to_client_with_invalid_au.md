---
title: "Pulseaudio:“Denied access to client with invalid authentication data”"
date: 2017-09-05
forum: Multimedia Software
---

### Post by tringler on 2017-09-05
Hello,

I know this an Ubuntu forum and not a raspbian forum, but that topic is not directly related to RPi and Raspbian.
I'm running Debian Stretch on a RPi 3 and to play audio via my bluetotth box without any luck. This is basically what I did:


["]https://github.com/davidedg/NAS-mod-config/blob/master/bt-sound/bt-sound-Bluez5_PulseAudio5.txt]("https://github.com/davidedg/NAS-mod-config/blob/master/bt-sound/bt-sound-Bluez5_PulseAudio5.txt)


My bluetooth box is connected, but I don't get any audio output, because of this error:


    ```

&#9679; pulseaudio.service - Pulse Audio
       Loaded: loaded (/etc/systemd/system/pulseaudio.service; enabled; vendor preset: enabled)
       Active: active (running) since Tue 2017-09-05 00:23:34 CEST; 19min ago
     Main PID: 336 (pulseaudio)
       CGroup: /system.slice/pulseaudio.service
               &#9492;&#9472;336 /usr/bin/pulseaudio --system --disallow-exit --disable-shm --exit-idle-time=-1
    
    Sep 05 00:41:52 raspberrypi pulseaudio[336]: W: [pulseaudio] protocol-native.c: Denied access to client with invalid authentication data.
    Sep 05 00:42:05 raspberrypi pulseaudio[336]: W: [pulseaudio] protocol-native.c: Denied access to client with invalid authentication data.
    Sep 05 00:42:18 raspberrypi pulseaudio[336]: W: [pulseaudio] protocol-native.c: Denied access to client with invalid authentication data.
    Sep 05 00:42:22 raspberrypi pulseaudio[336]: W: [pulseaudio] protocol-native.c: Denied access to client with invalid authentication data.
    Sep 05 00:42:25 raspberrypi pulseaudio[336]: W: [pulseaudio] protocol-native.c: Denied access to client with invalid authentication data.
    Sep 05 00:42:38 raspberrypi pulseaudio[336]: W: [pulseaudio] protocol-native.c: Denied access to client with invalid authentication data.
    Sep 05 00:42:52 raspberrypi pulseaudio[336]: W: [pulseaudio] protocol-native.c: Denied access to client with invalid authentication data.
    Sep 05 00:43:05 raspberrypi pulseaudio[336]: W: [pulseaudio] protocol-native.c: Denied access to client with invalid authentication data.
    Sep 05 00:43:08 raspberrypi pulseaudio[336]: W: [pulseaudio] protocol-native.c: Denied access to client with invalid authentication data.
    Sep 05 00:43:21 raspberrypi pulseaudio[336]: W: [pulseaudio] protocol-native.c: Denied access to client with invalid authentication data.
```


What I tried to solve it:


The users (root, pi and mopidy) are in the groups pulse, pulse-access and audio


Added that line to system.pa load-module module-native-protocol-unix auth-anonymous=1 socket=/tmp/my-pulse-socket-name and added the file ~/.config/pulse/client.conf with that content default-server = unix:/tmp/my-pulse-socket-name


Any hints?


Thanks in Advance!

PA Config: 
system.pa: [https://gist.github.com/tringler/c3935577cf00c333e072ee17c99b0f5f](https://gist.github.com/tringler/c3935577cf00c333e072ee17c99b0f5f)
default.pa: [https://gist.github.com/tringler/2fce9b1bfc92c5d114f26c32bd8a5255](https://gist.github.com/tringler/2fce9b1bfc92c5d114f26c32bd8a5255)
daemon.conf: [https://gist.github.com/tringler/dff6f4ec9e2fd5614f315f3d44b38a2b](https://gist.github.com/tringler/dff6f4ec9e2fd5614f315f3d44b38a2b)
client.conf: [https://gist.github.com/tringler/fae77ddaa1ae69a70078663c7f88edaf](https://gist.github.com/tringler/fae77ddaa1ae69a70078663c7f88edaf)

PulseAudio Log: [https://gist.github.com/tringler/f88b227e99624ad990b836dda9de5507](https://gist.github.com/tringler/f88b227e99624ad990b836dda9de5507)

---

### Post by ddombrowsky on 2018-03-22
I have seen this problem when I have X11 forwarding on and I've set up pulse audio to forward through a tunneled port, and authenticate using ~/.config/pulse/cookie.  THis doesn't work

```

$ paplay test.wav
Connection failure: Access denied

```

But this does:

```

DISPLAY= paplay test.wav

```

So something in the X11 auth is messing it up.  Unsetting the DISPLAY environment variable was good enough for me.

---

