---
title: "no sound XFCE$, sound nonX"
date: 2009-05-22
forum: Multimedia Software
---

### Post by daycarl on 2009-05-22
No sound while in xfce4, can get sound while
not in X windows with current AMD64 release 9.04 cdrom 
(clean install). While not in X, can do this command from sox:
play /usr/share/sounds/alsa/*.wav
plays the speaker-text wave files.
From X-term using same play command get the  error:
ALSA-LIB: confimisc.c :768 (parse card) cannot find card '0'.
Mplayer spits same error plus pulse error and other (guesses) errors,
while playing  a mpeg-ts, vid shows no sound , non-X session
mplayer plays the sound from the mpeg-ts, no vid (no frame-buff).
-------------------------------------------------------------------
After install, moved gdm out of /etc/init.d, edit /etc/shadow
for real root user & user with no passwords. 
I Do not run [gkx]DM on any of my linux systems, 
do run Xwin from root. Will not change shadow or DM.
---Sound changes for problem  -----------------
Searched this site and google 
Added .asound  file in user dir
My other distro on this system Mandriva 2009.1 (sound working in X)
has a lot pulseaudio files installed.
Myth cd only had the libpulse files ?
Got the latest Debian 5.1 amd64 (5dvd sets)
installed pulseaudio, pulseaudio-module-x11, pulseaudio-utils
still no sound in X-windows
---------------------------------------------------------
Yours Carl Day  [email]daycarl@gmail.com[/email]  </* spammed to max */>

---

### Post by kerry_s on 2009-05-22
have you tried installing alsa? (**apt-get install alsa-base alsa-utils**)

you don't need to use root, you should have left it locked, congratulations on cutting security by 50%. do yourself a favor> 
**sudo passwd -l root**

---

