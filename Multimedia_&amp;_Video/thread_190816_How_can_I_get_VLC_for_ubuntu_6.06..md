---
title: "How can I get VLC for ubuntu 6.06."
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by sidy on 2006-06-06
Hi there,

When I first upgraded the ubuntu from 5.10 to 6.06 it came 'VLC'. (that is in one partition)

On the other partiton I have, 'VLC' didn't came on the 'Synaptic Package Manager' when I did the upgrade to 6.06.

WHAT CAN I DO TO GET VLC?, because it seams to be not available.

Can you give me full commands, because I have never done this before.

rgds

---

### Post by murph2481 on 2006-06-06
edit sources.list and make sure all the repos are open then do

sudo apt-get update
sudo apt-get VLC

---

### Post by BitTorrentBuddha on 2006-06-06
I would recommend using [Automatix](http://ubuntuforums.org/showthread.php?t=177646) to install it instead of editing your sources.list if you've never done this before.

---

### Post by sidy on 2006-06-06
[QUOTE=murph2481]edit sources.list and make sure all the repos are open then do

sudo apt-get update
sudo apt-get VLC[/QUOTE]

Hi, I don't know how to 'edit sources.list', but on terminal I typed

sudo apt-get update

then

sudo apt-get VLC

Came up:  ' E: Invalid operation VLC ' 

then I typed

sudo apt-get install VLC

Came up:  ' E: coudn't find package VLC ' 

What should I have done?
What commands to use?

---

### Post by BitTorrentBuddha on 2006-06-06
If you honestly must install it without automatix, try: ```
sudo gedit /etc/apt/sources.list
``` and in that file, remove the "#" from all lines that start with "deb" and then do ```
sudo aptitude install vlc vlc-plugin-alsa wxvlc
``` that should get it into your menu under Applications -> Sound & Video -> VLC Media Player.

---

### Post by sidy on 2006-06-07
[QUOTE=BitTorrentBuddha]```
sudo gedit /etc/apt/sources.list
``` [/QUOTE]

Hi, as soon as typed the above code, opened a window that was empty.
there wasn't a list with anything.

Is there another way?

What can I do now?

rgds

---

### Post by murph2481 on 2006-06-07
Sorry about the case problem with 'VLC' vs 'vlc'

If it is coming up blank then you probably are typing the path wrong.

Try going into terminal then typing
cd /etc
cd apt
ls

you should see the sources.list file there.  Then try typing
sudo gedit sources.list

remember linux is case sensitive

---

### Post by sidy on 2006-06-07
[QUOTE=BitTorrentBuddha]I would recommend using [Automatix](http://ubuntuforums.org/showthread.php?t=177646) to install it instead of editing your sources.list if you've never done this before.[/QUOTE]

Perfect!

I have them all, vlc, flash, mplayer, etc.

Thank you for the support.

Sidy

---

