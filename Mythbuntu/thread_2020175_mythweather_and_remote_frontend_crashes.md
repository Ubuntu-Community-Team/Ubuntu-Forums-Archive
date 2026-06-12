---
title: "mythweather and remote frontend crashes"
date: 2012-07-07
forum: Mythbuntu
---

### Post by jim09 on 2012-07-07
mythweather seems to work fine on front end / backend but when you
try from a remote front end you get a frame without any weather data.  I assume that I should not have to configure it on the remote front end.  If I try,  the remote front end crashes.

Jul  7 21:19:33 jim-mythbuntu-remote kernel: [  281.578375] mythfrontend.re[1414]: segfault at 8 ip a5c81bdb sp bfb432f0 error 4 in libmythweather.so[a5c68000+43000]
-----------------------------------------------------------
Jul  7 21:32:46 jim-mythbuntu-remote kernel: [ 1074.906475] mythfrontend.re[2148]: segfault at 5f ip a33c1bdb sp bfa2da30 error 4 in libmythweather.so[a33a8000+43000]

Works ok in 10.10

---

### Post by crbnrod on 2012-07-08
afaik mythweather is a FE addon and does not interact w/the backend, so you would need to configure it on every FE you wish to use it on.

You might try uninstalling & reinstalling the plugin from the MCC and then configuring it from the setup menu in the FE.

---

### Post by anonymousdog on 2012-07-08
If any of your FE are stable with MythWeather installed, you're doing better than me.  On all five of my FE, MythWeather, when displayed, immediately crashes the FE and randomly crashes it when polling for new data (in the background).

---

### Post by jim09 on 2012-07-08
I did a remove and install from the mcc.  No luck.  Did and install and remove using apt and same result.

---

### Post by jim09 on 2012-07-08
It helps if you configure it first on each remote front end.  Thanks crbnrod for the clarification.  I dont know how I missed that.

---

