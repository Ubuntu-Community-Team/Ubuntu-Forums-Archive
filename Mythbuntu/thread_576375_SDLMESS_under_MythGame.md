---
title: "SDLMESS under MythGame"
date: 2007-10-15
forum: Mythbuntu
---

### Post by Mykro on 2007-10-15
Hi, I'm using Mythbuntu 7.10 Beta.  

Neither MythGame or the mythtv user is able to launch SDLMESS correctly for me.

BUT the whole thing works fine from the console as the default user.  Here are the steps I followed:

1. downloaded SDLMESS 0.199u3
2. extracted to /usr/share/games/sdlmess
3. compiled with default makefile => "mess" executable

4. created link accessible to all users:
  /usr/local/bin$ sudo ln /usr/share/games/sdlmess/mess mess --symbolic

5. created directory structure for the ROMS:
  /usr/local/share/games/sdlmess/.
  /usr/local/share/games/sdlmess/mess.ini
  /usr/local/share/games/sdlmess/roms/.
  /usr/local/share/games/sdlmess/roms/cpc464.zip
  /usr/local/share/games/sdlmess/roms/Amstrad/.
  /usr/local/share/games/sdlmess/roms/Amstrad/demo.dsk

6. I can run mess from the command line (as long as its in the correct directory) and it will find and boot the BIOS ROM and load the game ROM onto the media device with no problems:

  /usr/local/share/games/sdlmess$ mess cpc464 -flop1 /roms/Amstrad/demo.dsk

7. All good, so I then configured a MythGame player:

  Player Type: MAME
  Command: mess cpc464 -flop1 
  Rom Dir: /usr/local/share/games/sdlmess/roms/
  Working Dir: /usr/local/share/games/sdlmess/

8. Scan for games works.  The database is populated with the ROMs, and I can browse them within MythTV.  When I press 'M' the launch information for the player is correct. 

9. BUT when I actually launch the ROM, nothing happens (screen flickers black for a second)

10. I finally get the idea it might be a user permissions problem.  When I try to launch mess using the mythtv user:

  /usr/local/share/games/sdlmess$ sudo -u mythtv mess

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
       ---------------------- DirectFB v0.9.25 ---------------------
             (c) 2000-2002  convergence integrated media GmbH  
             (c) 2002-2004  convergence GmbH                   
        -----------------------------------------------------------
(*) DirectFB/Core: Single Application Core. (2007-08-07 19:21) 
(*) Direct/Memcpy: Using MMX optimized memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
Could not initialize SDL: %s.
: DirectFBCreate: Initialization error!

I'm ASSUMING this is the same error that MythGame is failing on, but I don't know if MythGame is actually launching it with the "mythtv" user, or how to find out what error MythGame is encountering.

So in short, launching SDLMESS as either the root user or as my own default login works, but launching it as the mythtv user fails.  

NOTE: it's not a MythGame issue in general as I have SDLMAME working perfectly in MythGame.  But that was an apt-get package, not compiled.

Does anyone know what is going wrong here?  I'm kind of stuck here in an empty place between the MythGame documentation and SDLMESS documentation.  

Please help if you can!  Thanks!

---

### Post by superm1 on 2007-10-15
Well actually mythfrontend isn't ran as the mythtv user.  It's ran as your normal user.  Try to run things as your normal user to debug this.

---

### Post by Mykro on 2007-10-16
> **superm1 said:**
> Well actually mythfrontend isn't ran as the mythtv user.  It's ran as your normal user.  Try to run things as your normal user to debug this.

Thanks superm1, that info helps.  I can abandon the "sudo -u mythtv mess" approach.  But everything does run great under my normal user from the command-line.

I've got a little further now - I started mythfrontend with logging:

  mythfrontend -v all -l /var/log/mythtv/mythfront.log

Went into MythGame and tried to start the ROM.  The log contains:

2007-10-16 18:39:15.315 MSqlQuery: SELECT system,gamename,genre,year,romname,favorite,rompath,country,crc_value,diskcount,gametype,publisher,version FROM gamemetadata WHERE gamename="tech" AND system="Amstrad" ORDER BY diskcount DESC;
2007-10-16 18:39:15.315 MSqlQuery: SELECT screenshots FROM gameplayers WHERE playername = "Amstrad";
2007-10-16 18:39:15.316 MSqlQuery: SELECT count(*) FROM gamemetadata WHERE gametype = "MAME" AND romname = "tech.dsk";
Launching Game : Amstrad : mess cpc464 -flop1 "/usr/local/share/games/sdlmess/roms/tech.dsk" : 
src/mess/drivers/amstrad.c: cpc464p has empty ROM region (warning)
src/mess/drivers/amstrad.c: cpc464p has empty ROM region (warning)
src/mess/drivers/amstrad.c: cpc6128p has empty ROM region (warning)
src/mess/drivers/amstrad.c: cpc6128p has empty ROM region (warning)
cpc464.rom NOT FOUND
cpcados.rom NOT FOUND
ERROR: required files are missing, the game cannot be run.
Ignoring MAME exception: cpc464.rom NOT FOUND
cpcados.rom NOT FOUND
ERROR: required files are missing, the game cannot be run.
MythThemedDialog.o: something is requesting a screen update of zero size. A widget probably has not done a calculateScreeArea(). Will redraw the whole screen (inefficient!).

The "Launching Game" command looks correct - BUT the error messages that occur are the same messages that occur when launching in the wrong directory at the command line.

Below is the correct directory and command for a working launch:

:/usr/local/share/games/sdlmess$ mess cpc464 -flop1 "/usr/local/share/games/sdlmess/roms/tech.dsk"

Remember the player is defined as:

Player Type: MAME
Command: mess cpc464 -flop1
Rom Dir: /usr/local/share/games/sdlmess/roms/
Working Dir: /usr/local/share/games/sdlmess/

This seems to suggest that the Player's Working Dir might not actually be honored by MythGame.

I can't find any bug to this effect on the MythTV trac.  Can anyone else reproduce this?

---

### Post by Mykro on 2007-10-16
I couldn't fix it via the Working Dir but I did get it working by making SDLMESS run-anywhere.  So for those who are on the same path...

Making SDLMESS able to run from anywhere:

- create a .mess directory in your $HOME
- run "mess -createconfig" to create a mess.ini config file
- copy mess.ini to ~/.mess
- modify the paths in mess.ini to point to the working directory:

rompath                   /usr/local/share/games/sdlmess/roms
hashpath                  /usr/local/share/games/sdlmess/hash
samplepath                /usr/local/share/games/sdlmess/samples
artpath                   /usr/local/share/games/sdlmess/artwork
ctrlrpath                 /usr/local/share/games/sdlmess/ctrlr
inipath                   /usr/local/share/games/sdlmess
fontpath                  /usr/local/share/games/sdlmess

(ctrlrpath and fontpath might be wrong... )

Now MythGame can launch SDLMESS, because it no longer needs the player's Working Dir property.

I've placed the full steps to install SDLMESS under MythGame here: [http://www.mythtv.org/wiki/index.php/Configuring_MythGame_Emulation#SDLMESS](http://www.mythtv.org/wiki/index.php/Configuring_MythGame_Emulation#SDLMESS)

Would still be great if someone could confirm the Working Dir issue however - happy to report it if there is indeed a bug!

thanks for listening.

---

