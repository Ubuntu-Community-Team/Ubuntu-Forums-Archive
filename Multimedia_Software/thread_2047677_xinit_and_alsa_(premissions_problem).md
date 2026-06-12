---
title: "xinit and alsa (premissions problem?)"
date: 2012-08-25
forum: Multimedia Software
---

### Post by Skystriker on 2012-08-25
Hi!

I have a ubuntu-minimal installation, running xserver and dolphin-emu (nintendo wii-emulator).

The problem that i have is, that if the emulator runs without root-permissons the sound (alsa-backend) is not working...

that means if i run:

```
xinit dolphin-emu
``` ---> no sound

but if i do:

```
xinit
```

and from another terminal:

```
export DISPLAY=:0
sudo /usr/games/dolphin-emu
``` ---> everything works as aspected!

I do not think that my alsa configuration causes problems, because it works if the emu runs as root.

my user is in the audio group.

i also noticed another strange thing which might be helpful for finding the solution:

if i run xinit with any other application, for example:

```
xinit firefox
```

i do not have sound even if i run the emu as root.

i figured out that the only working case is:

```
xinit
``` (without parameter)

and than run the emu as root as shown before...

I hope somebody can at least point me to the right direction as i do not have any idea how to fix that behaviour. :)

---

