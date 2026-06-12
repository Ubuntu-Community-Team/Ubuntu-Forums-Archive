---
title: "can't watch video files"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by teetee on 2007-05-06
When I try to play a movie/video clip X restarts (black screen comes and I am threw to sign in window).

I tried earlier to get WMV-files to work (in AMD64) and that most likely made my problem. I have also tried to get tv-out to work with my ati x550, but I don't think it is the problem here. (I might be wrong...)

Few days ago I managed to make videos work, but now again them aren't working. That time I reinstalled some stuff, but cannot remember what (players at least, maybe codecs also). I tried again to reinstall some stuff, didn't work.

I have Feisty, but this problem occurred already before upgrading to it.

Is there any way to change graphic settings back to original ones (which comes on first install).

I am sure that you would like to have some more information, but what?

Thanks for your time.

---

### Post by nsleiman on 2007-05-06
do you have the w32codecs installed ? 
if not take a look at:
[Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by teetee on 2007-05-06
I have w64codecs installed and earlier I had w32codecs.

---

### Post by Ambimom on 2007-05-06
[http://getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt](http://getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt)


This will do it!  After you follow these instructions, open automatix and install the media codecs.

Everything should work after that.

---

### Post by teetee on 2007-05-07
Didn't work... :( 

Where is stated what codecs are used (where is a file where used codecs are stated)? Or are those updated during (re)install?

---

### Post by MichaelSM on 2007-05-07
Get VLC Media Player. Works like a wet dream. Mike.

---

### Post by teetee on 2007-05-07
I reconfigured xserver (with this command:" sudo dpkg-reconfigure xserver-xorg ") and now videos started to work again. Well, that is nice.

I restart my computer and see if them are still working.

---

### Post by hellblade on 2007-05-07
seems like a driver issue. make sure you use the right driver for your VGA card.

---

### Post by teetee on 2007-05-07
I should have correct drivers. Display driver have been working fine before, but then I tried to make WMV:s and tv-out to work (it is my next problem, get tv-out to work with amd64 ati x550), and then problems started. But now them seems to be working ok.

Maybe during those operations I have change xserver (or some) settings and them made videos not to play.

Thanks to everybody involved.

---

### Post by MichaelSM on 2007-05-07
I don't know much about any of this but I gave up trying to download and configure codecs for MPlayer, Xine, you name them. Waste of effort. VLC 4 me. It's in Synaptic, and it works. Mike. PS. As long as you've enabled all the suppositories (repositories) System>Admin>Software Sources. Give them all a tick. It won't kill ya. Mike.

---

