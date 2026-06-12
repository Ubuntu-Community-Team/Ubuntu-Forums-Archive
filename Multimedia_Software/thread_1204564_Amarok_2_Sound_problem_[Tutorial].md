---
title: "Amarok 2 Sound problem [Tutorial]"
date: 2009-07-04
forum: Multimedia Software
---

### Post by Drk Guy on 2009-07-04
(As a rule of thumb) READ THE ENTIRE TUTORIAL BEFORE ACTUALLY DOING ANYTHING!!!!

No this is not a "Gimme a solution, kthxbai" thread, i'm giving you my solution, after having wondered A LOT in the Internetz (:lolflag:), i've found a solution, and a very simple one, you have to be able to know your way in konsole already, cuz i dont have too much time to explain what wget does...

1. Update ALSA
For some odd reason, the phonon-gstreamer backend didnt work until i   updated ALSA compiling it from source (?), so i'll teach you how to do that:

1.1 Check the links
Fire up your favorite note-taking app and copy-paste the download links that appear in [www.alsa-project.org](www.alsa-project.org) for:
- Alsa driver
- Alsa lib
- Alsa tools

1.2 Download Stuff
Now, fire up a console, and create a special directory for those files, then:
```
wget <link>
```
As of today (4th of July), the latest version is 1.0.20, so i'll post steps for those:
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2
```
```
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2
```
```
wget ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.20.tar.bz2
```

1.3 Extract the archives
Now that you have those on a folder, do as follows:
```
tar xvjf <filename>
```
for each file, that will extract them to an almost-usable state, if you're lazy enough to write down the complete filename (as i do :D) you can just write down "alsa-l" and push TAB (If you're using bash, if you dont know what the hell is bash, just push it, idk about other shells) so the filename of the alsa lib package will be auto-completed, so you dont have to write it down, do it again for each of the three files, those commands  will generate three different folders with similar names to the ones of the compressed files.

1.4 Compile
Now i'll only explain this once ¬¬ (Hey, i'm volunteering my time :p), cd into alsa-driver folder (remember the Tab thingy? it works for *virtually* anything...) and run this:
```
 sudo apt-get -y install build-essential ncurses-dev gettext xmlto linux-headers-`uname-r` 
``` (That wasn't actually *compiling* the program, this was the easy part, installing the dependancies ;) now do this:
```
 ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r) 
``` (The hda-intel thingy is for ppl using realtek integrated HD audio, that can also be re-branded as nVidia HD audio, Intel HD audio, Ati.... it doesnt matter if you compile it or not if you dont have one of those AFAIK, but if you have one, DO IT ...ot (4chan?), After it is complete, just run ```
 make && sudo make compile 
``` It will ask you for your password (If you aren't on sudo'ers file, you're out of luck), insert it and let it run, after it is done, run this ```
 cd ../ && cd alsa-utils-1.0.20
``` (Remember, this guide is done as of 4th of July, filenames could change with version changes, so you might get an error or two, but you should be able to fix it by now if you have some brains), after that, just copy-paste this into console [code] ./configure && make && sudo make install [/install]

1.5 Reboot (You might want to do this AFTER step 2, to save time)

1.6 Half-profit

2. (The easy part) Installing the needed stuff
Well, this is sorta, really easy, just install "phonon-backend-gstreamer" and reboot. Then go to KDE's control center -> Multimedia -> Engine (Tab) Then move gstreamer up to the top, and press apply, then go back to the "Device priority" tab (It might be different i have kubuntu in spanish), and go to the music option, push the "hw 0,0" to the top (Make sure it works by pushing "Test" down th on the little bar), click apply...

PROFIT!

At least this was the easy, digested way i got it to work :p, i dont know if it will work for you guys :D Hope it does, good luck...

Final commentz:
- If you use custom kernel, you SHOULD know there's something wrong for you on the dependancies step.
- If it doesn't work, i dont know any other way to make it work
- My english isnt the VERY best, because it ain't my native langauge, but i think i made myself clear
- Good Luck!
- Took a long time to do this, hope you like it ;)

EDIT: This has been a phailure, idk why, but when i rebooted, amarok's sound was gone, so i resorted the audio devices and it finally worked out try doing that too :S

Another EDIT: Pulseaudio seems to work weel too, idk why ;)

---

