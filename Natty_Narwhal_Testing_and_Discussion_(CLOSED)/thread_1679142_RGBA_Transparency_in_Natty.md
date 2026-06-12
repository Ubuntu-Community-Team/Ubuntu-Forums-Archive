---
title: "RGBA Transparency in Natty"
date: 2011-01-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2011-01-31
I found this great tutorial on webup8 on RGBA Transparency. Have any of you guys tried it? Will it work as it is stated on blog or does it need modifications for Natty.

Thanks.

[http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html]("http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html")

---

### Post by snkiz on 2011-01-31
Works in Mavrick, I haven't bothered to do it with natty yet. But I don't see why it wouldn't work, its just a gtk module without any extra dependencies. Easily removed if need be, give it a shot.

---

### Post by Starks on 2011-01-31
As far as I know, implementing RGBA and client-side decorations is a forgotten endeavor.

---

### Post by Merk42 on 2011-01-31
> **Starks said:**
> As far as I know, implementing RGBA and client-side decorations is a forgotten endeavor.What are you talking about? I...
[quote=Web UPD8's article]RGBA transparency has been confirmed to be included in Ubuntu 10.10 Maverick Meerkat by Mark Shuttleworth at UDS-M[/quote]
...oh

---

### Post by snkiz on 2011-01-31
It mostly works, only a few apps really choke on it. Truth is using natty without transparency has been refreshing. I didn't realize I was getting tired of til I spent some time without it. I think that since it never really left beta applications are not setup to take advantage of it in meaningful ways. (The notable exceptions would be *-terminal,  *-panel that sort of thing.)  Because of that when you do run gtk transparency it tends to to look out of place. I wouldn't say development has stopped on it , Nattys grip-able shadows are proof of that. More like they are just trying yo find more useful ways to use transparency than eye candy. I expect when development of wayland ramps up we'll see some movement on this since that's exactly the kind of thing wayland promises to do well.

---

