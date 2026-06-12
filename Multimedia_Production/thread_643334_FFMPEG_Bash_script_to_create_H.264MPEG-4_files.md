---
title: "FFMPEG Bash script to create H.264/MPEG-4 files"
date: 2007-12-17
forum: Multimedia Production
---

### Post by philc on 2007-12-17
I've spent some time putting together a Bash script for creating H.264 and MPEG-4 files, using x264 and xvid codecs, with FFMPEG.

The script takes you through a few questions such as output filename, output container video codec, height, width, bitrate, audio codec, cropping requirements etc

You should just be able to follow the user prompts. Some are multiple choice, some you have to type things in.

The script is located here:

[http://www.kapitalworks.com/projects/ffmpeg/kapitaltranscode](http://www.kapitalworks.com/projects/ffmpeg/kapitaltranscode)

Copy and past this into a text document saved somewhere locally. For the sake of this post, let's call the file "kapitaltranscode" without an extension.

Give the file execution permissions:

***chmod 755 kapitaltranscode***

Move the file to your path for ease of execution later:

***sudo mv kapitaltranscode /usr/bin***

You can then execute the script simply by typing "kapitaltranscode" at your terminal prompt.

You will need to specify an input video. So usage is:

***kapitaltranscode video_name.avi***

There's a couple of other things you need to know.

Obviously this script depends on FFMPEG having been build in such a way as to allow X264 and xVid transcoding. This is how I did it on Ubunutu Gutsy:

[http://slashdot.org/~PhillC/journal/190344](http://slashdot.org/~PhillC/journal/190344)

Within the FFMPEG Tools directory (/ffmpeg/tools) is a qt-faststart file. You'll need to make this separately:

***make qt-faststart***

For the script to work this file needs to have execute permissions and also be in your user path. See the commands above regarding how to do this with the script itself.

qt-faststart allows for a QuickTime file to be played back over the Internet as a Progressive Download file. That is, it will start playing before the whole file has been downloaded. This option will only appear in the script if you've chosen a mov or mp4 container.

That's pretty much it. The script isn't very attractive. I could have written it much nicer using functions I guess. Initially I wrote it only for my own use and creating x264 QuickTime mov files with aac audio. So, this is the output that has been most extensively tested.

It's up to you, the user, to choose audio codecs that work with your video codec choices. There's no checking of this in the script. For example, the script lets you choose aac audio with an avi file container, which produces only silence.

I'd really like feedback. Is this a useful script? What else could be added to it? More formats perhaps? I didn't include Ogg Theora, because there is already ffmpeg2theora. But I'm happy to include it if it's a useful addition. There's no aspect ratio conversion, but it could be added. Can my ffmpeg execution be improved?

Thanks and good luck!

---

### Post by FakeOutdoorsman on 2007-12-19
I saw this from the ffmepg mailing list but your link was broken at the time.  I recommend looking at the [iPod Video Encoding]("https://help.ubuntu.com/community/iPodVideoEncoding") entry on the Ubuntu Wiki and adding it to the other encoding scripts if you think it would be a good alternative to the other scripts.

---

### Post by philc on 2007-12-19
Hmmm, didn't notice the link was broken when posted to the FFMPEG list. Never mind.

My script actually started life as Eric Hewett's ipodvidenc script (credits left in), and I took it from there, adding more options so it's not just for iPod encoding anymore.

I'm happy to add it to the Wiki if there's value in it.

I'm working on putting a Zenity GUI on it at the moment.

Although maybe my time is better spent learning Python and doing the whole thing "properly"!

---

