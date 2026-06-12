---
title: "after saving mp3s in EasyTag id3v2 lists only v1 information"
date: 2013-03-03
forum: Multimedia Software
---

### Post by npr77 on 2013-03-03
Hi there,

I just encountered a strange problem. I wrote a little script that creates playlist based on the genre of an mp3 file. It worked fine on some test files, but when I unleashed it on my real mp3 library it did not work. Basically the id3v2 command list option output suddenly changed, so my regex did not work any more.

Anyway, here is the "normal" "correct" output of id3v2:
```

user@host:~/test/Clutch$ id3v2 -l 02.mp3 
id3v1 tag info for /home/user/test/Clutch/02.mp3:
Title  : Goat Warfare                    Artist: Clutch                        
Album  : Blast Tyrant                    Year: 2004, Genre: Hard Rock (79)
Comment:                                 Track: 11
id3v2 tag info for /home/user/test/Clutch/02.mp3:
TIT2 (Title/songname/content description): Goat Warfare
TRCK (Track number/Position in set): 11
TYER (Year): 2004
TCON (Content type): Hard Rock (79)
TALB (Album/Movie/Show title): Blast Tyrant
PRIV (Private frame):  (unimplemented)
PRIV (Private frame):  (unimplemented)
TPE1 (Lead performer(s)/Soloist(s)): Clutch
```

As soon as I save the file with EasyTag the id3v2 command does not print the v2 information any more ("No ID3v2 tag"). Thus my regex looking for the genre nice name in the TCON field does not work any more (in this example I could use the v1 information, but I have a few genres that are listed as 'Unknown (255)' in v1 :-({|=).

```

user@host:~/test/Clutch$ id3v2 -l 02.mp3 
id3v1 tag info for /home/user/test/Clutch/02.mp3:
Title  : Goat Warfare                    Artist: Clutch                        
Album  : Blast Tyrant                    Year: 2004, Genre: Hard Rock (79)
Comment:                                 Track: 11
/home/user/test/Clutch/02.mp3: No ID3v2 tag
```

I use defaults in EasyTag, and double checked that I in fact WRITE v2 information. If I open that file in EasyTag again I can see the v2 information again, so it's there, apparently. Only id3v2 is not able to read it.

Anyone else encountered this problem? Is id3v2 still the right tool for command line tag extraction?

Nick

---

### Post by npr77 on 2013-03-03
After saving files in EasyTag the id3v2 version is set to 2.4 - my old files have 2.3 - maybe id3v2 cannot handle v2.4 tags? Still investigating ... yes, after setting the id3v2 version to 2.3 in EasyTag the extraction works again. Still, it's not kewl that the id3v2 command apparently cannot handle v2.4. Now I will a. have to understand the differences of 2.3 and 2.4 and b. decide whether I will let EasyTag retag all my files to 2.3 - bummer :x

---

### Post by npr77 on 2013-03-03
Just wanted to mark this thread [Solved], yet I do not have that option in the "Thread Tools" menu. Only "Show Printable Version, Email this Page&#8230; and Subscribe to this Thread&#8230;" - so please feel free to mark this [Solved] if you are an Admin or something :)

---

