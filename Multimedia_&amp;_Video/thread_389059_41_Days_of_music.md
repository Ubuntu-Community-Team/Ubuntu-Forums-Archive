---
title: "41 Days of music"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by Lutherian on 2007-03-20
Not sure what category this would fit into, but anyway.

I have an average (by today's standards) number of mp3s, oggs, aac's files totalling about 41 days of continuous play.

All these files sit on an Ubuntu machine in another room.

When I attempting to import all the songs into an applications such as Banshee or Similar - the application will "bomb out" at about 75%.

OK *** Here's the interesting part ****

I booted to Windows and tried to build my library with Winamp - exactly the same thing happened. I looked at the Windows Task Manager Performance Monitor and noticed that the Page File Memory Usage steadily climbed higher and higher until it reached 100% and about 75% of all the files to be imported. Then WinAmp "Bombed Out"

==========================

So my theories are:
1) The Samba "Server" is feeding files in a manner that causes memory leaks of some kind on the client side.?
2) All the respective programs used to import the files have a limitation on the number of file that can be imported at once.?
3) The server does not have enough memory to handle the files?

---

### Post by ThinkBuntu on 2007-03-20
Just move it in parts then. 41 Days must be about 50GB, so move it in two parts, and continue breaking it up smaller until it doesn't crash. It stinks, but only a little bit because it's a one-and-done task.

---

### Post by Lutherian on 2007-03-21
Yes, about 35 GB (Very good estimation BTW) Most of the files are [aac] format so they're smaller than the average mp3 (+/- 1.2 Mb) and the oggs (+/- 2Mb).

I agree, "in parts" is the way to go, not a problem, but technically interesting.
BTW - I tend to use **Banshee** because of the solid [aac] support, but I've heard a lot of good things about **RythmBox**. In your opinion, is it better? (and if so why) and can it support [aac]?

My Totem can play [aac] due to enabling of faad, faac in gstream, but RythmBox doesn't seem to play [aac.]

In a perfect world ogg files would be the same quality as aac and *all* hardware devices would play them. LOL (aac+ogg=aog the new open source codec that can play on an mp3 device at 25% of the MP3 file size, with JPG embedded CD Covers and TXT embedded lyrics with Karaoke function timed play-back lyrics..)

Sorry, I was daydreaming out loud again ;P

---

### Post by slayerboy on 2007-03-21
Trust me from experience, about the only app that I've used that hasn't bombed out yet is Amarok.  You just need to let it take it's time.  I have a H - U - G - E collection and it probably took about an hour to update Amarok after I moved everything.

Also, how much RAM do you have?  What about swap space?  I have 1GB RAM, not sure I'd attempt this with anything less.

---

### Post by Lutherian on 2007-03-21
Ahhh, here we come to the sensitive topic of Gnome/KDE 
Is it possible to run Amarok in Gnome. I've heard a LOT of good things about it.

Yes, my memory (RAM) is much lower about 256 MB, but I'm pigheaded about such things [-( - I refuse to upgrade memory and then I start to rant about how it was once possible to run a spreadsheet, word processor and database all in 640kb of RAM on an XT machine and so why the hell should I upgrade upgrade RAM - :-({|= etc, etc and anyway I go on like that for 45 minutes .... until I realize that no one's listening to me and have all gone away.:tongue: :tongue: :tongue: 

When I switched to Linux I was kind of hoping to find a lot of  simple low memory programs so that I could do a lot of different things at the same time. I would've gone the command line route for my music but, a command line / console music library? Seems contradictory to me and a console aac/mp3/ogg player - doubtful.

---

### Post by slayerboy on 2007-03-21
As far as KDE/Gnome thing, I'm not getting into it.  Amarok runs fine in Gnome, KDE, XFCE, Fluxbox, E17, blackbox...etc....etc....

With only 256MB of memory, you're going to see this happen because it just takes too much to load all of that.  Like I said, I have 1GB and when I try to load my 58 day long collection it takes forever.

Also, there is a big difference between just loading the songs into the library and putting them all on one playlist. The library loads fine once all the original scanning has been done.  If you have your entire collection in a playlist, it's going to self-implode.  I almost thought Amarok did when I tried putting all my songs in the playlist.  It loads slower than heck if I keep the playlist loaded for next time.

Try using Amarok and specify where you want it to look to add to your library.  Then from there, you can use some auto generated playlists or browse and create your own.  I love the one auto playlist that you can generate that gives you 50 random songs.

Try it, I think you'll like it.

---

### Post by Lutherian on 2007-03-22
As long as I can get the files imported into a library - that's fine. I don't use playlists too much, but I like to find a particular song quickly when I want to listen to it. 

Thanks for the info - will download Amarok  tonight. :)

---

