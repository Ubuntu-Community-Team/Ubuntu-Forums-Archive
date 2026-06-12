---
title: "trying to get fce-ultra set up in mythgame"
date: 2008-01-14
forum: Mythbuntu
---

### Post by onesojourner on 2008-01-14
I have all my roms stored at in my home directory at roms/nes. I have fce ultra installed and I added the line

fceu -fs 1 -joy1 1 -xres 1024 -yres 768 -soundvol 25

to my mythgame listing.

for some reason I still have no games showing up and when I tell it to scan for games nothing seems to happen.

---

### Post by aaltieri on 2008-01-15
Greetings!

I ran into a similar problem after a system crash.  I couldn't add game roms or emulators.  It ended up being a bad data table.  This site helped immensely:

[http://help.hardhathosting.com/question.php/123]("http://help.hardhathosting.com/question.php/123")

Also, when you are setting up the emulator in mythgame, I always use the full literal directory for the roms, as opposed to ~/ as I've run into issues with that too.

Lastly, I forget off hand, but fceu may have a config file and may need to be told where the roms are as well.  I used it breifly on my last server, I'm running SDLmess now.

Peace.

--anthony

---

