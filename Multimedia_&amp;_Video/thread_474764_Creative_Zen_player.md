---
title: "Creative Zen player"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by colecole on 2007-06-15
I recently bought the creative zen player, vision: m. I've been trying to get things working with it for days now and keep running into more and more problems.
First I downloaded gnomad2 and it recognizes my player but freezes every time it tries to retrieve the metadata of my music collection. It picks a different file number everyday and sticks to it-yesterday was file number 214. Is this some weird bug in the program? Have other people had this problem? If so, how can I get it to work properly?

I also downloaded amarok, hoping I could use that instead. But I can't for the life of me figure out how to get it ot recognize the zen player when it's plugged in. After pressing the 'connect' button it asks for connecting commands. What should I type in there???

(if you can't tell already I'm very new to linux, and very lost. Any help would be much appreciated)

---

### Post by timcredible on 2007-06-15
well, if it gets auto-mounted as a usb-attached drive, can't you just copy-paste mp3 files onto it?  that's what i do for my daughter's sandisk mp3 player, and it works fine, it even reads subdirectory names as CD name and artist.  the ipod has a database file and completely renames every file, so that's why you need a special program for it, like amarok or gtkpod (both work with the ipod just fine - i see that rhythmbox also has an ipod interface, haven't tried it yet).

---

### Post by colecole on 2007-06-15
That's what I thought too, and that's how it worked with my old ipod. But the new zen players have this thing called MTP that is supposed to make them run smoothly on microsoft but not so much on linux (it's called play for sure I believe). Amarok and Gnomad are the only programs I've come across that can recognize the zen player. And the programs aren't working for me....

---

### Post by hummingbird59 on 2007-06-15
Have you seen this:  [http://ubuntuforums.org/showthread.php?t=467525&highlight=creative+zen](http://ubuntuforums.org/showthread.php?t=467525&highlight=creative+zen).  Specifically "you will need to install "libnjb5" to allow the other programs to access the Zen. If you install Gnomad2 it will be installed as a dependancy and then Amarok and Rhythmbox will also see it."  Thanks to grege for the advice!

---

### Post by catdriver on 2007-06-16
In addition to ensuring NJB (Nomad Juke Box) support you may also need MTP (Microsoft Transport Protocol) support.  Once installed you have to manually connect to the Zen devices.  Additional configuration using the Configure Amarok menu is needed.

---

### Post by 19tk74 on 2008-06-17
It turns out you only need the audible manager to activate your player but once that is done or if your player is already registered you can download the files from audible, by opening the perl file the stream link sends (aw_assemble_title_stream-1.pl) you can paste the url from that into your browser and it will save the file for you. From there I use the datatransfer tab in gnomad2 to send it to my Zen. I don't remember where I saw the solution, but it has saved me from having to keep a windows box around.

---

