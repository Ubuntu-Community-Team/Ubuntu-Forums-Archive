---
title: "Jack"
date: 2010-05-06
forum: Multimedia Software
---

### Post by Jordii on 2010-05-06
I can't get Jack to work, when I hit start, a window appears:

Could not connect to JACK server as client.
 - Overall operation failed.
 - Unable to connect to server.
 Please check the messages window for more info.


> 
[COLOR=#999999]16:26:14.405 Patchbay deactivated.[/COLOR]

[COLOR=#999999]16:26:14.521 Statistics reset.[/COLOR]

[COLOR=#66cc99]16:26:14.655 ALSA connection graph change.[/COLOR]

[COLOR=#cccc99]16:26:15.047 ALSA connection change.[/COLOR]

[COLOR=#999999]16:26:24.219 Startup script...[/COLOR]

[COLOR=#990099]16:26:24.219 artsshell -q terminate[/COLOR]

sh: artsshell: not found

[COLOR=#999999]16:26:24.635 Startup script terminated with exit status=32512.[/COLOR]

[COLOR=#999999]16:26:24.650 JACK is starting...[/COLOR]

[COLOR=#990099]16:26:24.651 /usr/bin/jackd -R -p128 -dalsa -r48000 -p64 -n2 -D -Chw:0,2 -Phw:0,1 -S[/COLOR]

[COLOR=#999999]16:26:24.688 JACK was started with PID=8041.[/COLOR]

[COLOR=#ff0000]16:26:24.693 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

no message buffer overruns

jackd 0.116.1

Copyright 2001-2005 Paul Davis and others.

jackd comes with ABSOLUTELY NO WARRANTY

This is free software, and you are welcome to redistribute it

under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.

cannot use real-time scheduling (FIFO at priority 10) [for thread -1216641344, from thread -1216641344] (1: Operation not permitted)

cannot create engine

[COLOR=#999999]16:26:25.765 JACK was stopped successfully.[/COLOR]

[COLOR=#999999]16:26:25.765 Post-shutdown script...[/COLOR]

[COLOR=#990099]16:26:25.766 killall jackd[/COLOR]

jackd: no process found

[COLOR=#999999]16:26:26.198 Post-shutdown script terminated with exit status=256.[/COLOR]

Hopefully someone can help.

---

### Post by cchhrriiss121212 on 2010-05-06
> cannot use real-time scheduling (FIFO at priority 10)
Here's the problem. You need to edit the limits.conf file found in /etc/security. See [this]("https://help.ubuntu.com/community/UbuntuStudioPreparation") for details.
This is the relevant part:
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'
sudo adduser <username> audio

---

### Post by Jordii on 2010-05-06
Edit: I logged in & out, now i get this:
>   [COLOR=#999999]18:30:11.899 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]18:30:11.900 Statistics reset.[/COLOR]
 [COLOR=#66cc99]18:30:11.972 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]18:30:12.167 ALSA connection change.[/COLOR]
 [COLOR=#999999]18:30:14.820 Startup script...[/COLOR]
 [COLOR=#990099]18:30:14.821 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]18:30:15.235 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]18:30:15.236 JACK is starting...[/COLOR]
 [COLOR=#990099]18:30:15.236 /usr/bin/jackd -R -p128 -dalsa -dhw:0 -r48000 -p64 -n2 -D -Chw:0 -S[/COLOR]
 [COLOR=#999999]18:30:15.244 JACK was started with PID=26478.[/COLOR]
 [COLOR=#ff0000]18:30:15.386 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 48000
 creating alsa driver ... hw:0,0|hw:0,6|64|2|48000|0|0|nomon|swmeter|-|16bit
 control device hw:0
 [COLOR=#999999]18:30:19.680 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]18:30:19.796 Post-shutdown script...[/COLOR]
 [COLOR=#990099]18:30:19.797 killall jackd[/COLOR]
 [COLOR=#cc3366]18:30:19.805 JACK has crashed.[/COLOR]
 jackd: no process found
 [COLOR=#999999]18:30:20.736 Post-shutdown script terminated with exit status=256.[/COLOR]


---

### Post by Jordii on 2010-05-06
bump

---

### Post by cchhrriiss121212 on 2010-05-06
There's no need to bump after an hour, you should generally give it 24 hours. Your settings seem to indicate that you are setting different input and output devices, so try changing them to default.

---

### Post by Jordii on 2010-05-06
> **cchhrriiss121212 said:**
> There's no need to bump after an hour, you should generally give it 24 hours. Your settings seem to indicate that you are setting different input and output devices, so try changing them to default.

Nothing changed, thanks for your help though. I'll try this further after this weekend.

---

### Post by Jordii on 2010-05-11
Doublepost.

---

### Post by Jordii on 2010-05-11
Do I have to change something about the setup?
The current message:
>  
 [COLOR=#999999]13:33:06.469 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]13:33:06.513 Statistics reset.[/COLOR]
 [COLOR=#66cc99]13:33:06.560 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]13:33:06.841 ALSA connection change.[/COLOR]
 [COLOR=#999999]13:33:09.262 Startup script...[/COLOR]
 [COLOR=#990099]13:33:09.262 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]13:33:09.665 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]13:33:09.666 JACK is starting...[/COLOR]
 [COLOR=#990099]13:33:09.666 /usr/bin/jackd -R -p128 -dalsa -dhw:0 -r48000 -p64 -n2 -S[/COLOR]
 [COLOR=#999999]13:33:09.677 JACK was started with PID=3668.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 `default' server already active
 [COLOR=#999999]13:33:09.845 JACK was stopped with exit status=1.[/COLOR]
 [COLOR=#999999]13:33:09.846 Post-shutdown script...[/COLOR]
 [COLOR=#990099]13:33:09.846 killall jackd[/COLOR]
 [COLOR=#ff0000]13:33:09.861 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#999999]13:33:11.866 Post-shutdown script terminated successfully.[/COLOR]


---

### Post by cchhrriiss121212 on 2010-05-12
Possibly, but you should make sure that you are not using any other audio programs when you start jack, that means firefox or anything else that uses sound.
If that is OK, then I would try unchecking the realtime box in setup.

---

