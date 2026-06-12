---
title: "Playing a CD in Rhythmbox (without ripping)"
date: 2013-01-11
forum: Multimedia Software
---

### Post by chiron80 on 2013-01-11
This is going to sound like a ridiculous question, and I can't believe I'm asking it, but I've already spent far longer than should be necessary to find the answer to this question, and nothing is popping up.

I can't figure out how to play music directly off a CD in Rhythmbox, without ripping it to the computer first.

I'm running Ubuntu 12.04. I had Rhythmbox open and playing music. I have only one album actually stored on my computer, so it reached the end of this album vey quickly and looped around back to the first track. So I put a CD into the drive. The CD shows up in Rhythmbox. Under "Devices" it is showing the title of the Album. On the right it is showing the tile of each track. However, it continues to show the title of the song from the "Music" folder at the top of the window, and continues to play this song. If I double click the song on the CD, it just gives me the opportunitity to rename the track. If I hit pause, it stops playing, but play just resumes the same song from my "Music" folder. Right-clicking the track does nothing. If I right click on the name of the CD (below "Devices"), I can Extract to Library, Duplicate Audio CD, or Eject. The only options I can see are to "Extract", "Eject", "Reload", or "Copy CD".

It must be possible to play a CD directly from the CD, right? Am I going crazy?

The Rythmbox manual suggests it is trivial:
[http://library.gnome.org/users/rhythmbox/stable/AudioCD.html.en](http://library.gnome.org/users/rhythmbox/stable/AudioCD.html.en)
"To play and pause playback, or to skip forward or backwards, use the same controls as used for playing from the library." However, those controls simply stop and restart the song in my existing library.

I know I can just import the CD to my library, but is that really required to play a CD in Rhythmbox? Hypothetically, lets say this wasn't my machine, and I just wanted to play the CD, not dump music files onto someone else's hard drive.

OK, enough ranting, I'll just import the CD and be done with it. But I'm still really curious to know why I can't find the "Play CD" option.

- Ben

---

### Post by chiron80 on 2013-01-11
So, I went into the Rhythmbox preferences to make sure the ripping would be done as MP3, not Ogg, and to adjust the bitrate. Apparently, the "Settings" button doesn't work (known bug), and all the "solutions" involve editing configuration files somewhere. Really? I quit Rhythmbox and fired up Banshee.

Everything is working fine with Banshee, and you can even adjust the bitrate when importing the CD, from a GUI. In other words, it is doing what I expected pretty much any music playing application would do.

Guess I don't need an answer regarding Rhythmbox anymore, but in case someone stumbles upon this thread in the future, if someone knows the answer, feel free to share.

---

### Post by Nevetsjc on 2013-01-12
You should be able to just double click on a song when the CD opens in Rhythmbox (and shows the track listing).
Maybe try reinstalling?

---

### Post by chiron80 on 2013-01-12
> **Nevetsjc said:**
> You should be able to just double click on a song when the CD opens in Rhythmbox (and shows the track listing).
Maybe try reinstalling?

I'll give it a shot on my laptop (running 12.10) tomorrow. Perhaps something is configured wrong on my desktop.

---

### Post by chiron80 on 2013-01-13
> **Nevetsjc said:**
> You should be able to just double click on a song when the CD opens in Rhythmbox (and shows the track listing).
Maybe try reinstalling?

Turns out you need to double-click within the column under the speaker icon (which was the very first, narrow, column for me). Double-clicking anywhere else let you edit that field (e.g. double-clicking the title of the song let yo edit the title).

---

