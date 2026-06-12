---
title: "Legality of Codecs"
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by tpg on 2006-12-17
I am wondering, what exactly are the legal issues surrounding the use of proprietary audio/video codecs (such as windows media) on linux. Is it legal for me to download and use them (in the UK)? Also regarding commerical DVD playback, I know the libdvdcss library is illegal in the US, but is it legal to use in the UK?

---

### Post by pay on 2006-12-17
If you own a copy of Windows then it should be alright to use windows codecs.

---

### Post by PurplePenguin on 2006-12-17
> **tpg said:**
> I am wondering, what exactly are the legal issues surrounding the use of proprietary audio/video codecs (such as windows media) on linux. Is it legal for me to download and use them (in the UK)? Also regarding commerical DVD playback, I know the libdvdcss library is illegal in the US, but is it legal to use in the UK?

I'm Canadian, so I can't help you with UK specific stuff, but we don't have a DCMA here.  Downloading (and it seems that file sharing is legal, too) copyrighted materials is not illegal in Canada.  I am not sure if any other countries in the world have anything as strict as the DCMA.

---

### Post by az on 2006-12-17
> **pay said:**
> If you own a copy of Windows then it should be alright to use windows codecs.

No.

Those codecs are not licenced for use with linux.

---

### Post by az on 2006-12-17
> **tpg said:**
> proprietary audio/video codecs (such as windows media) on linux. Is it legal for me to download and use them (in the UK)? 

AFAIK, you can legally download and use the free (gstreamer and the like) implementations of the codecs.  Those are reverse-engineered and fully GPLed code.  It is not legal for Ubuntu to distribute some of them (like mp3) without paying a royalty to the patent holder, which is why they are not shipped with the distribution.

---

### Post by Azakus on 2006-12-17
I personally don't care about these stupid "illegal because no one will license it for Linux" laws, so you can go to [http://download.videolan.org/pub/libdvdcss/1.2.9/](http://download.videolan.org/pub/libdvdcss/1.2.9/) and either download the i386 deb file, install it from rpm with alien or I'll attach one I made for AMD64 (I haven't tried this yet, so consider yourself a beta tester :-D)
Made with the source code on videolan and checkinstall.

---

### Post by az on 2006-12-17
> **Azakus said:**
> I personally don't care about these stupid "illegal because no one will license it for Linux" laws, 

Actually, if you pay the royalty, or if the company you got your linux distribution from paid it, you can legally use it.

> **Azakus said:**
> 
so you can go to [http://download.videolan.org/pub/libdvdcss/1.2.9/](http://download.videolan.org/pub/libdvdcss/1.2.9/) and either download the i386 deb file, install it from rpm with alien or I'll attach one I made for AMD64 (I haven't tried this yet, so consider yourself a beta tester :-D)
Made with the source code on videolan and checkinstall.

I would suggest the ubuntu wiki RestrictedFormats page.  It is better to use community-supported stuff than something made with checkinstall.

[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

---

### Post by ardvark71 on 2006-12-17
> **azz said:**
> Actually, if you pay the royalty, or if the company you got your linux distribution from paid it, you can legally use it.

I've heard this before, how and who would one pay this royalty to?

Best Regards...

---

### Post by az on 2006-12-17
> **ardvark71 said:**
> I've heard this before, how and who would one pay this royalty to?

Best Regards...

[http://www.dvdcca.org/faq.html](http://www.dvdcca.org/faq.html)

They offer the licence to the distributer.  For the end-user, you would have to pay a third-party distributer (like Linspire) for a licence.  I am unaware of an easy way to do this for Ubuntu.  These distributers tend to bundle the licence with the money you pay for their distribution.

---

### Post by ardvark71 on 2006-12-17
> **azz said:**
> [http://www.dvdcca.org/faq.html](http://www.dvdcca.org/faq.html)

They offer the licence to the distributer.  For the end-user, you would have to pay a third-party distributer (like Linspire) for a licence.  I am unaware of an easy way to do this for Ubuntu.  These distributers tend to bundle the licence with the money you pay for their distribution.

Thanks! 

Is there a similar set up for the W32 codecs (to play mp3's?)

Best Regards...

---

### Post by Azakus on 2006-12-17
By the way, the version in /usr/share/doc/libdvdread3/install-css.sh is 1.2.5, with the current version being 1.2.9_1. Not sure if that will affect the use, but it is something to consider.

---

### Post by ardvark71 on 2006-12-19
> **ardvark71 said:**
> Thanks! 

Is there a similar set up for the W32 codecs (to play mp3's?)

Best Regards...

Anyone?

---

### Post by silvagroup on 2006-12-19
In the US if you have ever bought anything with these technologies ever you have paid the royalties and so have the right to use, play install and copy for backup any and all products so associated, That is per the US Supreme Court.

---

### Post by az on 2006-12-19
> **ardvark71 said:**
> Thanks! 

Is there a similar set up for the W32 codecs (to play mp3's?)

Best Regards...

I would assume that Linspire pay a royalty to Microsoft for distributing and using their software.

---

### Post by az on 2006-12-19
> **silvagroup said:**
> In the US if you have ever bought anything with these technologies ever you have paid the royalties and so have the right to use, play install and copy for backup any and all products so associated, 

Yes, but not to use one part of the software in another operating system.

The last time I waded through the licencing agreements that cover those codecs, it was expressedly forbidden to use them with any software other than Windows.

---

### Post by r4ik on 2006-12-19
> **ardvark71 said:**
> Anyone?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Good luck !

---

### Post by silvagroup on 2006-12-19
> I would assume that Linspire pay a royalty to Microsoft for distributing and using their software You assume correctly, and so therefore since the user paid Linspire back for those the user now owns them and is free to use them. If you have ever owned anything that uses dvd/cd, cd/dvd, mpeg, avi, css, blah, blah, blah, you have already bought the rights to the technology. That's why the DRM technology is becoming so popular with the corporate world, they want to stick you for everytime you use their product. So that they can have all your money.
DRM will hold the world ransom in very many ways. I hope we all wake up to that before it's to late. However looking at history, were in deep trouble with DRM.](*,)

---

### Post by mrunion on 2006-12-19
@silvagroup

So true!  Wake up people!

---

### Post by ardvark71 on 2006-12-19
> **azz said:**
> Yes, but not to use one part of the software in another operating system.

The last time I waded through the licencing agreements that cover those codecs, it was expressedly forbidden to use them with any software other than Windows.

How does this work out with the Supreme Court decision mentioned by Silvagroup? Does their descision trump that of Microsoft?

Best Regards....

---

### Post by ardvark71 on 2006-12-20
Bumpidee doo daa...

---

### Post by az on 2006-12-20
Is there a licence distributed with the w32codecs package?

As far as it being legal to use if you own a copy of windows, I know that is a popular phrase, but I don't think it has any legal foundation.  I know a lot of people use that to justify using the w32codecs on linux.  Again, read the licence under which the actual codec is distributed.

As far as saying that you have already paid a royalty, I really don't know what is meant by that.  Does that make it okay to use a free and open source implementation of a codec that would require you pay a royalty or does that mean that you have the right to steal the codec (by using a proprietary implementation)?  I would have to read the actual text of whatever Supreme Court decision.  I certainly have never heard that it is legal.

---

### Post by ardvark71 on 2006-12-20
> **azz said:**
> Is there a licence distributed with the w32codecs package?

As far as it being legal to use if you own a copy of windows, I know that is a popular phrase, but I don't think it has any legal foundation.  I know a lot of people use that to justify using the w32codecs on linux.  Again, read the licence under which the actual codec is distributed.

As far as saying that you have already paid a royalty, I really don't know what is meant by that.  Does that make it okay to use a free and open source implementation of a codec that would require you pay a royalty or does that mean that you have the right to steal the codec (by using a proprietary implementation)?  I would have to read the actual text of whatever Supreme Court decision.  I certainly have never heard that it is legal.

Thank you, azz. I'm just trying to see if there are any legal openings, courtesy of the U.S. court system, that Microsoft and the Recording Industry are trying to keep me from discovering so that I can legally play my stuff.

And really, all of this is such a load of nonsense, to put it nicely. I PAID Walmart for the music files that I downloaded, I should be able to use whatever codec in whatever operating system to play the music I PAID for the right to have and listen to! 

It really stinks that people are punished for trying to do this the right and legal way, yet it's no problem whatsoever to log into Limewire or some file sharing program and get whatever you want. :mad: 

Yes, this DMCA/DRM nonsense has gotta go. ](*,) 

Best Regards...

---

### Post by az on 2006-12-20
> **ardvark71 said:**
> Thank you, azz. I'm just trying to see if there are any legal openings, courtesy of the U.S. court system, that Microsoft and the Recording Industry are trying to keep me from discovering so that I can legally play my stuff.

You're fine if you use the gstreamer codecs.

> **ardvark71 said:**
> 
Yes, this DMCA/DRM nonsense has gotta go. ](*,) 

Best Regards...

[http://www.defectivebydesign.org/en/node](http://www.defectivebydesign.org/en/node)

Sign up, join, donate, participate...

---

### Post by Azakus on 2006-12-20
From what I've heard, Amazon.com is planning on opening a DRM-Free music store.

---

### Post by silvagroup on 2006-12-20
This issue goes way back to the developers pf dvdcrypt, they took the issue to the supreme court, and won those rights for the rest of us. At the sake of sinking all their finance into the fight and then having to dissolve the company because they did not  have the finances that the media giants and Microsoft had to fight against them.
The latest thing with microsoft is to insure that you only use it for one machine one install, and whenever you agree to their licensing you have committed to that specific contract with Microsoft and now your stuck. You just signed up to have them intrude into your use of your system and committed your self to using the product on one system, and to make sure of that they stamp it with a code to make sure you only use it on one. They can then assure that you can not use it else where.
The codecs are not strictly OS based so they are licensed differently.
Of course they are not or are the media giants going to tell you all these wonderful things, they want to keep you dumb. A well educated consumer will end up costing them. After all isn't better to sell you a new movie to replace the scratched one that no longer plays, as opposed to letting you know you can back it up and using the backups, or that you already paid me for this you don't have to do it again. 
How many millions are they making from the stupidity of the consumer.
In case you haven't realized this, not every body is in world has your wellfare as their top priority, especially if you have a bank account.
As for me I have better uses for my money than making those folks richer, if you like giving your money away to others would please, instead of making Microsoft richer and the media folks richer give to those who really need it. I have several suggestions and in the overall picture would make the world a whole lot better for us all.:-k

---

### Post by az on 2006-12-20
> **silvagroup said:**
> This issue goes way back to the developers pf dvdcrypt, they took the issue to the supreme court, and won those rights for the rest of us. At the sake of sinking all their finance into the fight and then having to dissolve the company because they did not  have the finances that the media giants and Microsoft had to fight against them.

You still can not legally decrypt css-encrypted dvds without a licence.


[http://en.wikipedia.org/wiki/DeCSS](http://en.wikipedia.org/wiki/DeCSS)

---

### Post by ardvark71 on 2006-12-20
> **silvagroup said:**
> 
In case you haven't realized this, not every body is in world has your wellfare as their top priority, especially if you have a bank account.


Oh, believe me, I have learned that lesson VERY well....and the fact that I am writing this using Opera from an Ubuntu system is one result of that. ;) 

Best Regards...

---

### Post by silvagroup on 2006-12-20
Many American legal experts believe that under United States' Federal law making a backup copy of a DVD-Video or an audio CD by a consumer is legal. Some feel this provision of US law conflicts with the Digital Millennium Copyright Act prohibition of so-called "circumvention measures" of copy protections. In the noted "321" case, Federal District Judge Susan Illston, of the Northern District of California, ruled that the backup copies made with software such as DVD Decrypter are in fact legal but that distribution of the software used to make them is illegal.  
[http://news.com.com/html/ne/Special/Legal/brief.pdf]("http://news.com.com/html/ne/Special/Legal/brief.pdf")
As of the date of this revision, neither the US Supreme Court nor the US Congress has taken definitive action on the matter.

---

### Post by 1peter318 on 2007-05-19
> You're fine if you use the gstreamer codecs.

I do not know if i can open up this old thread, but i too want to be legal in regards to this. With my 3  old Windows pc's and this one dual bootting with Vista basic (which is why i now need Ubuntu) i can play and encode most any kind of format  (with k-lite codec pack and freeware apps), even flv files in windows media, but i cannot even come close with Ubuntu (to my suprise), But i cannot see how i qualify to use the gstreamer codecs, such for .wmv, as i live in the US, and have no license that i know of, and am not using it for research purposes. Regardless of the excesive restrictions of some media companies , i want to be legal. Please advice.

---

### Post by silvagroup on 2007-05-20
Well to recap, for US folks as per the Supreme Court. (Follow the link in prior post to see it yourself.)

If you have currently anything which plays any of the formats you mentioned or if you have bought any of these formats, you have purchased the license. That gives you the rights to play any of the "protected" formats and not only that but you have the right to back up your media. That is to back up, not to reproduce and or to re-distribute, but to back up. Essentially that's the law.
That's it in a nut shell.:popcorn:

---

### Post by 1peter318 on 2007-05-21
Thanks, and i hope that is true. If we had a legal encoder that could convert everything to OGG then we would not have to worry. But reading this whole thread  it seems AZ disagrees with you? and that is way i asked.

---

### Post by silvagroup on 2007-05-22
1peter318 for clarification AZ is right in that the software to decrypt is illegal if not licensed. 
So all cd/dvd players must have a license to decrypt the media legally, that's the law.

 What I stated was that you could back up and play what ever format (technology) you have legally purchased. You have paid for the license to use the technology in the media, and as per the decision this also give you the right to back it up.

The supreme court ruling specifically states the the selling, or distribution of the decryption software must also be licensed. Which as stated earlier is licensed by the manufacturers of the equipment.

Now there are some very obvious and glaring incongruities in the Supreme Court decision. That I will leave for you to think about.

But the ultimate effect was achieved by the decision, in that the perpetrators who compromised the CSS went bankrupt fighting the case and were shutdown. This decision also made it very very clear that the use of decryption software MUST be licensed. 
So major manufacturers have to get licensed if they legally wan to play the protected media in the equipment you buy from them. :popcorn:

Also check your cd's, because the majority of cd's that I buy also have the ogg format on them.

Again  there is a link to the decision so you can check it out yourself.

---

### Post by 1peter318 on 2007-05-23
Thanks again. I am not even looking to back up DRM media, mostly just to be able to play it. Automatix2  put this big warning on dwnldg, codecs, but i did get the VLC player which works. However, i was looking to be able to copy DVD which i have permission to copy (Glimpse into eternity at [http://www.spiritlessons.com](http://www.spiritlessons.com)) as well as to make dvd's from other video's i have permission to do, all which i can do (with freeware and some work) on Windows Vista basic (so far). 

Out of curiosity, where is the link to the court case?  Thanks for your help.

---

### Post by silvagroup on 2007-05-23
Warning - Read in bed or soft chair.
[http://news.com.com/html/ne/Special/Legal/brief.pdf](http://news.com.com/html/ne/Special/Legal/brief.pdf)

As as far as DRM treat it as a leper, and stay away from it totally. The less people use it the less it will pervade our lives. Read these links on DRM and tell everyone you know. All my friends have been informed as well as their friends, etc.
 [http://www.gnu.org/philosophy/can-you-trust.html](http://www.gnu.org/philosophy/can-you-trust.html)
[http://www.gnu.org/philosophy/opposing-drm.html](http://www.gnu.org/philosophy/opposing-drm.html)
[http://polishlinux.org/gnu/drm-vista-and-your-rights](http://polishlinux.org/gnu/drm-vista-and-your-rights)
A google will bring you up even more information on DRM.

---

### Post by stchman on 2007-05-23
> **tpg said:**
> I am wondering, what exactly are the legal issues surrounding the use of proprietary audio/video codecs (such as windows media) on linux. Is it legal for me to download and use them (in the UK)? Also regarding commerical DVD playback, I know the libdvdcss library is illegal in the US, but is it legal to use in the UK?

From everything I have read Ubuntu cannot ship install these codecs with the distribution.  I can say that as an individual you are allowed to use these codecs for listening/watching media you purchased.  If you bought a Hollywood DVD then you are entitled to watch it.  Since nearly every studio encrypts their movies then you need a CSS decryption method.  If you bought a CD then you are entitled to make an mp3 of it so you can listen to it on your ipod or car stereo.  I wish all the devices out there would include OGG support.

If you use the codecs to pirate/steal/sell the you are in violation of the law.  Believe me that the RIAA, MPAA and other groups are not after people that BUY their media.  They are after the people that steal music/movies.

---

### Post by silvagroup on 2007-05-23
stchman you have correctly put it all a in a nut shell.:D

---

