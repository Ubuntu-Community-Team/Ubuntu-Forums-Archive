---
title: "m4a --&gt; mp3"
date: 2006-12-27
forum: Multimedia &amp; Video
---

### Post by Moisteh on 2006-12-27
I googled mp4 to mp3 converter for ubuntu, nothing showed up....

So does anybody know how to convert mp4s to mp3s?

I need this done because my sansa does not play m4a's, any help woudl be greatly appreciated.

Thanks,
Moisteh.

---

### Post by KenSentMe on 2006-12-27
You could try ffmpeg for the conversion. Never really tested it with audio, but i think it will work.

Do this in console:

ffmpeg -i original_filename -sameq -acodec mp3 -o mp3 output_filename.mp3

Please post the results. You can also set options. See man ffmpeg for those.

---

