---
title: "DVB-T recording software for ubuntu"
date: 2018-02-25
forum: Multimedia Software
---

### Post by cazz on 2018-02-25
Hi
Right now I have use ARGUS TV to schedule TV recording from my USB TV Card that have a CA-Modul.
Now I'm curious if that is any good software for ubuntu that can do the same thing for me.

I just want it to recording that channel I have.
Just write a word of a title of a tv show or movie that is going to show on TV and it recording it for me.
It also have to help me with the CA-modul so I can watch all the channel I have.

---

### Post by amino2111 on 2018-02-26
[COLOR=#000E2E][FONT=&amp]https://www.mythtv.org/

TV it's available via apt-get if you add the launchpad repository. To do so:[/FONT][/COLOR]

[LIST]
[*]Execute (ALT+F2):sudo gedit /etc/apt/sources.list
[*]Then add this two lines and save:
deb [http://ppa.launchpad.net/michael-lamothe/ubuntu](http://ppa.launchpad.net/michael-lamothe/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/michael-lamothe/ubuntu](http://ppa.launchpad.net/michael-lamothe/ubuntu) gutsy main
[/LIST]
[COLOR=#000E2E][FONT=&amp]After that, you only need to update the sources and install the program:[/FONT][/COLOR]

[LIST]
[*]sudo apt-get update
[*]sudo apt-get install me-tv
[/LIST]
[COLOR=#000E2E][FONT=&amp]Now, you have Me TV under the menu Applications -> Image and Sound -> Me TV[/FONT][/COLOR]
[CENTER][COLOR=#000E2E][FONT=&amp][[IMG]http://stc.obolog.net/multimedia/fotos/100000/99682/99682-83155_p.jpg[/IMG]]("http://stc.obolog.net/multimedia/fotos/100000/99682/99682-83155.jpg")[/FONT][/COLOR][/CENTER]
[COLOR=#000E2E][FONT=&amp]Requirements:[/FONT][/COLOR]

[LIST]
[*]If you want your tv card working on a Linux box, ensure you are using the latest kernel. Ubuntu 8 is a good choice, or you can try also Linux MCE.
[*]Not all the hardware is supported. [Check yours]("http://www.linuxtv.org/wiki/index.php/DVB-T_Devices"). I bought a Pinnacle PC DVB-T that I had to refund back because didn't work. Now I have a Hauppauge WinTV NOVA-T that works like a charm
[*]Install **lirc** (sudo apt-get install lirc) for remote control support
[/LIST]
[COLOR=#000000]finally visit my website to download softwares for windows: [https://www.topvoce.com](https://www.topvoce.com)[/COLOR]

---

### Post by deadflowr on 2018-02-26
Mythtv or tvheadend come to mind.
Those two you can set up an always on backend server that you can then connect to from any frontend enabled device.
Mythtv has it's own frontend while tvheadend relies on any number (from what i remember about tvheadend) most notably it works well with kodi as the frontend.

Both have various methods of grabbing the EPG data of your local schedules.
Which then you can access through either the frontend or usually a local browser webpage (much in the same way you can access the cups page through a browser)
Both accessing through the frontend or webpage should allow you to search and set recordings up.

Of course all that would be moot without knowing if the ca-modul usb tv tuner card is linux compatible.
Do you know what the card model is?

---

### Post by cazz on 2018-02-26
Thanks for the replay
Is a TBS 5880 and I have the Swedish "boxer"

---

### Post by deadflowr on 2018-02-26
> **amino2111 said:**
> 
[LIST]
[*]Execute (ALT+F2):sudo gedit /etc/apt/sources.list
[*]Then add this two lines and save:
deb [http://ppa.launchpad.net/michael-lamothe/ubuntu](http://ppa.launchpad.net/michael-lamothe/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/michael-lamothe/ubuntu](http://ppa.launchpad.net/michael-lamothe/ubuntu) gutsy main
[/LIST]
[COLOR=#000E2E][FONT="]After that, you only need to update the sources and install the program:[/FONT][/COLOR]

No, do not add ppa's from 10 year old releases.
me-tv is already in the repos and newer then what you would get from the gutsy ppa.

Otherwise, yes. me-tv not a bad option either.
But it's a combo frontend/backend so run one means run both.
So it requires to always be running as a whole, rather then having an isolated backend to do the dirty work.

Same goes for other programs like kaffeine, also in the repos.
(I think smplayer also supports tv tuners, and so does vlc, for what it's worth)

Here's the fun of getting your card to work:
[https://www.linuxtv.org/wiki/index.php/TBS_driver_installation]("https://www.linuxtv.org/wiki/index.php/TBS_driver_installation")

Good luck
Hope this gets you a nice starting point of ways to get what you want.

---

### Post by cazz on 2018-02-26
Thanks

---

