---
title: "Using pulseaudio with netcat"
date: 2010-05-05
forum: Multimedia Software
---

### Post by rorestuff on 2010-05-05
Hi,
I have a remote server without a sound card or speakers and I want all the server's audio to be redirected to a simple client.
I'm trying to set up pulseaudio to this, but I've had no luck so far.
The server doesn't have speakers or a sound card, so I cleared out the default.pa file and started pulseaudio: ```
pulseaudio -L "module-simple-protocol-tcp port=4712 rate=44100 format=s16le channels=2" 
```

Then I try to play a file on the remote server with mplayer -ao pulse, but get the error: Could not open/initialize audio device -> no sound.


I've googled around for a while but haven't figured out how to get mplayer to connect to  pulse.

I basically followed[ this blog]("http://gleamynode.net/articles/2228/") to get where I have, but couldn't any further.

Any insight would be greatly appreciated!

Thanks

---

