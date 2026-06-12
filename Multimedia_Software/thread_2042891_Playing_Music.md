---
title: "Playing Music"
date: 2012-08-15
forum: Multimedia Software
---

### Post by cosmarchy on 2012-08-15
Hi, 
 
This is a bit of a first for me so I am not sure what to look for.
 
I need to be able to play a piece of music at predetermined times.  For example one piece at 1300, the second at 1400 and the third at 1500.
 
How do I best go about this?  Is there a player that will allow me to create a playlist and a time for the piece to play?
 
Thanks

---

### Post by cortman on 2012-08-15
> **cosmarchy said:**
> Hi, 
 
This is a bit of a first for me so I am not sure what to look for.
 
I need to be able to play a piece of music at predetermined times.  For example one piece at 1300, the second at 1400 and the third at 1500.
 
How do I best go about this?  Is there a player that will allow me to create a playlist and a time for the piece to play?
 
Thanks

You can make a [cron job]("http://www.google.com/search?q=how+to+use+cron") for each song. (there are a lot of resources out there about it). Use the command

```
xdg-open filename
```

To open it with the default music player, or just the name of the music player-

```
vlc file_name
```

---

