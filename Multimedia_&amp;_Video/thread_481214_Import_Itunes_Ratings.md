---
title: "Import Itunes Ratings"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by krugman on 2007-06-22
Hi to all:p

I have recently switched from windows to the penguin and I am quite happy about that.
However, I am now tackling the multimedia part of the switch, and I have some troubles importing ratings from my itunes library.

After some searches, I found one plugin in Amarok, but Amarok is a bit slow on Gnome. Moreover, it does not work for me. Then, seearching again, I found this:
[http://www.hicks-wright.net/blog/itunes-and-rhythmbox-ratings](http://www.hicks-wright.net/blog/itunes-and-rhythmbox-ratings)
which is a Pyhon script which allows you to transfer you ratings from you itunes database to your rhythmbox one. So far so good. However, since I am quite new to those Python scripts, I can't make it work!
After downloading the script, I tried a
```
sudo python transferRatings-0.8. py ~/data/iTunes/iTunes Music Library.xml
```

which does not do anything apart telling me this:

[HTML] Usage: transferRatings-0.8.py iTunesLibraryFile [RhythmboxLibraryFile]

transferRatings-0.8.py copies your iTunes ratings into your Rythmbox library.
To ensure nothing is lost, a backup of your Rhythmbox
Library will be made.  It is recommended that you quit
Rhythmbox before running this script.

Arguments:
  iTunesLibraryFile - This file is usually:
    {Music Folder}/iTunes/iTunes Music Library.xml

  RhythmboxLibraryFile [optional] - Usually found at:
    ~/.gnome2/rhythmbox/rhythmdb.xml
  If this argument is not specified, the default location
  will be used instead.
[/HTML]

Any ideas?

I know that a lot of people would like to import ratings from iTunes, so I guess this could also be useful for the community;)

---

### Post by krugman on 2007-06-22
No one?

Nobody ever encountered this problem???

:(

---

### Post by krugman on 2007-06-25
Still no one?

---

### Post by bartong on 2007-08-23
Hi there, i'm getting the EXACT same problem only with version 0.8.1

Did you ever resolve this?

---

### Post by tghw on 2007-08-27
Hey Guys,

Glad to see you found the script.  It seems the problem has to do with the spaces in "iTunes Music Library.xml".  Remember that in the console, filenames with spaces have to be escaped, so instead of inputting ```
python transferRatings-0.8.1.py /path/to/iTunes Music Library.xml
``` you should do ```
python transferRatings-0.8.1.py /path/to/iTunes\ Music\ Library.xml
```

I'll also add something to help detect and remind people about this.

As always, let me know if you find any more problems!

++Tyler

---

### Post by krugman on 2007-08-30
Thanks Tyler for the help.

But, it is still not working for me, I get the following error message after using the following code:
```

sudo python transferRatings-0.8.1.py ~/data/iTunes/iTunes\ Music\ Library.xml

```


```

Backing up Rhythmbox Library
Parsing iTunes
Could not parse iTunes file /home/fred/data/iTunes/iTunes Music Library.xml

```

I must be dumb I guess...
But I will keep trying. At least, I don't have the same problem as I used to.

EDIT: btw, could it be because that my itunes library is in a FAT32 partition, i.e. the one that I share between linux and windows?

---

### Post by naitram on 2007-08-31
I don't think the file system should have any effect on what's going on. 

Are you sure you're specifying the right location for the iTunes library?  Mine in my windows install lives in /Documents and Settings/david/My Documents/My Music/iTunes/iTunes Music Library.xml

and yours wouldn't be in your linux home directory unless you copied it there yourself.  Forgive me if this seems a bit of a silly question, but i noticed that when i mistyped the location, i got the "could not parse" error.  Could not parse in my case meant it couldn't find it at all.  Maybe the script could be updated to reflect this?  

And if you get it working, let me know.  The script runs successfully for me, but doesn't actually push any of the ratings into the new library.   And my knowledge of python (and my patience level currently) aren't sufficient for me to figure out what's going on *frustrated*

---

### Post by krugman on 2007-08-31
Yes, indeed, you are right: since I have a new laptop, I have changed the location of my iTunes library. So, I have tried:

sudo python transferRatings-0.8.1.py /media/sda6/iTunes/iTunes\ Music\ Library.xml


since it is located in another partition, i.e. sda6. However, I first get the message "parsing itunes", but then I got the same error message.

---

