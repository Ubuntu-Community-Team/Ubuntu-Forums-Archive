---
title: "(hardy) - rhythmbox crashes while trying to play anything"
date: 2008-05-17
forum: Multimedia Software
---

### Post by oskar2000 on 2008-05-17
When I try to play an mp3/ogg/flac (that's what I tried) in rhythmbox, the status bar stays at 0:00 for a couple of seconds, and then the window turns gray, and rhythmbox stays unresponsive until I kill it.

I started it from the command line, but I get no error output, until I kill it - then it sais "killed", which makes sense. No further information.

I can play these files through Totem, VLC, and m-player.
I have the same issue with exaile and banshee though. They also stop responding the the moment I click 'play'.

Might not be relevant, but it might shed some light:
Ubuntu is using my on-board sound card - which is actually disabled in the bios! It won't play through my m-audio 2496 (PCI sound card - officially supported by ALSA and OSS) - which has worked with every System since Suse 9.3.

I strongly suspect pulseaudio to cause yet another problem - so a viable solution might be to get rid of the damn thing altogether.

---

