---
title: "Could not connect to JACK server"
date: 2008-07-03
forum: Multimedia Software
---

### Post by Aesmodeus on 2008-07-03
Hi, when i try to start jack audio connection kit it gives me this error - Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info

21:27:05.181 JACK is starting...
21:27:05.183 /usr/bin/jackd -R -dalsa -dhw:0,0 -r44100 -p256 -n2 -m
21:27:05.199 JACK was started with PID=6061.
could not open driver .so '/usr/lib/jack/jack_freebob.so': /usr/lib/jack/jack_freebob.so: undefined symbol: jack_midi_get_event_count
could not open driver .so '/usr/lib/jack/jack_alsa.so': /usr/lib/jack/jack_alsa.so: undefined symbol: jack_midi_get_event_count
jackd: unknown driver 'alsa'
21:27:05.220 JACK was stopped with exit status=1.
21:27:05.226 Post-shutdown script...
21:27:05.227 killall jackd
jackd: no process killed
21:27:05.664 Post-shutdown script terminated with exit status=256.

Can anybody help? :confused:

---

### Post by Aesmodeus on 2008-07-05
no ideas??

---

### Post by Aesmodeus on 2008-07-08
](*,)

---

### Post by GurktheBurp on 2008-08-03
Hey,
I tried going Settings>Configure Rosegarden, under Audio in the Jack Startup tab ticking the 'Start JACK When Rosegarden Starts box and changing the command to: /usr/bin/qjackctl -- s
Hope this works for you.
James.

---

