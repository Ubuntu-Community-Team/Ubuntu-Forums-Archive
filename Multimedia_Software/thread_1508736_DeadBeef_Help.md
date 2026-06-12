---
title: "DeadBeef Help"
date: 2010-06-13
forum: Multimedia Software
---

### Post by h8uthemost on 2010-06-13
I have finally found a native Linux music player that's as light and as simple as Foobar(unfortunately Foobar under Wine is giving me problems so I needed to find a native player). But I need a little help on creating custom columns for the player. And since I can't find any DeadBeef forums, I'm hoping people here are familiar with this player.

So, the two main custom columns I'm looking to create are Codec and Bitrate. Codec to show if the tracker is mp3, ogg, flac, etc. And Bitrate to show the bitrate of each track.

Now there's an option in DeadBeef to create columns, but I'm having trouble figuring out how to get the column to show the info that I want. I was hoping that the way you get [_custom columns_](http://wiki.hydrogenaudio.org/index.php?title=Foobar2000:Titleformat_Reference) to show up in Foobar would work in DeadBeef. But inputting %bitrate% and %codec% into the columns in DeadBeef does not work.

So would anyone happen to know how to get the two columns that I'm wanting to display the info that I want?

Any help will be greatly appreciated.

Thanks.

---

### Post by jampe on 2010-12-06
The only ones currently supported in the columns are:

%a = artist
%t = title
%b = album
%B = band
%C = composer
%n = track number
%N = total tracks
%l = length
&y = year
%g = genre
%c = comment
%r = copyright
%f = filename
%F = full path name
%T = tags
%d = directory
%D = directory with path

---

### Post by Baloeb on 2011-05-20
I'm going to bring this back from the dead.  Is there a way to make a disc number column?  When my box sets show up all the track numbers are grouped together.  1, 1, 1, 2, 2, 2 etc.

---

### Post by Baloeb on 2011-05-25
If anyone is interested.  You can make a column for whatever metadata you want.  %@ALBUM@ for example.  My disc column is %@Disc@.

---

### Post by 3D-TiMi on 2011-05-26
How to change the skin in deadbeef to [THIS]("http://deadbeef.sourceforge.net/screenshots/0.4/deadbeef-openbox-aurora-midnight-orange.png")?

---

