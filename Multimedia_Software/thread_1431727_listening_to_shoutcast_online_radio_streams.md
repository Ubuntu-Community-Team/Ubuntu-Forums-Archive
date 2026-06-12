---
title: "listening to shoutcast online radio streams"
date: 2010-03-17
forum: Multimedia Software
---

### Post by varonbondumb on 2010-03-17
this post is to help anyone else who has had the same problem with the new version of amarok and wants to listen to shoutcast online radio (for me, KCRW)

the old amarok included support for listening to shoutcast radio streams.  however, they've taken that out and rendered amarok useless to me.  I tried using rhythmbox, and it was a no go.  after searching, I realized that VLC plays shoutcast streams just fine.  you'll have to download the .PLS file from shoutcast.com of your radio station to your hard drive and open it with VLC.  to permanently associate the PLS file type with VLC, do this:

right click - properties - open with - vlc media player - close

does anyone know of a better (more lightweigt) program than vlc to use for the purpose of listening to vlc?

---

### Post by tgalati4 on 2010-03-17
sudo apt-get install tunapie audacious

In the tunapie preferences you can specify audacious (or xmms for older systems) for playback of streams.

But, I remember that KCRW uses real player (*.rm) streams so that might not work.  In that case, you can either use Real Player for linux or continue to use VLC (as it has a real player codec).

---

### Post by mc4man on 2010-03-17
> does anyone know of a better (more lightweigt) program than vlc to use for the purpose of listening to vlc

If you search launchpad ppa's there is something called 'Gnome Media player', which uses libvlc 
(though it's very new and probably too 'lightweight  

There is also just use the older amarok 1.4 ( amarok14 in a ppa) or build pana - basically a fairly full featured amarok 1.4 ( I use pana here

[http://ubuntuforums.org/showthread.php?t=1400314&page=2](http://ubuntuforums.org/showthread.php?t=1400314&page=2)

---

### Post by cybrsaylr on 2010-03-17
I'm still using rhythmbox to listen to shoutcast radio streams. The station I listened to put 3 selections in rhythmbox and the last few weeks the first to no longer play but the third choice still works but will cut out at times. Shoutcast must have changed something recently and is not as stable as it used to be before but it still works with rhythmbox for me.

---

### Post by jwillar on 2010-10-02
I also enjoy 'Shoutcast', I use Exaile and it in the default repositories.  If you also install Streamripper, you'll be able to enable Exaile to record your songs.

---

### Post by indymike on 2010-12-06
Shoutcast was removed from Amarok because of licensing issues... You can add shoutcast using the script that [cotko]("http://kde-apps.org/usermanager/search.php?username=cotko") provided on [kde-apps]("http://kde-apps.org/content/show.php/SHOUTcast+service?content=116823").  It's not very hard, and improves Amarok's utility substantially.

---

### Post by oldos2er on 2010-12-06
Very nice! Thank you for sharing that info.

---

### Post by rchiossi on 2011-01-17
I had to stick to rhythmbox... no other solution seems to work for shoutcast... =/

---

### Post by johntaylor1887 on 2011-01-17
> **rchiossi said:**
> I had to stick to rhythmbox... no other solution seems to work for shoutcast... =/

If you add **gecko-mediaplayer** to firefox, you can listen to shoutcast directly from firefox.

---

### Post by BLTicklemonster on 2011-03-07
> **johntaylor1887 said:**
> If you add **gecko-mediaplayer** to firefox, you can listen to shoutcast directly from firefox.

??? How? I looked to see if it was an addon, but it doesn't show up.

---

### Post by ron999 on 2011-03-07
> **BLTicklemonster said:**
> ??? How? 


[SIZE="4"][FONT="Courier New"]**sudo apt-get install gecko-mediaplayer**
[/FONT][/SIZE]

---

