---
title: "Several Final Steps, Help Needed"
date: 2011-07-17
forum: Mythbuntu
---

### Post by jlacroix on 2011-07-17
Hello everyone, I am working on setting up my Mac Mini as a Mythbuntu machine, primarily for games. I have it mostly set up now, including Mythmote (Android application) for the remote.

Here are the final things I need help with:

1.) I hope I can shut down the box from Mythmote, without needing a keyboard

2.) I also would like to be able to exit the games from Mythmote (i.e. killall zsnes mednafen)

3.) In the menu there is an option for "Watch Recordings." I will never use this. How do I get it off the menu?

4.) I would also like to be able to have it stream media from my mediatomb service from another PC, since the hard drive isn't big enough to hold all my videos. Is this possible?

I appreciate all help with this, I was able to get most of it done but now I'm frustrated with the rest.

---

### Post by itlarson on 2011-07-19
You could use NFS or samba to point "watch recordings" at the directory on the other computer where they are stored.

---

### Post by jlacroix on 2011-07-19
> **itlarson said:**
> You could use NFS or samba to point "watch recordings" at the directory on the other computer where they are stored.
That sounds like a very clever idea. How do I go about doing that? The path to the videos on my other PC is this:

/home/jlacroix/Videos/Movies

And all of my shares are with Samba. Thanks!

---

### Post by itlarson on 2011-07-20
Sorry, I've never set up samba, only NFS, and that's been a while.  But I can explain the general concept-  you mount the directory on the windows computer to the file structure on your mythtv computer with samba, then set this directory as the source for "watch videos" in mythfrontend settings.  You will need to scan for new videos in the context meneu- 'm' on the keyboard.  Maybee [this]("https://help.ubuntu.com/community/Samba") will help with samba setup.

---

### Post by thatguruguy on 2011-07-20
If you're never going to use the computer to actually record anything, you may consider putting xbmc on it instead of mythtv.  It would be considerably easier to set up.

---

