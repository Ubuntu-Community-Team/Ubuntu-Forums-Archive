---
title: "h264 (x264) vs Theora"
date: 2010-01-11
forum: Multimedia Software
---

### Post by Emanuele_Z on 2010-01-11
Hi all,

Today I was testing some HD (720p, 1080p) video compression with:
- h264
- Theora
A lot of people are boasting about Theora effectiveness, so I compressed some short HD videos with the same bitrate with above codecs and the results of Theora (1.1) were a bit appalling compared to h264.
I've used HandBrake 0.9.4, both codecs with 2pass encoding and same bitrate.
Apart that libtheora was monothread while x264 is multithread, really one could tell the difference between the two videos.
Am I the only one experiencing this?
Which codec do you use to save your HD videos?

I know h264 is patent protected and in US is possibly illegal to use it without paying a fee to someone, but Theora is a bit behind.
What do you think?

Cheers,

---

### Post by patrickaupperle on 2010-01-18
From what I have seen (around the internet), theora seems pretty close to h264. Could you post the videos, supposing it is legal to do so and they are not too big, for me to compare? Are you sure handbrake is using libtheora 1.1? I am extremely interested in this comparison.

---

### Post by JohnAStebbins on 2010-01-18
> From what I have seen (around the internet), theora seems pretty close to h264.
The theora zealots would like you to think that. But I've never seen the claim backed up with real data. Every fair comparison I've seen places x264 far ahead of theora.  Here's one of my favorite comparisons.
[http://saintdevelopment.com/media/](http://saintdevelopment.com/media/)

---

### Post by VertexPusher on 2010-01-19
Theora is nowhere near x264. The only reason why people use it at all is because they believe it's not covered by patents.

---

### Post by patrickaupperle on 2010-01-19
> **VertexPusher said:**
> Theora is nowhere near x264. The only reason why people use it at all is because they **believe** it's not covered by patents.

It is not covered by any patents, though, is it?

---

### Post by VertexPusher on 2010-01-19
> **patrickaupperle said:**
> It is not covered by any patents, though, is it?
That's the problem with patents: There is no way to tell.

The only way to be sure is to wait until the technology is older than any patent that could possibly cover it. If you are concerned about patents, use MPEG-1.

---

### Post by patrickaupperle on 2010-01-19
That is interesting. I think (this is without much backing) that Theora is safe, though. Isn't the whole point behind it that there are no patents? I just finished encoding Harry Potter and the Half Blood prince in h264 and Theora. The Theora file, despite my settings, came out 50 megs smaller (658 to 708). Unfortunately, the quality difference is pretty large. What are the restrictions on h.264? Could I use it to stream over the net without paying? If I couldn't, is that not enough reason to use theora for many purposes? I think that we will probably see another improvement to theora soon, we just have to hope that it is enough to make it more comparable.

---

### Post by patrickaupperle on 2010-01-19
I just did another similar test, this one is more promising for Theora. I downloaded a video off of youtube (1080p). I then ran it through ffmpeg2theora and mencoder to resize to 720 vertical lines. I see no quality difference between the two output files. :D
Here are the files if you want to compare (sorry, I have low upload speeds) :
Source: 
[http://74.192.55.127:1024/4N2YWRJ-ppo.mp4](http://74.192.55.127:1024/4N2YWRJ-ppo.mp4)
Encoded to mp4:
[http://74.192.55.127:1024/4N2YNew.mp4](http://74.192.55.127:1024/4N2YNew.mp4)
Encoded to theora:
[http://74.192.55.127:1024/4N2YWRJ-ppo.ogv](http://74.192.55.127:1024/4N2YWRJ-ppo.ogv)
Tell me if my server works, I just set it up yesterday.

Edit:
The commands I used where:
for the mp4: mencoder 4N2YWRJ-ppo.mp4 -vf scale=1732:720 -ovc x264 -oac faac -o 4N2YNew.mp4
for the ogv: ffmpeg2theora 4N2YWRJ-ppo.mp4 -y 720
I hope those where the proper commands to use. I really had no idea what oac to pick (though, I figured it was unimportant).

---

### Post by VertexPusher on 2010-01-20
> **patrickaupperle said:**
> That is interesting. I think (this is without much backing) that Theora is safe, though. Isn't the whole point behind it that there are no patents?
You can't prove that there are no patents that cover Theora. Nobody can.

That is exactly why the EFF and others fight software patents: You can prove the presence of patents but not their absence. Patent trolls have turned this into a profitable business: They aquire patents which vaguely describe some fundamental technology (e.g. browser plugins, see Eolas vs. the rest of the world), then they wait until the technology becomes popular. Finally they send everyone the bill or take them to court.

Theora isn't safe. In fact it is more unsafe than H.264 whose patent holders are well known. If you need something safe and free, MPEG-1 is your only option because its patents are expired.

---

### Post by patrickaupperle on 2010-01-20
> **VertexPusher said:**
> You can't prove that there are no patents that cover Theora. Nobody can.

That is exactly why the EFF and others fight software patents: You can prove the presence of patents but not their absence. Patent trolls have turned this into a profitable business: They aquire patents which vaguely describe some fundamental technology (e.g. browser plugins, see Eolas vs. the rest of the world), then they wait until the technology becomes popular. Finally they send everyone the bill or take them to court.

Theora isn't safe. In fact it is more unsafe than H.264 whose patent holders are well known. If you need something safe and free, MPEG-1 is your only option because its patents are expired.
True, we do not know, I did not suggest otherwise. I simply am guessing (something we can always do, regardless of situation), without any backing nor a great understanding of the situation, that Theora is safe. Back to the original questions, though. Is h264 really far superior? Did I use the best commands above? I do not notice a difference between those two files. One, the h264, is 4/5 the size, but does that make a huge difference? Is the comparison fair? Do results on a single file matter at all?

---

### Post by VertexPusher on 2010-01-21
> **patrickaupperle said:**
> True, we do not know, I did not suggest otherwise. I simply am guessing (something we can always do, regardless of situation), without any backing nor a great understanding of the situation, that Theora is safe.
Yes, and I said the only reason why people use Theora is because they *believe* it's safe.

> Back to the original questions, though. Is h264 really far superior?
Yes. Theora is somewhere on the level of Xvid, a MPEG-4 ASP codec.

> I do not notice a difference between those two files.
Upload the files, then I'll point out the differences for you. I've encoded a lot of video, and I ran lots of tests with Theora too.

> One, the h264, is 4/5 the size, but does that make a huge difference?
Yes, 20% reduction is a huge difference, especially when you are trying to put a feature film on a single CD. With x264 you can do that in DVD resolution (704x480).

> Is the comparison fair? Do results on a single file matter at all?
You'll get similar results with any other file as well.

---

### Post by patrickaupperle on 2010-01-21
> **VertexPusher said:**
> Yes, and I said the only reason why people use Theora is because they *believe* it's safe.


Yes. Theora is somewhere on the level of Xvid, a MPEG-4 ASP codec.


Upload the files, then I'll point out the differences for you. I've encoded a lot of video, and I ran lots of tests with Theora too.


Yes, 20% reduction is a huge difference, especially when you are trying to put a feature film on a single CD. With x264 you can do that in DVD resolution (704x480).


You'll get similar results with any other file as well.

I posted the links earlier (from my server). I am uploading to megaupload, now. Will post links asap.
Here is the source: [http://www.megaupload.com/?d=4XKELM5W](http://www.megaupload.com/?d=4XKELM5W)
Here is the ogg: [http://www.megaupload.com/?d=DFE677YY](http://www.megaupload.com/?d=DFE677YY)
Here is the h264: [http://www.megaupload.com/?d=F9FN8UH8](http://www.megaupload.com/?d=F9FN8UH8)

---

### Post by Emanuele_Z on 2010-01-21
Hi,

I'm sorry I can't post the results, as seen as I've used as source my own BD of BBC's Life (source is 1080i, avg 36 mbps, so could be like avg 18mps 1080p) to do this test.
Imho nature sequences provide the best benchmark because are:
[LIST]
[*]Full of details
[*]Many different bright colors (most of all coral reef scenes)
[*]Lot of motion
[*]Lot of gradients as well
[/LIST]
Basically all things that human eye reacts and are hard to compress.
Now, you can find some free 1080p video on Apple's HD website. They have the Shark video, underwater scene that should be good as well.
Probably we could consider those videos reference.

What I did was to test them in 720p, 1080p 2 passes with Handbrake 0.9.4 (uses libtheora 1.1) with same bitrate, using default settings but changing only the bitrate.
Again, the results were appalling.
With 2 mbps theora was really bad; with 4 mbps theora was ok, but for the same bitare x264 was able to preserve a lot of details. Small details that I wasn't able to see (they were blurred with libtheora) on my 19 inch display, let alone if I tried to see it on my 40 inch LED display...
Now, I think if these (theora) guys want to improve their codec they simply have to start developing against 720p/1080p content. Here x264 shines a lot more; and I'm sorry because I would like to see theora succeed as well.
I don't know if the PSNR ( [http://en.wikipedia.org/wiki/Peak_signal-to-noise_ratio](http://en.wikipedia.org/wiki/Peak_signal-to-noise_ratio) ) is similar, I doubt, but in case it is, theora is saving 'useless' information.

Plus, let me add, x264 is multithread by defualt, libtheora is monothread. Is there a way to run theora multithread? Is it a Handbrake issue?

Anyway, the best would be to produce maybe a 2mbps and 4mbps x264/libtheora of the Shark - Apple video, and produce PSNR as well, so we could agree more. Too bad I've used BBC's Life BDs.

Let me know,

---

### Post by JohnAStebbins on 2010-01-21
> libtheora is monothread. Is there a way to run theora multithread? Is it a Handbrake issue?
As you stated, libtheora is single threaded.  Only the theora developers can fix this.

---

### Post by Emanuele_Z on 2010-01-21
Hi,

I've re-run some compression against an aquarium 1080p high bitrate source.
As before I've converted to 720p and used a double pass.
Target bitrate 3000 kbps. No audio. **15 FPS** (so you know that video will be not smooth).
Here is the link to x264:
[http://rapidshare.com/files/338953040/hd_other_pioneer_aquarium.m4v.html](http://rapidshare.com/files/338953040/hd_other_pioneer_aquarium.m4v.html)
Here is the link to libtheora:
[http://rapidshare.com/files/338959906/hd_other_pioneer_aquarium.ogg.html](http://rapidshare.com/files/338959906/hd_other_pioneer_aquarium.ogg.html)
And here the original:
[http://www.demo-world.eu/trailers/redirect-high-definition.php?file=hd_other_pioneer_aquarium.part1.rar](http://www.demo-world.eu/trailers/redirect-high-definition.php?file=hd_other_pioneer_aquarium.part1.rar)
[http://www.demo-world.eu/trailers/redirect-high-definition.php?file=hd_other_pioneer_aquarium.part2.rar](http://www.demo-world.eu/trailers/redirect-high-definition.php?file=hd_other_pioneer_aquarium.part2.rar)

I can see some lost details in ogg video, but is not *that* bad at 3000 kbps. I guess at a lower bitrate we can start see more artifacts.
Let me know what you think.

Btw handbrake used 2 cores to convert the theora one, so maybe they've fixed it.

Cheers,

Ps. This site is cool for 1080p videos: [http://www.demo-world.eu/trailers/high-definition-trailers.php](http://www.demo-world.eu/trailers/high-definition-trailers.php)

---

### Post by patrickaupperle on 2010-01-21
> **Emanuele_Z said:**
> Hi,

I've re-run some compression against an aquarium 1080p high bitrate source.
As before I've converted to 720p and used a double pass.
Target bitrate 3000 kbps. No audio.
Here is the link to x264:
[http://rapidshare.com/files/338953040/hd_other_pioneer_aquarium.m4v.html](http://rapidshare.com/files/338953040/hd_other_pioneer_aquarium.m4v.html)
Here is the link to libtheora:
[http://rapidshare.com/files/338959906/hd_other_pioneer_aquarium.ogg.html](http://rapidshare.com/files/338959906/hd_other_pioneer_aquarium.ogg.html)
And here the original:
[http://www.demo-world.eu/trailers/redirect-high-definition.php?file=hd_other_pioneer_aquarium.part1.rar](http://www.demo-world.eu/trailers/redirect-high-definition.php?file=hd_other_pioneer_aquarium.part1.rar)
[http://www.demo-world.eu/trailers/redirect-high-definition.php?file=hd_other_pioneer_aquarium.part2.rar](http://www.demo-world.eu/trailers/redirect-high-definition.php?file=hd_other_pioneer_aquarium.part2.rar)

I can see some lost details in ogg video, but is not *that* bad at 3000 kbps. I guess at a lower bitrate we can start see more artifacts.
Let me know what you think.

Btw handbrake used 2 cores to convert the theora one, so maybe they've fixed it.

Cheers,

Ps. This site is cool for 1080p videos: [http://www.demo-world.eu/trailers/high-definition-trailers.php](http://www.demo-world.eu/trailers/high-definition-trailers.php)

I really want to look at those files to see if I can see the differences, but it looks like rapidshare is overloaded right now. Wow, rapidshare seems to be doing this a lot lately.

Edit: I finally got those files. I actually see absolutely no difference between them. Of course, my eyes are not trained to such things. Also, I did not run them side by side (my computer already didn't like the m4v). This is promising, maybe theora 1.2, whenever it comes out, will put theora on level with h264.

---

### Post by VertexPusher on 2010-01-22
I'll look at the files when I get home. Thanks for uploading the source as well. This way I can run an encode myself and upload it for you to compare. x264 has lots of encoding options, and the defaults in applications such as Avidemux are not always the best.

There is one rule that applies to video encoding in general: Any encoder can produce transparent results (i.e. indistinguishable from the source) if there's no cap on the bitrate.

So the question is: How much can you reduce the bitrate until artifacts become visible? This is what separates good codecs from less good ones.

There are several reasons why Theora cannot be as efficient as H.264, even in future versions. The most obvious one is the number of reference frames. Theora supports two frame types: I-frames and P-frames. An I-frame is a frame that is fully encoded by itself, like a JPEG image. A P-frame is a frame that only contains changes since the previous I- or P-frame. This means that a P-frame has 1 reference frame: the frame that preceeds it. The ability to refer to a preceeding frame reduces the size of P-frames considerably, because only the things that have changed need to be encoded.

In H.264, you can have up to 16 (!) reference frames, depending on the profile. And you can have B-frames, i.e. frames that refer not only backward but forward as well. H.264 even supports mixed references, i.e. reference frames can be chosen per macroblock. This makes H.264 extremely efficient when objects move in front of a static background or when objects appear and then disappear again. More reference frames means that less has to be encoded from scratch.

Theora cannot add any of these features without
[list][*]breaking compatibility and
[*]violating MPEG patents.[/list]
That's why H.264 will remain superior, at least until the patents expire.

Go to [http://www.apple.com/trailers/](http://www.apple.com/trailers/), download a movie trailer and encode it to Theora. I bet I can encode a H.264 file that is significantly smaller and looks at least as good, if not better. Apple's own H.264 encoder is not particularly good, but x264 is ahead of pretty much everything else.

---

### Post by Emanuele_Z on 2010-01-22
Indeed, the points are other.
Basically h.264 and Theora (VP3) are part of the same (DCT/iDCT) family.
If we can say that MPEG-1 is like a chimp, XviD can be seen as primitive man, Theora as barbarians (200 a.d.) and H.264 as 20th century man.
They're all from the same species (the lossy compression technique is DCT/iDCT) but they are different, and difference is really noticeable.
H.264 is more evoluted than Theora because, apart before examples, it can apply the DCT/iDCT technique not only on 8x8 blocks but on 4x4. It does implement arithmetic compression (in two different ways) that is able to save up 15% of size. It does implement many other features.
We know for sure that a large part of these nifty features are patent protected (in US only, in the rest of world those are not, because software can't be patented)
The questions (for Theora devs/creator) are:
[list]
[*] With current Theora (VP3) format, is there a way to achieve better encoding without having to extend the format itself?
[*] Can Theora (VP3) format be extended to include new algorithms to achieve better encoding (but this could be not backwards compatible)?
[/list]

I've re-ecoded the same short clip to 1500 kbps (this time preserving the original frame rate). Now the artifacts appear more noticeable and frankly if H.264 is acceptable, Theora becomes appalling.
I'll post the links later.

On a side note, is there some script/utility to perform proper PSNR on the fly? Because probably this is the only way we have to base conclusions on objective results.
For sure subjective results are improtant as well, but PSNR could be a good starting point.
Again, I think, as a community, we should start focusing on 1080p/720p video compression; this is the future.

Cheers,

---

### Post by patrickaupperle on 2010-01-22
Well, I think this has already shown that h264 is better than theora. In every case h264 did as well or better. In some cases, the difference was significant. Also, due to the whole b-frames thing, these results make perfect sense. I do agree that it would be nice to get that PSNR, though.

---

### Post by VertexPusher on 2010-01-22
PSNR results have to be taken with a grain of salt. x264 can perform some psychovisual tricks to preserve film grain and dithering noise. The results will look subjectively closer to the original, but the PSNR will be worse. For PSNR comparisons this feature should be turned off.

---

### Post by patrickaupperle on 2010-01-22
> **VertexPusher said:**
> PSNR results have to be taken with a grain of salt. x264 can perform some psychovisual tricks to preserve film grain and dithering noise. The results will look subjectively closer to the original, but the PSNR will be worse. For PSNR comparisons this feature should be turned off.

It'd still be nice to see those results. If the h264 has as good results as the Theora file, that really would tell us something. We will have to keep in mind that they can be misleading.

---

### Post by VertexPusher on 2010-01-22
> **patrickaupperle said:**
> It'd still be nice to see those results.
Here they are:
[img]http://web.mit.edu/xiphmont/Public/theora/correct_is_good.png[/img]
Source: [http://web.mit.edu/xiphmont/Public/theora/demo7.html](http://web.mit.edu/xiphmont/Public/theora/demo7.html)

---

### Post by Emanuele_Z on 2010-01-22
Probably would be better to get the results of (PSNR) above compressed movie, as seen as we've used a very high bitrate compared to what you posted.
Know any utility/script that performs this in a simple manner?
Cheers,

---

### Post by patrickaupperle on 2010-01-22
Nice, that chart, I think, pretty much sims this thread up, unless we can get some charts of the actual posted files. The only other thing is to wait and see what theora and h26x due in the future.

---

### Post by patrickaupperle on 2010-01-23
Just for fun, I took some screenshots of the harry potter encodings. I redid the Theora encoding with handbrake and the results are better. Also, it ended up in an mkv, if that makes any difference. Both files are over 700 mb and within a mb of each other. To take the screenshots I used totem, edit - take screenshot. If there is a better method, please share.
I have a few more, but it looks like Ubuntu Forums only wants to take 5 attachments. Ill put the rest up on image shack. I'll add them when I am done.

[[IMG]http://img59.imageshack.us/img59/6894/11025theora.th.png[/IMG]](http://img59.imageshack.us/i/11025theora.png/)
[[IMG]http://img137.imageshack.us/img137/5437/11025h264.th.png[/IMG]](http://img137.imageshack.us/i/11025h264.png/)
[[IMG]http://img251.imageshack.us/img251/9656/10703theora.th.png[/IMG]](http://img251.imageshack.us/i/10703theora.png/)
[[IMG]http://img251.imageshack.us/img251/4680/10703h264.th.png[/IMG]](http://img251.imageshack.us/i/10703h264.png/)

One interesting thing to note, the two videos are different lengths. It is only one second, but it still is interesting. I think this is related to the fact that the screen shots are not identical. Look at this:

[[IMG]http://img5.imageshack.us/img5/1814/theora.th.jpg[/IMG]](http://img5.imageshack.us/i/theora.jpg/)
[[IMG]http://img197.imageshack.us/img197/6087/h264x.th.jpg[/IMG]](http://img197.imageshack.us/i/h264x.jpg/)

---

### Post by JohnAStebbins on 2010-01-23
> **VertexPusher said:**
> PSNR results have to be taken with a grain of salt. x264 can perform some psychovisual tricks to preserve film grain and dithering noise. The results will look subjectively closer to the original, but the PSNR will be worse. For PSNR comparisons this feature should be turned off.

When doing PSNR measurements, x264 provides an option that disables all the psy optimizations in order to get valid readings.  "--tune psnr". This should always be used when doing such comparisons.

---

### Post by patrickaupperle on 2010-01-25
I am really wondering now, what does cause the differences in the above screen shots? Look in the screenshot galleries, created by totem, they have the exact same times listed, but the scenes in them are pretty far apart. Can someone explain this?

---

### Post by elitenoobboy on 2010-01-30
What is the preferred quality settings when encoding theora? What do most people use for regular 480p? 720? Is using quality 10 worth the size?

---

### Post by clevin on 2010-02-09
> **elitenoobboy said:**
> What is the preferred quality settings when encoding theora? What do most people use for regular 480p? 720? Is using quality 10 worth the size?
in terms of file size
treat 5 as 400kbps H.264
treat 8 as 1100kbps H.264


I think 8 is more than good enough

---

### Post by VertexPusher on 2010-02-10
> **patrickaupperle said:**
> I am really wondering now, what does cause the differences in the above screen shots? Look in the screenshot galleries, created by totem, they have the exact same times listed, but the scenes in them are pretty far apart. Can someone explain this?
The frame rates don't match.

---

### Post by MetalMusicAddict on 2010-02-10
With all the chat about patents, I wonder about the consumer use of Dirac? I was very impressed with how the BBC went about it and all it's technical merits are very nice. But consumer use seems very limited.

h264 seems to be getting ahead because of HW adoption and MPEG LA doing a [temporary permissive free license]("http://arstechnica.com/media/news/2010/02/royalty-free-codec-still-needed-despite-no-cost-h264-license.ars") to help things along.

Anyone on the forum put Dirac through it's paces vs. h/x264?

---

### Post by VertexPusher on 2010-02-11
> **MetalMusicAddict said:**
> With all the chat about patents, I wonder about the consumer use of Dirac?
Dirac's situation is not much different from Theora's. Its patent status is unknown until someone shows up with a patent.

Fighting software patents with alternative software simply doesn't work. Patents are like hidden weapons of mass destruction: You can prove their presence (if you find them) but not their absence.
> h264 seems to be getting ahead because of HW adoption and MPEG LA doing a [temporary permissive free license]("http://arstechnica.com/media/news/2010/02/royalty-free-codec-still-needed-despite-no-cost-h264-license.ars") to help things along.
People often mention hardware adoption of H.264 as an advantage over Theora, but this is not quite fair. If you encode H.264 for hardware, you can't use many of the features that put H.264 ahead of Theora. This is the reason why YouTube's H.264 clips still look crappy, even if they were transcoded from a perfect source. In order to be compatible with devices such as the iPod, YouTube has to use the H.264 Baseline Profile which indeed isn't far ahead of Theora (no B-frames, no CABAC, no 8x8 DCT, no more than one reference frame). Bottom line: H.264 offers efficient compression **or** hardware compatibility, but not both at the same time, with the same files.

> Anyone on the forum put Dirac through it's paces vs. h/x264?
I ran some test encodes recently. Dirac is not (yet) as good as x264, but definitely better than Theora.

---

### Post by Emanuele_Z on 2010-02-11
Btw, do you default Handbrake Theora (1.1) parameters (apart bitrate naturally) are ok to be used to test HD video encoding?

Cheers,

---

### Post by VertexPusher on 2010-02-12
This is interesting: [http://x264dev.multimedia.cx/?p=102](http://x264dev.multimedia.cx/?p=102)

Theora 1.1 was pretty much at the end of the list, outperformed even by ffmpeg's MPEG-2 and FlashVideo-1 codecs. But things got even worse:
> **Postscript re Theora (October 6th):**

With the release of Theora 1.1, I re-tested Theora due to a request by a reader.  The results are summarized as follows (and I will explain why they are not on the graph):

Theora has not improved significantly since the beta version I tested.  Specifically, the score I got on the beta was 17.35 and the score on the final version was 16.56; if anything a slight negative change.  There was one improvement: the encoder achieved within 2% of the target bitrate, rather than me having to try a dozen bitrates to get it to reach the target as previously.

Anyways, I did much more detailed investigation this time, and discovered the problem…

*The encoder was dropping frames, even in two-pass mode.  To be exact, 124 frames.*

This is of course a sure path to quality disaster and suggests some serious bugs.  I did a constant-quality encode and found that -v 4.1 was needed to get the bitrate necessary–which clearly means that the encoder wasn’t running out of bits during the two-pass encode and makes the dropped frames seem even more weird.  But what if we ignore the dropped frames, sync up the remaining frames, and measure their quality?  Obviously, this unfairly biases in favor of Theora as it assumes the dropped frames wouldn’t have cost any bits, but let’s do it for argument’s sake.

**The result is a score on the graph of 23.13, putting Theora a bit below ffmpeg FLV1.** This makes much more sense given that the Theora format itself is quite similar to H.263 (which FLV1 is based off of).  Of course, until the encoder is fixed such that it doesn’t drop frames, even that number is dubious.
This of course explains why the frame numbers and video durations in patrickaupperle's test were off. Theora 1.1 does not only suck quality-wise, it is outright broken.

---

### Post by FakeOutdoorsman on 2010-02-12
> **VertexPusher said:**
> YouTube has to use the H.264 Baseline Profile which indeed isn't far ahead of Theora (no B-frames, no CABAC, no 8x8 DCT, no more than one reference frame).

Perhaps it depends on what resolution you choose to watch.  I investigated the 720p Avatar Trailer and it was H.264 High Profile with CABAC and psy-rd minus b-frames and weightp.

---

### Post by VertexPusher on 2010-02-13
> **FakeOutdoorsman said:**
> Perhaps it depends on what resolution you choose to watch.  I investigated the 720p Avatar Trailer and it was H.264 High Profile with CABAC and psy-rd minus b-frames and weightp.
If it is High Profile, QuickTime will not be able to play it back (unless some 3rd party plugin is installed, e.g. Perian). This will make AppleTV and iPad users very unhappy.

As far as I remember, the whole point of YouTube going H.264 was to make the content compatible with Apple consumer electronics.

Some time ago I was working on a video project, and I found out it was a major pain to make content compatible with QT because QT is limited in many ways. You can't just load any H.264 video into QT and expect it to play back fine; that would be too easy. Unfortunately Apple's interpretation of H.264 has become a de-facto standard.

This kind of trouble would never happen with Ogg formats, because both Theora and Vorbis don't have multiple profiles. There is only one bitstream format, and it will work with all decoders anywhere.

---

### Post by Chronon on 2010-02-15
> **VertexPusher said:**
> You can't prove that there are no patents that cover Theora. Nobody can.

That is exactly why the EFF and others fight software patents: You can prove the presence of patents but not their absence. Patent trolls have turned this into a profitable business: They aquire patents which vaguely describe some fundamental technology (e.g. browser plugins, see Eolas vs. the rest of the world), then they wait until the technology becomes popular. Finally they send everyone the bill or take them to court.

Theora isn't safe. In fact it is more unsafe than H.264 whose patent holders are well known. If you need something safe and free, MPEG-1 is your only option because its patents are expired.

The patent also has to predate your related work otherwise your work is prior art and it invalidates the patent.

---

### Post by howlingmadhowie on 2010-02-15
> **VertexPusher said:**
> You can't prove that there are no patents that cover Theora. Nobody can.

That is exactly why the EFF and others fight software patents: You can prove the presence of patents but not their absence. Patent trolls have turned this into a profitable business: They aquire patents which vaguely describe some fundamental technology (e.g. browser plugins, see Eolas vs. the rest of the world), then they wait until the technology becomes popular. Finally they send everyone the bill or take them to court.

Theora isn't safe. In fact it is more unsafe than H.264 whose patent holders are well known. If you need something safe and free, MPEG-1 is your only option because its patents are expired.

Now that's not quite true.  Some H.264 patent holders are known, but H.264 may also have a number of unknown patent holders, just like Theora may have. But H.264 also has a number of known patent holders, which Theora doesn't have.

So basically, with theora you don't know if the codec is free or patented and with H.264 you don't know if the codec is patented or patented multiple times.

---

### Post by xtremethegreat1 on 2010-02-15
Theora isn't protected by patents. It was developed specifically, so that Open source lovers could use that.

---

### Post by VertexPusher on 2010-02-15
You guys have no idea how patents work.

Theora isn't safe. OK, maybe H.264 isn't safe either, even if you pay the MPEG LA license fees. But that's not the point.

The point is that there are only so many (known) ways to do video compression. And there is no way to be sure about a codec's patent status until you have checked each and every patent which may relate to that codec even in the most remote and obscure way.

Of course you can choose to ignore the problem and tell yourself again and again that Theora is safe until you start believing it. But it is not safe until you prove it, and proving it would take an army of lawyers wading through thousands of patents.

Very few entities can afford that procedure. That is why even Microsoft didn't see the Eolas submarine patent until it finally surfaced and kindly asked MS to hand over $521,000,000.

There is no way out of this mess until the US abolish software patents.

Citizens of the EU have few incentives to use Theora because the MPEG LA patent pool is only enforceable here as far as hardware is concerned. MPEG formats and software codec implementations are not protected. So we just use the best codec available, which happens to be H.264.

---

### Post by howlingmadhowie on 2010-02-15
> **VertexPusher said:**
> You guys have no idea how patents work.

Theora isn't safe. OK, maybe H.264 isn't safe either, even if you pay the MPEG LA license fees. But that's not the point.

The point is that there are only so many (known) ways to do video compression. And there is no way to be sure about a codec's patent status until you have checked each and every patent which may relate to that codec even in the most remote and obscure way.

......

Citizens of the EU have few incentives to use Theora because the MPEG LA patent pool is only enforceable here as far as hardware is concerned. MPEG formats and software codec implementations are not protected. So we just use the best codec available, which happens to be H.264.

As far as i know, the MPEG LA does not offer patent immunity for other claims on their codecs.  With more than a million software patents out there it is just as likely that H.264 has unknown submarine patents on it as Theora has, and just as likely that a patent holder will come after the end user as with Theora.

Citizens of the EU have the incentive that if they want to be good netizens and use formats others can freely view and use themselves, then they should use Theora.

---

### Post by VertexPusher on 2010-02-15
> **howlingmadhowie said:**
> As far as i know, the MPEG LA does not offer patent immunity for other claims on their codecs.  With more than a million software patents out there it is just as likely that H.264 has unknown submarine patents on it as Theora has, and just as likely that a patent holder will come after the end user as with Theora.
Absolutely correct.

Bottom line: In a software patent system, there is no such thing as safety. But people claim that Theora is somehow more safe than H.264, and that argument doesn't hold because no one can prove it.

> Citizens of the EU have the incentive that if they want to be good netizens and use formats others can freely view and use themselves, then they should use Theora.
No, because it's not a solution. Fighting software patents is the solution. And that's what good netizens are doing already.

---

### Post by Emanuele_Z on 2010-02-15
Hi all,

I couldn't stand anymore on the subjective quality so, I decided to code a dynamic multithreaded PSNR calculator* (no tmp files, all in memory and extremely quick).

Only issue is that I use libavcodec and apparently it's not able to properly read the theora video made with HandBrake (I'll test maybe produced with ffmpeg...).

On a preliminary test of x264 vs XviD (as seen as can't read theora files) in some cases XviD is better than x264...LOL!

Btw, I'll post deb package(s) and sources once I polish it a bit.
Let me know if you want to help me test it...

Cheers,

*Clearly is all done in C++

---

### Post by FakeOutdoorsman on 2010-02-15
> **Emanuele_Z said:**
> Only issue is that I use libavcodec and apparently it's not able to properly read the theora video made with HandBrake (I'll test maybe produced with ffmpeg...).

That shouldn't happen.  Show your FFmpeg command and the complete output.

---

### Post by Emanuele_Z on 2010-02-15
> **FakeOutdoorsman said:**
> That shouldn't happen.  Show your FFmpeg command and the complete output.

I'm using HandBrake to create Theora (libtheora 1.1) video streams.
Then I use straight libavcodec in my C++ code...

Cheers,

---

### Post by Chronon on 2010-02-15
> **VertexPusher said:**
> Absolutely correct.

Bottom line: In a software patent system, there is no such thing as safety. But people claim that Theora is somehow more safe than H.264, and that argument doesn't hold because no one can prove it.

I accept that nobody can demonstrate non-existence of a threat.  Theora appears more safe because H.264 has visible, verifiable patent protection.  Both may infringe upon various other unknown patents.  I have no a priori reasons to think that the likelihood of Theora infringing on unknown patents should exceed the likelihood of H.264 infringing on unknown patents, so I would consider H.264 riskier because of the verifiable threat.  The lack of evidence for a positive threat against Ogg Theora certainly shouldn't provide a basis for considering H.264 as safer than Theora.

---

### Post by VertexPusher on 2010-02-15
> **Chronon said:**
> Theora appears more safe because H.264 has visible, verifiable patent protection.
MPEG LA owns by far the largest pool of patents related to digital audio/video compression and formats. It is just much more likely for Theora to infringe on some MPEG patent than for H.264 to infringe on some unknown patent outside the MPEG LA pool. And even if there is such an unknown patent on some obscure aspect of H.264 technology, it may still hit Theora as well.

This is why corporations feel safer paying the MPEG LA portfolio license fee, even if they choose to support Theora as well. Call it protection racket if you will.

---

### Post by Emanuele_Z on 2010-02-16
Hi guys,

I've actually done some objective comparisons between x264 and XviD.
I've taken the VOB high quality video of the following song:
[http://www.youtube.com/watch?v=oXyuQECvjns](http://www.youtube.com/watch?v=oXyuQECvjns)
(clearly **not** from youtube...)
This video should be a *nightmare* for codecs because it has very short sequences, light/darks and a lot of details/moving objects. 
Then, with HandBrake (latest version), I've compressed it from VOB to:
x264 (1000, 500, 250 kbps)
XviD (1000, 500, 250 kbps)
The settings I've changed have been the rate (clearly) and the fact to use two pass (turbo).
After this I've run the **PSNR** on *every frame* (VOB like vs each one, 6 of them in parallel) and reported on the attached charts the average of every 25 frames.

It's funny to notice how with 1000 kbps XviD sometimes outperforms x264, but when the latter is better than XviD, XviD does *suck* (like around from 5100 to ~6000 on focus chart).
Instead, with very low bitrate, 250 kbps (yellow) x264 is basically equal to XviD 500 kbps (brownish) in most of the movie!
For example, take a look at frame 5601 (attached).

Please keep in mind the following: PSNR is logarithmic measure, that means that 1 point difference on the chart and image quality has 10 times more accurate information!
When you see the two big spikes  is because the screen gets dark and actually for both codecs is easy to get a very good PSNR.

Let me know what you think, plus if you want to help me test my PSNR generator, please let me know!

Cheers,

Ps. Again, my C++ program does use libavcodec and actually it can't properly process Theora video streams (I get rubbish RGB data). All the other codecs are fine (eg. x264 and XviD are working brilliantly and in parallel).
PPs. Here [http://yfrog.com/htx264xvidfocusj](http://yfrog.com/htx264xvidfocusj) the focus chart in a bigger size, and [http://yfrog.com/0wf5601p](http://yfrog.com/0wf5601p) the full comparison png image.

---

### Post by VertexPusher on 2010-02-16
> **Emanuele_Z said:**
> Let me know what you think, plus if you want to help me test my PSNR generator, please let me know!
When publishing test results, always include the encoding settings used during the test. Both Xvid and x264 have dozens of parameters which can be tweaked. Target bitrate is just one of them. These parameters can have a huge impact on compatibility (Profile, Level) and compression efficiency.

Reference videos with lots of scene changes diminish the differences between codecs because each scene change results in a keyframe inserted by the encoder. However, the actual "magic" of video compression (i.e. motion estimation/compensation) happens **between** those keyframes. To emphasize the differences between codecs (and minimize measurement error), you'll want to use reference videos with lots of motion but **few** scene changes.

If you pick a reference video from a public source (e.g. Apple's QuickTime HD gallery), I will contribute some encodes that you can compare with your own.

By the way, you may be able to work around the Theora problem by converting the Theora result to HuffYUV (lossless) before measuring it.

---

### Post by Emanuele_Z on 2010-02-16
> **VertexPusher said:**
> When publishing test results, always include the encoding settings used during the test. Both Xvid and x264 have dozens of parameters which can be tweaked. Target bitrate is just one of them. These parameters can have a huge impact on compatibility (Profile, Level) and compression efficiency.

I've used the default (normal) settings.
> 
Reference videos with lots of scene changes diminish the differences between codecs because each scene change results in a keyframe inserted by the encoder. However, the actual "magic" of video compression (i.e. motion estimation/compensation) happens **between** those keyframes. To emphasize the differences between codecs (and minimize measurement error), you'll want to use reference videos with lots of motion but **few** scene changes.

I know, but I want to measure the ability of the codec to choose keyframes and what is their compression level as well.

> 
If you pick a reference video from a public source (e.g. Apple's QuickTime HD gallery), I will contribute some encodes that you can compare with your own.

Thanks, once I polish the program will let you know.
> 
By the way, you may be able to work around the Theora problem by converting the Theora result to HuffYUV (lossless) before measuring it.
What do you mean? I'm using libavcodec, and every time a frame is ready to be processed I convert from the codec's colorspace (usually with my Theora test is YUV420) to RGB, then perform the PSNR.
Naturally I don't try to execute a PSNR with compressed bitplanes!
With Theora I only get rubbish images (macroblocks with wrong hue/colours and image that is totally wrong as well), while with other tested codecs (x264/xvid/wmv/wmv2) everything is working ok (eg. I get the proper frames with libavcodec).

Cheers,

---

### Post by VertexPusher on 2010-02-16
> **Emanuele_Z said:**
> I've used the default (normal) settings.
Default settings differ between host applications. You are not measuring the codec but the host application's tendency towards compatibility vs. compression efficiency.

Example: Some applications optimize Xvid for DivX 5 compatibility, because this is a frequently requested profile. Some don't. Some applications choose x264 parameters with iPhone compatibility in mind. Some don't. You get the idea.

> I know, but I want to measure the ability of the codec to choose keyframes and what is their compression level as well.
OK, and I am telling you there is not much difference in keyframe compression between the codecs. But there is a **big** difference in size between a keyframe and a delta frame. The more keyframes you have in the video, the less accurate your measurement will be.

> With Theora I only get rubbish images (macroblocks with wrong hue/colours and image that is totally wrong as well), while with other tested codecs (x264/xvid/wmv/wmv2) everything is working ok (eg. I get the proper frames with libavcodec).
My suggestion is as follows: You encode the Theora video from the source video, then convert the Theora video to HuffYUV. Then you feed the HuffYUV video into your tool instead of the Theora video. This should not affect the PSNR measurement because the conversion from Theora to HuffYUV is lossless. But you may have more luck decoding the HuffYUV video properly.

---

### Post by Emanuele_Z on 2010-02-16
> **VertexPusher said:**
> 
My suggestion is as follows: You encode the Theora video from the source video, then convert the Theora video to HuffYUV. Then you feed the HuffYUV video into your tool instead of the Theora video. This should not affect the PSNR measurement because the conversion from Theora to HuffYUV is lossless. But you may have more luck decoding the HuffYUV video properly.

Given that my psnr software is multi threaded, dynamic and kinda fast, I'd rather not encumber the user with the *forced* conversion to another uncompressed colorspace.

Btw, I managed to know why and what is going wrong.
the **libavcodec-dev** package in Ubuntu 9.10 (x86-64) is ***outdated***; apart that the function *avcodec_decode_video2* is missing, the libraries loaded with it are **not** able to read Theora files (or better decompress those).
Proof is then I downloaded the latest svn cut of libavcodec from FFmpeg website and after having built my executable against those libraries (static libraries FTW :) ) it is working properly with Theora video streams (both *avcodec_decode_video* and *avcodec_decode_video2*).
So, how can we make/ask the Ubuntu packages maintainers update it? 
What is the official channel/way?

Originally my executable relies on dynamic libraries...I'd like to keep it this way...

Cheers,

---

### Post by VertexPusher on 2010-02-16
> **Emanuele_Z said:**
> the libraries loaded with it are **not** able to read Theora files (or better decompress those).
Confirmed. Using ffmpeg to convert a Theora file produces garbage. Interestingly, mencoder is not affected because it seems to use libtheora directly, bypassing libavcodec.

---

### Post by FakeOutdoorsman on 2010-02-16
> **Emanuele_Z said:**
> So, how can we make/ask the Ubuntu packages maintainers update it? 
What is the official channel/way?

You can file bug reports and package requests at Launchpad: [Bugs in “ffmpeg” package in Ubuntu](https://launchpad.net/ubuntu/+source/ffmpeg/+bugs).  You should check to see if this has already been filed, otherwise your bug report will get marked as a duplicate, although that's no big deal.  Better to file than not.

---

### Post by Emanuele_Z on 2010-02-16
Thanks mate,

the link to the bug is here:
[https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/522812](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/522812)

Cheers,

---

### Post by FakeOutdoorsman on 2010-02-16
The bug report doesn't show what version of Ubuntu you're using.  Does this also occur if you use the FFmpeg binary?  I don't know how to use the API.  Can you show some information on the Theora input (*ffmpeg -i foo.ogv* or *mediainfo foo.ogv*)?

---

### Post by VertexPusher on 2010-02-16
> **FakeOutdoorsman said:**
> Does this also occur if you use the FFmpeg binary?
Yes. Here's an example:
```
# MP4 works
wget -q -O - http://videos.mozilla.org/firefox/3.6/getpersonas.mp4 | ffmpeg -i /dev/stdin -f yuv4mpegpipe -y /dev/stdout | mplayer -demuxer y4m -

# OGV doesn't
wget -q -O - http://videos.mozilla.org/firefox/3.6/getpersonas.ogv | ffmpeg -i /dev/stdin -f yuv4mpegpipe -y /dev/stdout | mplayer -demuxer y4m -

# But here it does
wget -q -O - http://videos.mozilla.org/firefox/3.6/getpersonas.ogv | mplayer -
```

---

### Post by Emanuele_Z on 2010-02-17
Guys, they marked the bug invalid...
Could you please post that this bug affects you as well?
I'll try to make them understand...

Cheers,

---

### Post by VertexPusher on 2010-02-17
Maybe the bug is in libavcodec-extra-52 (multiverse) but not in libavcodec52.

That would explain why they were unable to reproduce the problem.

---

### Post by Emanuele_Z on 2010-02-17
I've posted my simple program (**qpsnr**) to execute a parallel PSNR on Ubuntu/Linux natively (no scripts/tmp files needed).
The link is here:
[http://qpsnr.youlink.org/](http://qpsnr.youlink.org/)
Please keep in mind that is still in early stage of development.
Any questions, ask!

Cheers,

---

### Post by Emanuele_Z on 2010-02-21
(I made work the tool with latest build of libav* libraries).

Here are the charts for the PSNR and SSIM for this file:
[http://web.mit.edu/xiphmont/Public/theora/matrix-300-AQ.ogv](http://web.mit.edu/xiphmont/Public/theora/matrix-300-AQ.ogv)
Video size is 640x272
It has been encoded with default parameters, baseline profile for x264 and default settings with libtheora 1.1. Both of them 2 passes (first pass turbo).
Stats are the average each 25 frames.

PSNR: [http://yfrog.com/jymatrixpsnrj](http://yfrog.com/jymatrixpsnrj)
SSIM: [http://yfrog.com/0umatrixssimj](http://yfrog.com/0umatrixssimj)

As you can see both stats are in total favour of x264. The SSIM is even greater.
I'll post some HD video stats later on.

Cheers,

---

### Post by VertexPusher on 2010-02-21
> **Emanuele_Z said:**
> As you can see both stats are in total favour of x264. The SSIM is even greater.
And this is only H.264 Baseline Profile, i.e. the bottom end of H.264 compression efficiency.

Here's an example from the top end: The new Wall Street movie trailer, 1280x544, encoded at 1800 kb/s (average bitrate) with High Profile settings.

[http://www.filefactory.com/file/b03d52b/n/ws2t_1800_x264_mkv](http://www.filefactory.com/file/b03d52b/n/ws2t_1800_x264_mkv)
Size: 20 MB (no audio)
SHA1: 9568d938101d9faeead95a5c766d296f8031f81b

The source file (70 MB) can be downloaded from Apple's website:
```
wget -U "QuickTime/7.6.5" http://movies.apple.com/movies/fox/wallstreetmoneyneversleeps/wallstreet-tlrd_h720p.mov
```I did not make a Theora version, but my guess is that the compression artifacts at 1800 kb/s will totally destroy the video.

---

