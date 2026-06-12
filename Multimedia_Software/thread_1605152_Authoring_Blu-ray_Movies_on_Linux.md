---
title: "Authoring Blu-ray Movies on Linux"
date: 2010-10-24
forum: Multimedia Software
---

### Post by kylemallory on 2010-10-24
I'm a independent filmmaker who also is a die-hard Ubuntu fan... After spending the summer making a short film, I needed to author Blu-ray discs for festival screenings, so I started digging around and trying stuff out until I got it working.

I thought I would share my results for others who might find it of value.  I have a full write-up including a bit of a shell script that I whipped up today to ease the burden of it all.

[http://irishjesus.wordpress.com/2010/10/17/blu-ray-movie-authoring-in-linux/]("http://irishjesus.wordpress.com/2010/10/17/blu-ray-movie-authoring-in-linux/")

I've also included the script in this post (since I don't host files on my blog).

Enjoy, and feel free to comment or critique.

--Kyle

---

### Post by DeeKay64 on 2011-05-18
Forget this script. It will produce Blurays that only play on very few "don't care at all about the spec, I'll play anything" Bluray-Players, and most certainly not on the most widespread Bluray-player of all, the PS3. You don't use the proper BD/AVCHD-compatible x264 settings for encoding the stream and also don't burn the disc as UDF 2.5 (which OSS-tools, *even 8 years after it was speficied **still cannot do***, so you have to use Nero4Linux). Check the comments, the proper way, tested on countless Bluray-players to work perfectly, is described in there!

---

### Post by kylemallory on 2011-05-18
You are correct.  Unfortunately, I still have yet to find a detailed description anywhere else that completely describes how to author a Blu-ray Video disc, using linux tools, that works even partially.  Also, your timing is apropos, as I had just updated the article this morning to reflect the information conveyed in the comments.

The real crime here is, exactly as you mentioned, the state (or lack thereof) of UDF 2.5/2.6 support in the udftools package.  This is a real shame, and should be made a priority by those that do so...

Cheers--

---

### Post by theirishfozz on 2011-10-20
Apparently linux 2.6 now has UDF 2.6 support, has anyone mad any progress on bluray authoring?

---

### Post by kylemallory on 2011-11-11
Still no direct support for creating UDF 2.6 filesystems... But, I recently purchased Nero Linux for $20, and authored a Bluray using the same steps above to generate the BDMV structure, and then used Nero for the UDF stuff. It worked great, and has success on a number of Bluray players at the local Best Buy, including a PS3.  So, it is possible, just not entirely free, yet.

---

### Post by 1clue on 2011-11-11
It's an interesting project anyway.  I have a BD burner in my Linux box at home, and have wondered about this for some time.  At the moment it's just a big backup device.

As far as I'm concerned this thread is a big help.  I'm not one of the people who drink the Richard Stallman kool-aid.  There is plenty of room in my computer for free and non-free software to coexist and cooperate.

---

### Post by ricardisimo on 2012-01-20
> **1clue said:**
> It's an interesting project anyway.  I have a BD burner in my Linux box at home, and have wondered about this for some time.  At the moment it's just a big backup device.

As far as I'm concerned this thread is a big help.  I'm not one of the people who drink the Richard Stallman kool-aid.  There is plenty of room in my computer for free and non-free software to coexist and cooperate.

I doubt Stallman's issue is with Blu-ray so much as it is with DRM on Blu-ray. There are industry issues that are serious, and he's 100% right on those issues. That said, BRD are great for storage, as you no doubt know, and a filmmaker like the OP need not use DRM on his product.

Voila. No Kool-Aid.

I would love to render a BRD as easily as I currently do with DVDs. I coordinate and project festivals here in LA, and putting shorts programs together onto one disc from a multitude of files and formats is a boon for festival programmers. To be able to do this in HD is what I now need.

---

### Post by 1clue on 2012-01-21
I'm either a minority on this issue with regards to other Linux users, or the other ones are smart enough to shut up about it.

I'm not opposed to DRM.  That's up to the producer of the content IMO.

If there were a commercial Linux app which plays BD+DRM discs in the way the creators of DRM intended and did so effortlessly, then I would buy it.  I don't want to duplicate a BD disk, I only want to play it.

Again as you said, the OP doesn't seem to care either, so this is just off-topic noise on the thread.

---

### Post by two4two on 2012-11-07
OK, it's a year later.  Any progress on Blu-ray authoring for linux?  Or on playing Blu-ray video discs?  I have numerous videos that I produced in HD and would like to put on Blu-ray from Linux.  So far I've had to downgrade them to SD and author on regular DVD, if I want to use Linux.  If I want to put them on Blu-ray I need Windows.  So sad. :( 

Also, it is very difficult to even play the Blu-rays on linux.  I don't use DRM for the authoring and so playing them SHOULD be do-able on Linux.  But alas, it is not easy.  My Ubuntu Natty has a package that tries to do it but can't exactly do it.  It can't do the menues, etc, and the player freezes eventually.  :mad:  I am talking about playing my non-DRM discs -- not bought ones -- although it would be nice to play bought ones too  :)  .

---

### Post by BicyclerBoy on 2012-11-07
All official licenced BD players must use DRM for native BD video formats.

Generating the required AACS nonsense on write-able media could be a problem.
The write-able media has a pre-written lead-in area.

This does not apply to BD data disks with mkv files etc..

---

### Post by wildmanne39 on 2012-11-07
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

