---
title: "Howto: Pandora via command line.    -- pianobar --"
date: 2010-07-17
forum: Multimedia Software
---

### Post by greenwom on 2010-07-17
I just found this and it's not new.  There are some posts about it.
Here is the consolidated how-to

Pianobar is a command line tool: [Dev's Link]("http://github.com/PromyLOPh/pianobar")

Make sure you have what you need to compile the software

```
sudo apt-get install build-essential
```

install the dependencies

```
sudo apt-get install libao-dev libmad0-dev libfaad-dev
```

download the source
```
wget http://github.com/PromyLOPh/pianobar/archives/master/PromyLOPh-pianobar-3631791.tar.gz

```

or download it from 
[http://github.com/PromyLOPh/pianobar](http://github.com/PromyLOPh/pianobar)

untar it
```
tar xvf Promy*.tar.gz
```

change directory
```
cd Promy*
```

compile
```
make

sudo make install

```

then start the program & follow the prompts to log in.
```
pianobar
```

Press "+" if you want to give the song a thumbs up.
Press "-" if you want to give the song a thumbs down.

Press "N" to skip the song.

Pretty sweet! No more flash crashing or having the browser open for no reason.

Hope this helps

---

### Post by v1ad on 2010-07-18
sweet perfect explanation. is there a way 2 pause it?

---

### Post by greenwom on 2010-07-19
Just hit "P"

Just like any other command you can always look at the man page to get instructions and descriptions.

```
$ man pianobar
```

---

### Post by v1ad on 2010-07-19
> **greenwom said:**
> Just hit "P"

Just like any other command you can always look at the man page to get instructions and descriptions.

```
$ man pianobar
```

sorry for the stupid post, i didn't think.

---

### Post by v1ad on 2010-07-19
```
  act_stationdelete = d
              Delete current station.

       act_songexplain = e
              Explain why this song is played.

       act_stationaddbygenre = g
              Add genre station provided by pandora.

       act_history = h
              Show history.

       act_songinfo = i
              Print information about currently played song/station.

       act_addshared = j
              Add shared station by id. id is a very long integer without "sh"
              at the beginning.

       act_songmove = m
              Move current song to another station

       act_songnext = n
              Skip current song.

       act_songpause = p
              Pause/Continue

       act_quit = q
              Quit pianobar.

       act_stationrename = r
              Rename currently played station.

       act_stationchange = s
              Select another station.

```

---

### Post by nhasian on 2010-07-21
thanks greenwom, pianobar is a lot less resource intensive than playing pandora through flash.

---

### Post by greenwom on 2010-07-22
Just a FYI, for some reason, I can't wget the file.  It's resolving and downloading a file with that name but it's not a tar ball.  So just go to the web site (link above and download it through the browser.)  Then the tar ball will be right.

---

### Post by nhasian on 2010-07-24
> **greenwom said:**
> Just a FYI, for some reason, I can't wget the file.  It's resolving and downloading a file with that name but it's not a tar ball.  So just go to the web site (link above and download it through the browser.)  Then the tar ball will be right.

yes thats what i had to do as well.  i thought it was just me ;)

---

### Post by v1ad on 2010-08-21
yea the problem is you don't get the header info when you download through wget.

you can download it through the link below. 

[http://github.com/PromyLOPh/pianobar/tarball/master]("http://github.com/PromyLOPh/pianobar/tarball/master")

or use the link in the first post.

---

### Post by v1ad on 2010-08-21
also if you want to customize your pianobar for autologin. make, save, and edit this script to your needs in /home/your_user_name/.config/pianobar/config

the config will be the file name.

```

# This is an example configuration file for pianobar. You may remove the # from
# lines you need and copy/move this file to ~/.config/pianobar/config
# See manpage for a description of the config keys
#
# User
#user = your_pandora_username
#password = your_pandora_password

# Proxy (for those who are not living in the USA)
#control_proxy = http://127.0.0.1:9090/

# Keybindings
#act_help = ?
#act_songlove = +
#act_songban = -
#act_stationaddmusic = a
#act_stationcreate = c
#act_stationdelete = d
#act_songexplain = e
#act_stationaddbygenre = g
#act_songinfo = i
#act_addshared = j
#act_songmove = m
#act_songnext = n
#act_songpause = p
#act_quit = q
#act_stationrename = r
#act_stationchange = s
#act_songtired = t
#act_upcoming = u
#act_stationselectquickmix = x

# Misc
# mp3, mp3-hifi or aacplus
#audio_format = mp3
#autostart_station = 123456
#event_command = /home/user/.config/pianobar/eventcmd
#sort = quickmix_10_name_az


```

uncomment the lines that you will use. i will try to work on a script that will run it in a screen in the foreground.

---

### Post by chaanakya_chiraag on 2010-09-17
Very nice!!! :)

---

### Post by spkoc on 2010-10-17
edit. Found a way to enable auto_start: [http://talk.maemo.org/showpost.php?p=491405&postcount=36](http://talk.maemo.org/showpost.php?p=491405&postcount=36)

Basically the number that has to be input in the config file is this long long string of integers that appears when a station starts playing in the terminal(as opposed to 0, 1, 2 etc whatever number you give pianobar in the terminal station chooser).


Hey, I'm trying to get pianobar to autoload a certain station(say station 0). However though I've uncommented

```
Misc
autostart_station = 4
```It just gives an "Error: Autostart station not found." when it starts(despite station 4 existing in the options list).

Oh and just in case someone else struggled to figure out how to add pianobar to startup make a pianobar.sh file somewhere and link to it when adding a new startup program. In pianobar.sh write:

```
#!/usr/bin/env bash
gnome-terminal -c pianobar
```This also works for creating a shortcut that automatically opens a terminal and starts pianobar. As an added feature the terminal is opened in the background(which is less of a feature since it doesn't actually autostart a station :().

---

### Post by hermdog on 2011-01-03
i have 10.10 installed on several boxes at home, and i was able to apt-get install pianobar onto them all. i didnt have to make any changes or wget anything.

loving this program! been using it non-stop since i installed it.

---

### Post by akshayc11 on 2011-04-03
Figured out the Autostart problem:

When you enter your Station(0-whatever), you will notice a HUGE number in brackets at the end of the next line. 

Copy and paste that in the autostart option and you are good to go.
Dunno why this cant be fixed, but anyway....

Now, hoping for a GUI skin over this AWESOME CLI

---

### Post by EveyCurls on 2011-04-16
Just wanted to say thanks to everyone that's posted. I figured pianobar out and now I'm really excited to not have to deal with Pandora's crazy flash issues. Thanks!

---

### Post by Tubboi on 2011-07-19
> **spkoc said:**
> Oh and just in case someone else struggled to figure out how to add pianobar to startup make a pianobar.sh file somewhere and link to it when adding a new startup program. In pianobar.sh write:

```
#!/usr/bin/env bash
gnome-terminal -c pianobar
```This also works for creating a shortcut that automatically opens a terminal and starts pianobar. As an added feature the terminal is opened in the background(which is less of a feature since it doesn't actually autostart a station :().

how do i access/control this background terminal? ive looked around a bit online.. "jobs" doesn't return anything. "ps" shows "bash" and "ps," and trying to use fg %-pid- returned "bash: fg: %-pid-: no such job (-pid- being the pid of said job).

some help would be much appreciated!

---

### Post by Subito Piano on 2011-12-28
Hmm - can't make install:

```
me@ubuntu:~/PromyLOPh-pianobar-a33f98d$ sudo make install
    CC  src/main.c
In file included from src/main.h:28,
                 from src/main.c:52:
src/libwaitress/waitress.h:30:27: error: gnutls/gnutls.h: No such file or directory
In file included from src/main.h:28,
                 from src/main.c:52:
src/libwaitress/waitress.h:99: error: expected specifier-qualifier-list before ‘gnutls_certificate_credentials_t’
src/main.c: In function ‘BarMainGetLoginCredentials’:
src/main.c:106: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
src/main.c: In function ‘main’:
src/main.c:341: warning: implicit declaration of function ‘gnutls_global_init’
src/main.c:390: warning: implicit declaration of function ‘gnutls_global_deinit’
make: *** [src/main.o] Error 1

```

I'm 64-bit - perhaps that's the problem?

---

### Post by rjh336 on 2012-01-05
Getting the following error message when trying to compile:

```
hill2@ubuntu:~/pianobar$ make
    CC  src/main.c
In file included from src/main.h:28:0,
                 from src/main.c:52:
src/libwaitress/waitress.h:30:27: fatal error: gnutls/gnutls.h: No such file or directory
compilation terminated.
make: *** [src/main.o] Error 1

```Im on ubuntu 11.10

---

### Post by ivesjd on 2012-01-07
```
 CC  src/main.c
In file included from src/main.h:28:0,
                 from src/main.c:52:
src/libwaitress/waitress.h:30:27: fatal error: gnutls/gnutls.h: No such file or directory
compilation terminated.
make: *** [src/main.o] Error 1
```

I would hope it is not because I'm running x64... Running 6GB of RAM I need it. :P

---

### Post by elrond_14 on 2012-01-25
For those who had this issue:

```
 CC  src/main.c
In file included from src/main.h:28:0,
                 from src/main.c:52:
src/libwaitress/waitress.h:30:27: fatal error: gnutls/gnutls.h: No such file or directory
compilation terminated.
make: *** [src/main.o] Error 1
```Try installing libgnutls-dev:

```
sudo apt-get install libgnutls-dev
```

---

### Post by alexhayes on 2012-04-04
Hello all,

Below is a script I've made to make it easy for new users to install pianobar. Copy the code into a file in your home directory, called 'pianobar-install.sh'. You can change your username and password to automatically login yourself in.

**Update**: This script was working as of May 1st, when pianobar added json its dependencies.

```
#!/bin/bash

#this is a script designed to install the latest version of pianobar
echo 'moving to downloads folder'
cd ~/Downloads

echo 'downloading pianobar source'
wget http://github.com/PromyLOPh/pianobar/tarball/master

echo 'renaming to compress file'
mv master pianobar.tar.gz

echo 'extracting tarball'
tar -xvf pianobar.tar.gz

echo 'renaming ugly tarball'
mv Promy* pianobar-install-files

echo 'entering source directories'
cd pianobar-install-files

echo 'installing dependencies'
sudo apt-get install libao-dev libgnutls-dev libfaad-dev libmad0-dev libjson0-dev libjson0

echo 'compiling'
make clean && make

echo 'installing'
sudo make install

echo 'cleaning up leftover files'
cd ~/Downloads
rm pianobar.tar.gz && rm -rf pianobar-install-files

if [ -f ~/.config/pianobar/config ]; then
    echo "pianobar already configured"
else
    echo 'writing configuration file'
    cd ~/.config
    mkdir pianobar
    cd pianobar
    echo 'user = your.user@name.com' > config
    echo 'password = your.password' >> config
fi

```Make it executable and run it as sudo.

```

sudo chmod +x pianobar-install.sh
./pianobar-install.sh

```The latest version of pianobar will be installed. There is currently a version of pianobar in the repositories that can be installed with 'sudo apt-get install pianobar', but it is not the most recent version and wasn't working for me as of April 3rd (Error: protocol incompatible, please upgrade libpiano). This script will update pianobar to the latest version and fix that error.

---

### Post by joksanxfr on 2012-05-20
Thanks for the script dude, it was of great help

---

### Post by neonpolaris on 2012-09-23
Thank you SO much for putting all of the proper requirements in one place. I can confirm that this works on the Raspberry Pi! I was pulling my hair out trying to get this to work. Thank you again!

---

