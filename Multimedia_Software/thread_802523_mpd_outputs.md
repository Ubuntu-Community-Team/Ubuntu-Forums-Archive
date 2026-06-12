---
title: "mpd outputs"
date: 2008-05-21
forum: Multimedia Software
---

### Post by Nythain on 2008-05-21
ok, so i set up mpd (my prefered music player) and decided to set up an icecast server so others could experience the total awesomeness that is my music collection...

this leads me to my main only issue... i dont want to have to listen to the music 24/7, i sometimes like to watch movies and whatnot... i was under the impression i could have mpd only output to the icecast server, but i havent found a way to yet...

if i remove the alsa audio_output block mpd wont play... if i set it to a dummy /null device, it still runs through my soundcard/headphones/speakers... if i just turn down teh volume of mpd it naturally adjust the pcm volume wich makes everythign quiet/mute naturally....

so, is it even possible to do what i want, have mpd silently source to teh icecast server, or will i be forced to listen to the music when i want to be "broadcasting"???

---

### Post by mplexus on 2009-01-04
exactly my question as well.

when both alsa and icecast outputs are enabled music plays through my speakers and also is streamed through icecast. then if i disable alsa output (either from gmpc or command line mpc disable 1) the icecast output keeps working and streaming is normal.

how can i disable alsa and enable icecast other than manually do it?

is it really necessary to have alsa enabled so that streaming starts?

i tried adding in /etc/rc.local:

mpc disable 1
mpc enable 2
mpc play

but nothing - without alsa enabled the streaming does not start.

**NEW**: i changed the above lines in /etc/rc.local into:

/usr/local/bin/mpc_start &

(**NEW2**: I wonder if i must replace it with: su -c "/usr/local/bin/mpc_start &" <username_here>)

and added this into /usr/local/bin/mpc_start :

#!/bin/bash
mpc enable 1
mpc enable 2
mpc play
sleep 5
mpc disable 1

and it works. A workaround that is.

---

### Post by berot3 on 2009-12-18
hmm for me it works by commenting out alsa-output in mpd.conf. so if i want to listen to mpd i have to listen to my icecast-stream. 
maybe becasue its fixed in newer versions? i have mpd-0.15.6-1

---

