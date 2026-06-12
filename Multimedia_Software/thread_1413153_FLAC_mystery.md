---
title: "FLAC mystery"
date: 2010-02-22
forum: Multimedia Software
---

### Post by nnjond on 2010-02-22
Hi,

I hope someone can help me? I've dled some CDs. Each one is a single FLAC wich i can play, But surely i should be able to access individual pieces recorded on the CDs? I know I'm missing something here.

---

### Post by hallu on 2010-02-22
you can split it with

```
shnsplit -f *.cue -t "%n %t" -o flac *.flac && cuetag *.cue [0-9]*.flac &&  metaflac --add-replay-gain [0-9]*.flac
```

---

