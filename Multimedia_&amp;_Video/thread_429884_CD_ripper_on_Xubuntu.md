---
title: "CD ripper on Xubuntu"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by dangerousnerd on 2007-05-01
Hello!  I'm looking for a good cd ripper for xubuntu 7.04.  I tried xripper, but frankly it sucks.  Can anyone recommend one that doesn't depend on Gnome to work?  Thanks in advance!

--
The Dangerous Nerd

---

### Post by corevette on 2007-05-01
well, you could always try K3B

it doesn't really require gnome, but it's not based on xfce.....
but, hey it's my fave 
[http://k3b.plainblack.com/](http://k3b.plainblack.com/)

---

### Post by kerry_s on 2007-05-01
try graveman

---

### Post by dangerousnerd on 2007-05-01
Thanks for the reply corevette!  I believe that K3b is based on KDE though.  My goal here is to install one that is native to XFCE. ;-)  Do you have any other suggestions?  Thank you!

---

### Post by dangerousnerd on 2007-05-01
I suddenly realize there is some confusion with my question.  I would like to [rip]("http://en.wiktionary.org/wiki/rip#Verb") cd's to my computer; meaning I would like to stick in an audio cd and get ogg's at the other end.  I think people are thinking I meant [burn]("http://en.wiktionary.org/wiki/burn#Verb").  But thanks for your help!!!  :) 

So, anyone with ideas for ripping cds?  Thank you!

---

### Post by ckaya on 2007-05-01
+1 for graveman. xcdroast is an alternative as well.

OOPS... Hadn't seen your last post.

---

### Post by stchman on 2007-05-01
> **dangerousnerd said:**
> Thanks for the reply corevette!  I believe that K3b is based on KDE though.  My goal here is to install one that is native to XFCE. ;-)  Do you have any other suggestions?  Thank you!

K3B is a CD burning program not a CD ripping program.  I recommend you install Sound Juicer.  It will work on XFCE.

---

### Post by dangerousnerd on 2007-05-01
> **stchman said:**
> K3B is a CD burning program not a CD ripping program.  I recommend you install Sound Juicer.  It will work on XFCE.

Will do!  Thanks!

---

### Post by stchman on 2007-05-01
> **dangerousnerd said:**
> Will do!  Thanks!

Both KDE and Gnome apps will work on XFCE.  Go to the Add/Remove or Synaptic and you can install them there.

I use a few KDE apps like K3B, K9Copy, and Ktorrent.  They all work very well under Gnome.  I use K3B on a PC I installed Xubuntu to.

---

### Post by dangerousnerd on 2007-05-01
> **stchman said:**
> Both KDE and Gnome apps will work on XFCE.  Go to the Add/Remove or Synaptic and you can install them there.

I use a few KDE apps like K3B, K9Copy, and Ktorrent.  They all work very well under Gnome.  I use K3B on a PC I installed Xubuntu to.

My goal, though, is to not install gnome or kde (which is a dependency for most KDE and Gnome software).  The computer that I am running this on can not run the dependencies without a major performance hit.  That is why i check the dependencies of the packages very carefully after I click them in Synaptic.  Thanks though!

---

### Post by tmatt95 on 2007-05-01
I use Ripperx to create .mp3, which are compatable with my MP3 player. The interface is not as uniform as some but it seems so far to be a good little encoder.

---

### Post by ckaya on 2007-05-03
Just found this: [http://www.hayber.us/rox/Ripper/](http://www.hayber.us/rox/Ripper/)

It is a ripper for ROX-Desktop.

---

### Post by dangerousnerd on 2007-05-03
> **ckaya said:**
> Just found this: [http://www.hayber.us/rox/Ripper/](http://www.hayber.us/rox/Ripper/)

It is a ripper for ROX-Desktop.

Hey!  That looks awesome!  Thanks a lot!  I'm gonna install it tonight.

---

### Post by Co.Sinecure on 2007-05-08
I just installed ripperx ontop of icewm, and that seems pretty good, i had it set up and ripping to ogg in about 30 seconds (including synaptic time!)

Once it has ripped one track to the temp wav file, it starts ripping the next track while encoding the first at the same time! I like it!

---

### Post by dangerousnerd on 2007-05-08
> **Co.Sinecure said:**
> I just installed ripperx ontop of icewm, and that seems pretty good, i had it set up and ripping to ogg in about 30 seconds (including synaptic time!)



Thanks for the tip!  It seems that most people like RipperX.  How did you get it to encode ogg, though?  Mine is only encoding mp3. :(

---

### Post by Co.Sinecure on 2007-05-08
> **dangerousnerd said:**
> Thanks for the tip!  It seems that most people like RipperX.  How did you get it to encode ogg, though?  Mine is only encoding mp3. :(
Under the Mp3 tab in the options, the Encoder drop-drown had an entry for OggVorbis. I'm not sure if it was something I installed or what. Perhaps the vorbis-tools package (just did a quick search through synaptic)?

Also I had installed cdparanoia which was picked up by ripperx as the ripper plugin.

---

### Post by dangerousnerd on 2007-05-08
> **Co.Sinecure said:**
> Under the Mp3 tab in the options, the Encoder drop-drown had an entry for OggVorbis. I'm not sure if it was something I installed or what. Perhaps the vorbis-tools package (just did a quick search through synaptic)?

Also I had installed cdparanoia which was picked up by ripperx as the ripper plugin.

Thanks!  I'll try this when I get home tonight. :)

---

### Post by dangerousnerd on 2007-05-09
It worked!  I don't know how I missed this... maybe because the tab is labled "MP3"...

Well, thank you very much Co.Sinecure!  I have all kinds of fuzzy ogg happiness now! :D

---

### Post by zazen666 on 2007-08-09
after downloading, how do you install ripper?

---

### Post by dangerousnerd on 2007-08-09
I installed it using synaptic, I believe.  I'm assuming it doesn't have a make file if you download the source? No "sudo ./ make" or "install"?  (It's been a little while since I've compiled as you can see).

---

### Post by Co.Sinecure on 2007-08-09
> **zazen666 said:**
> after downloading, how do you install ripper?

If you installed it via synaptic, it should just appear in your application menu (top left)

---

### Post by zazen666 on 2007-08-09
would that be ripperX then?

---

### Post by zazen666 on 2007-08-09
i got it. works great

---

### Post by marties on 2007-10-20
There is also [asunder]("http://littlesvr.ca/asunder/") you can install it via [getdeb]("http://www.getdeb.net/search.php?keywords=asunder")

It does WAV, MP3, OGG, and/or FLAC

---

