---
title: "Sanitised filenames from Rhythmbox"
date: 2011-06-07
forum: Multimedia Software
---

### Post by javine on 2011-06-07
Hi,

Short version - can Rhythmbox be made to avoid characters like colon (:) and question marks (?) in filenames?

And an aside - what's the best way of bulk re-naming the names with colons etc. I already have?

---

I have been using Rhythmbox to rip my CDs onto my Ubuntu machine. I decided that I would like to copy them onto my NAS. This threw up a problem - a bunch of the files refused to copy across - some whole albums, some individual tracks. I eventually tracked it down to the presence of some characters like question marks and colons in the filenames, which I think the NAS refuses because they're not usable on Windows (possibly a FAT issue). This affects album names as well as individual tracks, because Rhythmbox uses that as the folder/directory name.

So, is there any way to tell Rhythmbox that I want it to use sanitised file and folder names when ripping my CDs?

---

And, that aside: I have already ripped quite a large number of CDs. Does anyone have a suggestion about the best way of bulk renaming these ready for me to copy across? I'm sure with a bit of Googling I can work out how to do a bulk rename on Linux, but I'd appreciate any tips (a) to make it easier, (b) to minimise problems with confusing my Rhythmbox library in the process (if that's an issue) and (c) any tips on what's a sensible thing to replace these character with - my thought was to strip out question marks and replace colons with dashes, but I'm open to suggestions.

Thanks in advance,
Javine

---

### Post by javine on 2011-06-11
Hi,

Further to my last message, I have been having a dig around the options on Rhythmbox and I've not been able to spot anything that might help - I'm happy to invoke it using text commands if it is there but not on the front end.

But I should also say I'm not wedded to Rhythmbox for my CD ripping - I'm very happy to use any other software that can rip to FLAC. I have quite simple requirements - I'd like it to grab CD data from the Internet so I don't have to type them all in, I'd like it to save the tracks with meaningful names into sensible folders (in Rhythmbox I use the folder hierarchy as "Artist/Album", and the file names as "number - title"), and, as you know, I'd like the option for characters that confuse Windows to be left out of file names.

Any pointers greatly appreciated.

Thanks,
Javine

---

### Post by nothingspecial on 2011-06-11
Hi,

There are lots of file naming utilities available with ubuntu.

I'd suggest having a look at rename. I'll give you an example. Supposing your music is in your Music directory and the structure is

Music/Artist/Album/song.flac

Then you could do something like this to change all the colons to dashes.
```

for f in Music/*/*/*.flac; do rename -n 's/:/-/g' "$f"; done
```

At the most basic level the rename command will replace what is between the first 2 slashes to what is between the next 2. In that case : to -

I'll show you with an album I happen to have on my netbook at the moment, changing any spaces for underscores.

```
~/Music/Hugh Laurie/Let Them Talk$ for f in *.mp3; do rename -n 's/ /_/g' "$f"; done
After You've Gone.mp3 renamed as After_You've_Gone.mp3
Baby, Please Make A Change.mp3 renamed as Baby,_Please_Make_A_Change.mp3
Battle Of Jericho.mp3 renamed as Battle_Of_Jericho.mp3
Buddy Bolden's Blues.mp3 renamed as Buddy_Bolden's_Blues.mp3
John Henry.mp3 renamed as John_Henry.mp3
Let Them Talk.mp3 renamed as Let_Them_Talk.mp3
Police Dog Blues.mp3 renamed as Police_Dog_Blues.mp3
Six Cold Feet.mp3 renamed as Six_Cold_Feet.mp3
St. James Infirmary.mp3 renamed as St._James_Infirmary.mp3
Swanee River.mp3 renamed as Swanee_River.mp3
The Whale Has Swallowed Me.mp3 renamed as The_Whale_Has_Swallowed_Me.mp3
They're Red Hot.mp3 renamed as They're_Red_Hot.mp3
Winin' Boy Blues.mp3 renamed as Winin'_Boy_Blues.mp3
You Don't Know My Mind.mp3 renamed as You_Don't_Know_My_Mind.mp3
```

The first bit of the command I showed you ---

--- for f in blah slashes and stars and general commandline gobbldygook ----

Will loop through all your flac files and do it it for every one.

The -n (after rename), means that the command will not actually run, it will just show you what would happen if you did run it.

If you are happy with the results, run it again without the -n

Bear in mind that the command I showed you will change anything found in the whole path, ie change any colons in the Album folder or Artist folder names to dashes also.

You should be able to modify it to your needs.

Cheers

---

### Post by javine on 2011-06-11
Hi nothingspecial - thanks for the tip. One of my concerns was about whether changing file / folder names might confuse Rhythmbox for my existing library. Of course, this was easy to test - I just changed one, re-opened Rhythmbox, and it quickly found it, no bother. So, I can simply do a bulk rename. This will sort 90% of my problem for me, so is really helpful, thanks.

In the longer run I had hoped to set the NAS as my default target for ripping, which I think would require my ripper to play ball with the characters the NAS is happy with, so if anyone has any ideas on that it would be helpful, but in the meantime, nothingspecial's suggestion certainly gets me on the way!

Thanks,
Javine

---

