---
title: "Import DVD has Spanish not English"
date: 2007-12-11
forum: Mythbuntu
---

### Post by ahood on 2007-12-11
Hi All,

I am experiencing something strange with Mythbuntu. When I import a DVD, the actors are speaking Spanish rather than English. I make sure that I have selected 'en AC3 6 Ch' in the audio setting of the DVD import and iso image. There are a few trailers before the main video, which are in English. Only the main 2.5 hour video/m0vie is in Spanish.

I have imported one other dvd and the language was English on that one, but not this one.

Curious to know the the cause and a possible fix. Any help will be greatly appreciated,

---

### Post by spalVl on 2007-12-11
[http://www.knoppmyth.net/phpBB2/viewtopic.php?t=6574](http://www.knoppmyth.net/phpBB2/viewtopic.php?t=6574)

Short version


I reseached in the gossamer threads a bit and another solution is to create a .conf file in /home/mythtv/.mplayer
Below is a sample file.

Code:
# config file /home/mythtv/.mplayer/rippedmovie.iso.conf
aid=128


After adding .conf file worked fine. I recall reading problem had to do with perfect quality recording all audio tracks and mplayer not choosing correct track.

---

### Post by ahood on 2007-12-12
> **spalVl said:**
> [http://www.knoppmyth.net/phpBB2/viewtopic.php?t=6574](http://www.knoppmyth.net/phpBB2/viewtopic.php?t=6574)

Thank you spalVI!

I read the post linked above and I realize the following:

The default language to Spanish is not a player issue as it occurs if I switch the player to xine (xine -pfhq dvd://) instead of mplayer. 

It must be an import issue.

I can get English simply by pressing the 'Menu/i' button on my Hauppauge remote (m key on the keyboard) that brings up a menu list and select the second option 'Select Audio Track' and change the language setting to '3:Spanish'.

It is unfortunate that the language tracks are mixed up as those that expect perfection will undoubtedly be annoyed. 

However, for me, this is a minor issue and I am perfectly happy to just change the language from English to Spanish in the menu system when the audio tracks do not correspond correctly.

Again, thank you for the help.

---

### Post by jr_herman on 2009-01-27
> **spalVl said:**
> ...reseached in the gossamer threads a bit and another solution is to create a .conf file in /home/mythtv/.mplayer
Below is a sample file.

Code:
# config file /home/mythtv/.mplayer/rippedmovie.iso.conf
aid=128

I'm new to linux. Could you walk me through how to create such file?#-o

---

