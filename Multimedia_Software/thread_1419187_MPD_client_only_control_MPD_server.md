---
title: "MPD client only control MPD server"
date: 2010-03-01
forum: Multimedia Software
---

### Post by yocec on 2010-03-01
I'me currently try to configure MPD and I have a doubt.

MPD clients (sonata et co) are only used to control MDP ?
They don't play the music ?

is it :

```
Server  <---- order ---- Client
MPD                      Sonata
= MUSIC
```

or      
  
```
Server  <---- order ---- Client
MPD     ---- stream ---> Sonata
                         = MUSIC
```



Thanks
Yoann


PS : I want the second choice (music stored on server, played on client)

---

### Post by denarced on 2010-04-21
> **yocec said:**
> I'me currently try to configure MPD and I have a doubt.

MPD clients (sonata et co) are only used to control MDP ?
They don't play the music ?

is it :

```
Server  <---- order ---- Client
MPD                      Sonata
= MUSIC
```

or      
  
```
Server  <---- order ---- Client
MPD     ---- stream ---> Sonata
                         = MUSIC
```



Thanks
Yoann


PS : I want the second choice (music stored on server, played on client)

The client controls the server and the server plays the music. If one would want it the other way, a simple file-sharing would do the trick.

---

