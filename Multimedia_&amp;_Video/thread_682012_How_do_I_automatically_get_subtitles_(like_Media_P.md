---
title: "How do I automatically get subtitles (like Media Player Classic)?"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by bornagainpenguin on 2008-01-29
Like many people migrating away from Windows, I'm a big fan of Media Player Classic (not the Microsoft one, the work-alike) often included in codec packs allowing for it to play nearly any and every video format.  I've since moved over to Ubuntu and am happy with it for the most part, just trying to fill in any missing pieces along the way...  One thing I find myself missing is the ability to have Media Player Classic suggest a subtitle from OpenSubtitles.org to go along with the video playing.

I used [these](http://blog.opensubtitles.org/opensubtitlesorg/downloading-subtitles-using-mpc) instructions for Media Player Classic, and have generally had good results.  I especially like the ability to save the subtitle because doing it this way allowed me to find the needed subtitles much more quickly than having to hunt and search around the web for working subtitles to go with my videos and save the working ones for later viewing.  Does anyone know how to do this in Ubuntu using the default Totem player?  Or with VLC?

--bornagainpenguin

---

### Post by wolfen69 on 2008-01-29
To enable them(in VLC), go to the Video menu, and to Subtitles track. All available subtitles tracks will be listed. Select one to get the subtitles. Depending on the media, a description (language, for example) might be available for the track.

[http://www.videolan.org/doc/play-howto/en/ch03.html#id290015](http://www.videolan.org/doc/play-howto/en/ch03.html#id290015)

---

### Post by bornagainpenguin on 2008-01-29
> **wolfen69 said:**
> To enable them(in VLC), go to the Video menu, and to Subtitles track. All available subtitles tracks will be listed. Select one to get the subtitles. Depending on the media, a description (language, for example) might be available for the track.

[http://www.videolan.org/doc/play-howto/en/ch03.html#id290015](http://www.videolan.org/doc/play-howto/en/ch03.html#id290015)

This will automatically **download** a list of subtitles from the internet for me to choose from?  I think you may have misunderstood my question.  I know how to display already existing subtitles, I'm looking for a way to retrieve new ones from the internet without needing a web browser....

--bornagainpenguin

---

### Post by bornagainpenguin on 2008-01-29
/BUMP foranswers by someone who reads the post....

--bornagainpenguin

---

### Post by bornagainpenguin on 2008-01-30
/BUMP for someone with answers (who has also read the posts)

---

### Post by bornagainpenguin on 2008-01-31
/Daily Bump

---

### Post by Major_Kong on 2008-01-31
> **bornagainpenguin said:**
> This will automatically **download** a list of subtitles from the internet for me to choose from?  I think you may have misunderstood my question.  I know how to display already existing subtitles, I'm looking for a way to retrieve new ones from the internet without needing a web browser....

--bornagainpenguin

I'm not sure you can do that...

---

### Post by bornagainpenguin on 2008-02-03
> **Major_Kong said:**
> I'm not sure you can do that...

That sucks.  It's one of the better features in MPC...  Anyone know if its possible to request features like this and where I'd have to go to do so?

--bornagainpenguin

---

### Post by JGJones on 2008-02-05
I didn't know you could automatically download subtitles in MPC via OpenSubtitles.org. That's a great idea. I wonder if Totem use plugin's? I wouldn't mind such a plugin like this for that (I'm profoundly deaf so need subtitles).

Currently what I do is to use OpenSubtitles.org to download the files, name it the same as the file that is playing to have it show up in Totem/VLC/Mplayer. It's not autodownload like MPC does - but you still get the subtitles (as they are all in SubRip format, which Totem/MPlayer/VLC can read)

Automagically download subtitles on request is a nice touch though - where do I put in a feature request for that in Totem then...?

---

### Post by JGJones on 2008-02-05
I was looking at MPC and the OpenSubtitles connection and I came across this Nautilus script where you can right click on a movie file and from that can download subtitles:

[http://www.gnome-look.org/content/show.php/download_opensubtitle?content=68085](http://www.gnome-look.org/content/show.php/download_opensubtitle?content=68085)

There is a similar one for KDE too - this link show a short list of software/script that make use of OpenSubtitles:

[http://trac.opensubtitles.org/projects/opensubtitles/](http://trac.opensubtitles.org/projects/opensubtitles/)

Hope that's of help - it's not quite directly in a media player like MPC, but it should simplify things a lot for you.

---

### Post by bornagainpenguin on 2008-02-11
> **JGJones said:**
> I didn't know you could automatically download subtitles in MPC via OpenSubtitles.org. That's a great idea. I wonder if Totem use plugin's? I wouldn't mind such a plugin like this for that (I'm profoundly deaf so need subtitles).

Currently what I do is to use OpenSubtitles.org to download the files, name it the same as the file that is playing to have it show up in Totem/VLC/Mplayer. It's not autodownload like MPC does - but you still get the subtitles (as they are all in SubRip format, which Totem/MPlayer/VLC can read)

Automagically download subtitles on request is a nice touch though - where do I put in a feature request for that in Totem then...?

I'm hard of hearing myself, so that's why I started looking into this type of thing.  It also helps when I'm watching unlicensed anime and want the subtitles in English.  So yeah I know what you mean and a plugin like this would definitely be appreciated!

Really, IMHO we need more plugins for apps like Totem and Rhythmbox.  That's one of the things I tend to miss from the Windows\MacOS world--they usually seem to have more plugins extending the functionality of their applications than we do in Linux.  At least as far as I'm concerned as a non-programmer.  I know its easier to script things in Linux and to use pipes (IIRC) to move data around until you get it where you want it, but that's only useful if you know how to script....

> **JGJones said:**
> I was looking at MPC and the OpenSubtitles connection and I came across this Nautilus script where you can right click on a movie file and from that can download subtitles:

[http://www.gnome-look.org/content/show.php/download_opensubtitle?content=68085](http://www.gnome-look.org/content/show.php/download_opensubtitle?content=68085)

There is a similar one for KDE too - this link show a short list of software/script that make use of OpenSubtitles:

[http://trac.opensubtitles.org/projects/opensubtitles/](http://trac.opensubtitles.org/projects/opensubtitles/)

Hope that's of help - it's not quite directly in a media player like MPC, but it should simplify things a lot for you.

Oh wow man!  This is a great discovery!!! I'll give it a shot as soon as I finish up what I'm doing in XP and go back to Linux!!!

Thanks!

--bornagainpenguin

---

