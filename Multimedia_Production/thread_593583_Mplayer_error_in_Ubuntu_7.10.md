---
title: "Mplayer error in Ubuntu 7.10"
date: 2007-10-27
forum: Multimedia Production
---

### Post by Gentoo bob on 2007-10-27
I installed Mplayer the other day and everything works great except when I go to view a downloaded .wmv file.  If I view the .wmv from within a webpage its fine.  When I download and go to view it, I get the following error...

"Cannot find codec matching select -vo and video format 0x33564D57."

I have tried editing my ~/.mplayer/config file with different "vo" types and doesnt seem to work.  

On a side note, this is the first time I've used Ubuntu...very amazing on what they have done.  Very feature rich!  My command-line use is very minimal compared to other distros.  Very nice to just install and go!

---

### Post by Gentoo bob on 2007-10-29
That's okay people I got it fixed anyways.  I love the new Ubuntu distro but I'm not a liking the forums.  This forum has been setting for 2 days unanswered and not one person offered one little bit of info.  I post on my Gentoo forums and my Fedora forums and bam! i had a response in like 30 minutes.  kind of crazy huh?  No worries though I got it fixed.  I guess if a Ubuntu needs the solutions they will have to search the Gentoo & Fedora forums for the answer.  have a good day.

---

### Post by eye208 on 2007-10-30
> **Gentoo bob said:**
> I post on my Gentoo forums and my Fedora forums and bam! i had a response in like 30 minutes.
I saw your post on the Gentoo forum. The suggested solution was:
> USE="win32codecs wmp" emerge mplayer
If that helped you, then it was a Gentoo-specific problem to begin with. Ubuntu's current version of MPlayer comes with native VC-1/WMV3 (Windows Media 9) support, no w32codecs required.

---

### Post by Gentoo bob on 2007-10-30
Very good cowboy.  No one would respond to my add so I created a response and you took the time to go hunt down my resolution.  No you won't find the resolution on any of those post, just a little pissy no one even offered to help in 3 days, but someone will offer to defy you.  Good job you won!

---

### Post by dodgydavec on 2007-10-30
I must admit, i find the same thing. I very rarely get responses to my posts. But it's not just here. It's other large communities too. The bigger they get, the more distant they seem to become :(

---

### Post by andrew.46 on 2007-10-30
Hi,

 Saw your frustration:

> **Gentoo bob said:**
> Very good cowboy.  No one would respond to my add so I created a response and you took the time to go hunt down my resolution.  No you won't find the resolution on any of those post, just a little pissy no one even offered to help in 3 days, but someone will offer to defy you.  Good job you won!

 Ubuntu is possibly getting too big too fast perhaps. Can I belatedly offer you the idea of using the svn mplayer rather than the repository version? I have written a walkthrough for this in these forums that should get around many odd issues as well as offering better overall performance:

[[Howto] Successfully install the svn mplayer + gmplayer + all the codecs.]("http://ubuntuforums.org/showthread.php?t=558538&highlight=mplayer+codecs+svn")

Hope this is useful to you?

           Andrew

---

