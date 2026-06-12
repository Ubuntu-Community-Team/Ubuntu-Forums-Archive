---
title: "Alternative to m.i.r.o"
date: 2008-06-30
forum: Multimedia Software
---

### Post by fishtoprecords on 2008-06-30
I love the idea of miro, and when it works, its great. But its clearly a work in progress. Every third show or so, it closes the Miro window when I click play. Every ten or so, it blows away X-Windows completely.(Not the whole OS, just X).

Are there other programs that are similar to Miro, perhaps a bit more robust?

Thanks
Pat

I'm running 8.04.

---

### Post by ex.hav0k on 2008-07-05
well, i looked at miro and i seem to remember, atleast about a year ago when i used to use linux, there was a program that was very similar and worked amazingly.  it ran off bit-torrent, so you could add any show you wanted to off torrent sites.  i got a note from nbc/universal for having House on there, so i ended up uninstalling it because there was no way to install a safepeer/ipblocker.  but it was a great program.  i haven't used miro yet, but it looks like it might be the same thing.  if anyone can remember the name of the program im thinking of, it was big in 06 if anyone remembers.

---

### Post by Thelasko on 2008-07-07
> there was a program that was very similar and worked amazingly.
Do you mean Democracy?  Democracy became Miro a while back.

I find Miro buggy too.  My biggest complaint is that the config files are not compatible from version to version.

---

### Post by dohko_xar on 2008-07-15
Miro is so damn buggy... I click the play button and it crashes.. it's unusable.

Right now I'm trying to learn enough bash script to be able to pull my podcasts into a folder and then watch them with whatever media player.. Miro is so crappy.

---

### Post by Kevbert on 2008-07-15
You could try[ zattoo]("http://zattoo.com") if it works in your country.

---

### Post by markbuntu on 2008-07-15
Miro works great for me, no problems at all since I changed the video renderer option to gstreamer from xine. Before that it gave me a bunch of unpredictable problems up to and including system crash.

---

### Post by Thelasko on 2008-07-16
I started using Hulu.  All is good now.

---

### Post by darkazurka on 2008-08-21
I know miro is buggy, and it doesn't do everything I tell it to do, but it's open source and I won't depart from it if the alternative is closed source.

The above shows why I'm still using the Ubuntu flavor of Gnu/linux.

---

### Post by Alex Libman on 2009-11-26
I wrote a home-brewed little perl script I called "pod-get", which parsed RSS URL's specified in a conf file and used existing command-line software (i.e. curl, youtube-dl, or libtorrent-rasterbar) to download media. It then used oggconvert / ffmpeg2theora to convert files into free formats, and generated an HTML5 / AJAX interface for browsing / playing those files in a Web browser (via the new AUDIO / VIDEO tags), either locally or remotely through a Web server.

That was a part of my little "Anarcho-Capitalist OS" project to avoid evil GNU / copyleft software (restrictive licensing is based on government force!) in favor of public domain / permissively licensed client software like Chromium. What I have so far is very buggy and isn't worth publishing yet (any programmer competent enough to get it working could write a better script in just a few hours), but if I get any farther with it I'll share.  In the meantime, there seems to be an existing repository package called "podget" (no dash) that offers some of the similar functionality.

---

### Post by darkazurka on 2009-11-26
> **Alex Libman said:**
> 
That was a part of my little "Anarcho-Capitalist OS" project to avoid evil GNU / copyleft software (restrictive licensing is based on government force!)

No problem, as long as you give all four freedoms to the users of the software. You don't need to be a GNU supporter to write **f**ree **l**ibre and **o**pen **s**ource **s**oftware.

-----------

Also to Miro users: If you want the latest (YES! Latest!) Miro release , add a repository directly from the Miro website. Look here: [http://www.getmiro.com/download/for-ubuntu/](http://www.getmiro.com/download/for-ubuntu/)

A direct repository for Hardy Heron 8.04: deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) hardy/ (but please verify this!!!)

---

### Post by mobilediesel on 2009-11-26
> **dohko_xar said:**
> Miro is so damn buggy... I click the play button and it crashes.. it's unusable.

Right now I'm trying to learn enough bash script to be able to pull my podcasts into a folder and then watch them with whatever media player.. Miro is so crappy.

[Bashpodder]("http://lincgeek.org/bashpodder/") works well for that.

You can also try [tormon.py]("http://ubuntuforums.org/showpost.php?p=7949235&postcount=19") written by [unutbu]("http://ubuntuforums.org/member.php?u=518895") right here on our forums. It was made primarily for getting torrent files but unutbu added support for other file types.

They are only scripts meant to download the files, then you use whatever media player you like.

---

