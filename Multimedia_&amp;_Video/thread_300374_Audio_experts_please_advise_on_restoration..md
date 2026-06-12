---
title: "Audio experts please advise on restoration."
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by PapaWiskas on 2006-11-15
I am an avid collector of old time radio episodes.  And I was thinking that some of them I would really like to try and restore or enhance them.  Is there a gui program that would allow me to filter or edit audio files, native to linux?

Thanks.

---

### Post by OffHand on 2006-11-16
> **PapaWiskas said:**
> I am an avid collector of old time radio episodes.  And I was thinking that some of them I would really like to try and restore or enhance them.  Is there a gui program that would allow me to filter or edit audio files, native to linux?

Thanks.
Audacity

[http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)

It is also available from the repositories.

---

### Post by damu on 2006-11-17
There are many plug-ins that you can use from audacity to clean/ enhance an audio file.

There is also [Gnome Wave Cleaner]("http://gwc.sourceforge.net/"), which should be in the add/remove section of Ubuntu, and which is more focus on cleaning audio files.

I don't know what is your original source format and what you aim to have as an end result format (wav, ogg, mp3...), but I would suggest to transfer the original files in wav with audacity. I kind of remember that GWC doesn't accept wav in 32 bit, so I would suggest to work in wav 16 bit in this case.

Then, you can open/import the wav file in GWC to clean it. It needs a bit of tweaking to find the optimal settings to clean the files with an optimum end result (the help of GWC is really a good way to start...).

For the last (optional)step you will need jack, jamin, audacity and rezound( all accessible from the add/remove program or synaptic).
Launch jack, and the 3 other apps.  
Open the cleaned file with Audacity. In Jamin , select Audacity from the in (left and right) and rezound for the output.
Put Rezound in record mod.
Start to play the file in Audacity. You can now hear it while processed through Jamin.
Change the settings of compression, EQ, etc in Jamin till you're happy with the end result.
Record this end result in rezound. You can now export it from Rezound in wav, ogg, mp3, etc.

Have fun!

---

