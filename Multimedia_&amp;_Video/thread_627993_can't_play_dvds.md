---
title: "can't play dvds"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by Excalibre on 2007-11-30
Okay, I don't seem to be able to play DVDs although I have the relevant legally-questionable software installed; I don't seem to be able to play DVDs in Totem, mplayer, or VLC, or at least not well. I just stuck a DVD in, and Totem sez "Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc." mplayer sez "No stream found to handle url: dvd://1". VLC suddenly exits if I tell it to display the menus, and makes weird buzzing/clicking sounds when I tell it to just play the DVD. With another disk, same results except (weirdly) Totem popped up an open file dialog when I ran the "PLAY DISK . . . " menu item. In fact, suddenly that's all Totem does when I try to play a DVD: I think a new misbehavior just started *as I was composing this message and testing things.*

With another DVD, VLC and mplayer will start playing the disk (but again, VLC just spontaneously closes if I try to play the menus. Which is really, really crappy behavior. WTF kind of error handling is that?!) They won't play more than about twenty minutes of title one (the disk is the first volume of *Firefly: The Complete Series*, so there are separate titles for several episodes on it) and they won't play anything from the other titles: VLC closes if I try, and mplayer sez "No stream found to handle url: dvd://2" (or 3, or 4, whatever the title.)

I don't seem to be able to get any DVDs to play properly, though I guess I haven't tried my whole collection. Regardless, this is weirdly difficult. Automatix installed the relevant libraries that are needed, so why won't any video software actually work?

---

### Post by ericartman on 2007-11-30
Well I never used Automatrix but I do use Ubackup! on all my Ubuntu syatems and it hasn't failed me yet. BTW I know it sounds like a backup program but it is really so much more like a codec installer and flash installer. I recommend it

[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

Cart

---

### Post by Excalibre on 2007-11-30
The necessary codecs ARE installed, or at least the ones that I've seen mentioned in guides: libdvdcss2 and libdvdread3 are both installed, according to Synaptic.

---

### Post by zenkaon on 2007-11-30
First of all make sure you have followed the instructions in 
[http://medibuntu.org/](http://medibuntu.org/)

Next see if your dvd is actually /dev/dvd type:
ls -l /dev/d*

and see if you see /dev/dvd

if it comes up as /dev/dvd1 or someting (as it usually does with my removable external dvd drive) then you need to symbolically link it to /dev/dvd using

sudo ln -s /dev/dvd1 /dev/dvd

You could try the KDE program kaffeine, which IMHO is better than totem. You can install it in gnome by typing

sudo atp-get install kaffeine kaffeine-xine

---

### Post by Excalibre on 2007-11-30
> **zenkaon said:**
> First of all make sure you have followed the instructions in 
[http://medibuntu.org/](http://medibuntu.org/)
I just made sure - and tried installing both libdvdcss2 and w64codecs (the whole package) from medibuntu, and it didn't download anything, I assume because it's all installed already.


> Next see if your dvd is actually /dev/dvd type:
ls -l /dev/d*

and see if you see /dev/dvd

if it comes up as /dev/dvd1 or someting (as it usually does with my removable external dvd drive) then you need to symbolically link it to /dev/dvd using

sudo ln -s /dev/dvd1 /dev/dvd
I checked, and I have both /dev/dvd (which is a link to /dev/scd0) and /dev/dvd1 (which is scd1); I was trying to play the dvd with the /dev/dvd drive (given that some of the disks played at least partially, I think we can be pretty certain that it's not because it couldn't find the right drive.)


> You could try the KDE program kaffeine, which IMHO is better than totem. You can install it in gnome by typing

sudo atp-get install kaffeine kaffeine-xine
Um, if three dvd programs are not working, what are the odds that a fourth one will, since it is (or should be) using the same codecs anyway?

---

### Post by fraia on 2007-11-30
Hi
 Just got my dvd playback working with VLC - I did  the following:
first i uninstalled automatix2 and all of my other attempts at video playback, including totem-xine, gxine etc. It could just be superstitious but i think it helps to start cleanly sometimes...
 
 sudo apt-get install libdvdread3 fakeroot debhelper
 
then run:
 sudo /usr/share/doc/libdvdread3/install-css.sh

then install vlc:
sudo apt-get install vlc

and now it works on all the dvd's i've thrown at it.
 Hope it helps

---

### Post by Excalibre on 2007-12-06
> **fraia said:**
> Hi
 Just got my dvd playback working with VLC - I did  the following:
first i uninstalled automatix2 and all of my other attempts at video playback, including totem-xine, gxine etc. It could just be superstitious but i think it helps to start cleanly sometimes...
 
 sudo apt-get install libdvdread3 fakeroot debhelper
 
then run:
 sudo /usr/share/doc/libdvdread3/install-css.sh

then install vlc:
sudo apt-get install vlc

and now it works on all the dvd's i've thrown at it.
 Hope it helps
Thanks for the advice . . . I haven't tried it out yet (end of the semester so I've been too busy to screw around with this stuff) but before I do, can you tell me what fakeroot and debhelper are? And what's the shell script do?

---

### Post by glasswalkerny on 2007-12-08
> **fraia said:**
> Hi
 Just got my dvd playback working with VLC - I did  the following:
first i uninstalled automatix2 and all of my other attempts at video playback, including totem-xine, gxine etc. It could just be superstitious but i think it helps to start cleanly sometimes...
 
 sudo apt-get install libdvdread3 fakeroot debhelper
 
then run:
 sudo /usr/share/doc/libdvdread3/install-css.sh

then install vlc:
sudo apt-get install vlc

and now it works on all the dvd's i've thrown at it.
 Hope it helps

I just tried this and either installing fakeroot and debhelper fixed DVD playback in Kaffeine or the downgrade and re-upgrade of libdvdcss2 fixed it.. not sure but it works again :confused:

---

### Post by Excalibre on 2007-12-22
Okay, I removed every relevant thing I could think of and reinstalled and both totem-xine and kaffeine claim that DVDs are encrypted and mention installing libdvdcss. But libdvdcss2 is definitely, absolutely installed. I don't understand this at all - there shouldn't be an issue here. I'm really getting frustrated that there seems to be no help for resolving what ought to be a simple issue.

---

### Post by Excalibre on 2007-12-23
Hmm, I guess I lied. In case anyone does stumble across this thread again, it appears that most DVDs *are* working now, including some that weren't before. It's just the first DVD I tried that wasn't (Disc 1 of Firefly). I'm guessing some discs use different encryption schemes than others? Is there any way to get them all to play?

---

### Post by diego.costa on 2008-05-27
(Sorry for ress this topic but i find an solution here)

I fix this problem based on comadre Excalibre instructions.

(I think that isn't a plugins extentions or codecs problem)
but:
I have the 'libdvdcss2' instaled and 'Ubuntu restricted extras'

MPlayer:
1-)Open Mplayer Aplication 
2-)**Right Click** on video windows
3-)Choose **Preferences**
4-)Chosse the **Misc** tab
5-)DVD Device: **/dev/dvd**
Choose /dev/dvd for **/dev/dvd1** 

SMPLayer:

1-)Open SMPlayer Aplication
2-)Choose **Options** on SMPLayer menu
3-)Chosse **Preferences**
4-)Now on a new Windows choose **Drivers**
5-)Go to **Select your DVD device**: and put /dev/dvd1

TOTEM:
hum......now it's works well... how? i dunno. "After" the Mplayer and SMPlayer it's work.

---

### Post by masonfoley on 2008-05-27
The problem with this is, it has been suggested, Hardy should not be incrementing these symlinks and it appears, even people with one drive, this has happened on occasion.  Enough where the solution actually is to remove the links, not adjust the apps to match the updated links in /dev as discussed [here]("http://ubuntuforums.org/showthread.php?t=767449").

---

### Post by ephemerat on 2008-06-17
Would just like to add my thanks to diego.costa for his solution - that sorted it for me as well. Blessed relief after all the interminable minutes spent wrestling with plug-ins and codecs.

To alter in VLC:

1-)Open VLC
2-)Choose **Settings -> Preferences**
3-)Select **Input / Codecs**
4-)Under **Default devices** find **DVD device** and alter it to /dev/dvd
5-)**Save** and you should be good to go!

---

