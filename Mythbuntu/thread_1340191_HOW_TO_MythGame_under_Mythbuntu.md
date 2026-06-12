---
title: "HOW TO MythGame under Mythbuntu"
date: 2009-11-28
forum: Mythbuntu
---

### Post by chipppy on 2009-11-28
HOW TO MythGame under Mythbuntu

Original How To written using Mythbuntu 9.10

First; this is a HOW TO and not a legal discussion.  If you want to break the law that is you choice.  Personally I encourage you to work within the laws of you land.

**_Step 1		Setup MythGame_**
Go to XFCE desktop ==> Menu ==> System ==> Main Control Centre (MCC)
Select plug-ins ==> MythGame
Apply and let this plug-in be installed.

**_Step 2.		MAME (Multiple Arcade Machine Emulator)_**
For this we are going to use SDLMAME ([http://rbelmont.mameworld.info/?page_id=163](”http://rbelmont.mameworld.info/?page_id=163")), from the  sdlmame4ubuntu ([http://sdlmame.wallyweek.org/](http://sdlmame.wallyweek.org/)) repositories.  All credit goes to the guy and girls that maintain both part of this excellent project pair.

Go to XFCE desktop ==> accessories ==> terminal
Run the following commands in order.  This is to set up the sdlmame major release (most stable) repositories and install the software on your computer
```
sudo apt-get install wget
```

```
wget http://sdlmame4ubuntu.org/repoc/957AC3A6.gpg -O- | \
sudo apt-key add -
```
```
sudo wget http://sdlmame4ubuntu.org/repoc/karmic.major.list -O \
/etc/apt/sources.list.d/sdlmame4ubuntu.major.list
```
```
sudo apt-get update
```
```
sudo apt-get install sdlmame
```
Instruction for the intermediate updates please follow the instructions at [http://sdlmame.wallyweek.org/repository/](”http://sdlmame.wallyweek.org/repository/”)

**_Step 3.	Load the ROMS_**
Effectively you can install your ROMS anywhere you wish, we'll tell SDLMAME when to look in a minute.  Personally I put then in the following folder.
```
/var/lib/mythtv/mythgame/sdlmame/roms/
``` 
If you are going to use the full capabilities of SDLMAME then you need to create a few other folders to store some stuff in eg.
```
/var/lib/mythtv/mythgame/sdlmame/artwork/
/var/lib/mythtv/mythgame/sdlmame/samples
``` 

**_Step 4. 	Setup SDLMAME_**
You need to tell SDLMAME where to find all the files that it needs, eg ROMS.  To do this you need to edit the sdlmame.ini file.  I personally use the gedit program to edit my text files.  Change the following terminal code by replacing the ******'s with your text editor
```
 sudo ***** /etc/sdlmame/mame.ini
```
An example using gedit is
```
 sudo gedit /etc/sdlmame/mame.ini
```

You will notice that the in first three line of code (in the CODE box below, that the folder structure matches the ones we created earlier.  In the mame.ini file you just opened you will notice that they don't match.  This is the three lines on code that you need to change to match the folder structure that you created in **_Step 3. _**.  
```
# CORE SEARCH PATH OPTIONS
#
rompath                   $HOME/.mame/roms;/var/lib/mythtv/mythgame/sdlmame/roms
samplepath                $HOME/.mame/samples;/var/lib/mythtv/mythgame/sdlmame/samples
artpath                   $HOME/.mame/artwork;/var/lib/mythtv/mythgame/sdlmame/artwork
ctrlrpath                 /etc/sdlmame/ctrlr
inipath                   /etc/sdlmame
fontpath                  /tmp;/usr/share/games/sdlmame
cheatpath                 $HOME/.mame/cheat;$HOME/.mame/cheat/cheat;/usr/local/share/games/sdlmame/cheat;/usr/local/share/games/sdlmame/cheat/cheat
crosshairpath             $HOME/.mame/crosshair;/usr/local/share/games/sdlmame/crosshair
```

If you are using a keyboard layout other then US you need to change a little bit further down the file.  Just change the 0 to a 1 after **keymap** and delete the **#** from ifront of the relevant  keyboard type eg **********/km-fr.txt for france keyboard layout.
```
# SDL KEYBOARD MAPPING
#
# If you are using one of the available non-us keyboard layouts
# set keymap to 1 and uncomment the appropriate line below
keymap                    0
#keymap_file               /usr/share/games/sdlmame/keymaps/km-be.txt
#keymap_file               /usr/share/games/sdlmame/keymaps/km-ch.txt
#keymap_file               /usr/share/games/sdlmame/keymaps/km-de.txt
#keymap_file               /usr/share/games/sdlmame/keymaps/km-fr.txt
#keymap_file               /usr/share/games/sdlmame/keymaps/km_it.txt
``` 

**_Step 5.		Setup MythGame in Mythtv_**
The emulator is refered to as a Game Player in Mythtv, as in the player use to play games, not player 1 or player 2 as most people first think.

In Mythtv
Utilities/Setup ==> Setup ==> Media Settings ==> Game Settings ==> Game Players

Create a New Game Player
Player Name:	SDLMAME		
Type:			MAME
Command:		/usr/games/sdlmame %s
ROM Path:		/var/lib/mythtv/mythgame/sdlmame/roms
tick the box for 'Allow games to span multiple roms/disks'
Finish

Now back out one level and select **Scan for Games**.  If all is good then this may take a moment or two.  Depending on the number of ROMS you have.
Now

**_Step 7.		Play a Game_**
In Mythtv
Media Library ==> Play Games
Scroll down to **By name** and a list should appear of the file name of the different ROMS that you have loaded.  Select one and hit enter.  You should now be able to play the game.


[I]I hope this help out a few people out there.  Please contact me about error that I can edit to fix.  there are many other emulators that can be added in, that I haven't tried yet.  Please contact me with details and I will add into this HOW TO

{More to be added later: Scripts to get coverart/fanart etc}[/I]

---

### Post by mellery on 2009-12-17
thanks for this guide.  I can't get sound to work when playing sdlmess launched from mythtv/mythgame.  Sound works fine when I launch sdlmess by itself.  Also I can't quit sdlmess games, when I press escape my system freezes, did you have to change something to make it work?

---

### Post by chipppy on 2010-01-03
Sorry for the delay.  I have been on Holiday for the last couple of weeks.

I didn't have to modify anything in Myth.  It all worked striaght up.  I tested this HOW TO using a relative clean install of 9.10 and the hardware as per my signature. (the motherboard is a none RAID unit).

The sound not working is strange.  It sounds like a Myth issue.  
What version of Myth you running?
Can you think of any mods to the Myth base install that might be affecting the sound? 
Have a look at your logs for what is happening when you run MythGame SDLMess, any clues in there.
Go to desktop and open a mixer (ALSA or whatever you use) have a look at the various volume levels.  Now play a game in MythGame and ALT+TAB to the mixer and have a look at the various volume levels.  Does MythGame change the levels?
Anything else that might help to fault find.

I have had a couple of frezze issue when quiting but I think it is the specific game more then the emulator as other quit fine.

Cheers
chipppy

---

### Post by mellery on 2010-01-07
I found out pressing F6 lets me quit mess back to mythfrontend without freezing the system.  I still havent figured out the sound, it plays fine when launched from the terminal.  Didn't see anything in the logs to give me any clues

---

### Post by stuarticus on 2010-02-05
Hi, I've installed as recommended, but I don't have the "Games Settings" menu there at all? any idea why?

 Thanks, Stuart.

---

### Post by bgiannes on 2010-02-05
i can't get my gamespad to work with sdlmame?  I does work with other programs.

what am i missing?

---

### Post by chipppy on 2010-02-13
Good Evening

stuarticus:
silly question but have you clicked the MythGame radial button in the setup page (Applications/Setting/MythTV Control Center)?

bgiannes:
I am assuming that gamespad is a joystick.  Personally I use a homemade arcade joystick desktp with an mame encoder.  Sad I know but I do love my old school games.
If you are using a joystick then you need to edit the ini file and change the seting from 0 to 1.  I am not infornt of my box at the moment and will have to look into it.  I do know that joysticks are a little bit of fun at the most common joystick system is the encorder which just translate joystick movements in the keyboard key inputs.  Therefore the program still sees keystrokes.
I will get back to you on this one.

Cheers
chipppy

---

