---
title: "wmv files wont play"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by norton1 on 2007-04-17
Hi - I've been trying to play a couple of wmv files in totem but although the sound works the screen remains blank - or starts to play the visualization effects if i resize the screen.  I had already installed all the codecs from add/remove programs but then i have also updated my system with 166 updates.

i've tried to play the file in mplayer also but all i get is 'unable to open the selected video out' (or something like that - i'm not at that computer right now)

has anyone got a solution for this - should i try to reinstall the gstreamer plugin codecs again?

yours in hope,

ben

---

### Post by phossal on 2007-04-17
I had luck with gxine.

---

### Post by Archmage on 2007-04-17
'unable to open the selected video out' means that mplayer is configurated to display on something that he don't find. Like you want to display it with the nvidia-driver, but you had an ATI-card.

---

### Post by phossal on 2007-04-17
I have an nvidia card. I get this error with MPlayer: *[COLOR="Red"]Error opening/initializing the selected video_out (-vo) device[/COLOR]*. I'm sure you're correct about the reason *why*, but I have luck with gxine. It didn't require any additional tweaking. I just grabbed the packages.

---

### Post by ajgreeny on 2007-04-17
Also worth trying totem-xine in place of totem-gstreamer.  I've never had success with totem-gstreamer in all the versions of ubuntu that I've had so far, but totem-xine always seems to do the job without problems.  wmv, avi, mpg, mov, all play OK.

---

### Post by norton1 on 2007-04-17
hi - sorry, no luck yet - the best i have found is if i save the file to disc and then play it in VLC player and then spend a while moving the screen around and resizing until a picture appears? its a bit like fiddling with a dodgy scart lead to get a tv picture .  gzine didn't work at all i'm afraid?

---

