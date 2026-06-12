---
title: "*Good* m4a encoding?"
date: 2010-03-17
forum: Multimedia Software
---

### Post by lesath on 2010-03-17
I have a large number of mp3 files that I wish to convert to m4a format. When I used Windows, I had converted some of my music collection already to m4a to store on my phone. The bitrate I used for this was 54kbps and I found it to be indistinguishable from 192kbps mp3. Now, maybe my phone's file converter thingy was using some different codec or something weird like that -- eAAC? -- to be honest, I don't know very much about this. All I know is that when I used SoundKonverter with faac to convert a file to m4a at that bitrate, the quality was abysmal.

The test file I used was an mp3 at 192kbps which I had already converted to m4a at 54kbps on Windows. Listening to the two side by side, I could hear absolutely no difference. Granted, I'm aware that my ears are somewhat less sensitive to audio compression than others', so there were probably differences others would have noticed that I didn't, but the point is that it Worked For Me. On the other hand, when I converted the exact same mp3 file at the same bitrate using SoundKonverter, it sounded like I had played the song out of my laptop speakers and recorded it using a microphone. I will gladly post short samples of the two m4as, if people are skeptical.

Again, I'm guessing my phone's software has some weird proprietary thing that makes it better, or *something*, but my question is whether it's possible to get this quality using Linux. Will I have to reboot into Windows and use my phone's awful, bloated, memory-leaking conversion software every time I want to put music on my phone?

(PS - Web conversion is not an option, due to a bandwidth cap imposed by my ISP.)

---

### Post by Chronon on 2010-03-17
Please reconsider.  Transcoding from a lossy format to another lossy format can cause considerable reduction in sound quality.

HE-AAC is a higher quality format than LC-AAC (the standard one).  It uses some fancy tricks to perform much better than LC-AAC at low bitrates.  This is probably the difference you're noticing.  However, if it is at all possible, you should still encode the HE-AAC from lossless source.  It seems that faac/libfaac0 should be able to do HE-AAC.

---

### Post by lesath on 2010-03-18
I have considered. If you read my post, you'll notice that I said that I have already converted many files in this way and I don't notice the sound quality difference, and if I don't notice, why should I care? I actually began the original post with a paragraph asking to be spared any lectures about this, but I deleted it because I felt it was rude and unnecessary. Perhaps it was necessary after all! I realize your intentions are good, but I find it irksome that whenever I ask a question about how to do something on Linux, the main response I get is "you shouldn't be using [this method, solution] or doing [this thing], you should just use the software or methods of my preference instead even if it's not what you want."

If libfaac/faac can encode as HE-AAC, why doesn't it? Or is it just that SoundKonverter doesn't provide the option? Is there another program I might use that does?

---

### Post by andrew.46 on 2010-03-18
Hi lesath,

> **lesath said:**
>  Is there another program I might use that does?

Have you tried the Nero AAC Encoder? Pretty straightforward commandline use, bear in mind that it only accepts wav as input...

Andrew

---

### Post by Chronon on 2010-03-19
> **lesath said:**
> I have considered. If you read my post, you'll notice that I said that I have already converted many files in this way and I don't notice the sound quality difference, and if I don't notice, why should I care? I actually began the original post with a paragraph asking to be spared any lectures about this, but I deleted it because I felt it was rude and unnecessary. Perhaps it was necessary after all! I realize your intentions are good, but I find it irksome that whenever I ask a question about how to do something on Linux, the main response I get is "you shouldn't be using [this method, solution] or doing [this thing], you should just use the software or methods of my preference instead even if it's not what you want."

If libfaac/faac can encode as HE-AAC, why doesn't it? Or is it just that SoundKonverter doesn't provide the option? Is there another program I might use that does?

Actually you only said this: 
> When I used Windows, I had converted some of my music collection already to m4a to store on my phone. The bitrate I used for this was 54kbps and I found it to be indistinguishable from 192kbps mp3. 
This does not actually tell the reader that you transcoded from mp3 to m4a, so please spare me the attitude.  I actually totally agree that if the result is transparent to your ear then that's all that matters.  Good luck.

---

