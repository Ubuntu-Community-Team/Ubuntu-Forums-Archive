---
title: "[SOLVED] Is it preferable to convert mp3 to ogg or flac?+some questions about quality"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by meindian523 on 2008-01-03
I plan to convert all my mp3 collection to either
1]ogg
2]flac
3]mp3 to ogg via flac

My questions:

1]I've searched high and low for a good conversion program,tried Switch from NCH Software via wine,didn't like it,would prefer a native converter,could someone recommend some suitable applications?
My currently installed audio apps are:
Amarok
VLC
Are there any plugins for either of these which can do the job?

2]I know that both mp3 and ogg are lossy formats while flac is lossless,my question is which would be better,to convert to ogg or flac?

3]I had an idea that I would convert mp3 to FLAC so I would have an exact copy before I convert to ogg,my question is would it make any difference to quality if I convert directly from mp3 to ogg or whether I convert via FLAC?

I also know that FLAC takes up more space because it stores more information,I presently have a approx 1.4 GB mp3 collection and I have 6 GB of free space on my /home partition ,is it possible(even by a long shot) that my collection could expand to fill up that entire 6 GB if I decide to convert to FLAC?

PS:I'm not a big audio buff BTW,that is I don't own Bose headphones,etc,but I would like to not feel much difference(ideally zero) between what I hear now and what I would hear after conversion)

---

### Post by shirilover on 2008-01-03
It is not preferable to convert a lossy format into any other format.
If you intend to do this from the original sources, either flac or vorbis would be fine.
Otherwise, I would stick with what you already have.

---

### Post by milton1 on 2008-01-03
If you absolutely must convert, convert to flac. Shirilover is right; converting from a lossy algorithm almost never has good results. Converting from one lossy format to another lossy format will compound the corruption of the original data. If you can play your mp3's, keep them as mp3's and simply switch to your preferred format for any new rips.

---

### Post by disturbed1 on 2008-01-03
Neither. If you convert your mp3 files to anything other than an uncompressed format, or a lossless format, your sound quality will tank. 6 gig isn't enough space for FLAC, if you figure the average compression ratio of mp3 is 192kb fuzzy math tells me it's ~11gig uncompressed. FLAC may be able to shave 30% off that. At the least, your collection converted to FLAC would take up ~7gig.

You should re-rip your collection to ogg format, or just install mp3 decoders, and choose ogg as your future format. If you are worried about a ***legal*** mp3 codec, install Fluendo's gstreamer codec, or use Real Player.

If you **_must_** convert your collection to ogg format try these 2 apps available in synaptic. dir2ogg or soundconverter. Soundconverter being my choice. Both support id3 tags.

---

### Post by meindian523 on 2008-01-03
It's not a must-do,but I would prefer to get rid of my proprietary leanings + I want to use MusicBrainz to make sure my tags are all proper and I'm not addressing a track from one album as part of another album.

Also,I don't have any ORIGINAL sources,what I have is what I received from friends and downloaded off the Net(that's piracy,I know)

Also,there's been no response regarding the ogg via FLAC route,or is that a no-no too?

---

### Post by meindian523 on 2008-01-03
One more question I would like to ask is how can I get Amarok to allow me to edit m4a ID tags?It plays fine,but I can't change the album/artist information and I don't really like that since the rest of my collection is neatly tagged and organized.

---

### Post by disturbed1 on 2008-01-03
> **meindian523 said:**
> 

Also,there's been no response regarding the ogg via FLAC route,or is that a no-no too?

No reason to. When you encode your mp3s to any other format, the first step is to decode it. So you would be going mp3 - wav - flac - ogg. When you could just go mp3 - wav - ogg.

---

### Post by meindian523 on 2008-01-03
Oh,so conversion is better avoided if I want to retain quality.

Any ideas about Amarok editing m4a ID3 tags?

---

### Post by disturbed1 on 2008-01-03
Sorry I've never used Amarok, nor have I ever even seen a .m4a file :(

I did a quick search in synaptic for "m4a id3" and "m4a tag". Didn't see anything that stuck out.

Easytag states it supports mp4/aac in the about screen, and according to the website. Give that a try.

---

### Post by meindian523 on 2008-01-04
I searched Synaptic too,and got no results,that's why I asked here.Isn't EasyTag included in the repos?

---

### Post by meindian523 on 2008-01-04
I found this but it's for Gentoo,can someone guide me what would be the similar procedure for Ubuntu?

[Gentoo  tutorial to playing and editing m4a tags in Amarok]("http://www.cydeweys.com/blog/2007/11/21/gentoo-linux-tutorial-playing-m4a-song-files-in-amarok/")

---

### Post by disturbed1 on 2008-01-04
> **meindian523 said:**
> I searched Synaptic too,and got no results,that's why I asked here.Isn't EasyTag included in the repos?

Easytag is in synaptic, it's a GTK2+ app.

The genntoo page is basically telling you to compile the app with m4a support.

There's gtkpod-aac as well

> 
manage songs and playlists on an Apple iPod
gtkpod is a platform independent GUI for Apple's iPod using GTK2. It
allows you to upload songs and playlists to your iPod. It supports ID3
tag editing, multiple charsets for ID3 tags, detects duplicate songs,
allows offline modification of the database with later synchronisation,
and more.

This version has aac/mp4-support.

 Homepage: [http://www.gtkpod.org](http://www.gtkpod.org)

---

### Post by meindian523 on 2008-01-04
You are mistaken if you believe I own a Pod,I don't!

I got the meaning of the page saying that we should compile amarok with m4a tag editing support,but that's for Gentoo,I would just want to know whether the steps would be same for Ubuntu too.

---

### Post by disturbed1 on 2008-01-05
> **meindian523 said:**
> You are mistaken if you believe I own a Pod,I don't!

I got the meaning of the page saying that we should compile amarok with m4a tag editing support,but that's for Gentoo,I would just want to know whether the steps would be same for Ubuntu too.

GTKPod-aac is just a music player that has the ability to edit m4a tags. It also adds the ability to interface with IPods.

---

### Post by meindian523 on 2008-01-07
Well,I know that,what I mean to say is that I just want a m4a tag editing capability without having to install another player.

---

### Post by meindian523 on 2008-01-08
bump

---

### Post by eye208 on 2008-01-08
(x) Do not convert.

---

### Post by meindian523 on 2008-01-08
For all people who came in late,or responded to the bump,here's a summary:

I decided[COLOR="Red"]** not **[/COLOR]to convert my collection on the advice of Shirilover,disturbed1 and others.My problem right now is that I want to edit tags of some m4a files I have.Amarok has this capability but it's not compiled in by default according to [this]("http://www.cydeweys.com/blog/2007/11/21/gentoo-linux-tutorial-playing-m4a-song-files-in-amarok") page,only problem is the tutorial is for Gentoo and I have no idea how to adapt them for Ubuntu.Could someone help me out with this re-compile of amaroK?

---

### Post by meindian523 on 2008-01-09
I've searched for the amarok development files in Synaptic but couldn't find it.Any ideas?

---

### Post by meindian523 on 2008-01-09
I think I will post a new thread about this since peole wouldn't know that the topic of the thread has changed.

---

### Post by tayran on 2008-01-10
I gradually convert all my mp3 collection to m4a (HE-AAC) in 80kbs. This format is over CD quality according to [ http://www.codingtechnologies.com/]("http://www.codingtechnologies.com/"). I have also tried 64kbps which is said to be equivalent of 128 kbps mp3 but i had problems with some of my files. In 80 bit i cannot feel any difference with the original mp3 file. My mp3 files are at least 160 or 192 so there isnt much loss of information during conversion.
I don"t recommend faad for m4a conversion. I use easy-çd extractor via wine instead. Believe me there is a huge difference.

---

