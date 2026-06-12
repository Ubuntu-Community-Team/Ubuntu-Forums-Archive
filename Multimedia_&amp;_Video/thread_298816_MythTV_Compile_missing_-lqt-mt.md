---
title: "MythTV Compile missing -lqt-mt"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by josesanders on 2006-11-13
I'm new to Ubuntu and linux.  I'm having trouble compiling MythTV.  I did the following:

./configure
qmake mythtv.pro
make

It compiles for maybe ten minutes or so, and then I get an error that it can't find -lqt-mt

I did a search on this and found a few similar errors, but none of their solutions worked.  I tried searching for qt-mt without any success, but I don't really know for sure what I am looking for.

---

### Post by lonce on 2006-11-13
The easiest way to install myth on ubuntu is through the repositories.  If you click on the bottom link in my sig, then click on How To's on the main menu on the top left.  There is a step by step how to install mythtv on unbuntu.  Should work like a charm.  I have done it a hudred times now and no issues what so ever any time.

---

### Post by josesanders on 2006-11-13
I've tried what you suggested.  It works to install mysql, but it says it can't find package mythtv.  Does it matter that I'm running Ubuntu 6.06?

---

### Post by superm1 on 2006-11-14
If you are running Ubuntu 6.06, the ubuntu 0.20 packages aren't included in the repositories.  I have assembled third party repository that you can obtain them from.

Edit /etc/apt/sources.list
```
sudo gedit /etc/apt/sources.list
```

Verify that both universe and multiverse are enabled.  If not, then add a line for them:
```
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
```

Add these two lines to the bottom for my repository:
```
         deb http://home.eng.iastate.edu/~superm1 dapper main
        deb-src http://home.eng.iastate.edu/~superm1 dapper main
```

Add my apt key
```
wget http://home.eng.iastate.edu/~superm1/80DF6D58.gpg -O- | sudo apt-key add -
```

Update repositories list.  
```
sudo apt-get update
```

Install mythtv and continue as necessary
```
sudo apt-get install mysql-server mythtv
```

---

### Post by josesanders on 2006-11-15
Thanks for your help.  Everything worked, although I had to install lame and liblam0 first.

Of course, nothing is ever easy, and so once I started MythTV, I found that it doesn't recognize my card.

---

### Post by superm1 on 2006-11-16
What card?

---

### Post by josesanders on 2006-11-16
I wish I knew what card.  I started a new thread about it.  It's totally generic, just called "Digital PC TV Capture Card", but I know it's based on the Phillips 7134 chipset, as I had it working for several months in Windows.  When I run dmesg, it says that it found the 7134 card, but there's no eeprom present, so it can't detect the card type.  It gives about a hundred options corresponding to different manufacturers.

Do you think it would hurt to just try each one?  Is there any way to know if I have the right one, other than opening MythTV and seeing if it can open the card?  I think I can find the commands to load and unload the module, but is it possible to permanently screw things up opening the card using the wrong card type?

---

### Post by superm1 on 2006-11-16
Well you shouldn't mess up the card by loading the wrong options.

You also shouldn't need to actually open up myth to try each one.  After loading each module, you should be able to

cat /dev/video0 > ~/test.mpg

Open up that mpg in video playback app and see if you can play it back.

No guarantees though.... I'm not really used to using anything but ivtv and dvb cards :)

---

### Post by josesanders on 2006-11-17
I loaded the saa7134 module for each of the card options, 0 through 94, and recorded a five second clip for each.  A few of them gave me errors when I used the cat command, but most worked.  Of course, none of the files play.

Since my card doesn't have hardware mpeg compression, though, I am not sure if the problem is with the movie player, or with the file.  A little more than half of the test clips won't open at all.  The rest will open, but Totem gives an error that it can't recognize the type of stream.  It seems to me though, that they aren't mpeg files, they are just raw video.  If the player is expecting mpg by the file extension, will it still play if they are uncompressed?

---

### Post by superm1 on 2006-11-17
Oh, i didn't even think of that possibility of them just being raw video since the card doesn't support mpeg2 encoding.

Well i glanced at the v4l wiki about saa7134 cards.  Have you seen this page? [http://linuxtv.org/v4lwiki/index.php/Generic_SAA7134_Card_Installation](http://linuxtv.org/v4lwiki/index.php/Generic_SAA7134_Card_Installation)

You may try using tv time with it, and if tv time can access the card (and its raw data for that matter), then you should be good.

---

### Post by josesanders on 2006-11-17
I just tried one card number at random, and opened TV time, and it worked.  I can see live TV and change channels.  Mythtv still can't open the card though.  I can't start mythtv without stopping the mythtv backend first, so could that be the problem?

How can I set it to load the module on bootup with a specific card number?

---

### Post by superm1 on 2006-11-17
Okay this being the case,

stop the backend with:

 ```
sudo /etc/init.d/mythtv-backend stop 
```

Open up mythtv-setup with

```
 sudo mythtv-setup

```Go to the capture cards page.  Make sure you chose the right type of card for your capture cards.  I believe it should be a standard V4L card in the list of options.

Follow through the rest of this wiki page to make sure mythtv-setup is configured correctly:
[https://help.ubuntu.com/community/MythTV_mythtvsetup](https://help.ubuntu.com/community/MythTV_mythtvsetup)

Fill the database data with
```
 
sudo /etc/cron.daily/mythtv-backend  
```start the backend with
```
 
sudo /etc/init.d/mythtv-backend start
 
```

---

### Post by josesanders on 2006-11-17
Mythtv still can't open the card.  Why would TVtime be able to open it, but not MythTV?

---

### Post by superm1 on 2006-11-17
Check the permission on all the 

/dev/video* files

the mythtv user needs to be able to access them.

---

### Post by josesanders on 2006-11-17
It can open the card, but it only sees the first 13 channels.  I knew I saw that before, so I searched and found another thread where you said it was a permissions issue.  The permissions seem fine for /dev/video*.

---

### Post by superm1 on 2006-11-17
Can you access the other channels in tvtime?

If so, then you have the wrong frequency table chosen in mythtv for this card.

---

