---
title: "How to convert videos having 5.1 audio to stereo using avconv"
date: 2013-12-06
forum: Multimedia Software
---

### Post by ras123 on 2013-12-06
Hi,

How to convert videos having 5.1 audio to stereo using avconv? can I use avformat? I don't need to change the video format.

Thanking You,
Ras

---

### Post by codenine75a on 2013-12-06
source: [http://libav.org/avconv.html#Audio-Options](http://libav.org/avconv.html#Audio-Options)

[h=2][5.9 Audio Options]("http://libav.org/avconv.html#toc-Audio-Options")[/h]   &#8216;-aframes number (*output*)&#8217;Set the number of audio frames to record. This is an alias for -frames:a. 
 &#8216;-ar[:stream_specifier] freq (*input/output,per-stream*)&#8217;Set the audio sampling frequency. For output streams it is set by default to the frequency of the corresponding input stream. For input streams this option only makes sense for audio grabbing devices and raw demuxers and is mapped to the corresponding demuxer options. 
 &#8216;-aq q (*output*)&#8217;Set the audio quality (codec-specific, VBR). This is an alias for -q:a. 
 &#8216;-ac[:stream_specifier] channels (*input/output,per-stream*)&#8217;Set the number of audio channels. For output streams it is set by default to the number of input audio channels. For input streams this option only makes sense for audio grabbing devices and raw demuxers and is mapped to the corresponding demuxer options. 
 &#8216;-an (*output*)&#8217;Disable audio recording. 
 &#8216;-acodec codec (*input/output*)&#8217;Set the audio codec. This is an alias for -codec:a. 
 &#8216;-sample_fmt[:stream_specifier] sample_fmt (*output,per-stream*)&#8217;Set the audio sample format. Use -sample_fmts to get a list of supported sample formats. 
 &#8216;-af filter_graph (*output*)&#8217;filter_graph is a description of the filter graph to apply to the input audio. Use the option "-filters" to show all the available filters (including also sources and sinks).  This is an alias for -filter:a.

---

### Post by ras123 on 2013-12-07
Could you please provide a command line example for how to use -ac option to convert 5.1 to stereo? I tried many, but all failed.

---

### Post by shantiq on 2013-12-08
> 

Audio options:
-aframes number     set the number of audio frames to record
-aq quality         set audio quality (codec-specific)
-ar rate            set audio sampling rate (in Hz)
-ac channels        set number of audio channels
-an                 disable audio
-acodec codec       force audio codec ('copy' to copy stream)
-vol volume         change audio volume (256=normal)




so     ```
avconv  -i   input.mp4  -c:v copy  **-ac 2 **output.mp4
```


copies video codec as is
changes audio channels to 2


i did this for mp4   but any extension you are using is fine

---

### Post by ras123 on 2013-12-08
Hi,
Thanks it is working, I used a codec option to change the audio codec as follows,

> avconv -i input.mkv -c:v copy -c:a libmp3lame -ac 2 ouput.mkv

---

### Post by Yellow Pasque on 2013-12-08
Great. Please mark thread SOLVED.

---

### Post by andrew.46 on 2013-12-10
> **ras123 said:**
> Hi,
Thanks it is working, I used a codec option to change the audio codec as follows,

Perhaps add in some quality settings for lame, I cannot remember the defaults but they might not be kind to your audio...

---

