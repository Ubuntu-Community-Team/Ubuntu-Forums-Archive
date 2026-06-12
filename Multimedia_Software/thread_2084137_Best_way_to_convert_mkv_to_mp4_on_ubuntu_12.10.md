---
title: "Best way to convert mkv to mp4 on ubuntu 12.10"
date: 2012-11-14
forum: Multimedia Software
---

### Post by RandyPro on 2012-11-14
Sorry it seems like an easy task and my searches havnt given me much luck, Most of my media is in mkv format which worked fine with windows but since recently switching to linux ive found not everything plays, mostly because of my ATI driver issues, but MP4 works flawlessly.  Any help is greatly appreciated, thanks in advance! 

*Also not as important but whats the best media server for ubuntu 12.10? considering swapping my windows server for a linux one and tbh i dont need anything to fancy just need it to work well with my PS3. Not sure how i feel about switching it because its working but since trying out some different versions of linux and falling in love with ubuntu i have to admit it has me considering throwing away my windows disks

---

### Post by evilsoup on 2012-11-14
That's a really odd problem...

I'll start with your second question, because it's the easiest to answer: in my experience, the easiest media server is ps3mediaserver. *Unfortunetely* it's not in the official Ubuntu repositories, so you'll need to add the ps3mediaserver PPA. From the commandline:

```
sudo add-apt-repository  ppa:happy-neko/ps3mediaserver
sudo apt-get update
sudo apt-get install ps3mediaserver
```

A little bit down [this](http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them) page are instructions on how to add a PPA without using the commandline.

--

As for your first question... well. There are other ways of doing things (winFF is a front-end for ffmpeg/avconv, so it can do the same things as here, but with a GUI) I'll give you my preferred (commandline) option, which is the swiss-army-knife of video/audio conversion: avconv. 

MKV and MP4 (and AVI, OGG, and a bunch of others) are both 'container' formats, and they contain audio codecs (MP3, AAC, FLAC, Vorbis) and video codecs (h.264, MPEG2, XVID). The most common codecs used in MKVs are compatible with MP4 files, so the following command will probably work:

```
avconv -i input.mkv -c:a copy -c:v copy output.mp4
```

Obviously, replace 'input.mkv' and 'output.mp4' with your input file and output file. To convert every MKV file in a folder to MP4:

```
for f in *.mkv do; avconv -i $f -c:a copy -c:v copy ${f/%mkv/mp4}; done
```

Now, this won't work all the time - MKV supports a lot of video codecs that MP4 doesn't - and in that case the options are: try doing the method detailed above, but with .avi instead of .mp4; or transcode (convert) the video codecs to something compatible with the MP4 container. Again, with avconv:

```
avconv -i input.mkv -c:a libvo_aacenc -ab 192k -c:v libx264 -crf 20 -preset medium output.mp4
```

This will always lose you some quality (transcoding always does). The -ab tag controls the bitrate of the audio - higher is better, up to (IIRC) 320k, but 192k will be more than good enough for all but studio-quality headphones. the -crf tag controls the quality of the h264 video - lower is better, 0 being completely lossless (guaranteed to give bigger files than you started with, though) and 18 being 'visually lossless' (maybe if you're a professional cinematographer you'll be able to tell the difference). The -preset tag controls the speed & size of the output file: ultrafast, superfast, veryfast, faster, fast, medium, slow, slower, veryslow - in order of fast encode/large file to slow/small.

If you need to use that, then play around with the settings; but the copy option *should* work for you.

If you look into avconv any more, bear in mind that it is very similar to the ffmpeg program, so any tutorials for the one will also work for the other.

---

