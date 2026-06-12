---
title: "Cinelerra 4.2 (Heroine Virtual Version) working in Ubuntu 10.04 &amp; 10.10 64-bit!"
date: 2011-01-22
forum: Multimedia Software
---

### Post by beccatoria on 2011-01-22
I know the Community Version of Cinelerra is much easier to install, but I've been wanting to try out the new Heroine Virtual version since the 4.2 release to see the nested sequences feature, among other things, especially given that it doesn't look like the Community Version is still being merged with the Heroine Virtual version after new releases.  But I couldn't compile it on Ubuntu, which isn't surprising given my experience compiling things is next to zilch.  

But I have found an easy way to get it working!  Apologies to all who think this is old news, but it was very exciting to me so I feel I ought to share it for other wayward noobs like myself who want to give it a try.  

Someone awesome make a .deb package to install 4.2 on Debian, and after checking the listed dependencies were all present and seemed to share the same name in the Ubuntu repositories, I tried installing it via the Debian .deb, and it works!  

I installed the Cinelerra 4.2 .deb as well as the Cinelerra-data .deb (which was the only listed dependency not present in the Ubuntu repositories, so I installed that first) which are available here:  

[http://debian-multimedia.org/dists/testing/main/binary-amd64/package/cinelerra.php](http://debian-multimedia.org/dists/testing/main/binary-amd64/package/cinelerra.php)

and

[http://debian-multimedia.org/dists/testing/main/binary-amd64/package/cinelerra-data.php](http://debian-multimedia.org/dists/testing/main/binary-amd64/package/cinelerra-data.php)

There is a link to a .deb file towards the bottom of the page in each instance.  

Those are for 64-bit but 32-bit versions are available if you search the site.  Be careful as the 2.1.5 CV version is also available from there.  

I haven't had a chance to test it at length, but so far it all appears to be working perfectly in 10.04 with the same defaults I used for CV.  

In 10.10 there are is a minor issue in that when I click on a menu, the menu doesn't appear until I move the mouse slightly and start scrolling over where it should be - the menu then appears.  Also hover-over text doesn't always work.  This is predominantly an issue regarding the insertion strategy you wish to use when opening new media as the HV version has changed that from a drop-down menu to a series of icons with hover-over text.  But the program itself appears to be working fine, and the menu-issue was one I occasionally had when running CV in 10.10 too.  In 10.10 I also had initial issues with audio playback, but those were fixed by trying a different audio driver preset in the Preferences.  

Anyway, I was quite excited!  And now I'm off to test more features!  :)

---

### Post by mrtorrent on 2011-03-26
I was excited to find your post after a quick search on Google, unfortunately the links are now 404s! :( Any leads on alternative sources?

---

### Post by no2498 on 2011-03-28
this should help you

[http://www.g-raffa.eu/Cinelerra/HOWTO/index.html](http://www.g-raffa.eu/Cinelerra/HOWTO/index.html)

---

### Post by mrtorrent on 2011-03-30
> **no2498 said:**
> this should help you

[http://www.g-raffa.eu/Cinelerra/HOWTO/index.html](http://www.g-raffa.eu/Cinelerra/HOWTO/index.html)

That's for Cinelerra CV, not the Heroine Virtual version.

For those interested, there is a list of Debian Multimedia mirrors here, where you can download the appropriate packages (cinelerra and cinelerra-data): [http://debian-multimedia.org/debian-m.php](http://debian-multimedia.org/debian-m.php)

4.2 is working great for me!

---

### Post by beccatoria on 2011-04-05
Hi!  :)
 
[FONT=Arial][SIZE=3]Very pleased to see someone else getting some use from this!  I’m sorry to hear that the original links weren’t working for you – I’m not sure what the issue was because they seem to work okay for me?  Maybe it was a temporary problem, but if not, thank you for posting an alternate solution.  Glad to hear it’s working for you now!  :D[/SIZE][/FONT]

---

### Post by yodermk on 2011-06-21
Hello,

I took this advice and installed said RPM on Ubuntu Natty.  Loads OK and seems to do some things, but the main reason I need Cinelerra 4.x is to read Maktroska format container files.  The reason I need that is to be able to use audio from my Canon 60D per this article:
[http://thegiftedbabies.com/2010/03/06/getting-canon-7d-footage-to-work-with-cinelerra-4-1/](http://thegiftedbabies.com/2010/03/06/getting-canon-7d-footage-to-work-with-cinelerra-4-1/)

Unfortunately, as soon as I load an .mkv file into Cinelerra 4.2, it crashes. :(

When I try to compile Cinelerra 4.2, configure gives an error that there is no videodev.h.  In /usr/include/linux, there is a videodev2.h.  I guess that is Video4Linux 1 vs 2, and 1 was removed lately from my understanding.  This RPM was obviously compiled somehow, but maybe on a slightly incompatible kernel?

Any solution here?  I need my Cin 4.2 .... :(

Maybe the only way forward is to install the version of Debian that this .deb was made for ...

---

### Post by yodermk on 2011-06-22
Wheee.  Tried to compile it on my laptop, which still ran Maverick 32-bit. Failed with some weird error, which from a Google search others were getting on 32-bit systems. So I reinstalled it with Maverick 64-bit.

After some package hunting grief, the ./configure and make worked without error. The plugin/ directory was full of compiled plugins.  But ... no 'cinelerra' executable -- anywhere!!!  *sob*

I finally just installed the suggested .deb files on Maverick 64, and it does seem to work.  It loads my .mkv file, which makes it crash on Natty 64.

So perhaps I am good for now, assuming my laptop is powerful enough for HD editing (an early Core 2 Duo with 2GB RAM).  I still want to run it on my desktop but am not interested in downgrading the OS.  Guess it will have to wait until Heroine Virtual fixes it for Video4Linux 2.

---

