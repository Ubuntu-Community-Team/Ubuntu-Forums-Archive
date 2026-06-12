---
title: "Spanish translation problem in mythfrontend"
date: 2011-04-11
forum: Mythbuntu
---

### Post by mtbdescender on 2011-04-11
I'm testing ubuntu 11.04 64 bits and I have a translation problem in mythfrontend. 

Mythfrontend shows some labels in English and some labels in Spanish. Seems like mythvideo load spanish traslations, but base mythfrontend not.

Logs of mythfrontend :

```

...
2011-04-11 21:48:22.664 Connected to database 'mythconverg' at host: 192.168.2.2
2011-04-11 21:48:22.670 Current locale es_ES
2011-04-11 21:48:22.670 No locale defaults file for es_ES, skipping
2011-04-11 21:48:22.811 ScreenSaverX11Private: Gnome screen saver support enabled
2011-04-11 21:48:22.813 DPMS is active.
2011-04-11 21:48:22.859 Desktop video mode: 1440x900 60.002 Hz
2011-04-11 21:48:22.933 Enabled verbose msgs:  important general
2011-04-11 21:48:22.990 Loading es translation for module mythfrontend
...
2011-04-11 21:48:25.041 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-11 21:48:25.046 Loading es translation for module mythvideo
...

```I make a standard Spanish (Spain) installation. My LANG is 'es_ES.UTF8'.

Someone can help ?

---

### Post by agamotto on 2011-04-14
Perhaps you forgot to set the language in the backend setup to Espanol?

---

### Post by mtbdescender on 2011-04-25
> **agamotto said:**
> Perhaps you forgot to set the language in the backend setup to Espanol?

I only found language configuracion in the frontend setup, and is set to Español;Castellano. In the backend setup I configure channels, tuners, etc.. but I don't find language configuration, only region for frequencies.

---

### Post by comtranslations1 on 2011-09-28
I think that its better to start backend setup to Espanol.
[URL="http://comtranslations.com/"]
Traducir español inglés[/URL] | [Spanish to English translation]("http://comtranslations.com/") | [English Spanish translation]("http://comtranslations.com/")

---

