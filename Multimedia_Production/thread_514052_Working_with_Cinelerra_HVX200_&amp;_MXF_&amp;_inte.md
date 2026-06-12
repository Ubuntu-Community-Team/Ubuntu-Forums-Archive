---
title: "Working with Cinelerra: HVX200 &amp; MXF &amp; interface questions"
date: 2007-07-31
forum: Multimedia Production
---

### Post by jkwarras on 2007-07-31
Hi,

I'm using cinelerra for the last 2-3 months for NLE, mainly DV for the time being. I'm working on a AMD64 intel HT 3.2GHz, 1GB RAM. 

2 SATA HDD:

* HDD A (160 GB):
- Ubuntu (ext3)
- Windows Xp (ntfs)
- Home (ext3)

* HDD B (160 GB):
- swap
- video (fat32) - only for editing.

I know that I should use another filesystem for the video partition, but I did it when I was a window user and ntfs write in ubuntu wasn't as safe as it is right now.

Before I've been working with Final Cut Pro and Adobe Premiere. I've swtched to Ubuntu 2 years ago and I'm really happy about my move. 

I'll love to have some feedback about cinelerra users, because there's some stuff I was used to, or I want to do, and I'm not quite sure how to do it or if I'll able to do it. I'll really appretiate some discussion.

First: I'm planning to shot in october with the **_panasonic HVX200, that works with P2 cards_**. In the case I'm not able tog et that camera, I'll probably use a DVX100. I'll love to use my cinelerra to edit it but:

1) **MXF format** (native format for the HVX200 P2 cards) isn't supported in cinelerra. I've tried yesterday to convert some mxf into something that cinelerra can handle, but I didn't achieve. 

I've used the sample P2 card image provided by raylight [here]("http://dvfilm.com/raylight/FlareContentsUnzip.exe").

Then I've used [mxflib]("http://sourceforge.net/projects/mxflib/") to extract the raw stream from the mxf wrapper. According to the [author]("http://www.freemxf.org/freemxf_board/viewtopic.php?t=78&start=0&postdays=0&postorder=asc&highlight="), the utility MXFsplit "can extract essence from any Generic-Container based wrapping". As I didn't manage to compile mxflib on my linux, I've used the win32 binaries via wine.

Using mxfsplit, I can extract the video from the mxf provided in the VIDEO folder. My ubuntu think it's a Generic DV file. No player seems to detect it (mplayer, xine or totem). Avidemux thinks it's a mpeg file an try to index it, and it fails.

Well, trying to import it directly into cinelerra doesn't crash. IN fact the stream is imported but only squares and lines with no sense show up.

So, 3 questions arises:

- Did MXFSplit fails to extract the raw content or it's just a matter of using other parameters?
- The content is extrated correctly but it's my ubuntu that can't read it.
- The content is really some squares and lines with no sense.

In any case, I'll love to convert it into something that cinelerra can handle, ideally some lossless (because DVCPRO HD is not supported by ffmpeg right now).

2) Apparently DVCPRO HD is a 100MB/s compressed file, so is not as CPU demanding as HDV. **Will my system be able to handle it** for simple editing (not rendering or post-processing): cuts, transitions, etc...?

3) If not, how difficult is to **work via proxy files**? I could downconvert the HD stuff into DV, and then edit my movie. Then "replace" the downconverted files with the HD sources files, to the final render. Is there some tutorial and/or howto?

4) The whole idea is to work with my linux. i'm planning to get some ram if needed. In case I finally shot with the HVX200 and still unable to import my footage into cinelerra, I could always capture it via windows or Mac (Final Cut Pro), but in something that cinelerra could read (**h264 lossless** maybe?).

**_And now some cinelerra interface questions_**:

- In FCP and premiere I'm used to the **drag and drop editing**. In cinelerra you can do it, but when dragging a file in front of another one that's already in the timeline, there's no way it can push it forward and place the track before it, it just overlap the current track.

- Another option I'm missing and don't know if it's there, is the ability to** link/unlink** a video and a audio track. Imagine that I want to use video from a source and the audio from another one, not the real audio from the video file. Once you get it lip-synced I don't see a way to link both and move them via drag and drop together in the timeline.

- Is there an option to select as premiere does? I mean the **selection tools**: Range select, Block select, Track Select, multitrack select. I know I can select and move the selection on the timeline, but it moves just the selection, no the whole track(s). So if you select in the middle of a track it'll move this selection. Which it's the intended behavior but maybe I'm just not used to it ;)

After such a long post, if someone is not asleep, I'll appreciate some feedback :)

Thanks.

---

### Post by cotcot on 2007-07-31
I am in an early stage of video editing in linux and exploring kdenlive and cinelerra. I used Magix video deluxe a couple of years ago and was not happy with the rendered result and the burning tool. 
I am swallowing currently the cinelerra manual. I read that you can arm or disarm tracks. So I guess that it is enough to arm only the tracks you want to edit together and do then the cut and paste or whatever.

---

### Post by jkwarras on 2007-07-31
> **cotcot said:**
> I read that you can arm or disarm tracks. So I guess that it is enough to arm only the tracks you want to edit together and do then the cut and paste or whatever.

Yeah I know, but a link/unlink will be better. Arm/disarm is just a block/unblock track feature, which btw is nice.

Welcome to the video editing in linux world :)

---

### Post by jkwarras on 2007-08-02
So, no one has ever tried to import HVX200 (mxf) footage?

---

### Post by jkwarras on 2007-08-04
Raylight standalone Avi's didn't work neither under cinelerra or using virtualdubmod (it crashes). I've used Dvfilm maker demo to convert the mxf to uncompressed Avi and it works.

In the mean time I've just know that mplayer has a built int mxf demuxer, so you can playback it. If mplayer can do this, then mencoder can convert it to something else.

Downloading more mxf samples from here:
[http://www.freemxf.org/samples/index.html](http://www.freemxf.org/samples/index.html)

And it plays directly in mplayer (it's mpeg2, DV muxed in a mxf file).

The P2 sample doesn't work because it's using the panasonic DVCPROHD codec, and there's no way to decode it in linux, so mplayer doesn't recognize the format and doesn't play it, so no way to convert it.

So, under linux there's no easy way to convert P2 footage and edit it. You'll have to use a commercial solution (raylight) under wine.

---

### Post by Mr Mookie on 2008-05-29
This is it?! Nothing.. I cannot believe I can just drag and drop the .mxf file into Premiere Pro CS3 and Avid Media Exploder but there is not one program that converts these properly still in Ubuntu? The last comment here was in 2007! Any updates for simple use of the "simple open format" from Panasonic for Ubuntu?!

Avidemux, VLC, Mplayer, you name it, it doesn't work with the current Panasonic HD .mxf files...

Mookie

---

### Post by jkwarras on 2008-05-31
Yes, apparently no progress in editing mxf in linux. I finally had to switch to windows and Premiere Pro CS3 to edit my last shortfilm, and I really wanted to use ubuntu, since it's what I use everday for my other needs.

---

