---
title: "Looking for a script/progam to rename tags for Ipod Use"
date: 2008-10-01
forum: Multimedia Software
---

### Post by Kristian9K on 2008-10-01
Hi all,
I'm about to buy an iPod Classic, and of course I want my mp3s on it. I have been trying a bunch of programs for bot Win and Linux, but none of them seem to be able to perform the trick I want them to.

Here's how my music is organized:
/Music/Artist/Album/01 - First Song.mp3

I want to copy the above information into the tag like this:
/Artist/ -> Artist tag
/Album/  -> Album tag
/01 - First Song.mp3 -> Song name tag

... and I would like this done with ALL 20 gigs of music. 

Can anybody point me towards something useful?

- Kristian

---

### Post by kpkeerthi on 2008-10-01
exfalso can do what you want. To install, run this command:
```
sudo apt-get install exfalso
```

---

### Post by dfreer on 2008-10-01
> **Kristian9K said:**
> Hi all,
I'm about to buy an iPod Classic, and of course I want my mp3s on it. I have been trying a bunch of programs for bot Win and Linux, but none of them seem to be able to perform the trick I want them to.

Here's how my music is organized:
/Music/Artist/Album/01 - First Song.mp3

I want to copy the above information into the tag like this:
/Artist/ -> Artist tag
/Album/  -> Album tag
/01 - First Song.mp3 -> Song name tag

... and I would like this done with ALL 20 gigs of music. 

Can anybody point me towards something useful?

- Kristian

MP3tag for windows and easytag for windows/linux. For all 20 gigs of music, I'd recommend using mp3tag, don't have any particular reason why, it just "seemed" to handle the job of re-tagging my music better.

Open MP3Tag. Go to "File" -> "Change Directory..." and select one specific artist/album directory. Select all the tracks in that album in the right pane (you can use <Ctrl>+<a> select them all). Go to "Convert" -> "Filename - Tag", and then select the pattern:
```

%artist%\%album%\%track% - %title%

```
It should show the ID3 fields it's going to fill in **bold** in that same window if it thinks the pattern is valid. You can always click the preview button. Click ok/apply whatever.

If that works, go to your main music directory and do all your songs that way. Don't plan on using the computer for awhile.

---

