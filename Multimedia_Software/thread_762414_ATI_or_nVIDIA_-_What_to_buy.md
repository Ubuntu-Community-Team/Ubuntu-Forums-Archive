---
title: "ATI or nVIDIA - What to buy?"
date: 2008-04-22
forum: Multimedia Software
---

### Post by rajeshja on 2008-04-22
I'm buying a new desktop, on which I intend to install Ubuntu as my primary OS. I'm trying to decide which graphics card to buy, am trying to choose between ATI and nVidia. I'm not getting a clear picture of which company has better support for Linux drivers.

The cards I'm looking at right now, are the Radeon X1650 Pro, and the GeForce 8600GT.

I've read that nVidia generally has drivers with much better support for Linux, but have also read that that's not so true for the 8*** series of cards.

Then again, I've also read that ATI is attempting to open-source their drivers. But then the performance of their cards under linux is a lot worse than under Windows.

I intend to use Compiz Fusion, and run games under Wine, like Age of Mythology, and if I can make it run, Need for Speed Underground 2.

Any suggestions about what I should go for?

---

### Post by Saint Angeles on 2008-04-22
my ATI card works wonderfully. its an x1550 but we use the same proprietary driver (fglrx). I wrote a mini-tutorial on how to get ATI cards working beautifully and it seems to work for a lot of machines...

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

I don't know much about geforce cards but I believe that ATI drivers are getting better and better every month.

---

### Post by rajeshja on 2008-04-22
That's good to know.

Do you know of any benchmarks which compare performance of your card (or similar cards) between Linux and Windows with the latest drivers?

---

### Post by Stason on 2008-04-22
Save yourself some headache - get nvidia.

---

### Post by HyperHacker on 2008-04-22
Seconded. I couldn't get a Radeon 9550 to work at all, but a GeForce 6200 OC is working great right now.

---

### Post by lswest on 2008-04-22
yeah, my experience is always been that nvidia drivers play nicely with Linux, and ATI is more a hit-or-miss type situation.

---

### Post by 3rdalbum on 2008-04-22
Buy the 8600. As long as you're running Hardy, you should be alright (the drivers that come with Gutsy are buggy).

ATI still hasn't got its act together yet for Linux drivers.

---

### Post by Saint Angeles on 2008-04-22
> **3rdalbum said:**
> Buy the 8600. As long as you're running Hardy, you should be alright (the drivers that come with Gutsy are buggy).

ATI still hasn't got its act together yet for Linux drivers.
well the stuff i can do on my ati card with 256mb memory blows away what my roommate can do with his geforce with the same memory. he also has 6 gigs RAM and a quad core compared to my P4 and 2GB RAM.

watching video, spinning a cube around and stuff is totally smooth.

but as mentioned above, its prolly a hit or miss type of thing.

good luck with whatever you choose.

---

### Post by rajeshja on 2008-04-22
Well, this - [http://www.youtube.com/watch?v=oyoNCqwZX38](http://www.youtube.com/watch?v=oyoNCqwZX38) - is what got me sold on the ATI x1650 Pro.

The other thing was [http://pcquest.ciol.com/2007/images/gpu_price_feature.pdf](http://pcquest.ciol.com/2007/images/gpu_price_feature.pdf)

The X1650 seems to be 10-20% better than the 8600GT in most of the tests. But of course that's on Windows. Also, the 8600GT is currently around 25% more expensive than the X1650. Both have 512MB.

Saint Angeles, is there any specific reason why you believe the ATI drivers are getting better? ATI partially opening up the source to their drivers was going to be my reason for picking an ATI card, but I've read too many opinions that put the odds in nVidia's favour in spite of that.

The net result, right now, is that I'm extreeeemely confused :)

---

### Post by cor2y on 2008-04-22
Hassle free video playback with xvmc hardware support ati
Gaming in 3d then nvidia.
On the desktop effects side they are both equal depending on the version of the card you purchase, latter nvidia cards require the closed source drivers in order to use compiz-fusion, while on the ati side the opensource drivers can do compiz without having to install the closed ones.
3d acceleration for both require closed source drivers.
Depending on how new the card you buy is be prepared for bad driver support until they update drivers for the newer cards on linux.
Ati is finally getting their act together so expect better video drivers in the future they have been updating/improving their drivers very quickly for a bit although these updates you will have to install yourself they don't come through the official repos very often.

---

### Post by Bruce R on 2008-04-22
ASUS/NVidia 8500GT and XFX/NVidia 8800GS work well with Envy Legacy drivers,  conferring XServer Colour Correction (for desktop) and XServer XVideo Settings (for overlay) for Ubuntu 7.10 and Mint 4.0, but a Club/ATI 2600PRO is only starting to be usable with Ubuntu 8.04 Release Candidate and its repository envyng-core and envyng-gtk application of the ATI 8.4 Linux x86 driver.

Has anyone actually tried newer 3850 or 3870 series cards with 8.04 Release Candidate ?

Edit PS Alberto Milone has advised that a few days after 8.04 full release, an updated EnvyNG should allow use of ATI 3800 series cards,  so others interested should just keep checking !

---

### Post by jacob01 on 2008-04-22
i have the 8600 and it works beautifully although i did have a little problem with it a little while back where i had to install the drivers after the reboot but i believe that was an error on my part.

i cant say anything about any ati products since i have not had anything ati, but i can say that the intel x3000 is a good chip although its an igp, is recognized right away and the open source drivers are pretty good but dont expect to play games on it.

8600 is all that i could ask for plays quake wars on high will aa x4 and still able to play at 60 fps instead of the 30 fps frame cap.

counter strike source with wine i could get 60fps in the stress test


and in nexuiz i get an average of 114 everything maxed out.

---

### Post by Melcar on 2008-04-22
I was under the impression that the 8600 was faster (in Windows) than the x1650?  I have heard that the support for the nvidia 8xxxx series is less than spectacular, but such a card should still perform well on a normal Linux desktop.
As for fglrx, performance wise it's a very good driver.  In Nexuiz, fglrx is about 5-10% slower than the Windows driver (timedemo with Ultra settings @ 1680x1050), and about 15% slower in Doom 3 (timedemo with default settings @ 1280x1024).  Other games, like Alien Arena, don't seem to run any slower in Linux compared to Windows.  Feature wise, fglrx is a bit "lacking"; multiple display setups are still a pain, and some overlays for video capture are not supported.

---

### Post by cor2y on 2008-04-23
If you game then nvidia but don't expect stella 2d support.
If the desktop and movie watching is all you need then ati, don't expect stella performance in 3d games.

Its that simple i have used both an ati x850XT and currently have a Nvidia 8600GTS.
Comparing the two may be a bit unfair since they are nowhere near each other but i can say compiz-fusion with the X850XT worked without the need for the closed source 3d drivers , and video playback, desktop effects with and without the closed drivers was smooth, gaming on the other hand not so smooth. 
On the nvidia however , no 2d effects or compiz-fusion without installing the closed drivers (possibly because its a newish vid card and they haven't got much work for it on the open source side) with the closed drivers installed gaming was smooth but movie playback and desktop effects were jerky with a lot of tearing on screen when compiz-fusion was enabled for a while i thought i had a substandard/weak card, there is no hardware acceleration for mpeg and mpeg2 on the card unlike the ati (lack of xvmc) so the burden of playback is on the cpu not important if you don't watch a lot of movies but something to be aware of also the latest drivers have a bad hue setting so the color of your video will be off you will have to manually adjust your hue settings to fix this.
Finally both cards do not have hidef hardware video acceleraton in linux so don't expect the video card to take the burden of hidef playback off the cpu like it does in windows until they add this to the close source drivers or the folks working on the open drivers figure out how to do it its not active for both cards if they support this.

---

### Post by rajeshja on 2008-04-25
Melcar, the benchmark I posted a link to, seems to say that the ATI X1650 Pro 512MB has a lower 3D Mark06 score, but in most cases performs better than the nVidia 8600GT 512MB.

I'm taking all your opinions to mean that the ATI card is probably slower in Linux now, but given that ATI's drivers are getting better (and I've read this in other places too), since they've got more work going on the open source drivers, they might be a better bet in the long run.

The X1650 is an R500-based card, and I believe there is a lot of open-source work going on to get drivers out for that series.

At this time I'm planning on getting the ATI card. Does anyone else have any hard reasons to change my mind?

---

### Post by Darphas on 2008-04-25
well, if i have a integral Intel video card, with 256mb in memory
mmay work good with ubuntu 8.04? o i need to download and install the drivers.

In oficial webpage from intel, i was found my video card is compratible with linux, but i can't download the drivers from there, they wrote a webpage to download it!

[http://www.intellinuxgraphics.org/](http://www.intellinuxgraphics.org/)

someone from here was tested that?

In that link you found my model video card and more info:
[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2102&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2102&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go)!

---

### Post by Saint Angeles on 2008-04-25
> **rajeshja said:**
> Saint Angeles, is there any specific reason why you believe the ATI drivers are getting better? ATI partially opening up the source to their drivers was going to be my reason for picking an ATI card, but I've read too many opinions that put the odds in nVidia's favour in spite of that.

The net result, right now, is that I'm extreeeemely confused :)

well last October it was impossible for me to run compiz. in November, i was able to do it but it was jumpy with weird little lines across the screen.

with gutsy... i could only use November's fglrx because non of the new ones even worked... until I installed hardy.

the last two fglrx's are working smooth as butter under hardy. Its not "proof" but for me, I notice definite improvement in the last 6 months!

---

### Post by Galban on 2008-04-25
Nvidia all the way... why? Please read this short thread and you will see why?

[http://ubuntuforums.org/showthread.php?t=385743]("http://ubuntuforums.org/showthread.php?t=385743")

---

