---
title: "Min Hardware Req For Blu-Ray Play w VLC etc?"
date: 2016-06-08
forum: Multimedia Software
---

### Post by lah-ca on 2016-06-08
Hi,

This is multimedia software question in that I want to know what the realistic minimum system requirements are for Blu-Ray playing with, say, VLC.  

I am thinking about adding a Blu-Ray optical drive to my refurbished/salvaged old Shuttle media box.  It has an Athlon 64 X2 4200+ proc, 4 Gb RAM, and a 2 Gb NVidia 2100 PCI-e video adapter.  It is mostly running 14.04 64, although I do try other distros on it from time to time.  The current optical drive is an old Plextor IDE dual layer DVD burner, which is nice because Plextor has/had (Windows) utilities to tweak the drive to suit its purpose.  Mine is set for multimedia playback - slow and ***quiet***.  The drive is getting a little flaky now, experiencing minor difficulties every so often, and increasingly the public library is getting movie titles in Blu-Ray only.  I cannot just go to my PC recycling shop and pick up a tested Blu-Ray ROM/RW on the cheap on the off chance it might work, so I would like some advice before laying out $80 or so.  Thanks.

:popcorn:

---

### Post by T.J. on 2016-06-08
I apologise if I sound glum or hostile to the idea of Blu-Ray, but I have had some bad experiences dealing with it.  I feel it is better that I tell you honestly rather than sugar-coat it.

Playing BD discs requires video hardware that supports HDMI, as well as an updated AACS decoder.  Since VLC does not have a legal AACS decoder, you will not be able to play commercial discs using it.  The existing methods used to playback BD on Linux are likely to be a felony in most jurisdictions, due to WTO trade agreements. You can thank the Blu-Ray Association for that, as well as the fact that they have not licensed a FOSS Linux player.  Blu-Ray is so riddled with multiple layers of copy protection that I wouldn't expect support for Linux or VLC (regardless of OS) any time in the foreseeable future. 

In order to get what you want, you will have to install Windows, and have an up to date Blu-Ray player software. That usually costs about $60 every few years. You will have to replace the software each time they stop updating the player that you already have.

On a different but related topic, truth in advertising should have required certain disclosures about Blu-Ray, including the fact that if you insert a new BD disc into your drive OR your home player, it updates the firmware, and it does this without your consent. Those updates are access lists that can potentially disable playback, usually PERMANENTLY.  This is used in case the Blu-Ray Association believes that model of player has been tampered with or compromised. After that, that disc (and likely others in the future) simply will not play, unless the player is issued a new security key by the BDA.

In my opinion, Linux users are better served by simply buying DVDs or streaming video.  Fluendo sells a legal DVD player for Linux.  Amazon Video works great using Chrome/EME.  Other streaming services work on a Linux based on Android.

---

### Post by lah-ca on 2016-06-08
> **T.J. said:**
> 
I apologise if I sound glum or hostile to the idea of Blu-Ray, but I have had some bad experiences dealing with it.  I feel it is better that I tell you honestly rather than sugar-coat it.

No apologies necessary.  Thank you for your brutal candour.   As Count Floyd might have said, "Very scary, boys and girls!"  I just hope your *glumness* and *hostility* are not the result of having to wear an orange jump suit  at some government Spa.  :wink:

> **T.J. said:**
> 
Playing BD discs requires video hardware that supports HDMI, as well as an updated AACS decoder.

The little 2 Gb, silent Asus/nVida 2100 has an HDMI interface and is connected to my TV.  The AACS decoder is another matter, although my VLC implementation has, in its Open Disk sub-menu, a Blu-Ray button right after the DVD one and just before the Audio CD and SVCD/VCD buttons.  This is part of what prompted my question here.


> **T.J. said:**
> 
In order to get what you want, you will have to install Windows, and have an up to date Blu-Ray player software. That usually costs about $60 every few years. You will have to replace it each time they stop updating the one you have.

Been there, done that, and bought the TShirt and worse.  Open/Vol licensing .... 

I don't know what I want.  I have Windows licenses and some AV CALs.  I could do it, I suppose, but ....  I would miss Linux ...  :sad:

I might just go buy a retail big box store Blu-Ray player, although these can be a PITA (pain in the ...), as well.  My brother's won't work, really won't work, unless it has an Ethernet connection with lots of ports open, allegedly to check for firmware updates  - it wanted to PnP configure his router - LOL, yeah right.  He is techie enough to have it isolated from the rest of his network.  I would have just taken the player back to the store and told them what ports they could open to receive its return.  My son's, however, works just fine without a LAN connection, but if the copyright protection keeps changing, he may one day have to plug it in and let if phone home.

Thanks again.  ):P

---

### Post by lah-ca on 2016-06-08
How To Geek has an interesting article:  [http://www.howtogeek.com/240487/how-to-play-dvds-and-blu-rays-on-linux/](http://www.howtogeek.com/240487/how-to-play-dvds-and-blu-rays-on-linux/)

Their conclusion is more or less in line with TJ's advice above.

How To Geek Quote:

[INDENT]Playing Blu-ray discs [in Linux] is both unreliable and a hassle. [And] Only people who have actual commercial Blu-ray discs in their hands will have to go through this trouble – [ironically] if you’ve ripped the Blu-ray discs on another computer, or downloaded the ripped files, you should be able to play them in VLC just like any other video.[/INDENT]


[INDENT]In an age where you can get Netflix to work on Linux just by downloading Chrome, or use a quick tweak to make Hulu or Amazon Instant Video work, this [getting Blu-Ray disks to play in Linux] is a lot of work to play a legitimate disc.  It’s possible, but you’re better off getting your media in other ways on Linux, or using another device to play Blu-rays if you must use those physical discs.[/INDENT]

[INDENT]
[/INDENT]

---

### Post by T.J. on 2016-06-10
> **lah-ca said:**
> No apologies necessary.  Thank you for your brutal candour.   As Count Floyd might have said, "Very scary, boys and girls!"  I just hope your *glumness* and *hostility* are not the result of having to wear an orange jump suit  at some government Spa.  :wink:


Nope.  Just having one of my BD devices disabled by firmware updates was enough to convince me that Blu-Ray is the most ridiculously bug ridden distribution method ever conceived by the movie studios, solely for the purposes of treating you like a criminal while maximizing their profits - urging or forcing you to repurchase new equipment that you don't need.  HDMI in and of itself is entirely unnecessary, and is promoted for one purpose -  end to end DRM to close the "analog loop" because the studios are afraid you will use it to copy a film.

If anyone wanted to copy a disc, they can easily do so without breaking the DRM, just make a logical copy with a duplicating press.

---

