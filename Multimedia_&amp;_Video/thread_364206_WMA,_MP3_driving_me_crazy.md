---
title: "WMA, MP3 driving me crazy"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by durty_dawg on 2007-02-17
O.k. I'm getting frustrated here, I have installed codecs done this and done that, yada yada yada. I still can't play my wma's and mp3's off my external hard drive. I corrected the problem in my sources list. This is the last thing to deal with before I drop Win-Hoes 100% right now I'm 99.5% I just need to get my wma's and mp3's to play. I will provide all info if asked. 

Specs are Ubuntu 6.06 
Dell Inspiron 1150/ 2.6GHz pro. Celeron
512 RAM 
D-link Airplus DWL-G650(works great)
40gb toshiba Internal hd
250gb lacie external hd

Some assistance would be great guys

---

### Post by Cobikegeek on 2007-02-18
Here is the basic setup to get rhythmbox to play mp3's:

1. Install Lame codecs

2. Open rhythmbox

Select edit-preferences and click on the library tab.  Then, edit profiles box at the bottom of the window.   Click on "New" and create a profile named MP3.  Paste this code into the Gstreamer Pipeline text box:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux

Enter mp3 for file extension.  Check the "Active" box and "OK" to close.  From the profiles list select MP3 and close.  That sets up rhythmbox.  (if you want a different bitrate, just change the number in the code, ie. 196, 128...)

In the library tab and click the drop down list box for preferred format and select the MP3 profile.  Use the Browser in the library tab to select the folder with your mp3 files. Your files should populate the tracklist and you can just press play.

The same mp3 format you created can now be used by soundjuicer to rip mp3s.

I'm not sure about playing wma format.  Check the ubuntu restricted formats page for more info at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Good luck

---

### Post by ubuntu27 on 2007-02-18
**durty_dawg** I took a look at your other post.

In [the other thread]("http://ubuntuforums.org/showpost.php?p=2168473&postcount=8") you you posted your source.list 
and I see that you have BOTH Dapper and Breezy Sources.
That is a big problem, it could break your system.


So, which version of Ubuntu are you running? Breezy Badger (Ubuntu 5.10) or Edgy Eft (Ubuntu 6.10)?

You have to "clean" that Source

Or maybe it is already broken and you need to re-install...



As for the codecs, follow this one:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by durty_dawg on 2007-02-18
Well my partial bout of retardism is over with, Yes, I noticed I was actually running dapper, breezy, and edgy. I did a sources.list edit where i went through and changed all of the breezy and edgey to dapper, then did sudo aptitude update it messed up so i did a sudo aptitude clean, then update, then upgrade. My seriously hard hit retard factor was i was forgetting to actually install the dang codecs, lol. I had downloaded all dang day but forgot to place them.
So big retard on me guys I do apologize, but I'm only human.
 On the flip side I'm now offically through with Win-Hoes and Micro-Slop, as far as I'm concerned they can go hug a root. I'm trying to learn everything there is to know bout Linux/Unix. Next stop is the big money game of admin.

---

### Post by ubuntu27 on 2007-02-18
> **durty_dawg said:**
> Well my partial bout of retardism is over with, Yes, I noticed I was actually running dapper, breezy, and edgy. I did a sources.list edit where i went through and changed all of the breezy and edgey to dapper, then did sudo aptitude update it messed up so i did a sudo aptitude clean, then update, then upgrade. My seriously hard hit retard factor was i was forgetting to actually install the dang codecs, lol. I had downloaded all dang day but forgot to place them.
So big retard on me guys I do apologize, but I'm only human.
 On the flip side I'm now offically through with Win-Hoes and Micro-Slop, as far as I'm concerned they can go hug a root. I'm trying to learn everything there is to know bout Linux/Unix. Next stop is the big money game of admin.

I seriously think you should reinstall Ubuntu Edgy Eft. And strat over again.
There could be hidden problems (broken sys) because you had a repos for Dapper, Breezy, and Edgy in your source.list
Always make sure that the repos are for the version of Ubuntu you are running. :)


Good luck to you!

If you have another problem, just create a new thread about it. :popcorn: :popcorn: 
We wil always try to help you. :KS 


Take care!!

Links for Ubuntu Guide, Trick, how-to's and basic Help:

[https://help.ubuntu.com/](https://help.ubuntu.com/)

[http://doc.gwos.org](http://doc.gwos.org)

[http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by mlitty on 2007-08-26
I tried to change the preferred format as you described, however, I can't see any form of mp3 in the preferred format dropdown menu, even though I have two separate entries for mp3s listed in the "edit" option and they are both "active".  The ony entries that I have ever seen in the "preferred format" choices are 
Lossless FLAC
Lossy Ogg
Lossless Wav
Lossy Unknown

It doesn't seem to matter what I mark as "active".

I'm running Ubuntu Feisty.

Oh, and I have gstreamer0.8-mad installed.  It created a mp3 entry in the edit menu, but not the preferred format menu.

---

### Post by mlitty on 2007-08-28
Never mind.  It turns out that this is a known and long-standing bug with Gnome.  See [THIS TREAD]("https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/84007").

---

