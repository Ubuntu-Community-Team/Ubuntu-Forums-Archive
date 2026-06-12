---
title: "Cant play DVDs with Ubuntu Feisty/Totem Movie Player"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by 1feistymedic on 2007-07-30
I can not play any DVD&#347; on Ubuntu Feisty....the Totem movie player states : Totem can not play this type of media(DVD) because you do not have the appropriate plugins to handle it... Please install the necessary plugins  and restart Totem to be able to play this media

I tried the suggestions in this sticky: [http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)


Regarding the above sticky....I did what it stated to do but this is the message I received..can anyone help?  Thanks.  (also, when it stated to do this:

Add the following lines to add the Medibuntu repository to the file:


Quote:
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

Where was I supposed to add it to?  Thanks...A true total Nubian...

sean@desktop:~$ $gksudo gedit /etc/apt/sources.list
sean@desktop:~$ wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
OK
sean@desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
sean@desktop:~$ sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
sean@desktop:~$

---

### Post by 1feistymedic on 2007-07-30
no helpers...anybody....Buehler...Buehler.....anybody?

---

### Post by ACMarina on 2007-07-30
Look up Automatix, that's probably the first step for you..

---

### Post by Gremlinzzz on 2007-07-30
Install smplayer plays all my DVD movies.
[http://smplayer.sourceforge.net/linux/index_en.php](http://smplayer.sourceforge.net/linux/index_en.php)
This is the deb package i used to install.smplayer package (Qt3; without KDE support)
im using feisty 
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
codecs i use
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

---

### Post by 1feistymedic on 2007-07-30
I tries SM player and it works horribly....the picture jumps and freezes...any workarounds?

I will look up automatix

---

### Post by 1feistymedic on 2007-07-30
How does Automatix help me play DVD's?

---

### Post by normworthy on 2007-07-30
I don't know if this will help anything, but I put Automatix into Wikipedia, it does not sound like a good idea to use. this is the site:
[http://en.wikipedia.org/wiki/Automatix_%28software%29](http://en.wikipedia.org/wiki/Automatix_%28software%29)

hope you get a better answer soon, so I can play movies too.
Norm

---

### Post by normworthy on 2007-07-30
I might have a better idea,
try VLC   I got it by typing in a terminal:

sudo apt-get install vlc

it is playing a video just fine for me

Norm

---

### Post by kelvin spratt on 2007-07-30
change to Totem zine add extra zine plugins  download w32codecs and libdvdcss2 codecs in synpatic you should be able to play any thing.

---

### Post by 1feistymedic on 2007-07-30
> **kelvin spratt said:**
> change to Totem zine add extra zine plugins  download w32codecs and libdvdcss2 codecs in synpatic you should be able to play any thing.

How do I do that?  I am a total nubian...I need a baby-step walk through, ie.copy and paste for the terminal..thanks....

---

### Post by kelvin spratt on 2007-07-30
you don't need the terminal go to system look for synaptic click enter your root password thats the second one you enter when you login when program starts press search, type totem press ok it will then list al to do with totem, click on totem zine it will say totem gstreamer will be uninstalled click ok. that will install do the same with othe things you need to install
the reason for using synaptic rather than add remove in menu is that you are replaceing a conflicting application so it has to be done this way the codecs need to be install the same way
i hope this is not embarrassing as their is no intent on my part.

---

### Post by 1feistymedic on 2007-07-30
I will try this later and let you know how it worked..Thanks.....

---

### Post by 1feistymedic on 2007-07-30
Ok....I did as you directed...I now get an error message that says: "Totem could not play 'dvd:///media/cdrom0". There is no plugin for this movie

Now what do I do?

---

### Post by 1feistymedic on 2007-07-31
ok.....not only does it not play dvds..it doesnt play any sound file....cds either....

can I uninstall this program some kind of way and install something better?  I dont want this program to be the default player on my system.....thanks....

p.s.  I do have sm player and mplayer installed and they do not work either....

---

### Post by Evgeni45 on 2007-08-01
Install GStreamer extra plugins and GStreamer ffmpeg video plugin applications
DVD will start automaticalliy in TOTEM.


   Evgeni

---

### Post by Samhain13 on 2007-08-01
Hi I followed Kevin's instructions and got a result similar to 1feistymedic's. I was able to play DVD though after I installed libxine-ffmpeg from Synaptic. :)

---

### Post by BobLand on 2007-08-01
The Nubians are an ethnic group in Egypt and Sudan.

---

### Post by John.Michael.Kane on 2007-08-01
You can try redoing it this way.

Step one:
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

Step two:
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

Step three:
```
sudo aptitude update
```

Step four:
```
sudo aptitude install totem-xine libdvdcss2 w32codecs gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libdvdnav4 libxine-extracodecs
```

Should you still have issues playing movies using totem-xine. You may want to try  the player below.
```
sudo aptitude install vlc
```

---

### Post by wloescher on 2007-08-30
Another nube here, and that worked just great...thanks!

---

### Post by lxowle on 2007-09-30
I'm using gutsy, and I followed the instructions above exactly and now I can play dvd's. Thanks very much for that.

---

### Post by flarkit on 2007-09-30
Thankyou, SD-Plissken

I installed Feisty yesterday and tried a few suggestions for installing codecs and players to get DVD's working, without success. Your post worked 100% for me.

Thanks again
:)

---

### Post by Jegsy on 2007-10-09
I have been trying to play DVD's ever since installing Ubuntu over 2 weeks ago.  Being an Ubuntu/Linux Nooby I was beginning to become disillusioned.

I tried numerous suggestions which I found on the forum but your method worked first time and all of my DVD's now play.  Many thanks. :)

---

