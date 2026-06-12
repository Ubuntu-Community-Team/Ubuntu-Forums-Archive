---
title: "Too many media player choices"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by ascus4 on 2007-10-25
I searched this and found out that there are a lot of media players for Gutsy.
There are also a lot of opinions as to which are the best.

Is there a definitive 'official' list of the best media players to install.  I'm a multimedia lover and want to be able to play or listen to pretty much everything.  I'm tired of having to boot to windows to do certain things.

My default Gutsy installation has:
Movie Player
Rhythmbox

I have installed but not yet tested:
Realplayer
VLC

Thank you in advance.

---

### Post by earobinson on 2007-10-25
for me I use the stock ones

Rhythmbox for music
and totem (movie player) for movies

---

### Post by glupee on 2007-10-25
I like kaffeine. It's my sole movie player. For music I use Amarok. Just personal preference.

---

### Post by zettberlin on 2007-10-25
alsaplayer with jackd for ogg, wav and mp3 and VLC for everything else.

---

### Post by ascus4 on 2007-10-25
I'm not having much luck with any players except for MP3s on Jukbox.  Can't even play a movie from DVD.  It's probably a codec thing.  Is there an all inclusive codec installer that will accomodate all or most common video and music?

I want to watch DVD movies, play music off CDs, watch and listen to streaming media of common formats.

---

### Post by fain on 2007-10-25
> **ascus4 said:**
> I'm not having much luck with any players except for MP3s on Jukbox.  Can't even play a movie from DVD.  It's probably a codec thing.  Is there an all inclusive codec installer that will accomodate all or most common video and music?

I want to watch DVD movies, play music off CDs, watch and listen to streaming media of common formats.

you need the medibuntu repositories. you can easily enable them by installing mythbuntu control center and click the check boxes, or you can manually install the repositories from the medibuntu repo how-to

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by ascus4 on 2007-10-25
I just went through Synaptic and installed all of the more popular players that I hear about along with a bunch of plugins and stuff.

I'll now follow your suggestion and we'll see what happens.  I figure their are so many opinions on players that I'll just install everything I can fine and see what I like.

---

### Post by ascus4 on 2007-10-25
About Medibuntu.  I have an AMD64 with the 32 bit version of Ubuntu installed.  I use the AMD64 version on the website?

---

### Post by ascus4 on 2007-10-25
After dealing with Medibuntu, my DVD seem to play in VLC but not in anything else.  I guess that's ok.
I only need one player to work and it looks like a nice player.

I think the w32 codecs installed as well but I don't know how to tell unless I try to play something and it fails.

I'll have to test other media formats at a later date.

I appreciate your help.

---

### Post by VCSkier on 2007-10-25
I would *not* recommend using the 3rd party medibuntu repository.  Now (since feisty) you can simply install the "ubuntu-restricted-extras" metapackage after enabling the universe, multiverse, and partner repositories.  This installs all your common codecs, dvd playback support, flash, java, and everything else you need at once, with no 3rd party repositories.  It's by far the best way to go.

Here's a link. [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by ascus4 on 2007-10-25
That's what I was looking for.  A one stop shop for all the codecs I need.
I have already installed the Medibuntu codecs.  If that's really a problem, how can I uninstall them and use the ones you suggested.
Or...if I install yours', will it disable and override the Medibuntu versions.

---

### Post by VCSkier on 2007-10-26
I would just remove the medibuntu repositories and then install ubuntu-restricted-extras, but I'm not sure.  Give it a shot, I wouldn't think it would break anything.

---

### Post by fain on 2007-10-28
i didnt know this thanks for the info :)

you could set up a filter in synaptic for install sources and filter packages from medibuntu and mark completely remove this package on all the installed packages.

---

### Post by bazzard on 2007-10-29
Any recommendations for an all-in-one player that allows music, video and dvd play back. I want a program that uses a good library system and automaticlaly finds album art and stuff.

---

### Post by ascus4 on 2007-10-30
I did a clean install to try to get rid of the slow boot issue so I got rid of medibuntu that way.
Not a big deal.  I didn't have much on it at that point.
Still takes 3 minutes from power on to log in screen.

---

