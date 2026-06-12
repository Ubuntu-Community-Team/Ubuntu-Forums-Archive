---
title: "Stereo vs Joint Stereo?"
date: 2009-03-29
forum: Multimedia Software
---

### Post by casmok on 2009-03-29
I didnt quite understand exactly what Joint stereo exactly was. So I googled around a bit and vaguely understand what it is but am far from clear which I should use when I rip CD tracks to MP3 with variable bit rate.
From what I read it results in a slightly smaller file size than regular stereo. There also seems to be some controversy about its merits!

So if I'm riping to MP3 using VBR which should I use? I'm not to concerned  about only a slight reduction in file size. I AM bothered about maximum quality.

---

### Post by batharoy on 2009-03-29
> Whoever was responsible for incorporating Joint Stereo into mp3 made two big mistakes (IMHO):

The first mistake was in naming the technique "Joint Stereo" - the very name suggests to people that the Left and Right stereo channels are "joined" together.

The second mistake was to give this name to two completely different compression enhancement techniques: Intensity Stereo and Mid/Side Stereo. The two techniques have nothing in common other than the general principle of (slightly paraphrasing the FhG quote) "exploiting stereophonic irrelevancies and redundancies".

The name "Joint Stereo" could reasonably be applied to "Intensity Stereo", which does, in fact, combine Left and Right audio channels at higher frequencies. The reasoning behind this is that the human ear is very insensitive to the direction of sounds as we approach the upper limit of our hearing range. Upon decoding the compressed signal, the stereo image is partially restored by applying different scaling factors to the Left and Right channels. However, this technique is far from transparent.

The main point to appreciate about Intensity Stereo is that it was only ever intended to be used in situations where - for whatever reason - the bitrate needs to be restricted to 96k or less, but where some form of stereo signal is desired. In these circumstances, it is generally preferable to accept some loss of stereo definition than to attempt to encode in full stereo with insufficient bits. Most of the music which circulates around the Internet these days tends to be encoded at bitrates of 128k or higher. Above 96k, all the current generation of encoders will default to Mid/Side Joint Stereo, and hence, most music fans will rarely encounter Intensity Stereo.

The only exception to this is the old Xing encoder, which used Intensity Stereo at higher bitrates. This is one of the reasons why Xing has gained such a bad reputation.

And one final point: to a lesser extent, the human ear is also relatively insensitive to direction at very low frequencies. Anyone who uses a speaker system with a centralised sub-woofer is utilising a form of Intensity Stereo, and demonstrating the fact that full stereo is not really necessary at certain frequencies.

The form of "Joint Stereo" which you will invariably encounter in any recent audio encodings is Mid/Side Stereo. As mentioned above, M/S Stereo has been poorly served by being labelled as "Joint" Stereo; the Left and Right channels are not "joined" in any meaningful sense of the word. The numerical data which defines the left and right audio signals is simply rearranged mathematically and stored in a matrix form - but, in such a way that the original channels can be easily and losslessly reconstituted. Matrix Stereo would be a more accurate description. The basic theory behind Mid/Side Stereo is quite simple to understand - if you are not afraid of a little schoolboy algebra! 

Source:
[http://harmsy.freeuk.com/mostync/]("http://harmsy.freeuk.com/mostync/")

---

### Post by logos34 on 2009-03-29
> **casmok said:**
> So if I'm riping to MP3 using VBR which should I use? I'm not to concerned  about only a slight reduction in file size. I AM bothered about maximum quality.

I'd use joint-stereo with the lame mp3 encoder (latest stable version or even optimized) at VBR setting -V 2 (or better, but you achieve transparancy at ~192k). Lame is the standard.  This will give you optimal cd-quality lossy compression and smaller file size.

To add to what batharoy posted, there also this page at hydrogenaudio:

> [http://wiki.hydrogenaudio.org/index.php?title=Joint_stereo](http://wiki.hydrogenaudio.org/index.php?title=Joint_stereo)

Joint stereo

Joint stereo is a property of an audio data stream and means that the stream supports more than one method of stereo coding, such as SS ("simple" or "L/R" stereo), MS ("mid-side" stereo), or IS ("intensity" stereo). A joint stereo stream may still only employ a single coding method, but for the sake of efficiency or quality may switch between methods on a frame or even sub-frame basis.

For example, a high-bitrate "joint stereo" MP3 file may contain a mixture of SS and MS frames, or it may contain all SS frames or all MS frames. A non-"joint stereo" MP3 will never contain a mixture of frame types.

Very few MP3 encoders make ideal decisions about what mode to use from frame to frame in joint stereo files, so there has long been a misconception that joint stereo means too many (perhaps 100%) mid-side frames, which is rarely desirable in stereo music and can result in haphazard channel separation and/or suboptimal quality as measured by other criteria.

"Joint stereo coding methods" in prose generally refers to whatever alternatives to simple (L/R) stereo coding are supported by a particular format, even though simple stereo is also an option.

..

Whenever a signal is concentrated in the middle of the stereo image (i.e. more mono-like), **mid-side stereo can achieve a significant saving in bitrate,** since one can use fewer bits to encode the side-channel. **Even more important is the fact that by applying the inverse matrix in the decoder, the quantization noise becomes correlated and falls in the middle of the stereo image, where it is masked by the signal.**

**Unlike intensity stereo which destroys phase information, mid-side coding keeps the phase information pretty much intact. Correctly implemented mid-side stereo does very little or no damage to the stereo image and increases compression efficiency either by reducing size or increasing overall quality.**

Intensity Stereo

Intensity stereo coding is a method that achieves a saving in bitrate by replacing the left and the right signal by a single representing signal plus directional information. This replacement is psychoacoustically justified in the higher frequency range since the human auditory system is insensitive to the signal phase at frequencies above approximately 2kHz.

Intensity stereo is by definition a lossy coding method thus it is primarily useful at low bitrates. For coding at higher bitrates only mid-side stereo should be used.


Additional information

Some more details about joint stereo & mid-side coding:

    * Bugs and/or not-optimized encoders may implement mid-side coding incorrectly, making mid-side coding sound worse than simple stereo, while in reality (see the formulas above) there should be no difference in quality between mid-side stereo and simple stereo. 

    * Some older MP3 encoders interpret "joint stereo" to mean 100% mid-side, which for stereo music is almost certainly less than ideal. 

    * **Modern/optimized encoders will use mid-side coding or simple stereo coding as necessary, depending on the correlation between the left and right channels. **

---

### Post by casmok on 2009-03-30
OK thanks for those links. I sort of understand whats going on I think, emphasis on "sort of" here.

> I'd use joint-stereo with the lame mp3 encoder (latest stable version or even optimized) at VBR setting -V 2 (or better, but you achieve transparancy at ~192k). Lame is the standard. This will give you optimal cd-quality lossy compression and smaller file size.

 
But if I stick with regular Stereo I'm not going to lose anything am I? other than disk space

---

### Post by logos34 on 2009-03-30
> **casmok said:**
> OK thanks for those links. I sort of understand whats going on I think, emphasis on "sort of" here.


 
But if I stick with regular Stereo I'm not going to lose anything am I? other than disk space

right, I think quality is only an issue if you were, say, to rip at lower bitrates mono stuff that had been remixed for 2-channel stereo output (like so much is nowadays), where apparently sound degradation can occur

---

### Post by casmok on 2009-03-30
> **logos34 said:**
> right, I think quality is only an issue if you were, say, to rip at lower bitrates mono stuff that had been remixed for 2-channel stereo output (like so much is nowadays), where apparently sound degradation can occur

Thanks. Got it now!. And thanks for you help previously too:)
Mike

---

