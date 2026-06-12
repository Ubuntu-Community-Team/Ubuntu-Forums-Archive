---
title: "Calling All Super Linux Coders... A Challenge!"
date: 2009-09-07
forum: Multimedia Software
---

### Post by tomasrey88 on 2009-09-07
Hey,

I read on the Mitsubishi home electronics website that most home Blu Ray players use Linux: [http://techon.nikkeibp.co.jp/english/NEWS_EN/20090213/165586/](http://techon.nikkeibp.co.jp/english/NEWS_EN/20090213/165586/) . However, there's no Blu Ray player for Ubuntu Linux. Windows Vista doesn't play it reliably. Windows 7 is still in Beta test. This could potentially be the killer app that will propel Ubuntu ahead of Windows. Remember the DVD? It took awhile to catch on until there were DVD recorders. That's because nobody wants to buy 2 machines (a VHS to record and a DVD to play). Most consumers just want to keep it simple and inexpensive. If you were to develop a Linux Blu Ray player, it (and other innovations) will eventually cause Linux to overtake Windows. 

So, come on SUPER CODERS, I invite you to develop a Linux Blu Ray player. You don't have to reinvent the wheel. I mean, if consumer Blu Ray players use Linux, then why don't we crack it open to see how it's done so that we could make a copyleft/Ubuntu/GPL version of it? 

Buying a computer based blu ray rw player for your computer is cheap compared to a stand alone unit because the stand alone unit has a cpu, but you are using your coputer's cpu in a computer based unit. My local electronics store (Fry's) has a pc blu ray rw on sale for just $175. That's a price that is not different from many dvd rw stand alone units.  

I mean, this one app will do more damage to the evil Microcrap monopoly than any virus ever will do. I put the challenge out there Uber coders. I invite you to... Just Do It. 

Thanks,
:P

P.S. Whomever does this will be my Linux Superhero forever....

---

### Post by Revolutionary101 on 2009-09-07
I think Linux should have Blu-Ray support too but I think that you should have posted this thread in a different area of the Ubuntu Forums because this is mostly for Ubuntu support and help

---

### Post by Brandel Valico on 2009-09-07
[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

a bit cumbersome but here you go

---

### Post by tomasrey88 on 2009-09-07
Brandel Valico,

Yes, I already know about that thread, but as you said, it is "cumbersome". In other words, it cannot play blu ray disks. The thread you mentioned asks the impossible from the average home end user; 1. dump the disk to hard drive  2. decode the disk  3. play the disc. Not to mention that this process will take hours to do, especially if you have a slow processor. You might end up with a fat zero after hours of effort if your computer hangs or crashes in the process. 

C'mon, we need to worship some new stars in addition to RMS, MoRE and Jon Lech Johansen for a change of pace. I invite you supercoders to make a blu ray player for Linux. 

Thanks in advance, 
:P

---

### Post by lykwydchykyn on 2009-09-07
If I've heard correctly, the mplayer/ffmpeg developers are working on blu-ray support, though there is the whole sticky issue of DRM.

---

### Post by andrew.46 on 2009-09-07
Hi lykwdchykyn,

> **lykwydchykyn said:**
> If I've heard correctly, the mplayer/ffmpeg developers are working on blu-ray support, though there is the whole sticky issue of DRM.

There is a great deal of wrangling and more than a little name-calling here:

[MPlayer-dev-eng] Bluray playback
[http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-September/062312.html](http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-September/062312.html)

Hopefully some code will also eventuate :-).

Andrew

---

### Post by tomasrey88 on 2009-09-08
Andrew.46,

That thread you mentioned has got to be the world's most confusing forum software I have ever seen. You cannot see the list of posts in the entire thread at one time. You have to click through each post one at a time! I followed that thread about 10 or 20 posts deep and gave up as I did not see a post saying that a blu ray player solution was available. 

decrypting and key replication legality seems to be the hangup. However, if you offer 2 versions of the software, one with the decryption and replicated keys and another version without them, then those who live in countries where it is illegal could enjoy the mplayer without blu ray and those who live in countries where it is legal could enjoy the mplayer with the blu ray. Just make it available from a country where it is legal to do so and have a disclaimer that makes the end user choose which version to download with an alert for the user to check local legality before downloading and using the blu ray capable version. 

it seems to be stupid corporate think for the blu ray people (sony?) to exclude linux users from playing blu ray discs. After all, the more people who use blu ray discs, the more dics they will sell (and more profits). after all, we just want to play blu ray discs and be their customers. we don't want to copy them. corporations are often run by idiots. the only thing they have going for them is economy of scale. 

i mean, who the hell is going to sit there and wait HOURS for the blu ray disc to download and burn. It takes several hours to download and burn a DVD and blu ray is 5-10 times bigger so I estimate that it would take a computer a full day (give or take some hours, depending on the speed of your computer/net/drive) to download and burn a blu ray disc. Wouldn't it just be easier to rent it? It takes minutes to get something from the local video store. Many video rental places have unlimited rentals. If you were to amortize the cost of the monthly membership over an UNLIMITED number of discs, it's almost as good a s free. Most of the illegal copying is done in Asia. They don't decode discs to copy them in Asia. They just do bit-to-bit exact copies. Therefore, encryption is just there to inconvenience LEGITIMATE CUSTOMERS. So, Sony is inconveniencing the majority of legitimate users to guard against the minority of illegal users. Wow. Stupid corporate think at it's best.

---

### Post by lykwydchykyn on 2009-09-08
> **tomasrey88 said:**
> Andrew.46,

That thread you mentioned has got to be the world's most confusing forum software I have ever seen. You cannot see the list of posts in the entire thread at one time. You have to click through each post one at a time! I followed that thread about 10 or 20 posts deep and gave up as I did not see a post saying that a blu ray player solution was available. 

It's a mailing list archive, not a forum.  Developers seem to prefer these to forums, for various reasons.
> 
decrypting and key replication legality seems to be the hangup. However, if you offer 2 versions of the software, one with the decryption and replicated keys and another version without them, then those who live in countries where it is illegal could enjoy the mplayer without blu ray and those who live in countries where it is legal could enjoy the mplayer with the blu ray. Just make it available from a country where it is legal to do so and have a disclaimer that makes the end user choose which version to download with an alert for the user to check local legality before downloading and using the blu ray capable version. 

This is basically what is done with DVD support right now, and of course you get all kinds of people griping that "Linux doesn't support DVD playback out of the box" or "I had to add some stupid repository and install a bunch of cryptic files to make DVD's work".  Same thing with mp3, wma, and all the other restricted formats.  

> 
it seems to be stupid corporate think for the blu ray people (sony?) to exclude linux users from playing blu ray discs. After all, the more people who use blu ray discs, the more dics they will sell (and more profits). after all, we just want to play blu ray discs and be their customers. we don't want to copy them. corporations are often run by idiots. the only thing they have going for them is economy of scale. 


You're preaching to the choir here.  But there's a good object lesson here; when people ask the question "Why doesn't Linux support $TECHNOLOGY?", a lot of them jump to the conclusion that it's because FOSS developers are out of touch, or don't care, or are too lazy to support $TECHNOLOGY (I'm not suggesting that's what you were saying, but I hear it a lot from people in these contexts)  The reality is often more complex, and as in this case, the powers that be do not want a free, open-source implementation of $TECHNOLOGY because they see it as a threat to their business model.

---

### Post by rob-ward on 2009-09-08
I arn't positive but I beleive that VLC will playback non encrypted/DRM blu rays but it is the DRM that is the problem. Don't know, if I have a bluray player in my PC I would certainly have a play, unfortunetly I don't :-(

---

### Post by tomasrey88 on 2009-09-09
rob-ward, you are probably right. There is a Nero Linux application for a reasonable price that will allow you to burn blu ray data discs (not movies). It's only $30 (if I remember correctly). I have never used Nero in LInux before, but it should be just as good. I've never had any problems with Nero in Microcrap Loser before. However, Nero will not play blu ray. If it does, then I would buy a blu ray player and Nero to install on my computer right now. 

I would really like to buy a blu ray player, but I am saddened that Linux doesn't support it. I'd hate to have to buy a Windows XP disc, especially because it will lose support in 2 years.... I don't know anyone with Vista who likes it and don't even get me started on the "modular" or "subcription based" greed of Microcrap Loser 7.

---

### Post by rob-ward on 2009-09-09
Well as posted above the instructions at [http://https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD]("http://https//help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD") should work, only problem is there are a few steps which make it difficult for newbies, If I had a bluray or HDDVD player I would have a go at automatic the process inside on application, i'm sure someone out there must have a bluray drive that they can cobble together an application that does all these processes automatically...

---

### Post by DEC014 on 2009-09-19
> **tomasrey88 said:**
> Andrew.46,

it seems to be stupid corporate think for the blu ray people (sony?) to exclude linux users from playing blu ray discs. 

I don't think it's Sony making the problems for Linux Users.  I found this after a few hours search tonight:

[Sony Global - Linux Source Code]("http://www.sony.net/Products/Linux/Video/category01.html")

It appears that most of Sony's BD Players use Linux software, and in keeping with LGPL and GPL licenses, they've posted the software for each model.  Maybe this can give some developers a jump start on getting Blu-ray support for Open Source Software.

---

### Post by kamaboko on 2009-10-04
> **tomasrey88 said:**
> Hey,

I read on the Mitsubishi home electronics website that most home Blu Ray players use Linux: [http://techon.nikkeibp.co.jp/english/NEWS_EN/20090213/165586/](http://techon.nikkeibp.co.jp/english/NEWS_EN/20090213/165586/) . However, there's no Blu Ray player for Ubuntu Linux. Windows Vista doesn't play it reliably.

Do I want HDVD & Blu-Ray on my Ubuntu box?  Hell yes.  I have to say though that my Vista HTPC plays them perfectly.

---

### Post by jsmnuk on 2011-01-28
I do amateur Blu-ray videography, editing and burning. I edited a homemade video with Openshot. Everything was cool until I tried to burn it, just simply burn it to a BD-R. Ubuntu won't do it, and again, I'm talking about BURNING, not playing Blu-Ray. No program will burn Blu-Ray.

For me, this what keeps me using Windows video editing software programs. Once I can burn Blu-Ray in Ubuntu, I'm out of Windows.

Part of the problem here is that it seems that all that Linux people care about regarding Blu-Ray is how they can rip Blu-Ray movies. IMHO, that's got to change. Blu-Ray consumer products are at a standstill --- one STILL can't buy a standalone Blu-Ray recorder in any country but Japan, and I think the reasons are more political and control-based than stagnant technology.

Let's see what we can do --- this is a major challenge.

---

### Post by BicyclerBoy on 2011-01-29
K3b can burn bluray disc..I doubt it is the only app.

If it's not a data disc, don't know what you can author them with tho'.

Stand-alone BD recorder in shops here..
HDD/BD recorder with twin DVB-T tuners US$1K

---

