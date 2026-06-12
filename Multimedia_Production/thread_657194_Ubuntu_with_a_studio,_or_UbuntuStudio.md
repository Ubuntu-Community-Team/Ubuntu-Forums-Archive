---
title: "Ubuntu with a studio, or UbuntuStudio"
date: 2008-01-03
forum: Multimedia Production
---

### Post by liniaal on 2008-01-03
Hi people,

i have a tricky question. the background:
recently bought a new "server" slash "workstation" like pc, no multimedia wonder with extreme graphics card, most things intel and most things onboard (zero hassles with 3d and stuff :D, zero "restricted drivers" etc.) and a lot of hard drive space.
in the past year i've been experimenting with UbuntuStudio (7.04 as well as 7.10) quite a bit, and i must say i absolutely love it. but because i experienced problems with 7.10 (no java / openoffice), with the new pc i began with regular ubuntu. and it rolls lovely. but of course now follows, the question:

i'd like to get back to experimenting with beats 'n such again, but i would like to not have to install UbuntuStudio alongside the existing Ubuntu installation (would like to be able to use the same home directory, not have to do every update twice, etc. etc.). Could i install the -rt kernel and then, configure init.d files in such a way that if i launch ubuntu with the -rt kernel, mpd/icecast/apache2/mysql/sshd etc will not get started? and maybe jack automatically? i have no problem with editing these files, but i want to know first is this possible??

much obliged,

---

### Post by radi0j0hn on 2008-01-03
Don't quote me on this, but isn't Ubuntu Studio essentially Ubuntu with music specific programs pre-loaded?  If so, can you simply DL the needed ones to you existing O/S?

I haven't used studio, as I only do voice recording with limited BG music, so I haven't gotten into MIDI, sampling, etc.  I'm certain no Fatboy Slim, but I edit a mean radio talk show down to the proper time!

John

---

### Post by theacoustician on 2008-01-03
> **liniaal said:**
> Hi people,

i have a tricky question. the background:
recently bought a new "server" slash "workstation" like pc, no multimedia wonder with extreme graphics card, most things intel and most things onboard (zero hassles with 3d and stuff :D, zero "restricted drivers" etc.) and a lot of hard drive space.
in the past year i've been experimenting with UbuntuStudio (7.04 as well as 7.10) quite a bit, and i must say i absolutely love it. but because i experienced problems with 7.10 (no java / openoffice), with the new pc i began with regular ubuntu. and it rolls lovely. but of course now follows, the question:

i'd like to get back to experimenting with beats 'n such again, but i would like to not have to install UbuntuStudio alongside the existing Ubuntu installation (would like to be able to use the same home directory, not have to do every update twice, etc. etc.). Could i install the -rt kernel and then, configure init.d files in such a way that if i launch ubuntu with the -rt kernel, mpd/icecast/apache2/mysql/sshd etc will not get started? and maybe jack automatically? i have no problem with editing these files, but i want to know first is this possible??

much obliged,I've not yet done it this way, but you can "upgrade" your current install to Studio simply by installing the ubuntustudio packages you want.  Should do all the work for you, seeing as it will catch all the dependencies and no need to go editing a bunch of files. 

> **radi0j0hn said:**
> Don't quote me on this, but isn't Ubuntu Studio essentially Ubuntu with music specific programs pre-loaded?  If so, can you simply DL the needed ones to you existing O/S?

I haven't used studio, as I only do voice recording with limited BG music, so I haven't gotten into MIDI, sampling, etc.  I'm certain no Fatboy Slim, but I edit a mean radio talk show down to the proper time!

John

Well, Studio has the rt kernel.  That's rather important for audio production.  There are some other audio drivers, utilities, libraries, etc. that you may not think to install by default, but prove helpful for whatever music software you end up using.

---

### Post by liniaal on 2008-01-20
thanks all of you, i will do multi boot.

---

