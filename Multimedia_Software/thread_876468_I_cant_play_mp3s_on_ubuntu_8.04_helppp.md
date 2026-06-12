---
title: "I cant play mp3s on ubuntu 8.04 helppp"
date: 2008-07-31
forum: Multimedia Software
---

### Post by Millie da kidd on 2008-07-31
Well thats pretty much it. I've had ubuntu 8.04 for about 2 weeks and i cant play any mp3s.
What do i do?
Thanks in advance

---

### Post by lordadi on 2008-07-31
Hi,

You need to install the nonfree plugins to play mp3s as its a proprietary plugin. Try this howto:[Multimedia Howto]("http://ubuntuforums.org/showthread.php?t=766683&highlight=mp3").




Cheers,


Lordadi.

---

### Post by moolcool on 2008-07-31
is it the same problem im having? I have no trouble getting sound from Firefox (youtube and stuff) and pidgin has audible alerts but I can not hear audio from VLC or Amarok

---

### Post by tuxxy on 2008-07-31
install ubuntu-restricted-extras package this provides DVD, MP3 playback codecs amongst others

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by nbayiha on 2008-07-31
Mark your thread as "solved" dude.

---

### Post by Millie da kidd on 2008-07-31
> **moolcool said:**
> is it the same problem im having? I have no trouble getting sound from Firefox (youtube and stuff) and pidgin has audible alerts but I can not hear audio from VLC or Amarok

Exactly...

---

### Post by Millie da kidd on 2008-07-31
> **tuxxy said:**
> install ubuntu-restricted-extras package this provides DVD, MP3 playback codecs amongst others

```
sudo apt-get install ubuntu-restricted-extras
```


after using the code on the terminal this is what i got



msttcorefonts uses defoma

 Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use
the fonts provided by this package under the X Window System, you must 
configure it to use defoma fonts.


The easiest way to do so is to use the x-ttcidfont-conf package. For
more information, install the x-ttcidfont-conf package and consult its
documentation under /usr/share/doc/x-ttcidfont-conf.

For uses of msttcorefonts not related to the X Window System (e.g.
printing) this is not required. 


What do i do =\

---

### Post by moolcool on 2008-07-31
The weirdest thing is it all works in KDE

---

### Post by Millie da kidd on 2008-07-31
any idea on what to do now:confused::confused::confused:
Im bout to back to windows and i like ubuntu more =\

---

### Post by nbayiha on 2008-07-31
Do this 
Application->ADD/REMOVE->  in the search bar input Mp3,
near the search bar put All available application. 
Enter. 

The first and second Gstreamer package that will appear install them . 

And you are good to go. :d

---

### Post by tuxxy on 2008-07-31
OPen synaptic and search for ubuntu-restricted-extras

---

### Post by Millie da kidd on 2008-07-31
> **nbayiha said:**
> Do this 
Application->ADD/REMOVE->  in the search bar input Mp3,
near the search bar put All available application. 
Enter. 

The first and second Gstreamer package that will appear install them . 

And you are good to go. :d

downloaded both....nothing.. :(

---

### Post by tuxxy on 2008-07-31
Once you install /ubuntu-restricted-extras the package you will have all this;

[http://packages.ubuntu.com/hardy/ubuntu-restricted-extras](http://packages.ubuntu.com/hardy/ubuntu-restricted-extras)

---

### Post by nbayiha on 2008-07-31
Try what @Tuxxy said ,if not working try to do this one.

In the menu you go to System / Preferences / Sound. Then change "Sound Events" to ALSA, and "Music and Movies" to ALSA

---

### Post by Millie da kidd on 2008-07-31
> **nbayiha said:**
> Try what @Tuxxy said ,if not working try to do this one.

In the menu you go to System / Preferences / Sound. Then change "Sound Events" to ALSA, and "Music and Movies" to ALSA

i did do what he said look at the first page
im going to try this now

---

### Post by Millie da kidd on 2008-07-31
> **tuxxy said:**
> OPen synaptic and search for ubuntu-restricted-extras

whats synaptic???? how do i open that..

---

### Post by nbayiha on 2008-07-31
System->Administration->synaptic Package Manager.

---

### Post by Millie da kidd on 2008-07-31
> **nbayiha said:**
> System->Administration->synaptic Package Manager.

ok gonna do that now
its just shows me 
ubuntu
xubuntu
and
kubuntu restricted extras 
what do i do now?

---

### Post by nbayiha on 2008-07-31
Before going further i have  question , with which program are you trying to read mp3 ? rythmbox or amarok ?

---

### Post by Millie da kidd on 2008-07-31
> **nbayiha said:**
> Before going further i have  question , with which program are you trying to read mp3 ? rythmbox or amarok ?

frost wire
or mixxx

---

### Post by nbayiha on 2008-07-31
Hej dude i think you are really confusing us now :lolflag:

FrostWire is a peer-to-peer file sharing , is not to be use to play mp3.

So why dont you try to install amarok
```
sudo apt-get install amarok
```
 and try to run a mp3 file throw them.

ps: u can try to use rhythmbox to if u want.
Application->sound and video-> Rythmbox should be there .

---

### Post by tuxxy on 2008-07-31
Or try Banshee in application > sound

---

### Post by Millie da kidd on 2008-07-31
> **nbayiha said:**
> Hej dude i think you are really confusing us now :lolflag:

FrostWire is a peer-to-peer file sharing , is not to be use to play mp3.

So why dont you try to install amarok
```
sudo apt-get install amarok
```
 and try to run a mp3 file throw them.

ps: u can try to use rhythmbox to if u want.
Application->sound and video-> Rythmbox should be there .

Oh? then why cant i play those??
is it nothing different?

---

### Post by Millie da kidd on 2008-07-31
plus i cant even play the song i download threw frost wire on mixxx

---

### Post by nbayiha on 2008-07-31
What is Mixxx ??? and did you try to play the song with those player we gave you, amarok banshee rythmbox ?Try it and report if it's working .

---

### Post by Millie da kidd on 2008-07-31
> **nbayiha said:**
> What is Mixxx ??? and did you try to play the song with those player we gave you, amarok banshee rythmbox ?Try it and report if it's working .

yea the files that i downloaded on frostwire work on amarok..but now i try to open frostwire and it doesnt work so im going to reinstall it .
Thank you so much how doing that it will work

---

### Post by nbayiha on 2008-07-31
You are welcome.
:)

Don't forget to mark your thread as " Solved " .

---

### Post by moolcool on 2008-07-31
Im still having the issue, not sure if its the same one as he did but i get sounds from some apps and not others. I cant even get amarok to play an OGG

---

### Post by tuxxy on 2008-07-31
moolcool, goto system > prefs > sound and here you will be able configure your sound, try ALSA for output device

---

### Post by moolcool on 2008-07-31
I tried all and the one that played a tone was ADC Capture. Even still no OGG playback from amarok and im still getting sound from Pidgin.

---

### Post by moolcool on 2008-07-31
Sorry for bumping, but if it matters its a Sound Blaster Live!

---

### Post by tuxxy on 2008-07-31
My friend has that card and he had some issues like yours, hes still waiting for a fix also.

---

### Post by moolcool on 2008-07-31
i do have an on board AC'97 audio chip but in both windows and linux it sounds like crap and is full of interference. Thanks for the help though. I just find it so weird that it does not do it in KDE

---

