---
title: "XBOX 360 Video Issue"
date: 2008-11-28
forum: Multimedia Software
---

### Post by fcm2005 on 2008-11-28
Hello.

I have some mkvs id like to play on my 360.Converting to mp4 results in files that are larger than the 4gb limit.A formatted hfs+ drive doesnt get around this issue for me.

Converting the mkvs to wmv via the following 

ffmpeg -i Whatever.mkv -s 1920x816 -b 8000k -vcodec wmv2 -ar 44100 -acodec wmav2 -ab 320k -ac 2 -y Whatever.wmv

Gives me a working video that gets around the 4gb limit.

If the movie consists of 2 mkv files how do i join them ?OR can i join the 2 wmv files at the end ? How do i do that ?

Also when i try to multithread i get an error that the codec doesnt have the ability to multithread.Is there a way around this ?

I am running ubuntu hardy heron 64.

Thanks for any insight you can provide.

---

