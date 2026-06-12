---
title: "Need to disable NVidia CK804"
date: 2006-05-24
forum: Multimedia &amp; Video
---

### Post by dimatrod on 2006-05-24
Just recently I upgraded to Dapper beta and one thing that surprised me was that it actually recognized my Chaintech AV710 sound card.  So I went along, set everything to alsa, and it just worked for a day.  Next day, it all pooped out and went back to the evil onboard sound.  Now, every time I set the AV710 to default in Sound, it reverts just when I press close.  Is there any way to disable COMPLETELY the NVidia CK804, and to set as default the AV710?  Thank you!

Edit:  Forgot to mention, it's an nForce 4 motherboard, and it shows up in device manager as AC '97

---

### Post by dimatrod on 2006-05-24
[QUOTE=dimatrod]Just recently I upgraded to Dapper beta and one thing that surprised me was that it actually recognized my Chaintech AV710 sound card.  So I went along, set everything to alsa, and it just worked for a day.  Next day, it all pooped out and went back to the evil onboard sound.  Now, every time I set the AV710 to default in Sound, it reverts just when I press close.  Is there any way to disable COMPLETELY the NVidia CK804, and to set as default the AV710?  Thank you!

Edit:  Forgot to mention, it's an nForce 4 motherboard, and it shows up in device manager as AC '97[/QUOTE]
Edit2:  Oh come on, please help!  I edited the asound.state file to match a config that was recommended in Hydrogenaudio, later modified the asound.config, rebooted, and now it shows as my default card, however no sound on any port and when playing a song it just opens the song, however it doesn't play it (it remains in 0:00)

Woops, double post.  Clicked on quote instead of edit.  Sorry bout that!

---

### Post by dimatrod on 2006-07-19
So I finally disabled it.  Turns out I had to switch the AC97 codec in the bios off.  So the good thing is I got rid of the horrible onboard sound, bad thing is I can't get audio working ](*,) .

---

