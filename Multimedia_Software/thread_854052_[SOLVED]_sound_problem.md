---
title: "[SOLVED] sound problem"
date: 2008-07-09
forum: Multimedia Software
---

### Post by mosty friedman on 2008-07-09
hey everyone, i need help with this...i have the sound working on my ubuntu and all but i've noticed that after i watch something on the browser that contains sound like youtube n then try to watch a movie or listen to an mp3, the sound doesnt work.. can anyone help me with this??

---

### Post by thorgal on 2008-07-09
which sound server are you using ?
alsa ?
pulseaudio
oss ?

Looks like you use OSS and the flash plugin excludes other apps to function once it has a grip on your sound card.

---

### Post by mosty friedman on 2008-07-09
so which one should i use??

---

### Post by thorgal on 2008-07-11
it's hard to say unless you know which sound server is running by default when you log in. pulseaudio is the new sound server and is maybe not fully compatible with all apps. Alsa on the other hand is a lower level layer and should be supported by most apps. It's a conservative choice but you should be safe with this choice. It has an oss emulation layer so even deprecated apps using oss should be fine.

If you now want to enter the world of pro audio, jack is the sound server of choice. It's a trikier road. Anyway, start with alsa. I don't know gnome so I cannot help you more on how to set this up unless you are OK with terminal commands (unix shell).

---

### Post by markbuntu on 2008-07-11
Ubuntu Hardy uses pulseaudio by default, so if you are using Ubuntu Hardy8.04 then you are using pulseaudio unless you have removed it yourself.

Flash uses pulseaudio by default and flash 9 has a bug in it that locks up the pulseaudio sound server. You can fix some or most or all of your problems by following the multimedia guide and the sound guide at the top of this forum.

If that doesn't work, come back here and we will try to help.

---

### Post by mosty friedman on 2008-07-12
on another thread some guy said removing the pulseaudio from the synaptic package manager shall solve the problem..do u recommend that??

---

### Post by thorgal on 2008-07-13
try it :)
if you need pulseaudio after that, reinstall it :)

---

### Post by mosty friedman on 2008-09-14
actually removing pulseaudio solve the problem...:) thanks a lot guys

---

