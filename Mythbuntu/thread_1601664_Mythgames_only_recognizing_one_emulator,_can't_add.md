---
title: "Mythgames only recognizing one emulator, can't add additional players"
date: 2010-10-20
forum: Mythbuntu
---

### Post by billsprestonesq on 2010-10-20
I just started working on getting my emulators up and running in mythgames, and after following the instructions on the wiki, I was able to get ZSNES working just fine.  I added the command and directory info, it scanned, populated the rom list in mythgames, and I was able to launch and play perfectly.  When I went into the game players menu to add additional emulators, after adding all the info according to the wiki and trying to rescan, the system only quickly scans for changes to the SNES directory, but doesn't scan the others, nor do the new emulators and roms show up in the mythgames menu.

The directories are pointed correctly, and I've tried the commands from the wiki, as well full, direct paths.  Nothing works.  Additionally, the emulators work just fine outside of the Mythtv frontend, so I know that the programs themselves are fine.  I can't seem to find anyone else with this problem or any troubleshooting documentation, so any help would be greatly appreciated.

---

### Post by thatguruguy on 2010-10-20
> **billsprestonesq said:**
> I just started working on getting my emulators up and running in mythgames, and after following the instructions on the wiki, I was able to get ZSNES working just fine.  I added the command and directory info, it scanned, populated the rom list in mythgames, and I was able to launch and play perfectly.  When I went into the game players menu to add additional emulators, after adding all the info according to the wiki and trying to rescan, the system only quickly scans for changes to the SNES directory, but doesn't scan the others, nor do the new emulators and roms show up in the mythgames menu.

The directories are pointed correctly, and I've tried the commands from the wiki, as well full, direct paths.  Nothing works.  Additionally, the emulators work just fine outside of the Mythtv frontend, so I know that the programs themselves are fine.  I can't seem to find anyone else with this problem or any troubleshooting documentation, so any help would be greatly appreciated.

Give me an idea of which emulators you're talking about, and I'll look at my settings to see if I can help.  I have dolphin-emu, pcsx-r, gens and zsnes.

---

### Post by billsprestonesq on 2010-10-21
I've managed to get ZSNES working.  The other emulators specifically  that I'm trying to get up and running are mednafen, gens/gs, and  mupen64plus.  All of these work fine if I run them from outside the Myth  frontend, but in mythgames, only the snes directory scans. 
If that makes any difference, I'm happy to try any suggestions.  

Also,  don't know if it matters, but I'm running Mythbuntu 10.04.  I don't  know if upgrading to 10.10 would make a difference or not.  I'm hesitant  to do so, as everything else in the system is running beautifully  except for this emulator issue, and I was afraid to chance it.

---

### Post by thatguruguy on 2010-10-21
I'm also running 10.04.  Although I don't have mednafen set up, I do have mupen64plus and gens up and running. Here are the steps I followed to get things set up.  You may have already followed all these steps, but this may be useful to someone else.

First, I set up a directory in my home folder for my game roms (which I gave the super-cryptic name of "gameroms").  I then set up separate sub-directories for the roms, based upon the associated emulator (e.g., gameroms/sgenroms for gens, and gameroms/mupen64 for mupen64, etc.).

After the roms were all properly stored and sorted, I set up the emulators in mythgames with the following settings under the "Game Player Setup" section:

**For Mupen64Plus:**

Player Name: **Mupen64Plus**
Type: **N64**
Command: **mupen64plus --nogui --noask --fullscreen**
Rom Path: **/home/john/gameroms/mupen64/**
Working Directory: 
File Extensions: **z64,n64**

**For Gens:**

Player Name: **GENS**
Type: [B]GENESIS/MEGADRIVE
[/B]Command: **gens --fs --game %s**
Rom Path: [B]/home/john/gameroms/sgenroms/
[/B]Working Directory:
File Extension: **bin**

After the players are set up, **make sure** that you clear out all the game date by choosing the "Clear Game Data" button.  For some reason, mythgames doesn't always fully update its database if you don't do that step.  After you've done that, you can select the "Scan for Games" button. The scanning process can take a few minutes (depending on how many roms you have); make sure you let it run completely.

After that, your games and the associated emulators *should* show up in mythgames.

---

### Post by billsprestonesq on 2010-10-21
I had everything right except including the rom file extensions.  I didn't need to add those with zsnes, so I left that field blank with the rest.  I did actually try to include them with mupen64plus, but I was using the period before the extension and when that didn't work, I guess I assumed that wasn't the issue.  

Sure enough though, I added the extensions, cleared data and rescanned - presto!  Thanks for the help.

---

