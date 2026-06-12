---
title: "Looking for a good Music Player for Ubuntu 20.04"
date: 2020-06-11
forum: Multimedia Software
---

### Post by wmrp on 2020-06-11
I am new to Ubuntu and have thus far only worked with Windows. For years I have been using a favorite (older version of) iTunes for a huge audio library (synced with a 160Gb iPhone Classic, to give you an idea of the size). 

Ubuntu 20.04 comes with Rhythmbox, but I would like something visually more appealing that will also allow me to easily organize the music library (I don't like how it all appears on Rhythmbox --seemingly random-- and the fact that there are so few options for customization).

What music players do you members on this forum like that might give me what I am looking for? 
Thanks in advance for any helpful suggestions.

---

### Post by CelticWarrior on 2020-06-11
[https://www.slant.co/topics/5260/~media-players-for-linux](https://www.slant.co/topics/5260/~media-players-for-linux)

And you can install iTunes with Wine but be aware it'll work as media player only, it won't sync with Apple devices. On top of that your *(older version of) iTunes* likely will be easier to install than the current version.

---

### Post by wmrp on 2020-06-11
Thank you @CelticWarrior. Good list; I will check if Clementine accomodates playlists and customization. 
I set up Ubuntu as double boot with W7 just so I can do the occasional sync between iTunes and iPod (on windows). So I won't be needing it for that on Ubuntu. I am just looking for an appealing player with enough options that is open source and Linux compatible.

---

### Post by T6&amp;sfpER35% on 2020-06-11
you could also check out banshee

---

### Post by monkeybrain20122 on 2020-06-11
[guayadeque]("https://launchpad.net/~anonbeat/+archive/ubuntu/guayadeque") is very featureful and is good at handle large music collections. [strawberry]("https://snapcraft.io/strawberry") seems nice but I don't know how it manage large collections. My own collection is very small, less than 10G. The previous post mentions Banshee, personally I don't like it, find it too bloated and I don't like a music management app that also plays videos, there are much better video players like mpv.

---

### Post by wmrp on 2020-06-12
Good points, @monkeybrain. I am indeed looking for a player for just music, not videos. I guess that rules out Banshee (thanks anyway, @3nd). I will see if I can find out how Guayadeque compares to Clementine. Thanks for the recommendation.

---

### Post by ra7411 on 2020-06-12
Audacious - it has tabs which make organization easy.

---

### Post by mIk3_08 on 2020-06-12
vlc is okay for me.

---

### Post by coffeecat on 2020-06-12
> **3nd said:**
> you could also check out banshee

In 20.04? It's not in the 20.04 repositories.

Banshee appears to be abandonware - last stable release was over 6 years ago. I found it very buggy in 16.04 and unusable in 18.04. A great pity - I liked it, but with no active development for years I've had to find an alternative.

@wmrp, I use Clementine now. It's good and at least it doesn't crash all the time the way Banshee did in 18.04. Let us know which of the suggestions you find best for your needs. Good luck.

---

### Post by wmrp on 2020-06-12
Reviewers state that they have a hard time getting [guayadeque]("https://launchpad.net/~anonbeat/+archive/ubuntu/guayadeque") to install on 20.04
I may give Clementine a try first, as it is in the Ubuntu Software store and is hopefully easy to work with. Hopefully it can handle my (currently) 147 GB of music.

---

### Post by ajgreeny on 2020-06-12
I agree with ra7411 and use audacious for audio; for video I am in agreement with mIk3_08 and choose vlc.

Both these applications are relatively simple but work well with playlists and as far as I am concerned do all I need without too many GUI bells and whistles.  They can play any file I have thrown at them which is what matters to me.

It's the music or video I want, not some fancy GUI application.

---

### Post by Yellow Pasque on 2020-06-12
I've used Audacious for a looong time now, but I like the playlist-driven interface as opposed to library/iTunes style.

I prefer Strawberry when I'm working on tagging/organizing: [https://launchpad.net/~jonaski/+archive/ubuntu/strawberry](https://launchpad.net/~jonaski/+archive/ubuntu/strawberry)

---

### Post by monkeybrain20122 on 2020-06-13
> **wmrp said:**
> Reviewers state that they have a hard time getting [guayadeque]("https://launchpad.net/~anonbeat/+archive/ubuntu/guayadeque") to install on 20.04
.

I installed it without problems.

The latest release of clementine is 1.3.1 from 2016 (there are new commits in the master branch though, but you have to compile from source). Strawberry is actually a fork of clementine and is up to date.

---

### Post by robhill19652 on 2020-06-13
I've used and loved Amarok for years, but it's incompatible with 20.04 right now. I did a bunch of research, tried a few, and settled on both Elisa and Clementine. The appearance is similar to iTunes, and handles your music library similar as well. You can add streaming radio stations to Elisa, but you can do that with a 3rd party app in VLC too, (which is my goto for video)

---

### Post by Yellow Pasque on 2020-06-14
> **monkeybrain20122 said:**
> The latest release of clementine is 1.3.1 from 2016 (there are new commits in the master branch though, but you have to compile from source).

No, Ubuntu takes care of that by offering 1.4.0rc1: [https://packages.ubuntu.com/focal/clementine](https://packages.ubuntu.com/focal/clementine)
I think I'd rather use the Strawberry PPA though, as the dev/maintainer does a good job of offering continuous updates.

---

### Post by wmrp on 2020-06-14
In Ubuntu Software I find Clementine and Clementine Music Player. I take it that it is the former we are talking about, correct?

---

### Post by CelticWarrior on 2020-06-14
Should be the same but one of them is a snap.

---

### Post by wmrp on 2020-06-14
I am new to Linux, so what again is a snap?

---

### Post by mc4man on 2020-06-14
> **CelticWarrior said:**
> Should be the same but one of them is a snap.
Beware of the snap, see

[https://github.com/kz6fittycent/clementine/issues/9](https://github.com/kz6fittycent/clementine/issues/9)

---

### Post by wmrp on 2020-06-14
Few more questions have come up: 
which player can
1) do smart playlists, where it adds to it automatically based on for example the name of the composer or genre? 
  (There is just no way to create playlists by hand from a huge library)
2) categorize music as albums instead of listing them by artist?
3) can handle large amounts of music (up to 160GB)?

---

### Post by monkeybrain20122 on 2020-06-14
> **wmrp said:**
> Few more questions have come up: 
which player can
1) do smart playlists, where it adds to it automatically based on for example the name of the composer or genre? 
  (There is just no way to create playlists by hand from a huge library)
2) categorize music as albums instead of listing them by artist?
3) can handle large amounts of music (up to 160GB)?

guayadeque.

---

### Post by wmrp on 2020-06-15
> **monkeybrain20122 said:**
> guayadeque.

I do not find it under Ubuntu Software, so for installing it, do I use the second method (from source code)? [URL="https://www.guayadeque.org/viewtopic.php?f=3&t=6656"]https://www.guayadeque.org/viewtopic.php?f=3&t=6656
[/URL]
I entered the following, but don't find any signs that it has installed: sudo add-apt-repository ppa:anonbeat/guayadeque
apt install guayadeque

---

### Post by Yellow Pasque on 2020-06-15
For guayadeque, why wouldn't you just use the PPA?: [https://launchpad.net/~anonbeat/+archive/ubuntu/guayadeque](https://launchpad.net/~anonbeat/+archive/ubuntu/guayadeque)

---

### Post by wmrp on 2020-06-15
> **Yellow Pasque said:**
> For guayadeque, why wouldn't you just use the PPA?: [https://launchpad.net/~anonbeat/+archive/ubuntu/guayadeque](https://launchpad.net/~anonbeat/+archive/ubuntu/guayadeque)

Thank you. Unless your question was rhetorical; the honest answer is that I am just starting out with Linux. It's like learning a completely new language, where at first one just guesses at the meaning of things, at other times one feels compelled to look up a definition in the hope it sheds light, then there is reading and asking questions....in short, there is a learning curve :-)

---

### Post by wmrp on 2020-06-15
I installed Guayadeque twice. Once as 
sudo add-apt-repository ppa:anonbeat/guayadeque
apt install guayadeque

and once as


sudo add-apt-repository ppa:anonbeat/guayadeque
sudo apt-get update

The process seems to complete itself and I don't receive any error message, BUT... I don't find it anywhere under installed programs. I shut down the pc and started it up again, but nothing. 
Anyone has a suspicion as to what may be going on?

---

### Post by monkeybrain20122 on 2020-06-15
sudo  apt update only update your repositories so that guayadeque is now  available, you forgot to actually install it by 

```
sudo apt install guayadeque
```

Your first attempt left out the sudo.

---

### Post by lister171254 on 2020-06-15
I've tried most of them over the years and settled on clementine now. Workds as expected, has a remote, random and dynamic playlist, etc.

---

### Post by wmrp on 2020-06-16
> **monkeybrain20122 said:**
> sudo  apt update only update your repositories so that guayadeque is now  available, you forgot to actually install it by 

```
sudo apt install guayadeque
```

Your first attempt left out the sudo.

That did the trick. Thank you!

---

### Post by HansCombee on 2020-06-16
I just love Clementine

---

### Post by wmrp on 2020-10-03
I just have no idea how to populate Guayadeque with music since the import option does not work.

---

### Post by wmrp on 2020-10-03
Another annoying thing is that it won't play a CD in its entirety, but only the track you click on. How inconvenient is that... I can't help think that there must be a way around this, but what is it?

---

### Post by monkeybrain20122 on 2020-10-03
> **wmrp said:**
> Another annoying thing is that it won't play a CD in its entirety, but only the track you click on. How inconvenient is that... I can't help think that there must be a way around this, but what is it?

I have no idea, I don't even have a CD drive anymore. In the old days I just ripped them with k3b instead of playing directly from the CD. If you prefer to play from the CD, just use good old vlc, it will do the job.

---

### Post by ajgreeny on 2020-10-03
> **monkeybrain20122 said:**
> I have no idea, I don't even have a CD drive anymore. In the old days I just ripped them with k3b instead of playing directly from the CD. If you prefer to play from the CD, just use good old vlc, it will do the job.
Audacious will also play audio CDs and is a much smaller, faster application than VLC; I use VLC for videos but not for audio for which I believe it's generally overkill

---

### Post by hk42 on 2020-10-03
There is a  nice application here:
[https://webamp.org/](https://webamp.org/)
It works nicely with firefox and your own files you don't install anything.
There is also an appimage stand alone file.
[https://www.appimagehub.com/p/1297098](https://www.appimagehub.com/p/1297098)

---

### Post by monkeybrain20122 on 2020-10-03
> **ajgreeny said:**
> Audacious will also play audio CDs and is a much smaller, faster application than VLC; I use VLC for videos but not for audio for which I believe it's generally overkill

I am sure it does, but I figured vlc is common and OP probably already has it installed.

---

### Post by wmrp on 2020-10-04
> **wmrp said:**
> I just have no idea how to populate Guayadeque with music since the import option does not work.


Posting the above again, as I think it did not get noticed.

---

### Post by Holger_Gehrke on 2020-10-04
I won't install Guyadeque just to check out a hunch, but if it's anything like other library oriented players I've tried in the past then you have to set a directory as your library in the settings. 'Import' will then copy or move the files you give it to that folder.

Holger

---

### Post by wmrp on 2020-11-30
I do not prefer to play from CD. The only reason I did that is that the music player does not import my huge digital music library (or even a portion of it). That is the whole point...but I guess anyone who read my original queries in this thread would have picked that up already. 
No clues anyone? How about the fellar who recommended this player in the first place, based on my expressed need to import my 15 GB (former iTunes) music library? 

One more time: I would really like to play music while I work, imported into a good music player on Ubuntu. Folks on here must be doing that, I am sure. This old newbie would love to know how. Thanks in advance!

---

### Post by speartip on 2020-12-01
Strawberry has been mentioned 3 times in this thread. Have you tried it yet? Handles my 150 gig of Music no problem.
[https://www.strawberrymusicplayer.org/](https://www.strawberrymusicplayer.org/)

---

### Post by CelticWarrior on 2020-12-01
> **speartip said:**
> Strawberry has been mentioned 3 times in this thread. Have you tried it yet? Handles my 150 gig of Music no problem.
[https://www.strawberrymusicplayer.org/](https://www.strawberrymusicplayer.org/)

+1

It handles my ~200GB music library just fine as well.

---

### Post by wmrp on 2020-12-09
that 15 should be 150! ;-)

---

### Post by wmrp on 2020-12-09
I did indeed install it after it came recommended here. Will check whether it cooperates more when importing a library. Thanks for the reminder!

---

### Post by wmrp on 2021-01-25
So I have been using Strawberry for a while now as music player. I have yet to find some sort of manual online as I have many unanswered questions regarding its use. For example, how to create playlists. When I play tracks it creates some sort of list to which it will add anything I play subsequently. I really don't get the point or use of this. When I try to handpick tracks to create a playlist, so I can create some order and organization I find that it won't let me. 

Before this I had only used iTunes to which I uploaded my personal 1K+ CD collection. Strawberry is so different, and (as yet) to me counter-intuitive, that I need some training. Is there anything like that online?

---

### Post by CelticWarrior on 2021-01-25
Try searching for Clementine tutorials. Starwberry is just a fork, not sure what the difference are, but I suppose basic functionality is the same.

---

### Post by wmrp on 2021-01-25
> **CelticWarrior said:**
> Try searching for Clementine tutorials. Starwberry is just a fork, not sure what the difference are, but I suppose basic functionality is the same.

Okay, thanks. Will do.

---

### Post by Yellow Pasque on 2021-01-25
The main dev working on Strawberry seems overloaded as is, so comprehensive user documentation is probably on a distant backburner. As an iTunes user, I don't know if you're going to be happy with anything other than iTunes. It seems like folks who are familiar with that don't find an acceptable alternative in Linux land.
Obligatory "workflow"  comic: [https://xkcd.com/1172/](https://xkcd.com/1172/)

> Try searching for Clementine tutorials. Strawberry is just a fork

And Clementine is a fork of Amarok 1.x, which may have some good docs as well.

---

