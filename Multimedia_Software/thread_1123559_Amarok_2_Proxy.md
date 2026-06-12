---
title: "Amarok 2 Proxy"
date: 2009-04-12
forum: Multimedia Software
---

### Post by anuvratSingh on 2009-04-12
Hi, I am using Jaunty and Amarok 2. The problem is that I am behind a proxy server and my Amarok fails to detect the proxy. As a result, the radio and lyrics fetching are not working. Is there any fix for it?

---

### Post by themusicalduck on 2009-04-12
If you go to settings > configure amarok > engine. There is a space to enter proxy details for streaming which should fix your radio problems. Not sure if it'll help lyrics fetching though.

---

### Post by anuvratSingh on 2009-04-12
Nopes, there is no engine option in the configure window. The only options I can see are General, Collection, Internet Services, PLayback and OSD. Also the internet services only has stuffs like ampache service, podcast service, etc. But no option to enter the proxy.
[IMG]http://farm4.static.flickr.com/3300/3436313475_c8d7c5af2a_o.png[/IMG]

---

### Post by themusicalduck on 2009-04-13
That's strange.. my version has at least 3 more option tabs in configuration than yours. Do you have the newest version? Although I am using gnome whereas it looks like you use KDE which might make a difference, but someone else'll have to clarify on that.

---

### Post by anuvratSingh on 2009-04-13
I am using Amarok 2.0.2, which is the latest I get on the repositories of ubuntu. Also I am in gnome. Amarok uses kde libs, does it not. It shows Using KDE 4.2.2 in th about Amarok section.

---

### Post by anuvratSingh on 2009-04-13
Well, as it turns out, the proxy is probably being detected bacause Amarok displays artist info from wiki and also the lyrics. But the last.fm radio and scrobbler do not work.

---

### Post by anuvratSingh on 2009-04-17
Its done ... I installed the Amarok 2.1 and last.fm scrobbling is working now :)

---

