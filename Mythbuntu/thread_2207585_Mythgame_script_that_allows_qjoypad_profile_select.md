---
title: "Mythgame script that allows qjoypad profile selection based on ROM"
date: 2014-02-24
forum: Mythbuntu
---

### Post by martin41 on 2014-02-24
I am trying to write a script that launches mupen64plus but allows for different qjoypad profiles to be selected based on which rom is running.  Right now I only have one rom that needs a different profile but I can imagine in the future I would have numerous different profiles needed based on rom.  I think I would use an elif statement for those additions in the future. I know the script works properly if I put the name of the rom into the ROM= field.  What I can't figure out is how to pull the rom file name that has been selected into the script.  I thought it would just be the %s that Mythgame uses as the variable but that doesn't seem to work.  Can someone please provide me some guidance?  Thanks.


#!/bin/sh -e
# Script to launch mupen64plus with correct settings

   # rom file
   ROM=%s

   # mupen64plus executable
   MUPEN64PLUS=mupen64plus

   # gamepad executable
   GAMEPAD=qjoypad

   # gamepad process name to kill
   GAMEPAD_PS=qjoypad

   # emulator process name to kill
   MUPEN64PLUS_PS=mupen64plus

if [ "$ROM" = "Brunswick Circuit Pro Bowling.z64" ]; then
        $GAMEPAD "n64-bowl" &
else
        $GAMEPAD "n64" &
fi

   $MUPEN64PLUS  --gfx mupen64plus-video-glide64mk2 --osd --resolution 1360x768 --fullscreen "$1"

   killall $MUPEN64PLUS_PS $GAMEPAD_PS

---

### Post by blm-ubunet on 2014-02-24
Do you call this script from inside mythtv?
Call it with cmdline option %ROMNAME%
(This is just a guess)
In your script this (first) parameter is $1
```
ROM="$1"
if [ "$ROM" == "" ]; then
             exit -1
fi
```

or get more fancy & use getopts to parse options..

---

### Post by martin41 on 2014-02-25
Yes I call the script from inside mythtv's mythgame application so when i set up the player name the command looks like this and my script is called run-n64:

Command: run-n64 %s
Where %s is the rom it pulls in so i think you are saying I should change my command to:

Command: run-n64 %ROMNAME%

Then go into the script and modify it with what you have suggested?

---

### Post by blm-ubunet on 2014-02-25
Looking at the source code:
[https://code.mythtv.org/doxygen/gamehandler_8cpp_source.html#l00828](https://code.mythtv.org/doxygen/gamehandler_8cpp_source.html#l00828)
I see that mythgame code does not follow the user job queue format..

Your original mythtv command line parameter "%s" is correct.
In your script you just need to use
```
ROM="$1"
```
The second to last (unblank) line of your script is already using this command line parameter..

If you want to extend this to additional parameters & have them parsed correctly etc you could use "getopts".

Does your script work?
The mixed use of $VAR & VAR & lack of quoted strings around strings looks a bit untidy..
Does the IF block work ?
```
if [ "$ROM" == "Brunswick Circuit Pro Bowling.z64" ]; then
```
should be better?

---

### Post by martin41 on 2014-02-25
As you can clearly see I no expert at writing scripts and know nothing about "getopts", I've just kind of cobbled together stuff from around the net and made it work.  Needless to say I still can't make this work.  Below are my current mythtv command and my run-n64 script.  I tested the "if statement" to make sure it works and it does if I change the "$1" to "Brunswick Circuit Pro Bowling.z64" then make the "if [ "$ROM" = "Brunswick Circuit Pro Bowling.z64" ]; then" line only have one equals instead of two like you suggested.  Any other ideas on how to make this work?  I really appreciate your time.

MythGame Command: run-n64 %s

run-n64 script
#!/bin/sh -e
# Script to launch mupen64plus with correct settings

   # rom file
   ROM="$1"

   # mupen64plus executable
   MUPEN64PLUS=mupen64plus

   # gamepad executable
   GAMEPAD=qjoypad

   # gamepad process name to kill
   GAMEPAD_PS=qjoypad

   # emulator process name to kill
   MUPEN64PLUS_PS=mupen64plus

if [ "$ROM" = "Brunswick Circuit Pro Bowling.z64" ]; then
        $GAMEPAD "n64-bowl" &
else
        $GAMEPAD "n64" &
fi

   $MUPEN64PLUS  --gfx mupen64plus-video-glide64mk2 --osd --resolution 1360x768 --fullscreen "$1"

   killall $MUPEN64PLUS_PS $GAMEPAD_PS

---

### Post by blm-ubunet on 2014-02-26
Single "=" is okay....forget about getopts there are no nicely delimited options here anyway..

The single equals "=" is posix compliant & seems to be what sh shell requires.
The bash shell is happy with "==" which makes more sense.
```
#!/bin/sh -e
# Script to launch mupen64plus with correct settings

# rom file
ROM="$1"

# mupen64plus executable
MUPEN64PLUS="mupen64plus"

# gamepad executable
GAMEPAD="qjoypad"

# gamepad process name to kill
GAMEPAD_PS="qjoypad"

# emulator process name to kill
MUPEN64PLUS_PS="mupen64plus"

echo $ROM
if [ "$ROM" = "Brunswick Circuit Pro Bowling.z64" ]; then
   $GAMEPAD "n64-bowl" &
else
   $GAMEPAD "n64" &
fi

$MUPEN64PLUS --gfx mupen64plus-video-glide64mk2 --osd --resolution 1360x768 --fullscreen $ROM

killall $MUPEN64PLUS_PS $GAMEPAD_PS
```

Be sure to set the execute bit of this script or you have to launch with "sh script.sh"
You can test from terminal...

./run-n64 some-rom
or
sh run-n64 some-rom
(where some-rom is an valid target)
does it work ?

---

### Post by martin41 on 2014-02-26
Ok it does work but only when I run it from the terminal, it does not work when I trigger it inside MythTV.  I have narrowed it down to the $ROM variable in the if statement.

if [ "$ROM" = "Brunswick Circuit Pro Bowling.z64" ]; then

I have tested it as

if [ "Brunswick Circuit Pro Bowling.z64" = "Brunswick Circuit Pro Bowling.z64" ]; then

just to make sure the statement does work in MythTV and it does so it leads me to believe that somehow MythTV is blocking that variable in that statement because it works everywhere else in the script.  I've tried all kinds of variations with no quotes, single quotes, echo $ROM, and so on.  I even tried removing the brackets [ ].  To say the least I am at a bit of a loss as to why MythTV won't recognized the variable in the statement, any ideas?

---

### Post by blm-ubunet on 2014-02-27
From looking at mythtv source & trying a myth game cmd line:
echo %s | tee /home/mythtv/mgame.txt

You can see that "%s" is the complete filename with full path..
You are testing this against just the filename (romname).
add this into line 6
```
ROMNAME=${ROM##*[/|\\]}
```

then use $ROMNAME in your if [] test

---

### Post by martin41 on 2014-02-27
I am pleased to say that it worked on the first try you're a genius thank you so much for your time and effort I would have never figured this out without your help.  Below is an example of my final code so if anyone else would like to do the same have at it. 

```
#!/bin/sh -e
# Script to launch mupen64plus with correct settings

   # rom file
   ROM="$1"
   ROMNAME=${ROM##*[/|\\]}

   # mupen64plus executable
   MUPEN64PLUS="mupen64plus"

   # gamepad executable
   GAMEPAD="qjoypad"

   # gamepad process name to kill
   GAMEPAD_PS="qjoypad"

   # emulator process name to kill
   MUPEN64PLUS_PS="mupen64plus"

echo "$ROM"
if [ "$ROMNAME" = "yourromename.z64" ]; then
        $GAMEPAD "n64-bowl" &
else
        $GAMEPAD "n64" &
fi

   $MUPEN64PLUS  --gfx mupen64plus-video-glide64mk2 --osd --resolution 1360x768 --fullscreen "$ROM"

   killall $MUPEN64PLUS_PS $GAMEPAD_PS
```

---

