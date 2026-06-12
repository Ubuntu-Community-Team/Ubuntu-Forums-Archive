---
title: "Suggested Music player?"
date: 2010-11-17
forum: Multimedia Software
---

### Post by Tekno.Statik on 2010-11-17
For Media Player enthusiasts as myself:

I've used Audacious and there are a few nifty things about it, however it glitches on me... sometimes I get static and scratching on parts of songs, and other times I hear the song in slow motion =/
But what really annoys me, is that Audacious opens up when I try accessing a folder from my "Places" menu... Like WTF? And it's NOT that Audacious tries to play the songs in the folder I select; no... it simply STOPS whatever it is that it's doing  on a dime (What a way to throw off my groove lol). I've gone through ALL the plugins in Audacious, I've checked them out one by one and I can't find anything that would cause that.
I tried uninstalling it; and the problem no longer exists, but after Re-installing; but the problem comes right back.

I also tried: Kaffeine, Amarok, and Muine and they all suck... they can't configure the output to my Default speakers, and they're just not as aesthetically pleasing as Winamp; followed by Audacious, nor do they have the keyboard shortcuts which is the only reason I listen to music, but now I'm addicted to music, so I can't change that.

Please, and thanks, ALL help and suggestions are GREATLY appreciated. :D

---

### Post by tommcd on 2010-11-18
I have never had those problems with audacious. Try configuring audacious to use alsa instead of pulseaudio and see if that makes any difference.
As for other music players *Exaile* is lighter than Kaffeine or Amarok, and it is much better imo.
If you want a player that can easily be controlled with the keyboard, I just run MPlayer right from the terminal. No need ever for a GUI. MPlayer can be controlled with simple keyboard commands. The commands are listed on the 2nd or 3rd page of "man mplayer".
There is also a player called **Deadbeef** (clever name, with all of the letters in the player's name taken from the chromatic scale!) that a lot of people seem to like. It does not seem to present in the Ubuntu repos, but there is a PPA repo for it. See this timely thread:
[http://ubuntuforums.org/showthread.php?t=1503749](http://ubuntuforums.org/showthread.php?t=1503749)

---

### Post by marl30 on 2010-11-18
Maybe you would want to also give this player a try: Qmmp. It is a Winamp look-alike alternative. 
```
sudo add-apt-repository ppa:stiff.ru/qmmp-releases && sudo apt-get update
  
sudo apt-get install qmmp
```Haven't tried it myself as I was never a big fan of Winamp, but I often see it recommended to people looking for an alternative to replace Winamp.

---

### Post by theozzlives on 2010-11-18
I've always been a fan of Amarok 1.4 as 2.x sucks. I don't remember the ppa, but you could google:
```
amarok14+ubuntu
```

---

### Post by Sylos on 2010-11-18
Hello there.

Personally I have used GmusicBrowser and more recently guayadeque as my music players. They both work well with large libraries and have some nice functionality. Not the pretiest in the world if aesthetics is what your looking for though.

---

### Post by Hreinsi on 2010-11-18
guayadeque:p

---

### Post by marl30 on 2010-11-18
> **Sylos said:**
> Hello there.

Personally I have used GmusicBrowser and more recently guayadeque as my music players. They both work well with large libraries and have some nice functionality. Not the pretiest in the world if aesthetics is what your looking for though.

guayadeque: I recently came across this player and it is pretty awesome. I really like it. I often see people saying that there are not many good media players available for Linux as on Windows, I beg to differ. I use to think so too until I came across  a long list of great players. I now have difficulty deciding which to use as my main one.

---

### Post by Tekno.Statik on 2010-11-18
> **tommcd said:**
> I have never had those problems with audacious. Try configuring audacious to use alsa instead of pulseaudio and see if that makes any difference.
As for other music players *Exaile* is lighter than Kaffeine or Amarok, and it is much better imo.
If you want a player that can easily be controlled with the keyboard, I just run MPlayer right from the terminal. No need ever for a GUI. MPlayer can be controlled with simple keyboard commands. The commands are listed on the 2nd or 3rd page of "man mplayer".
Cool, Thanks! I'm downloading DeadBeeF now as we speak, I saw that thread but previously I didn't want to try it since I couldn't find it in the Ubuntu software center. Anyways, I'll try that one as soon as it installs.

I went ahead and tried Exaile but all it did was turn gray (As if it were sick, lol) and I had to force quit... Audacious? ...well I am no longer able to deal with it, looks powerful and stuff, but it won't play anything other than the podcast I downloaded (Which cuts off when I overuse bandwidth.

Will let you know and post on the thread about my deadbeef experience :D Thanks a mil!

---

### Post by tommcd on 2010-11-18
> **Tekno.Statik said:**
> ... Audacious? ...well I am no longer able to deal with it, looks powerful and stuff, but it won't play anything other than the podcast I downloaded (Which cuts off when I overuse bandwidth.

Audacious can play any music files that most any other player can play. Have you installed all the multimedia codecs? Also, check the audacious plugins under preferences and make sure everything is enabled. 

Another lightweight player is **aqualung**. [http://aqualung.factorial.hu/](http://aqualung.factorial.hu/) Aqualung is in the Ubuntu repos. It comes preinstalled on Lubuntu 10.10 which I am using now. Aqualung works pretty well in my limited experience with it; and it is very light on system resources.

---

### Post by Tekno.Statik on 2010-11-19
> **tommcd said:**
> Audacious can play any music files that most any other player can play. Have you installed all the multimedia codecs? Also, check the audacious plugins under preferences and make sure everything is enabled. 

Another lightweight player is **aqualung**. [http://aqualung.factorial.hu/](http://aqualung.factorial.hu/) Aqualung is in the Ubuntu repos. It comes preinstalled on Lubuntu 10.10 which I am using now. Aqualung works pretty well in my limited experience with it; and it is very light on system resources.

So far VLC and ironically Rhythmbox 0.13.1 have been working great, keyboard shortcuts are automatically sunk.

Guayadeque crashed on me as well, and I can't imagine why VLC and Rhythmbox have not crashed, but I guess I will stick with these two... Once I get frustrated with something I will put effort into getting Deadbeef =] lol. Thanks though! Your suggestions were greatly appreciated!

Until then!~

---

### Post by tommcd on 2010-11-19
VLC is a great all around media player. VLC and MPlayer will play just about anything  you throw at them. The only reason I did not suggest VLC is because I thought you were interested in something simple and light on resources like Audacious. If you are happy with VLC then stick with it. It will serve you well.

---

### Post by Tekno.Statik on 2010-11-19
> **marl30 said:**
> Maybe you would want to also give this player a try: Qmmp. It is a Winamp look-alike alternative. 
```
sudo add-apt-repository ppa:stiff.ru/qmmp-releases && sudo apt-get update
  
sudo apt-get install qmmp
```Haven't tried it myself as I was never a big fan of Winamp, but I often see it recommended to people looking for an alternative to replace Winamp.

So... I've never actually entered codes or anything of the text sort into my Ubuntu yet... How or where should I enter this code? =] And what steps should I take before and after the code? ^^;

Thanks Marl!

---

### Post by tommcd on 2010-11-20
> **Tekno.Statik said:**
> So... I've never actually entered codes or anything of the text sort into my Ubuntu yet... How or where should I enter this code? =] And what steps should I take before and after the code? ^^;

You enter those commands in the terminal. See this link:
[https://help.launchpad.net/Packaging/PPA/InstallingSoftware](https://help.launchpad.net/Packaging/PPA/InstallingSoftware)
You can also use: system > administration > software sources, like this:
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20PPAs](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20PPAs)
If you want to remove a PPA repo you can do it from: system > administration > software sources, or install **ppa-purge** and run in the terminal
```
sudo ppa-purge ppa-name
```
Be aware that PPA repos are unsupported by Ubuntu, and their quality can vary. They are created by ordinary Ubuntu users and uploaded to the Launchpad PPA repo site.

---

### Post by shantiq on 2010-11-20
many think [deadbeef ]("http://ubuntuforums.org/showthread.php?t=1503749")is very good


not a library-type player but it has many features is very slick and plays many formats:KS




and also the master    the old and trusted [XMMS]("http://ubuntuforums.org/showthread.php?t=1525072")   also russian design    solid great sound   takes a bit of effort to install but all instructions are provided

---

### Post by cascade9 on 2010-11-20
> **shantiq said:**
> many think [deadbeef ]("http://ubuntuforums.org/showthread.php?t=1503749")is very good

not a library-type player but it has many features is very slick and plays many formats:KS


If it had an (optional) library it would be nicer, but I've never seen any linux player with a library function as good as foobar. I'd also like it if deadbeef supported .png album art, but hopefully that will come along in a while. 

All in all, its good enough that I'm not bothering with foobar under wine anymore.

---

### Post by shantiq on 2010-11-20
well cascade i now only use deadbeef or xmms

but you know the no library thing is not really a problem  as you can tab as many playlists as you want and organize your music that way






if library is not a priority i would really go with xmms and deadbeef in that order  **  qmmp** right behind them but not quite the same calibre       funny all 3 are russian design

vlc for me will always be a movie player i cannot see it as a music player     altho it does that too   



also forgot to mention **aqualung**    which is really quite nice  and guess what    russian :KS:KS

---

### Post by cascade9 on 2010-11-20
> **shantiq said:**
> but you know the no library thing is not really a problem  as you can tab as many playlists as you want and organize your music that way

With over 14,000 files in my music collection (including logs, .cue files, and album art) tabbing really isnt a solution. Not for me anyway. Ohh well, I'm just forced to go 'edit-> clear' then 'file-> add folder' to get what I want in the playlist. More stuffing around than I'd prefer, but I cant see any other way of doing things. 

Sometimes its almost a pity I fond foobar, it spoiled me.

---

### Post by tommcd on 2010-11-21
> **shantiq said:**
> well cascade i now only use deadbeef or xmms

Shantiq,
Where are you getting **xmms** in Ubuntu from? Are you getting it from a PPA repo? 
I always use xmms in Slackware, since it is light on system resources, it is "Winamp-like" (like Audacious), and it does everything I need in a music player, but that xmms2 that is in the Ubuntu repos does not seem to work at all for me.

Tekno.Statik,
If you like Audacious, then Xmms is very similar to Audacious and is even lighter on system resources than Audacious is. On Slackware Xmms is the only music player I need.

---

### Post by shantiq on 2010-11-21
tommcd    allinfo [**Here for His majesty Lord XMMS**]("http://ubuntuforums.org/showthread.php?t=1525072")


really worth the trip    i kinda campaign for it to be reactivated


as it has the best sound of them all    to my ears shorten format on xmms is the bee's knees the dog's bollox the camel's kidneys :KS:KS:KS

           =====================================

as regards xmms2 in ubuntu that is straightforward all formats supported but plain as sin

you need a gui for that one esperanza or promoe are ok find in synaptic and click all the formats you wish for     apparently it has nothing to do with xmms    different build

---

### Post by tommcd on 2010-11-21
> **shantiq said:**
> tommcd    allinfo [**Here for His majesty Lord XMMS**]("http://ubuntuforums.org/showthread.php?t=1525072")
really worth the trip    i kinda campaign for it to be reactivated


Ok, thanks a lot for this. That seems like quite a lot of stuff just for Xmms though. I would really like the Ubuntu devs to reactivate Xmms also.

---

