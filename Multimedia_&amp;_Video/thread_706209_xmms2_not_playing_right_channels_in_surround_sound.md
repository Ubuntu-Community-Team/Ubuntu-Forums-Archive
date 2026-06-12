---
title: "xmms2 not playing right channels in surround sound"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by tszanon on 2008-02-24
Back when I used xmms1, I set up my .asoundrc file in order to use all 6 sound channels when playing songs, like this:
```
pcm.ch51dup {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
}
```
Now I'm using xmms2. I've set it to use the device ch51dup:
```
xmms2 config alsa.device ch51dup
```
After I did this, xmms2 started using only 4 of the 6 channels, because the front-right and surround-right channels are not being used. I'm pretty sure it's not a hardware problem - if I use speaker-test, everything is fine; if I use the default device in xmms2, the front channels work fine. The numbers in .asoundrc seem to be correct, based on this output from speaker-test:
```
$ speaker-test -c 6 -D surround51

speaker-test 1.0.14

Dispositivo de reprodução é surround51
Parâmetros do stream são 48000Hz, S16_LE, 6 canais
Usando 16 oitavas de ruído rosa
Taxa alterada para 48000Hz (requisitada 48000Hz)
Tamanho do buffer tem um intervalo de 3 à 5461
Tamanho do período tem um intervalo de 3 à 5461
Usando tamanho máximo de buffer 5460
Períodos = 4
period_size definido = 1365
buffer_size definido = 5460
 0 - Da Esquerda [COLOR="Red"](left)[/COLOR]
 4 - Centro [COLOR="Red"](center)[/COLOR]
 1 - Da Direita [COLOR="Red"](right)[/COLOR]
 3 - Direita Posterior [COLOR="Red"](surround-right)[/COLOR]
 2 - Esquerda Posterior [COLOR="Red"](surround-left)[/COLOR]
 5 - LFE
```
Has anyone faced something similar? Maybe it's a xmms2 bug?

---

### Post by tszanon on 2008-02-25
Oh well...24h bump.

---

### Post by tszanon on 2008-02-26
Maybe someone has successfully configured alsa in gutsy to use 6 channels when playing mp3 files...it would help to verify if those things I did are correct.

Or maybe someone has already tried doing this same thing in xmms2 and succeeded. It would help a lot if I knew exactly what was done.

Oh well, 48h bump.

Edit:
maybe it's important: I tried using the device surround51 instead of ch51dup. I know, it would not give me the desired result, but I tried anyway. The interesting thing I found out is that the right channel was muted again. It seems that xmms2 has problems when handling 6-channel devices...

---

### Post by tszanon on 2008-02-27
all right...72h (and last) bump. If I ever find it out, I'll post it here.

---

