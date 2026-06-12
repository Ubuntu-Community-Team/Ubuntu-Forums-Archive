---
title: "Cannot read data track from data/audio CDs"
date: 2006-10-08
forum: Multimedia &amp; Video
---

### Post by jonread1983 on 2006-10-08
I have loads of CDs at home that contain videos. On a windows machine I am able to explore the data track of the CD and copy the video onto my hard drive so i dont have to get the CD each time i wish to watch it.

I cannot do that now, I get an empty window when i open media/cdrom. However the audio CDs play ok, 

I think im missing the package that allows data tracks on mixed data/audio CDs to be read.

Any advice much appreciated. :-k

---

### Post by eeried on 2006-10-09
Hello,

Same problem here with Xubuntu.

Only VLC reads an audio cd Menu File > CD

Xmms needs reconfig of cd audio plugins > /cdrom instead of /media/cdrom then Play directory (click cdrom).

No icon of the CD on the desktop.

No autorun (that is not bad).

Aren't the several cdrom and dir links confusing in Ubuntu?:

/cdrom (link)
/media/cdrom (link)
/media/cdrom0
/media/cdrom1

I understand the advantage, but can we customize to remove unnecessary links?

---

### Post by eeried on 2006-10-09
Hello again,

I've just reread an oldish article (for Breezy) I wrote on XMMS and audio cds (but it's in French, and needs revising)): [Libre-Fan: Améliorer le son et lire les MP3 sous Ubuntu]("http://libre-fan.apinc.org/article77.html")

In Xmms I can now see all the tracks. So I can play all or any of them. This is what you can try:

Launch Xmms > right clic > Menu Options > Preferences > Window: I/O plugins
> Click on Cd audio plugin (first line in the panel) > click on "Configure" button 
Config window: edit directory: /cdrom (instead of /media/cdrom)

Note: I only have one cdrom drive. I'll try this on a friend's computer and report.

Now you can choose to open a dir (/cdrom) to play the whole CD or to play certain tracks in the /cdrom dir

cheers

---

### Post by jonread1983 on 2006-10-09
Just tried that and now it cant ready any CDs!

Hmm

---

### Post by eeried on 2006-10-09
Do have one or two CD/DVD drives?

I tried the same settings on an Ubuntu with 2 cdrom drives and it didn't seem to work... but I didn't have time to look at it again.

At least on that fresh Ubuntu install the CD icon appeared on the desktop and so the CD could be ejected, but its contents could not be read.

On Ubuntu when your insert an audio CD Serpentine springs out and make a list of the tracks. Doesn't this work for you? ](*,) 

Cheers,

---

### Post by KBowz on 2006-10-17
I have a similar issue (and I should say this is my first venture into *any* linux box):

After a new installation of Ubuntu, I put in a mixed-media CD, and was prompted what do I want to do with it.  I inadvertently checked the box to always perform this action and selected play music.

I want to uncheck that box, but can't find the option anymore, and now I'm having problems reading the data portion of my mixed-media CDs because it always wants to play the music.

How can I change this setting?

Thanks in advance.

---

### Post by eeried on 2006-10-17
Can someone help us?

---

