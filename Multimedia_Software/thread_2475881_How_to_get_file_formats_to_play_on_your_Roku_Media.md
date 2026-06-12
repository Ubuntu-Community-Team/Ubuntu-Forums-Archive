---
title: "How to get file formats to play on your Roku Media Player smart tv"
date: 2022-06-10
forum: Multimedia Software
---

### Post by jonfisher on 2022-06-10
If you can't get a video file format, such as mp4 or avi, or even an mkv, to play on your Roku Media Player smart tv, I have found that if you run the file thorugh MKVToolnix, turning it into an mkv file, it will often work.  Simply click "Start Multiplexing" and it takes just seconds to convert it over.  This will also usually make videos that look scrambled to work also...

---

### Post by TheFu on 2022-06-11
> **jonfisher said:**
> If you can't get a video file format, such as mp4 or avi, or even an mkv, to play on your Roku Media Player smart tv, I have found that if you run the file thorugh MKVToolnix, turning it into an mkv file, it will often work.  Simply click "Start Multiplexing" and it takes just seconds to convert it over.  This will also usually make videos that look scrambled to work also...

Don't confuse a container  (mp4, mkv, avi, webm) with a codec.  They are very, very, different.  Some videos are just poorly created and the mkvtools will re-index them to a standard format, without altering the video or audio codecs used.

Different models of Roku devices support different video and audio codecs.  These are casually called vcodec and acodec which specifies the standard for the decoding hardware/drivers to use to create video and audio that can be displayed on a TV or monitor or projector.  For a long time, Rokus only supported mp3, aac, vorbis and DD audio along with h.264 video.  They didn't support DD+ or AC3 DTS at all, so audio needed to be passed through untouched to an audio device (typically an audio receiver) or another audio track with stereo and a supported acodec needed to be added to the container.

MKV is a container that can hold pretty much any video and audio and text and captions and subtitles along with multiple tracks of each which can be selected by the player software as desired.  I typically have 1 video track and all the different language tracks along with the different audio encodings - DTS, DD, AAC, and I'll convert the English highest quality audio to multi-channel vorbis to make picking from a menu on the player easy/automatic.  I'll also retain all the subs and captions for every language.  MKV containers handle this easily.

Because my players all support h.264 and mpeg2 video, I tend to use those.  A few of my devices can handle h.265, but encoding to that vcodec is 4x harder than using h.264.  There is greater file size efficiency when using h.265 - those videos are about 50% smaller than the same encoded into h.264.  Plus, my Roku3 won't play h.265 video.

Because Roku does so much tracking, probably 5x more than Plex server does, I use the roku only for streaming DRM'd content.  If I can stream content without DRM, I'll use OSMC/Kodi instead which don't phone home at all.  I don't like being tracked and much prefer the Kodi interface to Roku's.

**So, if you really want a foolproof way to convert content that a Roku can play, use Handbrake and transcode the input video to h.264 video,  AAC audio, and put it into an MKV container.**

---

### Post by SeijiSensei on 2022-06-13
My Roku plays Summertime Render which is about as up-to-date as you can be.

The [EMBER] encodes are in H.265 and AAC with ASS subtitles in the MKV container. Need to turn on closed captioning for the subs.

---

### Post by jonfisher on 2022-06-15
> **TheFu said:**
> Don't confuse a container  (mp4, mkv, avi, webm) with a codec.  They are very, very, different.  Some videos are just poorly created and the mkvtools will re-index them to a standard format, without altering the video or audio codecs used.

Different models of Roku devices support different video and audio codecs.  These are casually called vcodec and acodec which specifies the standard for the decoding hardware/drivers to use to create video and audio that can be displayed on a TV or monitor or projector.  For a long time, Rokus only supported mp3, aac, vorbis and DD audio along with h.264 video.  They didn't support DD+ or AC3 DTS at all, so audio needed to be passed through untouched to an audio device (typically an audio receiver) or another audio track with stereo and a supported acodec needed to be added to the container.

MKV is a container that can hold pretty much any video and audio and text and captions and subtitles along with multiple tracks of each which can be selected by the player software as desired.  I typically have 1 video track and all the different language tracks along with the different audio encodings - DTS, DD, AAC, and I'll convert the English highest quality audio to multi-channel vorbis to make picking from a menu on the player easy/automatic.  I'll also retain all the subs and captions for every language.  MKV containers handle this easily.

Because my players all support h.264 and mpeg2 video, I tend to use those.  A few of my devices can handle h.265, but encoding to that vcodec is 4x harder than using h.264.  There is greater file size efficiency when using h.265 - those videos are about 50% smaller than the same encoded into h.264.  Plus, my Roku3 won't play h.265 video.

Because Roku does so much tracking, probably 5x more than Plex server does, I use the roku only for streaming DRM'd content.  If I can stream content without DRM, I'll use OSMC/Kodi instead which don't phone home at all.  I don't like being tracked and much prefer the Kodi interface to Roku's.

**So, if you really want a foolproof way to convert content that a Roku can play, use Handbrake and transcode the input video to h.264 video,  AAC audio, and put it into an MKV container.**

Thanks for the very useful and very educational information!

I have found that many files that VLC won't play, irregardless of using Roku, then running it through MKVtoolinix clears them right up, also.

---

