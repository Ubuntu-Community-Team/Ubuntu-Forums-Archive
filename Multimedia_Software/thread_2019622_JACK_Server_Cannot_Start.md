---
title: "JACK Server Cannot Start"
date: 2012-07-07
forum: Multimedia Software
---

### Post by Gazok on 2012-07-07
Hi,

I've been trying to get JACK to run on a non-rt kernel, but I keep hitting the following errors:

```
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Sat Jul  7 16:04:59 2012: Starting jack server...
Sat Jul  7 16:04:59 2012: JACK server starting in non-realtime mode
Sat Jul  7 16:04:59 2012: control device hw:0
Sat Jul  7 16:04:59 2012: control device hw:0
Sat Jul  7 16:04:59 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory[0m
Sat Jul  7 16:04:59 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
Sat Jul  7 16:04:59 2012: [1m[31mERROR: Cannot initialize driver[0m
Sat Jul  7 16:04:59 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Sat Jul  7 16:04:59 2012: [1m[31mERROR: Failed to open server[0m
Sat Jul  7 16:05:01 2012: Saving settings to "/home/jamie/.config/jack/conf.xml" ...
16:05:01.886 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

I've closed pulseaudio, and fuser /dev/snd/* reports nothing using the hardware device. I'm a member of the audio group, and running with sudo makes no difference.

Does anyone know what the problem might be?

Thanks,
Jamie

---

