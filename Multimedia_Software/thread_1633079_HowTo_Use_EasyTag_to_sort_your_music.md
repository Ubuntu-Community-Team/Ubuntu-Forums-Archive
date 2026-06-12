---
title: "HowTo: Use EasyTag to sort your music"
date: 2010-11-28
forum: Multimedia Software
---

### Post by slooksterpsv on 2010-11-28
Because it took me about 25 min. to figure out what I was doing wrong with trying to get EasyTag to sort my music, I decided to create a quick little HowTo.

**What is EasyTag?**
EasyTag is a program that searches through databases of music to help update tags and even sort your music. - In a nutshell, there's more to it than that.

**Getting EasyTag**
Go ahead and open up Software Manager and search for easytag.
If you're more used to Terminal, type this in: 
```

sudo apt-get install easytag

```

Once complete open it up from: Applications -> Sound & Video -> EasyTag.

Let's do this in steps, considering your music is already tagged correctly, but needs organized do the following:

1. On the left hand side, click on the area where your music is located at, if need be you can select one of your folders you need to update first, then we can repeat for each folder of separate music you have (if not all located in /home/<yourname>/Music)

2. In the column that says filename, click on the first file, then press the button that's a black box with blue lines going through it.

3. Now that all the files are selected click on Scanner -> Rename Files and Directory.

4. Now it'll give you the following in the text field: %n - %a - %t
That will name the file: number - album - title.
Click on the folder with the plus next to the textbox to make it change to: /home/<yourname>/Music/%n - %a - %t

**NOTE: <yourname> denotes where it would be your username, mine is shawn so it would say /home/shawn/Music/%n - %a - %t**

5. Let's change it, now personally I like my music assorted by:
Artist/Album/Track # - artist - track name.mp3
So I'm going to modify the line to this:
/home/<yourname>/Music/%a/%b/%n - %a - %t

Which for 3 doors down will make it: 
/home/<myname>/Music/3 Doors Down/Away from the Sun/02 - 3 Doors Down - Away from the Sun.mp3

Now you can modify and use different %, if you click on the talk bubble with the ? in it, it'll tell you what each % item does. So if you wanted the disk number to be included you could do: %d
Organize by Genre you could do:
/home/<yourname>/Music/%g/%a/%b/%n - %a - %t

Which would do this for 3 doors down again:
/home/<myname>/Music/**Rock**/3 Doors Down/Away from the Sun/02 - 3 Doors Down - Away from the Sun.mp3

6. After you've changed it the way you want it, click on the Green file, next to the drop down menu.

7. Click on File -> Save File(s) - this will take a while with a large library, it'll update the file names, as well as sort them how you want to sort it.

Instead of my music being:
/home/shawn/Music/Music/iTunes Music/Albums/<artist>
It's now:
/home/shawn/Music/<artist>/<album>/<filenames>

Maybe that's not so clear... let me know if I should update it in any way.

---

### Post by Enigmapond on 2010-11-28
Ain't EasyTag Great?! Thanks for this tutorial. I've been using this wonderful app for quite some time and find very, very useful. Now I hope others will as well!

Best Regards!

---

### Post by slooksterpsv on 2010-12-09
Thank you myself, I forgot how to use the program and had to restore from a backup cause I reformatted trying a different OS, haha, it's rearranging my music as I type.

---

### Post by cotsy on 2010-12-09
Was using it earlier great piece of software. It's one downfall though was a lack of 'album artist' tag.....or is there one that im missing?

---

### Post by xQB12 on 2010-12-09
Worked beautifully!

---

### Post by slooksterpsv on 2010-12-10
> **cotsy said:**
> Was using it earlier great piece of software. It's one downfall though was a lack of 'album artist' tag.....or is there one that im missing?

You can only select up to 99 files, then there's a database in there it can contact lemme see if I can find it... Misc -> CD Database

---

### Post by lewisskinner on 2011-02-01
agree.  Lack of "Album Artist" support is a big downer for me.

Since I go to a lot of promo shows etc, I have a lot of mixCDs and split EPs.  All I want is a program which can read and sort by album artist, but doesn't believe that all the artists are playing on a particular track.  eg.

Bright Eyes/Son, Ambulance Split EP:
Album artist: Bright Eyes/Son, Ambulance
Album Title: Bright Eyes/Son, Ambulance Split EP
track 1. Son, Ambulance - Brown park
2. Bright Eyes - Going for Gold
3. Son, Ambulance - The Invention of Beauty
4. Bright Eyes - Oh, You Are the Roots That Sleep Beneath My Feet and Hold the Earth in

etc

etc

This split is tagged perfectly in Windows Media Player, but in Rhythmbox  the even-numbered tracks tagged as artist 'Bright Eyes', and the odd-numbered tracks tagged as artist 'Ambulance LTD/Bright Eyes/Son/Son, Ambulance'.  Thus, if I search for music by Bright Eyes, I cannot play this whole album, and have to re-search by album title.  As one who listens to whole albums and not individual tracks (not a shuffler!) this is really infuriating.

It also appears horribly on last.fm/audioscrobbler

---

