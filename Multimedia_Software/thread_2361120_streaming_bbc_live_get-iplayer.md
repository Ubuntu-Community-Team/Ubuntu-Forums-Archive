---
title: "streaming bbc live get-iplayer"
date: 2017-05-12
forum: Multimedia Software
---

### Post by shantiq on 2017-05-12
the original syntax i used a year ago no longer works

```
get_iplayer --stream --type=livetv "BBC Four" --player="mpv -cache 512 -"
```

has it changed or is BBC not longer streamable live this way?

thanx for info

---

### Post by dinkypumpkin on 2017-05-12
Streaming no longer supported. Try [streamlink]("https://streamlink.github.io/") instead.

---

### Post by shantiq on 2017-05-12
thanx dinky works a treat

---

### Post by monkeybrain20122 on 2017-05-12
Does youtube-dl+mpv work? I don't know since I am not in the U.K.

---

### Post by shantiq on 2017-05-13
not for the Beeb streams MonkeyB 

but once you have installed streamlink this does:

```
streamlink -p mpv --best www.bbc.co.uk/iplayer/live/bbcfour
```

altho probably still have to be on a uk ip

---

### Post by ajgreeny on 2017-05-29
A quick update for UK users.

Streamlink works with ITV as well as BBC using command ```
streamlink -p vlc --default-stream best https://www.itv.com/hub/itv
```Just change the final itv in the code to itv2, itv3, itv4 for the separate channels, though at the moment itv2 is failing for some reason; no idea why.
NB: I use vlc not mpv but either will work.

In the same way that Ch4 and Ch5 will not play in a browser plugin, they will not work this way either.

---

