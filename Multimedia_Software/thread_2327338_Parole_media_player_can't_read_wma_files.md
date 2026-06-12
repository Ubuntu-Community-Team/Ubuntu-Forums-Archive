---
title: "Parole media player can't read wma files"
date: 2016-06-09
forum: Multimedia Software
---

### Post by Jorhel on 2016-06-09
Hi,
All I want to do is playing an audio CD on my computer. Most of them have .wma files on them. but when I try to play them I get that message
**"Gtreamer back end error could not handle CDDA URI."**
gmusicbrowser will not let me add those files to the music listing not recognising them as music files.
I guess there is something missing in the package?
I'm using xubuntu trusty tahr on a compaq presario desktop.
thanks

---

### Post by X-RED_Tech on 2016-06-10
A CD with .wma files isn't a Audio CD. It's a data CD (CD-ROM) with .wma files inside. The practical results might be the same if the player supports both but technically nothing similar.
Any Audio CD should be supported out of the box. Any other situation depends on having or not the correct codecs for the file types involved. Whether they're in a CD, DVD, BD, harddrive, networks, etc. doesn't matter. Many relevant codecs aren't shipped in the Ubuntu installation media due to licensing restrictions. WMA, a Microsoft proprietary format, is among them for obvious reasons.

You should install additional multimedia codecs if you want to have the best possible multimedia support in Ubuntu. Try this:
```
sudo apt-get install xubuntu-restricted-extras
```

---

### Post by yoshii on 2016-06-11
Parole has some other isses as well.  
I'm not entirely sure, but VLC Media player can probably play them.  It seems to be able to play quite a lot of audio formats in addition to pretty much every mainstream video format.  It's freeware and you can get a decent version of it for the Ubuntus from their homepage.  If that doesn't work, Audacious (also freeware) might be able to play them too.  And if that doesn't work, you could try installing 32-bit Wine and then running 32-bit Foobar2000 (freeware).

---

### Post by Jorhel on 2016-06-12
> **X-RED_Tech said:**
> A CD with .wma files isn't a Audio CD. It's a data CD (CD-ROM) with .wma files inside. The practical results might be the same if the player supports both but technically nothing similar.
Any Audio CD should be supported out of the box. Any other situation depends on having or not the correct codecs for the file types involved. Whether they're in a CD, DVD, BD, harddrive, networks, etc. doesn't matter. Many relevant codecs aren't shipped in the Ubuntu installation media due to licensing restrictions. WMA, a Microsoft proprietary format, is among them for obvious reasons.

You should install additional multimedia codecs if you want to have the best possible multimedia support in Ubuntu. Try this:
```
sudo apt-get install xubuntu-restricted-extras
```

Thanks for that.
It's a bit counter intuitive since these are CD bought from the shop designed to be played on a CD player, but hey, you learn every day.
That still raise the question of why commercial CD of music are in a Microsoft proprietary format. 
unfortunately I seem to already have those packages installed... so it seems I will have to look at installing another player
```
sudo apt-get install xubuntu-restricted-extras
[sudo] password for jorhel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xubuntu-restricted-extras is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 15 not to upgrade.

```

> **yoshi2 said:**
> Parole has some other isses as well.  
I'm not entirely sure, but VLC Media player can probably play them.  It seems to be able to play quite a lot of audio formats in addition to pretty much every mainstream video format.  It's freeware and you can get a decent version of it for the Ubuntus from their homepage.  If that doesn't work, Audacious (also freeware) might be able to play them too.  And if that doesn't work, you could try installing 32-bit Wine and then running 32-bit Foobar2000 (freeware).

Thanks for that,
I installed VLC media player via terminal 
```
sudo apt-get install vlc browser-plugin-vlc

``` 
and it reads my CDs.
You can also get it via the software centre but for some reason I get a quick of doing it via the terminal, like if I was a real geek who know what he is doing.
But since I'm not really, is it safe to remove Parole media player since it was installed with my initial set up?

---

