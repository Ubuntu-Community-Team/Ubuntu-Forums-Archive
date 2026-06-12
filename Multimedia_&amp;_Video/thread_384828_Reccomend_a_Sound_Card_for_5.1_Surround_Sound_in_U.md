---
title: "Reccomend a Sound Card for 5.1 Surround Sound in Ubuntu?"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by silentrhythm on 2007-03-14
Hello!

I've been happily using Ubuntu for some time now, and these forums are a great resource. I've been a member for a while, and this is the first time I haven't found an answer to a question and have had a need to post a new thread.

** Note, if you don't feel like reading my story, and would just like to read my problem feel free to scroll down through these few paragraphs :)

I've had problems with Amarok, and sound in general on Ubuntu for some time now. First it was getting 5.1 surround to work, then sound at all. Now I've got my rear speakers working (but not center) by just duplicating the front. This is acceptable, but it would still be very nice to have 5.1 working when availabe (works in windows). But my bigger problem lately is that my sound will cut off intermitendly, for no apparent reason. I am usually forced to restart (at least X) to regain functionality. Theres no distinct pattern that I can find for the failures. I have the best luck with XMMS, it seems to work the longest but eventually it will fail as well. Amarok and video players fail the quickest.

So far I've assumed it was an issue with linux, drivers or improper configuration. 
I've been through every resource I could find, I've combed through ALSA documentation to no avail. But recently I've had a need to install Windows for the first time in months, and was actually rather pleased to find that I experienced the exact same problem in windows! So the problem is most likely my motherboard's onboard sound, I assume it it has failed (it's an intel chip, AC'97).


**** Skip to here if you don't want to read my story *****

But so now I'm looking to purcahse a dedicated sound card. Nothing too fancy, looking in the range of anywhere from $10-$40 total. I'm willing to buy a nicer one if there is any worthwhile benefit. My biggest concern that I haven't been able to find a whole lot of information on is getting a sound card that works well with linux. So often it seems that a specific model of hardware is well supported for whatever reason, and I wish I had it. And now I'm in the position of needing to purchase new hardware, and I want to make an informed purchase.

My main needs are audio and video playback. I have a set of 5.1 logitech speakers (x530 i think?). They are nothing too fancy, but get decently loud. I'd like to get a quality card that supports at least 5.1 in linux. I haven't found much information at all about getting true 5.1 surround working in linux: most of the time it seems people advise turning on the "duplicate front" option in alsamixer. 

I'm hoping someone that has a sound card similar to what I'm looking for that they are happy with can point me in the right direction. I've been shopping on newegg, and have come up with the following as favorites:

very basic, $7+s&h sound card. should work fine, I'll likely go with this if i don't find a reason to go with a nicer one.
[http://www.newegg.com/Product/Product.asp?Item=N82E16829130001&name=Item-%23%3A-N82E16829130001]("http://www.newegg.com/Product/Product.asp?Item=N82E16829130001&name=Item-%23%3A-N82E16829130001")

similar $10 card:
[http://www.newegg.com/Product/Product.asp?Item=N82E16829120102]("http://www.newegg.com/Product/Product.asp?Item=N82E16829120102")

found an interesting review on one nicer creative card, > 
Pros: Much better than the onboard audio; pretty cheap. Works okay with Linux.

Cons: Many. The sound quality is much better than the onboard audio--sound is rich, fuller, better volume. However, sound still has its flaws. If you pump the volume up to the maximum, it gets distorted. Further, the ALSA driver in Linux is subpar--the channels have bizarre labels and it's hard to figure out what's what. Maybe that's because there is one jack on the card that doubles as both a digital and as an analog jack--better cards have more jacks on them so that digital and analog have dedicated jacks. Linux driver did not even have a master volume slider, so you have to fiddle with individual channels even if you just wanted to cut the master volume.

Other Thoughts: I RMA'd this and got the Soundblaster Audigy 4, which is well worth it. No sound distortion even on maximum volume. No funky channels, and dedicated analog/digital jacks. Much better Linux driver. Definitely worth the more $$.

the Audigy 4 is a very high end card. i haven't found much else online that would lead me to believe it's well supported in linux - but this guy seems to think it is. i'd be interested to learn about the benefits of a higher end card like this, and what works well.

i've tried to check out creative's linux webpage, []("http://opensource.creative.com/soundcard.html")
but it doesn't seem to be working.


but I think I've rambled on enough for now.
 If you're still reading this far, thank you, and thanks in advance for any help you can offer!

---

### Post by silentrhythm on 2007-03-15
update: 

After doing some more shopping I found a card that I think meets my needs. 

I went ahead and ordered the chaintech AV710

[http://www.newegg.com/Product/Product.asp?Item=N82E16829118103]("http://www.newegg.com/Product/Product.asp?Item=N82E16829118103")

it seems to be a good value, and it's a very common card that is well documented. it also does a good job of supporting optical out, if i ever upgrade my speakers in the future. 

i'll post an update when i get it in and see how it works!

---

### Post by drhiii on 2007-04-04
Did you try this card?  How did it work for you?


> **silentrhythm said:**
> update: 

After doing some more shopping I found a card that I think meets my needs. 

I went ahead and ordered the chaintech AV710

[http://www.newegg.com/Product/Product.asp?Item=N82E16829118103]("http://www.newegg.com/Product/Product.asp?Item=N82E16829118103")

it seems to be a good value, and it's a very common card that is well documented. it also does a good job of supporting optical out, if i ever upgrade my speakers in the future. 

i'll post an update when i get it in and see how it works!

---

### Post by DealerMan on 2007-04-27
Bumping this thread to see if the card is working for you.  I've just installed 6.10 Edgy and can't get any sound.  I've read many of the other posts, and tried a new asound file without success.

Any help would be appreciated, I really miss my headphones.

---

### Post by silentrhythm on 2007-10-24
Card is working fine in 2.1 mode - supported by the kernel automatically.

unfortunately no luck with 5.1.
it works great in windows with 5.1, oh well.

---

