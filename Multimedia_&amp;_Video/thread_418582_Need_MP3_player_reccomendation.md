---
title: "Need MP3 player reccomendation"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by gorkur on 2007-04-22
I've been using XMMS for a while now because I like the Winamp-like interface. However, I seriously dislike, to the point of hate,  the fact that XMMS's volume control isn't independent but fiddles around with my system volume control (PCM) instead.

So, I am looking for an MP3 player that is simple, low on resources and does **not** move my music files around while building a library. Basically a Winamp clone or XMMS with independent volume control ;)

Any reccomendations?? :guitar:

---

### Post by ntetreau on 2007-04-22
I don't use it personnaly (I like rhythmbox), but audacious might be for you. [http://audacious-media-player.org/Main_Page](http://audacious-media-player.org/Main_Page)

Nic

---

### Post by gorkur on 2007-04-22
Installed Audacious and it suffers from the same issue I hate about XMMS :(

Thanks anyways :)

---

### Post by mohnkern on 2007-04-22
I use amarok, though I haven't looked to see if its moving stuff around or not.  and its library function isn't as good as windows mediaplayer.

---

### Post by douga on 2007-04-22
I use Amarok, and generally it will not move files around. That being said, there _is_ an operation that reorganizes your files within Amarok; I just don't remember what it is. But unless you specifically request it, your files are left alone.

---

### Post by avb on 2007-04-22
you need to change sound output plugin to 'Esound output'.

Open audacious prefs, select 'Audio' tab. In 'Current output plugin' choose 'Esound output plugin'.
Press 'Output plugin Preferencies'. Put the checkbox 'Volume controls OSS mixer'. 

Restart player and now u will be able to control 'PCM' volume in the mixer.

To control only PCM volume from gnome mixer panel applet and from hotkeys go to System->Preferencies->Sound  and in 'Default Mixer Tracks' select 'PCM'. 

Now you able to control volume of the same device from audacious and at least gnome mixer and hotkeys.

Hope this helps.

---

### Post by lvanderree on 2007-04-23
I use Amarok too, I like Songbird (but this hasn't matured enough yet).

I think a good alternative for you might be beep-media player

---

### Post by blitzer on 2007-04-23
Amarok is a great player but is made for Kde desktop.  Can or does anyone know how to configure it for Gnome  :confused: 

Thanks in advance

---

### Post by lvanderree on 2007-04-23
What do you want to configure? Just install it with synaptic, or from console, using

```
sudo apt-get install amarok
```

and you're their.

The first time it starts it will check for the mp3-plugin and if you haven't installed it yet, it should ask you if it can do it for you.

Finally I use keytouch to configure my multimedia keys, you can install this the same way as described above for amarok.

End else alternatives for gnome are: Rhythmbox and Exaile
But I find these less advanced/usefull than amarok.

---

### Post by blitzer on 2007-04-23
Thanks lvanderree downloading Amarok as I'm reading your reply.   :guitar: 

Lot's of people must be downloading it - it is really slow  b/s :(



All set-up and working Great !   A little confusing when it asked for password to get mp3 support and did nothing - Synaptic finally came up and downloaded it.

[COLOR=Red][FONT="Comic Sans MS"][SIZE="4"]Amarok + ShoutCast + Ubuntu + Beryl =   LIFE IS SWEET[/SIZE][/FONT] [/COLOR]

---

### Post by jointstereotype on 2007-04-24
I too would recommend Audacious - and as for its messing with your PCM volume controls, just go to Preferences > Audio, click the Output Plugin Preferences button, and check the "Use software volume control" box. Restart Audacious. This worked for me.

---

### Post by gorkur on 2007-04-30
Thanks for the replies guys! :)

I've swallowed my pride and downloaded amaroK. And I am liking it so far :guitar: 

Thanks again for the replies! 8)

---

### Post by Sethalos on 2007-04-30
I have a 220gig MP3 collection at this point, and the only one that I can use that will search that large of a collection without crapping out was Amarok.

Now, I'm addicted to it. I love the Last.FM support and the ability to play it straight through the player. I also like the skins and information about each track.

However, I find that it crashes alot, and has a heck of a time with my collection. Searching for any one track will crash the player, etc.

I tried Banshee as well, but it get's to about 28% searching for new media, then crashes and quits.

XMMS works the best, but I need the jukebox features as well.

Seth

---

### Post by ThinkBuntu on 2007-05-01
The latest release of Banshee 0.12.1 has gotten rid of the "song import overload" bug and functions ver, very nicely. I've used iTunes since it debuted a long time ago, and I feel very comfortable with the interface. You can organize your music, import CDs, use an iPod, play CDs, burn CDs, and fetch every sort of song data.

I highly recommend Banshee.

---

