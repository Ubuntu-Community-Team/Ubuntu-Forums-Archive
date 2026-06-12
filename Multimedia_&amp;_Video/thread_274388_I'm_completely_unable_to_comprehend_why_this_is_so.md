---
title: "I'm completely unable to comprehend why this is so hard."
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by sktfeelsdapper on 2006-10-09
Hi, it's me again.

This may come off as a sob story or boo look at me, cry for the wah-mbulence kind of thing but I'm really getting tired of these problems I keep having with sound.

Look, like I said before it's probably just me. I made the switch from Windows without very much information on what I was getting into. I had "heard" about Linux briefly over the past couple of years but always invisioned a black screen with a bunch of words and nothing else. I know this not to be true (of course) but I don't understand why this is so complicated.

Yah, everything is geared for Windows (so I've read) but isn't there an easier way? I've banged my head off several walls trying to figure out this soundcard/sound issue to no avail. I've "dsnooped" and "dmixed" and the likes of which any human being would think I've been listening to too much rap. It just isn't making any sense. 

I had sound, running moderately fine, until about 2 am last night when all the sudden I kept getting "segmentation faults" whenever I ran aplay or esd. 

Everything looks fine, including my card which is still listed under lsmod and whatever other command you dial in at the shell. 

I've read so many alsa guides and tried to make sense of them all, only coming to the conclusion that (A. My soundcard isn't geared for multiple sound instances at least on Linux. (I didn't have sound before, so I really couldn't tell you it's performance on Windows). (B. That I've got things so screwed up now that the computer doesn't know whether it's coming or going. Or (C. It's time for ANOTHER fresh reinstall (working on my 6th folks. 

At least on Windows, it was "you've got the wrong drivers installed, but these drivers are impossible to find anywhere other then the Win ME edition and below, so you are screwed to absolute silence and system beeps." I tasted sound, I HAD it...I caressed and cradled it like a newborn child and drank in it's wealth. I laughed along to youtube videos, I listened to many (and do mean many) a mp3 and tried to run multiple sounds at once with little or no conflicts (unless everything wsa set to alsa in which everything just died.)

And the guides and how to's (mostly on other sites the one here didn't apply to me mostly because I had sound out of the box) scattered all over the net make little to no sense, using words and definitions and references that were beyond my scope of comprehension. I followed everything to a tee, hoping for some answer.

My only regret that things have ended this badly with Linux. I am very impressed otherwise, it seems like the options are endless. If I had spent a little more time with my system I could probably get my other drives to work correctly and possibly dive into setting up my desktop environment the way I want. 

But I have sank many a day, and night into this alsa problem with little to no answers and even more issues than I began with. I'm so beyond frustrated with it, that at this point I would rather take a "blue screen of death" or even Macs questionmark start up screen to this. I admit it's a little childish to judge something on the basis of sound but you don't understand. I HAD SOUND. I HAD IT WORKING. And I lost it for whatever reason it being my complete misunderstand of guides or what have you.

And why do they make the guides sound so "easy"? Pages full of jargon about things I know hardly anything about (I could run Windows, I wouldnt say expertly but I was pretty good, never messed with a command promt.) and instructions to do things that effect the end result little to none. What's the point? Is it a bug? Are there constant bugs? Is it just one buggy bug after another?

If anyone could please help me, or contact me with help it is much needed as I'm pulling straws here. 

The deal is I have a via82xx onboard soundcard. Alsamixer looks fine, nothing is muted and the sound is completely up on everything that's needed.

Last night when I'd run at the command promt "esd" or "aplay" I'd get "Segmentation fault" after screwing around a few times with "modules" and "asoundrc" I don't know what I did but I followed the instructions TO THE TEE. 

Is it possible the perhaps my sound card is incapable of running more than one sound at a time on linux? Is it possible that I would have to perform my 6th reinstall to which I will say "nay" and do some research on other OS's. I hear FreeBSD is good. As well as SUSE.

So guys, please help me here. I've read the forums and been to the irc chat room, the traffic in there is so horrendous that even if I try to get a word in edge wise it's like yelling in a room with nothing in it. It just echo's off the walls. 

Please, help me.

---

### Post by az on 2006-10-09
> **sktfeelsdapper said:**
> 

The deal is I have a via82xx onboard soundcard. Alsamixer looks fine, nothing is muted and the sound is completely up on everything that's needed.

Last night when I'd run at the command promt "esd" or "aplay" I'd get "Segmentation fault" after screwing around a few times with "modules" and "asoundrc" 

AFAIK, the via82xx sound driver is not cutting edge and has been supported for quite a long time.  I had a computer with that onboard sound card running on Debian Woody in 2001.  

It should be autodetected and properly configured from the get-go.  Why are you screwing around with modules and a whole bunch of alsa under-the-hood crap?

What guide are you following and why?

---

### Post by sktfeelsdapper on 2006-10-09
I know it's not cutting edge that's not the point.

It isn't properly configured from the get-go. I cannot use things that have sound more than once at a time without it giving me the "make sure your soundcard is blah blah blah" and that's BEFORE I mess with anything else.

There's several guides out there, one for alsasource.
Basically I just google via82xx+alsa and found a bunch of places.
Is it possible for it to mutilstream or whatever they call it?

---

### Post by 3rdalbum on 2006-10-10
Dude, some programs use OSS (Open Sound System) which is old and cannot give sound to more than one program at a time.

Other programs use ALSA, which is much newer and allows multiple sounds.

As Ubuntu uses Gnome, it also has a software mixing thing called ESD. Sometimes, you have to turn ESD off in order for a particular program to work.

If you've having trouble with more than one sound-using program at a time, try turning off ESD. (System > Preferences > Sound > Use Software Mixing)

---

### Post by sktfeelsdapper on 2006-10-10
Dude, this is like the 8th time I've reinstalled because of this sound crap. I've done the software mixing, and I've researched everything I can. (As we speak I'm actually working on that install) So I don't know if it's just my card.

And I don't mean to lay it on thick to anyone, or even come down but it just seems like it should be way easier to do things since this IS "linux for humans" and with that being said and me being a human, why is it so hard?

Anyways, I should have done my research yada yada, me being such a dumb n00b and looking for a quick escape from soundless Windows I DO take the blame. Now that I know enough about Ubuntu/Linux to at least have some general knowledge it might be a while before I come back (if I get a windows disc that is.) 

Sorry but this frustration has taken over my thoughts. I sleep and dream about Ubuntu sound, I want it to work. What's it going to take? A play by play instructional guide? A "Ubuntu for dummies" book?

Like I said it's my fault, I know this for a fact I just wish I would have planned this out ahead of time. ](*,) ](*,) ](*,)

---

### Post by wererabbit on 2006-10-10
Ok skt, here's what you need to do.

Buy a Soundblaster.  Don't buy a knock-off or try using an onboard chipset that may or may not be working.  Buy a Soundblaster.  It's industry-standard.  It's recognized by everything and everyone.  Doesn't matter whether you use Windows or Linux.  Always invest in a Soundblaster.  They aren't perfect, but they're supported by everyone.  I know, I repeat myself a lot.  But I'm right. :)

Look here:
[http://www.newegg.com/Product/Product.asp?Item=N82E16829102003](http://www.newegg.com/Product/Product.asp?Item=N82E16829102003)

[http://www.newegg.com/Product/Product.asp?Item=N82E16829102004](http://www.newegg.com/Product/Product.asp?Item=N82E16829102004)

These will do what you want, as will the Soundblaster Audigy ZS  or 2 ZS series.  You can mess around with some stupid Via chipset for hours and wonder why it doesn't work, or you can spend a little money and get it right and never worry about it again.
Sorry to be so blunt.  I hope this helps.
-w-

---

### Post by Lord Illidan on 2006-10-10
I'm afraid I have to agree. One of the worst experiences of my life was getting my onboard sound working. Was quicker to pop in my genius soundmaker (oldie goldie) than to get it working.

---

