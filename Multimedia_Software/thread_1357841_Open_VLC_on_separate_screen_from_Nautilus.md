---
title: "Open VLC on separate screen from Nautilus"
date: 2009-12-17
forum: Multimedia Software
---

### Post by kloper on 2009-12-17
Hi,

I've just installed Ubuntu 9.10 on a PC with Nvidia 7600GT. I have one Samsung monitor and one TV hooked up.

I have used nvidia-settings and now I have a setup with separate screens. The monitor is display 0 (1280x1024) and the TV is display 1 (1024x768).

I want to watch movies on the TV, so I want to open video files in Nautilus, and the VLC player will open on the TV in full-screen mode.

I can do this in the terminal:
DISPLAY=:0.1 vlc <video file>

But then there's the Girlfriend Factor, so I need to make this work in Nautilus. Can I write a macro or something in Nautilus?

Cheers!

---

### Post by ajgreeny on 2009-12-17
Use that command in a shell script, make it executable and then all she needs to do is double click on it for it to work.  Call it something appropriate when you save it as a .sh file.
```
#!/bin/bash
DISPLAY=:0.1 vlc <video file>

```Or at least, I can't see why it will not work. Worth a try.  The only problem I see is the <video file> name entry, which may need some variable in the script.

---

### Post by fatum on 2009-12-20
I have the same issue. I wish VLC would implement the same screen selection as they do on OS X. It is just a selection in the Video menu and then you hit full screen. 
I am just starting on programming and all but is there a way to create a user input that just calls that input at the end of the command for terminal? so something like (in sinmple terms)

raw_input 
file=raw_input

run
 DISPLAY=:0.1 vlc file

make it so it can be a drag/drop on the executable to make the file open automatically and start playing.

---

### Post by joris1977 on 2009-12-20
Hi 

Was looking for the same thing and found a nice solution here:

[http://swiss.ubuntuforums.org/showthread.php?t=1231694]("http://swiss.ubuntuforums.org/showthread.php?t=1231694")

if the link ever disappears for some reason:

```
#!/bin/bash
export DISPLAY=:0.1 && vlc "$1"
```

save this script as for example television.  Make it executable and than you can open any videofile with just two clicks on the tv screen.

right mouse-click on any videofile and select open with television and there you go. Type F to get fullscreen

:popcorn:

---

### Post by fatum on 2009-12-20
> **joris1977 said:**
> Hi 

Was looking for the same thing and found a nice solution here:

[http://swiss.ubuntuforums.org/showthread.php?t=1231694]("http://swiss.ubuntuforums.org/showthread.php?t=1231694")

if the link ever disappears for some reason:

```
#!/bin/bash
export DISPLAY=:0.1 && vlc "$1"
```

save this script as for example television.  Make it executable and than you can open any videofile with just two clicks on the tv screen.

right mouse-click on any videofile and select open with television and there you go. Type F to get fullscreen

:popcorn:

I am very happy with this solution to the problem. And I do not want to sound rude asking this so please do not take it that way. 

It is very nice to have the solution to a problem but is there a way to explain why this works? Why does this script have "export DISPLAY" where the first one only has "DISPLAY"? I understand that both are calling DISPLAY but why the "export"? How does the "0.1" work when the displays connected are 0 and 1 neither is called by 0.1? Why the two "&&" before calling VLC? Why not just call VLC? And what does the "$1" at the end of the script do? 

I like being able to find answers to issues but I feel it is sometimes just giving the fish instead of teaching to fish, using an old analogy. But for me without understanding why it works then I do not feel I learned anything. 

Thank you for any reply I do appreciate it.

---

### Post by kloper on 2009-12-20
Hi guys,

Thanks for all your good advice!

I found a [guide]("http://g-scripts.sourceforge.net/faq.php") how to make a Nautilus script.

I managed to get it working, I created a shell script:

```
nano .gnome2/nautilus-scripts/TV
```

The content of the script:

```
#!/bin/sh
DISPLAY=:0.1 vlc --volume 512 --play-and-exit --fullscreen "$1"
```

I then made the script executable:

```
chmod a+x .gnome2/nautilus-scripts/TV
```

Then my TV script will appear in the context menu. If I right-click a video file and then select the sub-menu "Scripts", I can now choose "TV" and the video will open on my TV. :-)

I still have two problems:

[LIST]
[*]The screensaver starts after 5 minutes, is there a way to disable the screensaver when VLC starts? At least for the TV
[*]I have no VLC controls, it would be great if I can somehow have the VLC control window (pause, play, skip, volume, etc) open up on the monitor screen so I can, for example, skip to a certain point in time
[/LIST]

---

### Post by Agent ME on 2009-12-20
> **kloper said:**
> I still have two problems:

[LIST]
[*]The screensaver starts after 5 minutes, is there a way to disable the screensaver when VLC starts? At least for the TV[/list]
Change the script to this:
```
#!/bin/sh
gnome-screensaver-command -i -n "VLC" &
INHIBIT=$!
DISPLAY=:0.1 vlc --volume 512 --play-and-exit --fullscreen "$@"
kill $INHIBIT
```
The "gnome-screensaver-command -i" command disables the screensaver temporarily. The next line saves the process id of the screensaver inhibitor. Next, VLC is run, and after VLC is done, the process id saved in the $INHIBIT variable is killed (so the screensaver can run again). I also changed the 4th line to use "$@" instead of "$1", so multiple parameters can be passed.

> **kloper said:**
> [list][*]I have no VLC controls, it would be great if I can somehow have the VLC control window (pause, play, skip, volume, etc) open up on the monitor screen so I can, for example, skip to a certain point in time
[/LIST]
I don't know a direct solution for that, but maybe you can use the keyboard controls? I don't know if you can really give focus to VLC being on the other display though. Space is play/pause.

---

### Post by fatum on 2009-12-20
> **Agent ME said:**
> Change the script to this:
[CODE] I also changed the 4th line to use "$@" instead of "$1", so multiple parameters can be passed.

I made this change to my script that this thread has helped me create. But after doing so the top and bottom bars for Gnome show on the screen at all times. What is the purpose of making it so multiple parameters can be passed? 

As for control space bar does work to pause/play as long as my mouse is over on that screen. I have not tried any other keyboard shortcuts.

---

### Post by Agent ME on 2009-12-20
> **fatum said:**
> I made this change to my script that this thread has helped me create. But after doing so the top and bottom bars for Gnome show on the screen at all times. What is the purpose of making it so multiple parameters can be passed?
What does your script look like right now? If the only change you did from your previous one was to change "$1" to "$@", I'm not sure why anything would really change. What do you mean by make the top and bottom bars for gnome show? Do you have them set to autohide?

---

### Post by joris1977 on 2009-12-21
> **fatum said:**
> I am very happy with this solution to the problem. And I do not want to sound rude asking this so please do not take it that way. 

It is very nice to have the solution to a problem but is there a way to explain why this works? Why does this script have "export DISPLAY" where the first one only has "DISPLAY"? I understand that both are calling DISPLAY but why the "export"? How does the "0.1" work when the displays connected are 0 and 1 neither is called by 0.1? Why the two "&&" before calling VLC? Why not just call VLC? And what does the "$1" at the end of the script do? 

No I am really sorry, but I can't help you. I  don't know anything about programming. I was googling for the same 'problem' and then I found this thread and after that the other thread with a solution, so I decided to post that back here. Maybe somebody else can enlight you or you can send a pm to the poster in the other thread. 

good luck

---

### Post by fatum on 2009-12-21
> **Agent ME said:**
> What does your script look like right now? If the only change you did from your previous one was to change "$1" to "$@", I'm not sure why anything would really change. What do you mean by make the top and bottom bars for gnome show? Do you have them set to autohide?

The only change that I did to the script was "$1" to "$@" and the top menu bar was showing while playback was happening. When I changed it back to the original "$1" the menu bar does not show up.

---

### Post by fatum on 2009-12-21
> **joris1977 said:**
> No I am really sorry, but I can't help you. I  don't know anything about programming. I was googling for the same 'problem' and then I found this thread and after that the other thread with a solution, so I decided to post that back here. Maybe somebody else can enlight you or you can send a pm to the poster in the other thread. 

good luck

Thank you very much for the reply and thank you again for the original post/solution. It helped greatly. I have done more searching into why it works and plan on posting an explanation once I have it all figured out.

---

### Post by kloper on 2009-12-22
> **fatum said:**
> Why does this script have "export DISPLAY" where the first one only has "DISPLAY"? I understand that both are calling DISPLAY but why the "export"?

The *export* command makes the shell script remember the environment variable (DISPLAY) for the rest of the script's/shell's lifetime. So the following commands will open vlc and firefox on my TV, because the DISPLAY variable is remembered (exported):

```
export DISPLAY=:0.1
vlc
firefox

```

If you specify an environment variable ("DISPLAY=:0.1") before a command ("vlc"), the environment variable will only be available for that command. In the following example, firefox will therefore be opened on my monitor, because DISPLAY is only available for the first command ("vlc"):

```
DISPLAY=:0.1 vlc
firefox

```

> **fatum said:**
> How does the "0.1" work when the displays connected are 0 and 1 neither is called by 0.1?

Most of the counting in programming starts with zero (0,1,2,3,4...), not one (1,2,3,4,5,...) as we are used to in real life.
My guess: the "0" stands for "the first video card" and the "1" stands for "second screen for that video card".

You can learn more [here]("http://support.objectplanet.com/esupport/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=17").

> **fatum said:**
> Why the two "&&" before calling VLC? Why not just call VLC?

If you place "&&" between two commands (in this case "export" and "vlc") the command on the right will not be executed if the command on the left fails. You usually do this to ensure that A happens before B happens.

```
export DISPLAY=:0.1 && vlc
```

The above example means that if the export command fails, vlc will not be started. If you type like this instead:

```
export DISPLAY=:0.1
vlc
```

Then VLC will always be opened even if the export command fails. But if the export command fails, VLC will be opened on your monitor.

> **fatum said:**
> And what does the "$1" at the end of the script do?

"$1" means "the first argument" to the script. When you open a video using the script from Nautilus, Nautilus will send the video filename as first argument. You will therefore give the filename to vlc by using "vlc $1". Example from terminal:

```
.gnome2/nautilus-scripts/TV my_cool_video.avi
```

"$@" means sending all arguments instead of just the first.

> **fatum said:**
> I like being able to find answers to issues but I feel it is sometimes just giving the fish instead of teaching to fish, using an old analogy. But for me without understanding why it works then I do not feel I learned anything.

[Here]("http://www.ibm.com/developerworks/library/l-bash.html") is a Bash tutorial from IBM Developerworks if you want to learn more.

---

### Post by fatum on 2009-12-22
Kloper thank you very much. I will be reading that link to IBM when I get a chance. I realize now that I have had no clue how much can be done with bash. That is going to be my first undertaking for understanding Linux better.
For some reason even though I knew it was a bash script I was thinking we were making a script that used built in commands from vlc. Definitely have a lot to learn about Linux.

---

### Post by joris1977 on 2010-02-02
A bash script is nice, but I was still missing a way to control the player from the computer while playing a film on the tv. Of course you could learn the shortcuts from vlc or mplayer, but controlling from a gui is  much easier. 

So I figured smplayer out that smplayer can do this. Smplayer is a very nice front end to mplayer. 

It is easy to use smplayer for your tv-out. Under preferences -> advanced -> advanced -> select run mplayer in its own window

Than under 'options for mplayer' -> add this option -> 

```
-display :0.1 
```

apply and if you start a movie in smplayer it starts playing on your tv

:popcorn:

see this thread for more info:
[url=http://smplayer.berlios.de/forum/viewtopic.php?f=2&t=89]
http://smplayer.berlios.de/forum/viewtopic.php?f=2&t=89[/url]

---

### Post by MrQuincle on 2010-11-22
Some little script I use:

```

vlc --qt-fullscreen-screennumber=2 --play-and-exit -f $FILE

```

---

