---
title: "Mythbuntu and LIRC (homebrew serial)"
date: 2008-01-30
forum: Mythbuntu
---

### Post by jjohns63 on 2008-01-30
OK, I am at my wit's end with this one. I got a new machine and upgraded to mythbuntu on Gutsy. My only problem is the homebrew serial receiver I was using on my old machine (Feisty) does not correctly pass the keypresses to mythtv. irw works and sees all the buttons, so I know that the configuration is correct in my lircd.conf and hardware.conf. I've tried regenerating lircrc using mythbuntu-lircrc-generator and editing that to match my keymappings but nothing works.

I'm using 0.8.2 of LIRC and I've searched all over the place but haven't found a problem similar to mine. Any help?

---

### Post by jjohns63 on 2008-01-30
I checked and the remote works in mplayer, and I also set up a link from /home/user/.mythtv/lircrc-->/home/user/.lircrc

This way I only need to mess with one file, maybe the prog field is wrong? I have it as prog=mythtv for all the buttons, should it be different. That's what I had before and that's what is generated for me. Still looking for answers.

---

