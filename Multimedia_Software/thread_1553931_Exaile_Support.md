---
title: "Exaile Support?"
date: 2010-08-15
forum: Multimedia Software
---

### Post by schattengarde on 2010-08-15
For the last couple of months, I've been experimenting with Ubuntu on my laptop, seeing what I liked and didn't like and so on. The biggest difficulty I've run into is picking a media player. I ruled out Songbird pretty early because I really don't like the iTunes interface. I finally settled on Exaile after hearing that it was a Gnome-friendly player based on Amarok, which I'd read to have outstanding reviews.

So far: I really like Exaile's default interface, and it runs very well for long periods of time without any stability issues. However, there are a couple of issues I've come across with it, and was wondering what could be done about them.

1. Exaile does not seem to like anything with diacritic marks over the letters. It doesn't always transition cleanly between them, and has a bad habit of replacing the "special character" with random symbols. It makes listening to music in German and Russian an issue at times, and has also done some weird things to my Queensryche playlist.

2. Vaguely related to issue No 1., Exaile insists that I have two copies of Eisbrecher's "Antikörper" album. I checked the files, and I only have one. However, Exaile loads two copies of every song each time I try to play the album, and one "copy" plays just fine, while the other won't play at all.

3. Exaile also seems to only let me have one permanent playlist. I can create and save playlists normally, but they will often be gone when I close and restart the program.

TL,DR: What's your favorite media player for Gnome Ubuntu?

Thanks!

---

### Post by John Krow on 2011-01-03
Hi, I use exaile pretty much exclusively for music. Simple reason, my first home installation of GNU/Linux was on a HP machine with limited RAM and I found exaile's performance superior to that of Rhythmbox. Less juddery. I seem to recall I tried the other major music players with GUIs and nothing beat exaile's performance. So when I upgraded to a more recent machine, I've stuck with it. 
I've not come across your problems myself. Two suggestions occur to me. If you look on the exaile website there is a mailing list for exaile users at [http://groups.google.com/group/exaile-users](http://groups.google.com/group/exaile-users)
which I've not subscribed to myself but it may well be helpful, who knows?

Today i upgraded to exaile 0.3.2.0 by adding the developers ppa
```
sudo add-apt-repository ppa:exaile-devel/ppa
```and upgrading the program with 
```
sudo apt-get install exaile
```and this may solve your problem(s), possibly? Let us know whatever happens.

My main problems with exaile ATM is that it doesn't seem to be able to connect to Shoutcast at all these days, lyrics don't seem to download and it doesn't seem to be able to load *some* podcasts' feeds. Some interesting points about plug-ins here:
[http://ubuntuforums.org/showthread.php?t=1330144]("http://ubuntuforums.org/showthread.php?t=1330144&page=2")

I've also used MOC, an audio player for the terminal, which is fabulous in its own right.

---

### Post by DapperMe17 on 2011-01-04
See my post post about shoutcast here....[http://ubuntuforums.org/showthread.php?t=1655012&highlight=shoutcast](http://ubuntuforums.org/showthread.php?t=1655012&highlight=shoutcast)

---

### Post by John Krow on 2011-01-09
> **John Krow said:**
> 

Today i upgraded to exaile 0.3.2.0 by adding the developers ppa
```
sudo add-apt-repository ppa:exaile-devel/ppa
```and upgrading the program with 
```
sudo apt-get install exaile
```and this may solve your problem(s), possibly? Let us know whatever happens.


Just a heads up if anyone does this. I found the version of exaile (which appeared to be marked as stable rather than a dev release as such) i downloaded from the ppa above was playing files in a distorted fashion. Lots of drop out and distortion. I dunno if it was because of how the program was interacting with my sound set up, but removing exaile (with the apt-get  --purge command) and installing v0.3.2.0-1 from [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) lucid/main seems to have fixed this!

--eta: no it hasn't, the problem has returned . I think somethings up as --purge doesn't seem to be purging all files anyway.

---

