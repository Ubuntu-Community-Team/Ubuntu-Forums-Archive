---
title: "How to get lirc working programs and desktop"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by williammanda on 2007-04-09
I just got lirc working with mythtv and I would like to apply using the remote with other programs. I followed this guide to get lirc installed and the remote working help.ubuntu.com/community/Install_Lirc_Edgy
I read the lirc website but it doesn't answer a few questions.
1. Do I need to make one lircrc file for all the programs I want to control with the remote or make separate lircrc files for each program I want to control with the remote?
2. If I have to make separate lircrc files, where do I place them....the mythtv install placed it in /home/george/.mythtv?
3. I tried to make other lircrc files for other programs....ie kaffeine. I placed it in ~/kaffeine, in the lircrc file, there is a field to tell the OS what program the control function is for ie prog. I set prog=kaffeine, is this all that needs to be done?
4. Also I would like to apply using the remote to control the desktop / computer (replace the mouse & keyboard). The lirc website gave some info on this but since I'm not a programmer, it didn't help. Are there any examples? I would love as many examples as I can get of anything.
Any help would be appreciated.
Thanks

---

### Post by williammanda on 2007-04-10
Anyone with any examples of existing setups?
Thanks

---

### Post by LtPitt on 2007-04-11
I've tried...
Every kind of tutorial I've found...
No luck.

The best results are achieved NOT using lirc and using my Ati Remote Wonder with just Kubuntu Edgy...
The main problem I have is that even if some programs (like kaffeine) DO recognize buttons (such as volume up) when I program shortcuts they just don't work in the program...

One of the main reason that could force me to leave kubuntu...
I need a media center and MythTv looked nice...
I was not able to map Freevo keys, btw...

---

### Post by williammanda on 2007-04-11
I have some additional info from another thread that me be of help. Please review it and post your feedback.
[http://www.mepislovers.org/forums/showthread.php?t=6138](http://www.mepislovers.org/forums/showthread.php?t=6138)
Thanks

---

### Post by newlinux on 2007-04-11
All of my lirc configs are stored in ~/.lircrc, including myth. Current versions of myth look in the .mythtv folder (my understanding is that future versions will look in the "standard" place in your home directory). I just used a symlink to my global .lircrc file that controls everything else I use a remote for. I hope this is the information you were looking for.

I use gnome, and all the other programs I use it for (xine, mplayer, irexec) look in ~/.lircrc. If you encounter a program that doesn't you can still put them all in one file and use a symlink. Setting the prog is all that should need to be done.

Kaffeine may be a little different. I've only used it a few times, but I seem to remember people using irexec with DCOP to use LIRC with Kaffeine and Amarok. Here's an example that you may be able to modify to work with the lircd.conf (you'll have to change the button= to match the buttons you have defined for your remote). 

[http://www.netikka.net/holm/holm/linux/lircrc](http://www.netikka.net/holm/holm/linux/lircrc)

You'll need to have irexec running. 

What remote are you using? You'll probably need to use lircmd to emulate a mouse with the remote (haven't done it, but at one point I was interested so I remember looking into doing this) and irxevent for truer keyboard emulation:

 [http://www.lirc.org/html/irxevent.html](http://www.lirc.org/html/irxevent.html)

You can search for example config files using irxevent as well...


Hope this helps...

---

### Post by williammanda on 2007-04-12
Thanks for your reply!
A couple of questions:
1. Please explain dcop?
2. "lirc configs are stored in ~/.lircrc". Does this mean /home/username/.lircrc? Meaning .lircrc is a file in the username directory? If not please state the full path. Sorry I'm still learning the linux jargon.

Thanks for the irexec example with kaffeine, that goes a long way for me.

---

### Post by newlinux on 2007-04-12
> **williammanda said:**
> Thanks for your reply!
A couple of questions:
1. Please explain dcop?
2. "lirc configs are stored in ~/.lircrc". Does this mean /home/username/.lircrc? Meaning .lircrc is a file in the username directory? If not please state the full path. Sorry I'm still learning the linux jargon.

Thanks for the irexec example with kaffeine, that goes a long way for me.


1. DCOP (Desktop Communication Protocol) is KDE's interprocess communication protocol. It basically allows KDE applications to send messages and commands to each other. I haven't used KDE much (but I keep telling myself I'll become more familiar with it, but gnome seems to suit me just fine since I do most things commandline). I believe the application kdcop will allow you to see which DCOP commands each application that is currently running supports. So you could see all the Kaffeine supported commands by opening it up and then running kdcop.

2. Hey no problem. We were all learning this at some point. Yes ~/.lircrc equates to /home/username/.lircrc.  ~/ means the user's home directory. so typing:

```
cd ~/
```
takes you to the same place as

```
cd /home/username/

```
for the user who is logged in.

I hope all this is helpful.

---

### Post by newlinux on 2007-04-12
Oh, and you might not know what symlinks are either. They are a way of linking a file that is located in one directory to another directory (like a shortcut in windows).

So, for instance to link ~/.mythtv/lircrc to ~/.lircrc you would do:

```
ln -s ~/.lircrc ~/.mythtv/lircrc
```
 
In this example, ~/.mythtv/lircrc would actually be the same file as ~/.lircrc. And ~/.mythtv/lircrc cannot exist already before running this command. You can see what files in a directory are symlinked by typing ```
ls -l
```

Just in case you didn't know what I meant...

---

### Post by williammanda on 2007-04-12
Thanks again for all your help!
A question conerning dcop.
If I have more than one program setup in lircrc and the programs all use the same buttons on the remote, will irexec be able to distingish between the programs? I'll give an example:
begin
        prog = irexec
        button = PLAY
        config = dcop kaffeine KaffeineIface playDvb
end
begin
        prog = irexec
        button = PLAY
        config = dcop kmplayer KmplayerIface play
end
If these two programs were playing DVDs (not really but this gets the point across), kaffeine was highlighted or the focus window, would the remote just execute the play button for kaffeine? Or would it try to execute both play buttons? Is the highlighted or the focus window the key here?

Also the config field - ex. dcop kaffeine KaffeineIface playDvb. Is this the standard format:
kaffeine = program name
KaffeineIface = program nameIface
playDvb = function
Is the above assumuption correct?
Thanks

---

### Post by williammanda on 2007-04-12
Once I make a change to the lircrc file, I usually restart the program that I'm trying to get the remote to work with. Do I need to restart irexec and irxevent too?
Thanks

---

### Post by newlinux on 2007-04-12
I think you are right about the config, but I don't have first hand experience so I can't be certain.

I think irexec would send commands to both apps regardless of which one had focus. This is what happens for me in gnome when I have two commands from one button in lircrc.

I'm not sure if you would have to restart them, but it can't hurt to try if something doesn't work.

Hope this gets you going... I think I might start using KDE more just to get familiar.

---

### Post by williammanda on 2007-04-12
The above questions stem from the idea of how I would like the remote to work. The remote would function for the application that has focus. I'm trying to filter through all the available infomation and hopefully find way to accomplish this.
Thanks for your help!

---

### Post by williammanda on 2007-04-12
I setup the lircrc file as ~/.lircrc with a symbolic link to /.mythtv/lircrc. Also I setup kaffeine using the dcop (kdcop) and it is working well. Here is a short take of the lircrc - mythtv 
```
## MYTHTV ##
begin
        prog = irexec
        button = TV
	repeat = 0
        config =  mythfrontend
end

# Mythtv
begin
prog = mythtv
button = UP
repeat = 3
config = Up
end

begin
prog = mythtv
button = DOWN
repeat = 3
config = Down
end

begin
prog = mythtv
button = LEFT
repeat = 3
config = Left
end

begin
prog = mythtv
button = RIGHT
repeat = 3
config = Right
end

# Channel Up
begin
prog = mythtv
button = CH+
repeat = 3
config = Up
end

# Channel Down
begin
prog = mythtv
button = CH-
repeat = 3
config = Down
end
```

Here is a short take of the lircrc - kaffeine
```
 ## KAFFEINE ##
begin
        prog = irexec
        button = DVD
        config =  kaffeine
end

### Kaffeine

begin
        prog = irexec
        button = OK
        config = dcop kaffeine KaffeinePartIface dvdMenuSelect
end

begin
        prog = irexec
        button = FIREFLY
        config = dcop kaffeine KaffeineIface playDVD
end

begin
        prog = irexec
        button = OK
        config = dcop kaffeine KaffeineIface enabled
end

begin
        prog = irexec
        button = PLAY
        config = dcop kaffeine KaffeineIface play
end

begin
        prog = irexec
        button = PAUSE
        config = dcop kaffeine KaffeineIface pause
end

begin
        prog = irexec
        button = STOP
        config = dcop kaffeine KaffeineIface stop
end

begin
        prog = irexec
        button = FWD
        config = dcop kaffeine KaffeineIface posPlus
end

begin
        prog = irexec
        button = REW
        config = dcop kaffeine KaffeineIface posMinus
end
```

I have a previous lircrc entry for mplayer, the way I was trying to get the remote to work:
```
### MPlayer lirc setup

# Show OSD
begin
prog = mplayer
button = MENU
repeat = 3
config = osd
end

# Pause playback
begin
prog = mplayer
button = PAUSE
repeat = 3
config = pause
end

# Skip ahead a minute if playing
# If paused, resume playing
begin
prog = mplayer
button = PLAY
repeat = 3
config = seek +1
end

# Stop playback and exit
begin
prog = mplayer
button = Back
repeat = 3
config = quit
end

# Mute
begin
prog = mplayer
button = MUTE
repeat = 3
config = mute
end

# Seek back 10 seconds
begin
prog = mplayer
button = LEFT
repeat = 3
config = seek -7
end

# Seek forward 30 seconds
begin
prog = mplayer
button = RIGHT
repeat = 3
config = seek +30
end

# Quit
begin
prog = mplayer
button = EXIT
repeat = 3
config = quit
end
```
I never could get this part to work. Is there something I am missing? 
Thanks

---

### Post by newlinux on 2007-04-12
Can you post your lircd.conf and your entire .lircrc file (not separated out)? That would help me troubleshoot it a bit. You could also post them as attachments.

Glad you got most of it working..

---

### Post by williammanda on 2007-04-13
Here are the files you requested.

---

### Post by newlinux on 2007-04-13
Just from a quick browse, it looks you are using many buttons in your .lircrc for mplayer that aren't defined in your lircd.conf. I think you have to have them match exactly. Do your PAUSE and PLAY buttons work for mplayer?

---

### Post by williammanda on 2007-04-13
I started out with a copy of a lircrc file and modified it to fit my needs, so there are still a few buttons that I didn't setup correctly (I didn't want to erase them).
I have tried several values in the config fields for play and pause buttons but no luck!

On a better note....I just got the mouse function working on the remote.
Here is are my files: xorg.conf & lircmd.conf

Thanks for your help!

---

### Post by majoridiot on 2007-04-13
you were close with mplayer-  try pasting this into your .lircrc and test it out:

```
### MPlayer lirc setup

# Show OSD
begin
prog = mPlayer
button = MENU
repeat = 3
config = osd
end

# Pause playback
begin
prog = mPlayer
button = PAUSE
repeat = 3
config = Pause
end

# Play/Pause
begin
prog = mPlayer
button = PLAY
repeat = 3
config = Pause
end

# Stop playback and exit
begin
prog = mPlayer
button = Back
repeat = 3
config = quit
end

# Mute
begin
prog = mPlayer
button = MUTE
repeat = 3
config = Mute
end

# Seek back 10 seconds
begin
prog = mPlayer
button = LEFT
repeat = 3
config = seek -10 0
end

# Seek forward 30 seconds
begin
prog = mPlayer
button = RIGHT
repeat = 3
config = seek +30 0
end

# Quit
begin
prog = mPlayer
button = EXIT
repeat = 3
config = quit
end

begin
    prog = mPlayer
    button = VOL+
    config = volume +1
end

begin
    prog = mPlayer
    button = VOL-
    config = volume -1
end

begin
    prog = mPlayer
    button = FWD
    config = seek +30 0
end

begin
    prog = mPlayer
    button = REW
    config = seek -30 0
end
```

it the same as the one you previously posted, with a few added buttons.

---

### Post by williammanda on 2007-04-14
majoridiot found out that executing mplayer in the console allowed lirc to work. All the  buttons worked fine. When kmplayer was started from the gui, lirc didn't work. I tried to find something about this on the web but failed.I also tried the KDE & mplayer irc rooms but got nothing. Any ideas?

---

### Post by newlinux on 2007-04-30
Perhaps kmplayer needs it own set of LIRC commands - possibly using DCOP? run kdcop and see if you find kmplayer in there, and then basically copy your mplayer mappings (don't overwrite them, just duplicate them) and make them kmplayer mappings (change mplayer to kmplayer in al the prog lines, and change the config lines to match the dcop commands you find in kdcop). This is purely a guess, but maybe worth looking into.

---

### Post by mihaicj on 2007-12-01
Can you please give me a few pointers on setting up lircmd on Gutsy. It doesn't seem to work. I tried using the posted lircmd.conf and xorg.conf but nothing is happening when try the buttons. Is any other step needed?

---

### Post by williammanda on 2007-12-18
What equipment are you using?
Thanks

---

### Post by ezramorris on 2008-01-09
> **williammanda said:**
> 

On a better note....I just got the mouse function working on the remote.
Here is are my files: xorg.conf & lircmd.conf

Thanks for your help!

Hi. May I ask how you got the mouse driver working? I have got lircd working for irexec and mplayer, but I'm not sure how to get the mouse going.

I had a look at the files you attached. My lircmd.conf is similar, and I put in xorg.conf:
InputDevice "LIRC-Mouse" "CorePointer"  --> server layout section 
and
Section "InputDevice"
        Identifier  "LIRC-Mouse"
        Driver      "mouse"
        Option      "Device" "/dev/lircm"
        Option      "Protocol" "IntelliMouse"
        Option      "SendCoreEvents"
        Option      "Buttons" "5"
        Option      "ZAxisMapping" "4 5"
EndSection

Is there anything else I need to do?

Thanks in advance.

---

### Post by ezramorris on 2008-01-09
I tried doing cat /dev/lircm, and it gives an output when I press the suitable mouse buttons, so I'm gessuing it's something to do with xorg.conf.

---

### Post by williammanda on 2008-01-11
This is what I have in my xorg.conf to enable the mouse function:

```
Section "InputDevice"
        Identifier  "LIRC-Mouse"
        Driver      "mouse"
        Option      "Device" "/dev/lircm"
        Option      "Protocol" "IntelliMouse"
        Option      "SendCoreEvents"
        Option      "Buttons" "5"
        Option      "ZAxisMapping" "4 5"
EndSection

```

and this:

```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	**InputDevice	"LIRC-Mouse"**

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

Add only the bold entry.

Just make these two entries as I have them and it should work.
Thanks

---

### Post by ezramorris on 2008-01-12
Hi,
It turned out that I had all the settings correct; I had forgotten to restart Xorg.

I did this and it worked. Strangely, every time I start my computer, I have to manualy restart Xorg to get it to work.

Thanks, anyway.

---

