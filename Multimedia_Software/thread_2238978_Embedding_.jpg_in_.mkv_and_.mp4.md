---
title: "Embedding .jpg in .mkv and .mp4"
date: 2014-08-11
forum: Multimedia Software
---

### Post by yayou on 2014-08-11
Hi everybody,

I really need to know how to embed .jpg in video file. I've made a lot of googling but everybody seems to be waiting for the way to do it. Do you have any idea ?

Thank you for having read.

---

### Post by SeijiSensei on 2014-08-11
You need to much more specific.  Are you trying to add the image to an existing video stream?  As far as I know the Matroska container (.mkv) only accepts video, audio and subtitle streams.  I've never seen any with a single JPEG frame. Or are you talking about something like this: [http://www.youtube.com/watch?v=-FVpwYCbUlc](http://www.youtube.com/watch?v=-FVpwYCbUlc).  I presume the video portion is just the single image repeated at 24 frames per second for the duration of the song.

---

### Post by yayou on 2014-08-12
Thank you SeijiSensei but I've didn't succeed to view your link. I'm talking about the fact that usually to see the album art of a movie, we need to have a .jpg in the same directory of this movie. Then if you use for example XBMC, you can browse in your movie data base and each movie will be displayed by his cover art. I would like to do the same thing but with the album art embedded directly in each movie metadata and that way, I won't see any .jpg in the system file anymore. I know that there is 2 problems: first, embedding the image in the file metadata and second, having a program that could display each movie by their respectives images. I wish that now you'll get it.

---

### Post by SeijiSensei on 2014-08-12
I don't think any container format supports that.  You need to bundle the image with the video in an archive format like zip or rar.

---

### Post by yayou on 2014-08-13
Really ? That is very astonishing, given all the things computer science can do and has already shown to the world. I'm not sure to have well understood what you said. If I make this bundle, it seems to me that the video won't be readable by for example Vlc. I've read somewhere that Pitivi or KDEnlive could do it. Do you think that they could help ?

---

### Post by SeijiSensei on 2014-08-13
KDEnlive is a video editor.  It won't do what you want either.  Don't know anything about Pitivi.

Containers like Matroska are designed to hold streams not individual images.

When I said a "bundle," I meant an archive file like ZIP.  You would have the video in one file and the image in another.  Then you would package the entire thing together.  
```
zip mybundle.zip video.mkv image.jpg
```
When the file is unzipped, the video will be playable and the image can be viewed separately.

---

### Post by qyot27 on 2014-08-14
It's just file attachments.  MP4 and MKV both support them, in mildly different ways (MP4 stores it in one of the atoms, I think; MKV actually calls them 'Attachments' and this is readily available through mkvtoolnix and mmg).

On Windows, users typically do this for MP4, *et al.*, files with iTunes or Mp3tag or any number of other solutions that can insert cover art.  The closest equivalent of this for Linux that I found from a cursory Googling is [Puddletag](http://puddletag.sourceforge.net/index.html), which would seem to look and act in an extremely similar fashion to Mp3tag.

There's also a PPA:
[https://launchpad.net/~webupd8team/+archive/ubuntu/puddletag](https://launchpad.net/~webupd8team/+archive/ubuntu/puddletag)

---

### Post by yayou on 2014-08-14
Thank you very much qyot27. That's what I was looking for. I've already succeeded to embed .jpg in my .mp3 using mp3tag but it can't deal with video file. Are you sure that itunes can embed .jpg in .mp4 movie ?

---

### Post by qyot27 on 2014-08-14
I've never actually used iTunes to do this, it was only an assumption since music and video files bought from the iTunes Store have cover art attached (and under the Artwork tab in 'Get Info', it does have Add/Delete buttons).

Mp3tag handles certain containers, and MP4 and OGG are two of those containers that Mp3tag can handle that also happen to be able to store video streams.  Using Mp3tag I fixed the cover art to an MP4 video+audio file, so it does work for that (the cover art even shows up if I add the file to iTunes, so it is really there).  It's just that Mp3tag doesn't support Matroska - but like I said, mkvmerge and its GUI can do Attachments...whether a media center program would display a picture in the Attachments as the cover art for an MKV file, I don't know.  MKV also does have a little-used tagging feature that *might* be a straightforward analogue, and there's a few programs that can seemingly do this with a little leg work (mkvpropedit and mmg's Header Editor in mkvtoolnix, MkvTagger, mkvtag...).

Still haven't gotten the chance to test out Puddletag, but I'd be surprised if it couldn't do this too.  There is an open issue on [Puddletag's Google Code project page requesting batch MKV tagging](https://code.google.com/p/puddletag/issues/detail?id=227), so that would be something to watch for.

---

### Post by yayou on 2014-08-19
qyot27, I've succeeded to add .jpg in .mp4 using itunes and in .mkv. using mmg. It really worked and again I say thank you. The problem is that nothing can display the embedded image. XBMC, Ext4 and NTFS file system didn't show anything. Vlc shows it when reading metadata but that's all. So for now, only half the way is done but that's encouraging.

---

