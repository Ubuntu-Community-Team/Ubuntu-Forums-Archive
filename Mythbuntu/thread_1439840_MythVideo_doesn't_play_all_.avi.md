---
title: "MythVideo doesn't play all .avi"
date: 2010-03-26
forum: Mythbuntu
---

### Post by AndrewSJGrant on 2010-03-26
Hello,

I've got MythVideo running on my Mythbuntu machine. For some reason it can only play some .avi files. I've got mplayer, vlc and xine installed on all frontends and the backend. When I try to play some of them it stalls, once i've clicked play it displays 'Please Wait...' and then returns to the Play / Done box. Has anyone got any ideas?

Also, MythVideo isn't displaying all the files which i've dragged into MythVideo folder. I keep doing 'Scan for changes' but it doesn't seem to include all of them. All my files are copied across from my Mac via SMB.

Many Thanks!

Andrew

---

### Post by theiron on 2010-03-27
I found and used this from another thread, give it a try.  I had trouble getting my DVD to play any movies or TV on DVD back, and the following command made all right with the world:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2

Just copy and paste into a terminal window, and see what happens.  Afterward, a restart wouldn't hurt, but all of my DVDs play back now.

---

### Post by frego on 2010-03-27
I had a similar issue.  I checked my permissions on the files that wouldn't play and compared to the permissions that would play.  Apparently, Myth likes having the files group writable not just user writable.  I used chmod and now they all play.

---

