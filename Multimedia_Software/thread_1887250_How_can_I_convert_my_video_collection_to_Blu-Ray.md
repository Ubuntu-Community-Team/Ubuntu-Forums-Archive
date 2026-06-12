---
title: "How can I convert my video collection to Blu-Ray?"
date: 2011-11-26
forum: Multimedia Software
---

### Post by rmjohnson144 on 2011-11-26
My sister just upgraded to HDTV and Blu-Ray and wants me to convert all of her videos to Blu-Ray disks.

Can anyone point me to a program that can do this with minimal setup?

Videos are in all different formats from AVI to MKV to MPEG4, etc.

This is over a decade of videos on her computer.

In windows I was able to conert some videos to AVI, but they wouldn't burn to a Blu-Ray format.  they just copied the AVI directly to Blu-RAY disk.  and others wanted $100+ dollars to burn videos to Blu-RAY and another $100+ to convert videos to Blu-Ray format.

Thanks for any help
-=Mark=-

---

### Post by dniMretsaM on 2011-11-26
I think it's as easy as making an ISO and burning it to a blu-ray disk. I have no experience with blu-rays, so it might not be that simple. I Googled around and couldn't find any concrete information, so this is just my best guess.

---

### Post by Basher101 on 2011-11-26
not sure if by simply re-burning the data from one media to another will increase the quality to HD...

---

### Post by dniMretsaM on 2011-11-26
> **Basher101 said:**
> not sure if by simply re-burning the data from one media to another will increase the quality to HD...

No, it won't. But she may just want them on blu-ray disks so she doesn't have to keep a DVD player around.

---

### Post by MartyBuntu on 2011-11-27
Most Blu-ray players that I know of also play DVD disks.

Converting avi's to Blu-ray is pointless and a waste of money.
There is no increase in quality.

---

### Post by underquark on 2011-11-27
A lot of DVD players play Div-X as well.  Blank CDs are cheaper than DVDs are cheaper than Blu-Ray discs.

---

### Post by SeijiSensei on 2011-11-27
The only reason I can see for archiving existing content on Blu-ray is to take advantage of its larger storage capacity.  As others have said, burning to BD won't change the existing quality of the encode.

That said, you could consider simply making data disks if the Blu-ray player supports a common format like MP4 or DivX/XviD.  (I'd prefer Matroska myself, but it's hard to find commercial players that support it.)  MP4 with H.264 video and AAC or AC3 audio is probably the best choice for a single format that could encompass the variety of material your sister apparently has.

You might take a look at [ImgBurn]("http://www.imgburn.com/"), a Windows program that apparently will also run under Wine on Linux.  The website states that, "You can use it to build DVD Video discs (from a VIDEO_TS folder), HD DVD Video discs (from a HVDVD_TS folder) and Blu-ray Video discs (from a BDAV / BDMV folder) with ease."

How one builds a BDAV/BDMV folder in Linux is outside my ken.

---

### Post by rmjohnson144 on 2011-11-27
> **SeijiSensei said:**
> The only reason I can see for archiving existing content on Blu-ray is to take advantage of its larger storage capacity.  As others have said, burning to BD won't change the existing quality of the encode.

Yes,this is my goal.  I just want to get more movies on one disc more than anything.  If one format will make the files smaller would be even better.

> That said, you could consider simply making data disks if the Blu-ray player supports a common format like MP4 or DivX/XviD.  (I'd prefer Matroska myself, but it's hard to find commercial players that support it.)  MP4 with H.264 video and AAC or AC3 audio is probably the best choice for a single format that could encompass the variety of material your sister apparently has.

  I was thinking of converting to h.264 mostly for the hardware encoding of most hardware.

> You might take a look at [ImgBurn]("http://www.imgburn.com/"), a Windows program that apparently will also run under Wine on Linux.  The website states that, "You can use it to build DVD Video discs (from a VIDEO_TS folder), HD DVD Video discs (from a HVDVD_TS folder) and Blu-ray Video discs (from a BDAV / BDMV folder) with ease."

imgburnwas my guess, but it wasn't drag n drop like img files.  maybe I need a converter to make a img file first?  imgburn looks like it has a lot of features, but it looks like a lot of hard work to get working with Blu-ray.

> How one builds a BDAV/BDMV folder in Linux is outside my ken.

This seems my biggest challenge.  I just can't find a program that converts to this ts_video style like my DVDs have on a blu-ray.  not sure if blu-ray even uses the same format.

I guess I'm going to have to get my hands dirty and just do some trial and error to see if I can get this figured out.  hopefully I can figure out a simple way to convert all these videos.

Thanks for everyone's advice
-=Mark=-

---

### Post by inobe on 2011-11-27
> **rmjohnson144 said:**
> 
This seems my biggest challenge.  I just can't find a program that converts to this ts_video style like my DVDs have on a blu-ray.  not sure if blu-ray even uses the same format.

I guess I'm going to have to get my hands dirty and just do some trial and error to see if I can get this figured out.  hopefully I can figure out a simple way to convert all these videos.

Thanks for everyone's advice
-=Mark=-

please share your trials and errors:)

---

### Post by SeijiSensei on 2011-11-28
> **rmjohnson144 said:**
> I was thinking of converting to h.264 mostly for the hardware encoding of most hardware.

The choice of "[container]("http://en.wikipedia.org/wiki/Comparison_of_container_formats")" is equally important if you want to ensure wide compatability.  As I said, I'd prefer to use Matroska (MKV), but it's largely snubbed by commercial player manufacturers.  Sony pushed hard for the [MP4]("http://en.wikipedia.org/wiki/MPEG-4_Part_14") container so most players support it natively.

---

### Post by Johnny Buffalkill on 2011-11-28
Openshot is supposed to be able to author blu ray file structure.  I haven't tried it myself so I can't report how well it works though.  Once you have made the blu ray file structure, you could then burn it to blu ray media with another application, such as ImgBurn.  I think there are linux apps that can burn blu ray media, but I'm not familiar with them and ImgBurn is a pretty good program.  

If you really want to be daring, something you could try, since apparently this is all standard def, would be to author a huge DVD  (50GB, ~10hours), but then burn it onto blu ray media.  Since blu ray players can read DVDs it might work.  The questions are whether it would read DVD from blu ray media, and whether DVD authoring software would let you create that large of a DVD.

---

### Post by rmjohnson144 on 2011-11-28
> **SeijiSensei said:**
> The choice of "[container]("http://en.wikipedia.org/wiki/Comparison_of_container_formats")" is equally important if you want to ensure wide compatability.  As I said, I'd prefer to use Matroska (MKV), but it's largely snubbed by commercial player manufacturers.  Sony pushed hard for the [MP4]("http://en.wikipedia.org/wiki/MPEG-4_Part_14") container so most players support it natively.

ah, I see another thing I was confused on, I thought h.264 was all I needed.  But the encoding programs need to support it.  so would I need to convert all videos to MP4 first?

I found a free windows program to do some transcoding and it turns my current MP4's and makes DVD looking folders.  It must be blu-ray as it list a BDMV and Certificate and a few other DVD looking folders.  I guess I just copy the folders to a Blu-ray disk and it should play?

right now I can go to the BDMV/STREAM folder and play the movies from there.

It took me a while to find what I needed.  It turns out I needed blu-ray "Authoring" software, not burning software.

@Johnny Buffalkill

Thanks for the tip.  I'll try openshot and see how it goes in Ubuntu.

---

### Post by SeijiSensei on 2011-11-28
> **rmjohnson144 said:**
> ah, I see another thing I was confused on, I thought h.264 was all I needed.  But the encoding programs need to support it.  so would I need to convert all videos to MP4 first?

If you're comfortable using the command line, then mencoder would do the conversion and put the result in the mp4 container in one step.  Many of the GUI-based converters on both Windows and Linux use mencoder as the actual conversion engine.  A good starting point is this [guide]("http://en.gentoo-wiki.com/wiki/Mencoder"); for more details, you can read the [manual]("http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html").

---

