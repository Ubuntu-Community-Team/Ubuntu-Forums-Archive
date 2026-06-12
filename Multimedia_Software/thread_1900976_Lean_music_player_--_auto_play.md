---
title: "Lean music player -- auto play?"
date: 2011-12-27
forum: Multimedia Software
---

### Post by mk5500 on 2011-12-27
I'd like a media player (maybe something like Decibel) that I can put in the startup applications and have it automatically play my music folder.

Also need shuffle mode and no repeats.

Is there any player (lean or not) that I can get to do that?

Didn't see anything obvious with banshee or the decibel player I installed.

Once again --

PC ON > player auto starts > player plays the music folder


Thanks !  Using Ubuntu 11.10  (new user)

---

### Post by mk5500 on 2011-12-28
really? nobody?

seems like a simple issue -- maybe not.

---

### Post by rubylaser on 2011-12-28
If you really want it to start and run automatically, I'd be looking at a way to script this.  Personally, I'd use mplayer, and write up a bash script to create my playlist and play it back shuffled.  Something like t[his]("http://www.cyberciti.biz/faq/mplayer-shuffle-ubuntu-redhat-fedora-debian-bsd/") should get you pointed in the right direction.

Mplayer can also playback audio files, so don't be concerned that this is only discussing video files.  It doesn't get much more lean than the CLI ;)

---

### Post by mk5500 on 2011-12-28
Awesome -- thanks very much -- sounds like that will do the trick.

I'll get back if I can't get it working.

---

### Post by mk5500 on 2011-12-30
I have a lot on my plate right now -- I program vbnet and other "stuff", so not a chicken but I don't have time to research this.

I have Ubuntu 11.10 and it will start the banshee player when I turn on the PC --

I'd appreciate any **specific** instructions on what to do to get it to autoplay my music folder.

A bash script, no doubt, but I'll kiss you for a "copy and paste" so I can just get this going. (banshee or any music player).

THANKS

---

### Post by mk5500 on 2011-12-30
Is it possible to just add something to the command in my application startup?

Like I say, I put Banshee in the app auto start and that works fine -- now, just want it to kick on and play the music folder (in shuffle mode)    thanks !

---

### Post by rubylaser on 2011-12-30
I'm not going to go down the Banshee route because it has limited cli options, so you'd always have to interact with it which is not what you asked for.  So, the first thing you'd need to do is install mplayer.

```
sudo apt-get install mplayer
```

Then, you'd need to have a simple init script to run when the machine starts up.
```
sudo gedit /etc/init.d/auto_music_starter
```

and paste something like this in.
```

#! /bin/sh
# /etc/init.d/auto_music_player

# Some things that run always
touch /var/lock/auto_music_player

# Carry out specific functions when asked to by the system
case "$1" in
  start)
    echo "Starting Auto Music Player"
    cd /home/rubylaser/Music
    find . -name "*.mp3" -o -name "*.aac" -o -name "*.m4a" > playlist.txt
    mplayer -shuffle -playlist /home/rubylaser/Music/playlist.txt
    ;;
  stop)
    echo "Stopping Auto Music Player"
    mplayer_pid=`ps -C mplayer | tail -n1 | sed -e 's/^[ \t]*//' | cut -d " " -f1`
    kill -9 "$mplayer_pid"
    ;;
  *)
    echo "Usage: /etc/init.d/auto_music_player {start|stop}"
    exit 1
    ;;
esac

exit 0

```

You'll want to replace the /home/**rubylaser** with your username. Then set the script up to be executable.
```
sudo chmod +x /etc/init.d/auto_music_starter
```

Then, set it up to be run at startup and shutdown.
```
sudo update-rc.d auto_music_starter defaults 99
```

The 99 has it startup late in the boot process, otherwise my music ended up sounding like it was playing back at a slower rate than it should be.  You can start and stop the player from the command line at any time too.

```
sudo /etc/init.d/auto_music_starter stop
```
```
sudo /etc/init.d/auto_music_starter start
```

I hope that helps :)

---

### Post by mk5500 on 2011-12-30
How incredibly kind ! -- thanks so much. I'll get this going but I'm an absolute novice with Unix -- I'll figure it out how to get it to execute.

BUT -- of course I may get back with some other questions -- no experience at all with running scripts on Unix.

Many tutorials out there -- I'll get media player installed first.

Then, when I get it installed in startup applications, I can maybe just add your start code to the CLI?

Whatever -- I'll get er going -- thanks again !!!

---

### Post by rubylaser on 2011-12-30
You don't need to add it to startup applications.  If you follow my instructions exactly as I've written, and just change the paths to your music library, it will just work :) You'll just need to open a Terminal in Unity and copy / paste my commands in.

---

### Post by mk5500 on 2011-12-30
sounds great -- going to tackle it tomorrow morning -- I'll get it running I'm sure.

thanks again.

---

### Post by mk5500 on 2011-12-31
I know I probably shouldn't ask this as it's an UBUNTU forum but I have several P3 733 motherboards I hate to junk and thought I'd turn them into MP3 players.

So, mplayer is the right choice but I also need to ask which distro would be better suited? I don't need ANYTHING but a platform to run mplayer on and that's it. Something CLI friendly as well.

Also -- I'm limited to 512mb ram with these machines and I do want to boot from a hard drive, not CD.

Perhaps a leaner version of Ubuntu or ??

Thanks kindly.

---

### Post by rubylaser on 2012-01-01
Here are a few. :)
[Crunchbang]("http://crunchbanglinux.org/")
[Lubuntu]("http://lubuntu.net/")
[Xbuntu]("http://www.xubuntu.org/")

There are tons more, but those are just handfull off the top of my head.

---

### Post by mk5500 on 2012-01-01
Thanks Ruby !

---

### Post by mk5500 on 2012-01-03
working on this now --

this line --

find . -name "*.mp3" -o -name "*.aac" -o -name "*.m4a" > playlist.txt

just wanted to check if it's OK noticed a period there instead of the -o in the other lines --  don't know script so thought I'd ask.

---

### Post by mk5500 on 2012-01-03
I see it's ok the way you have it -- oh well can't get it to work.

I'll keep trying -- sure I will.

starting here --

[http://freeengineer.org/learnUNIXin10minutes.html](http://freeengineer.org/learnUNIXin10minutes.html)

---

### Post by mk5500 on 2012-01-03
First of all -- what is SUDO and how can I get past all of this password nonsense?

Here's what I can do in terminal (I'm using Lububtu and mplayer)

cd /home/mike/Music
mplayer -shuffle *.mp3

and they play fine.

BUT I can't get a grasp on much else in your code -- I'm not usinfg a playlist, so I made that change and of course changed to my user name. so in "starting music player", I just substituted what i did above.

Are you saying that as long as this line is there and I "save" it will MAKE the code executable? --
sudo chmod+x /etc/init.d/auto_music_player

?

I did a copy and paste on everything (of course left out "code:"
and your comments but can't get it running.

Even just did the line--
sudo /etc/init.d/auto_music_starter start  (no such command)

also I get a lot of crap on the screen when I load GEDIT "gtk error"  theme parsing? lines and lines of it then gedit comes up.

god this is fun.

---

### Post by mk5500 on 2012-01-03
If you don't mind would love to go over this with you step by step.

Code:
sudo apt-get install mplayer

already installed on Lubuntu -- cool


Then, you'd need to have a simple init script to run when the machine starts up.
Code:
sudo gedit /etc/init.d/auto_music_starter

gedit wasn't installed, it is now, but getting a lot of weird lines before it starts relating to "GTK error"  "Theme parsing" BUT it does come up after 5 or 10 seconds of this crap. So, with GEDIT we're calling our script "auto_music_starter"  correct?


and paste something like this in.
Code:
#! /bin/sh

Always the first line in a shell script?


# /etc/init.d/auto_music_player

And this is where it will be saved? (etc/init.d ?)


# Some things that run always
touch /var/lock/auto_music_player

touch -- var -- lock ?  what is this?


# Carry out specific functions when asked to by the system
case "$1" in
  start)
    echo "Starting Auto Music Player"
    cd /home/rubylaser/Music
    find . -name "*.mp3" -o -name "*.aac" -o -name "*.m4a" > playlist.txt
    mplayer -shuffle -playlist /home/rubylaser/Music/playlist.txt
    ;;
  stop)
    echo "Stopping Auto Music Player"
    mplayer_pid=`ps -C mplayer | tail -n1 | sed -e 's/^[ \t]*//' | cut -d " " -f1`
    kill -9 "$mplayer_pid"
    ;;
  *)
    echo "Usage: /etc/init.d/auto_music_player {start|stop}"
    exit 1
    ;;
esac

exit 0


Ok, with the above I just replaced the start code with --

start)
echo "Starting auto music player"
cd /home/mike/Music
mplayer -shuffle *.mp3

stop) 
left all the rest as is



You'll want to replace the /home/rubylaser with your username. 

Did that

Then set the script up to be executable.

sudo chmod +x /etc/init.d/auto_music_starter

Ok -- so just having this line in the text file makes it execute?
Or do I something more?

Then, set it up to be run at startup and shutdown.

sudo update-rc.d auto_music_starter defaults 99

The 99 has it startup late in the boot process, otherwise my music ended up sounded like it was playing back at a slower rate than it should be. 

OK

You can start and stop the player from the command line at any time too.

sudo /etc/init.d/auto_music_starter stop

sudo /etc/init.d/auto_music_starter start

OK -- but no go -- says "command not found"
and like I say, not getting an auto start and play either.


THANKS. !

---

### Post by nothingspecial on 2012-01-03
2 things from a quick glance

```
sudo chmod +x /etc/init.d/auto_music_starter
```

That doesn't go in the script itself, you type that in the terminal having created the script and saved it to make it executable.

```
mplayer -shuffle *.mp3
```

will not play the mp3s in your Music directory unless there are only mp3s in there and they are not in artist/album folders. The find bit in the original script will find any mp3 in all the subdirectories however deep of your Music.

Also, gedit is Ubuntu's default text editor, lubuntu uses leafpad. I would think you wouldn't get the errors if you used that instead.

Like I say, I've only given it a quick glance.

Oh, and please put any commands or terminal output in code tags by highlighting it and clicking the # button in the formatting options at the top of the posting box. Thanks :)

---

### Post by mk5500 on 2012-01-04
So the script is the code from --

#!

blah blah blah

exit 0      (correct?)


# /etc/init.d/auto_music_player  (2nd line)


And this is where it will be saved? (etc/init.d ?)

BUT -- there's a pound sign there, isn't that a comment? ?

(the script should be saved in the /etc/init.d    folder?)


THEN you go back to terminal and simply type --

sudo chmod +x /etc/init.d/auto_music_starter

which makes it an exe file?  (compiles it)(yeah but where did 
auto_music_PLAYER go?)



so you'll have 2 files in /etc/init.d ?

the source code file (auto_music_player) and the exe,(auto_music_starter) 


am I getting this right?

---

### Post by mk5500 on 2012-01-04
Have it working but we'll see.

Problem I was having was the line update-rc.d

It look like it was written update--rc.d ?

Anyway -- here's what I have and at least it starts ans plays. I'll add the other stop code later. I left some things out for now.


#! /bin/sh
# /etc/init.d/auto_music_player

touch /var/lock/auto_music_player

    echo "Starting Auto Music Player"
    cd /home/mike/Music
    mplayer -shuffle *.mp3
    ;;
  
exit 0

saved that and then in terminal --

sudo chmod +x /etc/init.d/auto_music_starter (to compile,right?)

then --

sudo update-rc.d auto_music_starter defaults 99


Actually, may have been me that put in the -- rather than -
anyway it starts and plays but do you see anything wrong? Like I say will put in the stop code -- if I always give it a hard power off -- will the routine become unstable as is?

---

### Post by rubylaser on 2012-01-31
Sorry for the massive late response, I usually lurk around in the Server forums and hardly ever check in on the multimedia forum.  I'm glad to see you got it working.  It would be to your benefit to add the stop and restart sections to your init file.  If you don't add the stop section, you'll notice your music will continue to play even when you shutdown / logout.  If you add the stop section, it will gracefully kill that process for you so the computer doesn't hang on shutdown.

---

