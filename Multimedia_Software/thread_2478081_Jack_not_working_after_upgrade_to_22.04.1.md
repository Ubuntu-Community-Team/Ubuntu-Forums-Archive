---
title: "Jack not working after upgrade to 22.04.1"
date: 2022-08-16
forum: Multimedia Software
---

### Post by sarka9000 on 2022-08-16
So as the title says, after upgrading jack doesn't want to work anymore.

Already tried to purge/remove all config and all jack-related packages and reinstalling them, didn't help. Tried googling around and there were comments about adding audio group permissions and such but so far no luck. 

Whenever I try to start jack through Qjackctl I get these messages:

```
[COLOR=#A0A0A4]14:47:10.246 Statistics reset.[/COLOR][COLOR=#000000][COLOR=#CCCC99]14:47:10.248 ALSA connection change.[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#A0A0A4]14:47:10.253 D-BUS: Service not available (org.jackaudio.service aka jackdbus).[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#A0A0A4]14:47:10.269 JACK is starting...[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#800080]14:47:10.269 /usr/bin/jackd -v -P90 -p1024 -t5000 -m -S -dalsa -r96000 -p512 -n3 -M -Xseq -D -Chw:US16x08,0 -Phw:US16x08,0 -i16 -o8 -I10 -O10[/COLOR][/COLOR]
[COLOR=#000000]Cannot connect to server socket err = No such file or directory[/COLOR]
[COLOR=#000000]Cannot connect to server request channel[/COLOR]
[COLOR=#000000]jack server is not running or cannot be started[/COLOR]
[COLOR=#000000]JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock[/COLOR]
[COLOR=#000000]JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock[/COLOR]
[COLOR=#000000]Cannot connect to server socket err = No such file or directory[/COLOR]
[COLOR=#000000]Cannot connect to server request channel[/COLOR]
[COLOR=#000000]jack server is not running or cannot be started[/COLOR]
[COLOR=#000000]JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock[/COLOR]
[COLOR=#000000]JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock[/COLOR]
[COLOR=#000000]/usr/bin/jackd: symbol lookup error: /usr/bin/jackd: undefined symbol: jackctl_server_create2[/COLOR]
[COLOR=#000000][COLOR=#66CC99]14:47:10.288 ALSA connection graph change.[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#A0A0A4]14:47:10.291 JACK was started with PID=879110.[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#A0A0A4]14:47:10.292 JACK was stopped[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#FF0000]14:47:12.496 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR][/COLOR]
[COLOR=#000000]Cannot connect to server socket err = No such file or directory[/COLOR]
[COLOR=#000000]Cannot connect to server request channel[/COLOR]
[COLOR=#000000]jack server is not running or cannot be started[/COLOR]
[COLOR=#000000]JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock[/COLOR]
[COLOR=#000000]JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock[/COLOR]

```

If I try to run jackd from terminal, I get:

```
jackd: symbol lookup error: jackd: undefined symbol: jackctl_server_create2
```

And with jackdbus:

```
jackdbus: symbol lookup error: jackdbus: undefined symbol: jackctl_server_create2
```


Trying to start jack_control gives:
```
Traceback (most recent call last):
  File "/usr/local/bin/jack_control", line 12, in <module>
    import dbus
ImportError: No module named dbus
```

---

