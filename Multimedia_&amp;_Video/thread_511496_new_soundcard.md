---
title: "new soundcard"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by nzadLithium on 2007-07-27
Hey

My onboard soundcard is screwed. It doesnt play out of the front right speaker. It also doesn't do hardware mixing which is really annoying because i can't find a way for oss games to use alsa without the sound choking.  Its realtek alc850.

I am going to get a new soundcard. the ones i'm looking at at the moment are soundblaster 5.1 and audigy value. Also if the closed source drivers for x-fi come out before i get a new soundcard i might get one of them. But from what i have seen on the alsa site these cards can only play at 48khz. I want to know whether these will give me better sound quality compared to my existing soundcard or not. (i couldn't find anything on realtek cards in the alsa matrix)

I also want to know If i get one of these soundcard's (they all have a line-in/mic a front a back and a side) is there somewhere on these cards i can plug in my sound connectors on the front of my case? Because I have  a tvcard that uses the line in and i still want to be able to use my microphone.

I'm thinking if i can't i should be able to use onboard sound to do either of the microphone or line in?

Thx

---

### Post by kyphi on 2007-07-28
If your onboard sound has worked in the past and now only works out of one speaker I would check that there is nothing wrong with your speakers or the connections to the speakers.

If you decide that you want to install a sound card, it would be advisable to disable the onboard sound in the BIOS.  Soundblaster 5.1 works very well in Ubuntu.  A separate sound card will usually give you better sound than integrated motherboard sound controllers.

To divert your sound in and out sockets to the front of your computer depends on the computer case and the motherboard.  You may have to fire up your soldering iron for that.

Does that cover it?

---

### Post by nzadLithium on 2007-07-28
The sound blaster 5.1 as i said only has line in/microphone (in one), front, back and center connections. I therefore would not be able to connect both my tv card and microphone at the same time.

I do not have much experience using a soldering iron and would probably make a mess of it. It also appears from the picture of the card that it doesnt have anywhere i could either connect or solder my front connectors onto.

This is why i want to know if i can use onboard sound just for microphone and use whatever new card i get for everything else. I should then be able to set the new card as default and then just tell all my microphone applications to use the mic on the other card right? 

You said it is advisable to disable the onboard sound. Is this because some programs might try to use the other sound card? If it is then what i said above would fix any problems right? Or are there other problems i am likely to find?

I know my front right speaker being screwed is neither an operating system nor speaker problem because it happens with both my old speakers and a 5.1 set i bought about 3 months ago.

I just thought of something else. Since i have both oss and alsa on this pc would the hardware mixing be able to mix any oss sound with already software mixed alsa sound? And alsa would continue to software mix my sound right?

---

### Post by kyphi on 2007-07-28
On my machine, the TV out is controlled by my graphics card.

For conferencing needing a mike I use the rear connections.

You cannot use your onboard sound chip for one thing and your sound card for another.  It is either or.

On every computer that I have built I have disabled onboard sound and relied on a s sound card.  It has been invariably superior in performance.

I cannot answer the issues raised in your last paragraph.

Sorry, but I have to log out for the night.  Will check this post in the morning.

---

### Post by nzadLithium on 2007-07-28
Perhaps i could buy an adapter like this one then:
[http://www.dse.co.nz/cgi-bin/dse.storefront/46ab021b007dbe242740c0a87f330677/Product/View/P6644](http://www.dse.co.nz/cgi-bin/dse.storefront/46ab021b007dbe242740c0a87f330677/Product/View/P6644)

would that allow me to plug both my tv cards audio out into the soundcards line in as well as a microphone into the soundcards line in and have them both work?

thx for your help

---

### Post by kyphi on 2007-07-28
What were you referring to in the DSE catalogue?

---

### Post by nzadLithium on 2007-07-29
oh lol link didnt work sry.

Adaptor 2.5mm Stereo Plug - 2 x 2.5mm Stereo Sockets

If this will work will it mix my line in and microphone? Or will one overpower the other?

---

### Post by kyphi on 2007-07-29
About the adapter - it looks like you are trying to attach two components to one output or input.  That can work for output devices such as headphones but I don't think your soundcard or your computer are designed to have multiple input devices into one socket.

I am puzzled by what you are trying to achieve here.

---

### Post by nzadLithium on 2007-07-29
At the moment on my tv card i have a sound out. I have to plug this sound out into my soundcards line in. On the soundblaster 5.1 there is only one plug for both line in or microphone. Now if this connector is already taken up then i cant plug my microphone in. 

I want to be able to get use my microphone but i want to also be able to hear sound from my tv card.

---

### Post by fredj on 2007-07-29
If you open the alsamixer (double click on the speaker icon in the taskbar) and go to the File->Change Device
menu then you should be able to select either your soundcard or the sound device from your video card.

---

### Post by kyphi on 2007-07-29
The 5.1 has a line out for your loudspeakers, a line in for your microphone and an aux in for ?

Doesn't that cover it?

---

### Post by nzadLithium on 2007-07-29
nope i only have an oss device and an alsa device for my soundcard. the only way my tvcard outputs its sound is through the line out on the tvcard.

On the picture on the 5.1 card i see a green connection for front speakers a black connection for rear speakers a orange connection for center/subwoofer and a blue one for line in _or_ microphone. I i think the blue one is also aux? It says the blue one does Line In/Mic In/Digital I/O This doesnt leave me anywhere to plug in a tv card. 

On my onboard i have a green for front a black for center/subwoofer a orange for rear (i think i got colors round right way?) a pink for microphone, a blue for line in and a brown one for side.

I don't actually need the side one but i need the rest. So i need a card with 5 connectors on it. All the cards i have looked at though only have four. :(

---

### Post by nzadLithium on 2007-07-29
actually it looks like the audigy 4 has enough connections. 
None of the x-fi cards have enough connections though :p

Audigy 4 costs alot of money though. More than x-fi xtreme audio...

I like the idea of the soundblaster 5.1 but i don't see how its gona work. 
Unless i can use the line in from my onboard then use 5.1 for the rest?
I read somewhere you can kindof turn to sound devices into one?
And if i had another sound card plugged in wouldn't ubuntu just add more dsp things to assess them?

---

### Post by kyphi on 2007-07-29
I would not recommend using more than one sound card, if I read your comment correctly.

I have a Soundblaster Live 5.1 that has 4 sockets.  The Soundblaster Live has undergone a number of changes since it was first introduced.  It first came out as a Creative Vibra 128 with 3 sockets.

The latest version has 5 connectors.

[http://us.creative.com/products/product.asp?category=1&subcategory=206&product=50](http://us.creative.com/products/product.asp?category=1&subcategory=206&product=50)

---

### Post by nzadLithium on 2007-07-30
That card should be perfect now i just have to convince my parents to take me to a shop i found which sells them :)

Thx

---

