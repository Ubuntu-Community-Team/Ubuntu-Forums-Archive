---
title: "where are my rhythmbox playlists?"
date: 2009-04-21
forum: Multimedia Software
---

### Post by sonaural on 2009-04-21
trying to find my rhythmbox playlists.  what format or folder are they in?  i've searched the names and can't seem to locate any files.

trying to salvage them off a hard drive from a computer that just died (not due to hard drive problems)


thanks a million

---

### Post by Anthon on 2009-04-21
find ~ | fgrep rhythm | fgrep playlist

---

### Post by sonaural on 2009-04-21
sorry, i always forget to mention that i need to be spoken to like i'm a 2 year old when it comes to this stuff... what does that mean exactly?

---

### Post by Anthon on 2009-04-21
It means you open up a terminal ( Menu: Applications -> Accessories -> Terminal) and there copy and paste the commandline:
  find ~ | fgrep rhythm | fgrep playlist
that searches through the files in your home directory and below and finds anything that has both rhythm and playlist in the complete path as listed by find.
On my machine it finds 
  /home/anthon/.gnome2/rhythmbox/playlists.xml
Which AFAIK is the file you would be looking for if you were me on my machine ;-)
Look in the file (with some texteditor to see if your playlist are recognisable)

---

### Post by John Jason Jordan on 2009-12-03
> **Anthon said:**
> It means you open up a terminal ( Menu: Applications -> Accessories -> Terminal) and there copy and paste the commandline:
  find ~ | fgrep rhythm | fgrep playlist
that searches through the files in your home directory and below and finds anything that has both rhythm and playlist in the complete path as listed by find.
On my machine it finds 
  /home/anthon/.gnome2/rhythmbox/playlists.xml
Which AFAIK is the file you would be looking for if you were me on my machine ;-)
Look in the file (with some texteditor to see if your playlist are recognisable)

Apparently the original poster gave up. 

I just tried this and the ~/.gnome2/rhythmbox/playlists.xml does not contain my playlists. 

I am trying to copy the Rhythmbox playlists from my desktop computer to my laptop. I copied the entire ~/.gnome2/rhythmbox/ folder from the desktop computer to the same folder on the laptop, but rhythmbox on the laptop still does not see the playlist.

I bet it's in a configuration file somewhere, but no one seems to know what it's called or where it's located.

---

### Post by Anthon on 2009-12-04
have you ran the original find command I suggested? On my machine (now running 9.04) it shows:
/home/anthon-athlon64/.local/share/rhythmbox/playlists.xml
you might also need the other file in that directory

---

### Post by jcarroll on 2009-12-24
Thank you for the quick and concise answer.  It helped me solve my problem.

FYI, From within Rhythmbox, You can right-click on a playlist and save it to a file, either in .m3u or .pls formats.

Cheers,
James

---

### Post by DouglasAWh on 2010-07-23
I think some people might be getting tripped up because rhythmbox cannot be open on either machine during the transfer.  I am migrating from Fedora to Ubuntu and the playlist file was in the specified folder on both OSes.

---

### Post by Emilie on 2011-10-14
The fgrep command given above is the best way to go about it.  FYI, on my machine they are located in "~/.local/share/rhythmbox/playlists.xml".

---

