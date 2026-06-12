---
title: "Mysterious DVD problems"
date: 2011-02-10
forum: Multimedia Software
---

### Post by HIPS on 2011-02-10
This problem came to light when I thought about ripping down some of the family's DVD movies to our media player. Some works perfectly, while some refuses to be ripped. I've tried DVD:: rip, K9Copy, OGMRip and Acidrip. The problem feels really strange. When I run for instance OGMRip and the program begins with backing up the DVD. This backup comes to about half the movie, then it stops. K9Copy crashes instead.

I then started to experiment and play these movies on the computer (via Totem) and skip forward chapter by chapter – or as the last test, just let them play. The same phenomenon occurs - up to about half the movie it's perfectly fine, then everything freezes, and I get this message “An Error occurred – Could not read from resource” 

Hope someone has some good ideas.  To my knowledge, I have installed all that is needed (like libdvdread4 and libdvdcss2, and also  Medibuntu). I have also tried VLC, but it also refuses to play more than half the movie.  
 

 Could it be a region settings problem? As far as I know my DVD player has no region.

---

### Post by robert shearer on 2011-02-10
you mention "half' several times.
Does your dvd drive read dual layer discs ?

I do have a few discs that halt when attempting to access the second layer.

This is so occasional that I blame the disc.
Were it happening every time I would investigate the player.

---

### Post by HIPS on 2011-02-11
[SIZE=3][FONT=Times New Roman]Hmm, I must admit that I took dual layer readability for granted (it is a HP Pavillion about two years old). I must check this out.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]During this time I have never stumbled upon a movie that wont play – until now. Still some of my movies both plays perfectly and are easy to rip and convert, while others just refuse to cooperate.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman]Of course it could be some kind of hardware failure. I’ll try to borrow an external DVD drive to see if there is a difference.[/FONT]

---

### Post by robert shearer on 2011-02-11
> **HIPS said:**
> [SIZE=3][FONT=Times New Roman]Hmm, I must admit that I took dual layer readability for granted (it is a HP Pavillion about two years old). 

Only two years, bound to be dual layer...unless it's a lappy..?

In a terminal run 
```
sudo lshw
```
(that's  lower case LSHW) to list your hardware and past back here inside code tags (just highlight the text then click on the # symbol at the top of the forum reply window you are in)

---

### Post by HIPS on 2011-02-11
Ok, here is what came out of that (only the part concerning the DVD player:

```
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-H653Q
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0303
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
```I don't understand all of it, but now I can tell for sure that something is not right with my player. I just borrowed an external player, and my test movie runs fine. I will try some more with the external drive, but it looks like the built in one is the source of my problems.

---

### Post by HIPS on 2011-02-12
I have done some more testing, and it seems clear that the problem was caused by bad hardware. I guess it was just bad luck that the player broke down on me just when I was supposed to backup our movies.

Thanks a lot robert shearer for bringing the hardware issue to my notice. I was so convinced it must have to do with a codec or some other software issue, that I didn't even consider hardware problems.

---

