---
title: "Mencoder sub merge problem"
date: 2010-04-20
forum: Multimedia Software
---

### Post by yodaz on 2010-04-20
Hi, I'm trying to transcode and merge sub with mencoder in order to watch a video on my nokia cellphone.

I'm using this command :
```

/usr/bin/mencoder -v -o myvid-subbed.avi -oac mp3lame -ovc lavc -lavcopts aspect=16/9,vcodec=mpeg4:mbd=2:trell:threads=2 -vf-add scale=320:240 -vf-add expand=320:240 -sub myvid.srt -fontconfig -font Arial -subfont-encoding iso-8859-15 -subfont-text-scale 3 myvid.avi

```

I've also tried with the following option :
-vf scale=320:240 and -vf scale=320:240,expand=320:240
without success. The transcoding works, but no subtitle is merged.

The transcoding log is [here]("http://pastebin.com/m2SbKbyf")

I'm using Karmic.

Thanks in advance for your ideas.

---

### Post by yodaz on 2010-04-20
I've just tried with
```

/usr/bin/mencoder -v -o myvid-subbed.avi -oac copy -ovc copy -sub myvid.srt -fontconfig -font Arial -subfont-encoding iso-8859-15 -subfont-text-scale 3 myvid.avi

```

and with 

```

/usr/bin/mencoder -v -o myvid-subbed.avi -oac copy -ovc copy -fontconfig -sub myvid.srt -font '/usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf' -subfont-encoding iso-8859-15 -subfont-text-scale 3 myvid.avi

```

And it doesn't work :-(

---

### Post by tkoco on 2010-05-02
The best approach to dealing with subtitles, like on foreign video, is to use a layered methodology.

First thing is to do is gather information. For an AVI file media package, in a terminal window try:
```
ffmpeg -i <filename>.avi
```
and ffmpeg will spit out the tracks stored within the media package.
If the media package is MKV, in a terminal window try:
```
mkvinfo <filename>.mkv
```

Assuming the media package has a subtitle track stored within, the next thing to do is to render the subtitle track into the video track so that the subtitles are visible in players (or media formats) which do not support subtitle tracks.

I use mencoder to do the rendering. I choose to render on a higher resolution video so that when the video is resized to a smaller size, the subtitles will be nice and sharp. It is a good idea to verify that the font (being used for rendering) is available on your system.  While the subtitles are being rendered, I also unravel the audio track into pure audio PCM. In a terminal window (using a MKV file with Japanese audio and English subtitles for this example), try:
```
mencoder <filename>.mkv -oac pcm -ovc lavc -noskip  -lavcopts vcodec=mpeg4:autoaspect=1:vbitrate=16000:vmax_b_frames=2 -alang jpn -slang eng -font Bitstream\ Vera\ Sans -spualign 2 -spuaa 20 -vf harddup -forceidx -of avi -o <filename>.avi
```

Note: Why use PCM? Two reasons:
1) All audio encoding methods know how to crunch PCM formatted audio. 
2) When you attempt to transcode the audio from one encoded format to another encoded format, you may run into a A/V synchronization issue. By going to PCM first and then to encoded audio, you avoid this problem. 

Once you have this intermediate file, the last step is to transcode the file into the target media format. Nokia phones use the 3GP media format. This website has the skinny on the correct conversion: 
[http://goinggnu.wordpress.com/2007/02/13/convert-avi-to-3gp-using-ffmpeg/]("http://goinggnu.wordpress.com/2007/02/13/convert-avi-to-3gp-using-ffmpeg/")

Use the newly created intermediate file as the input file. Once you have verified that your target video plays correctly, then delete the intermediate file. Good luck with your efforts!

---

### Post by yodaz on 2010-05-02
Thanks a lot for your very well documented answer. It is very helpful to me.

---

### Post by tkoco on 2010-05-02
> **yodaz said:**
> Thanks a lot for your very well documented answer. It is very helpful to me.

Glad to be of help. Now if you run into a problem with transcoding a MKV file, please let me know . I figured out how to split apart a MKV file into video and audio, process each part, and then merge the parts back into a correct/usable media file.

---

