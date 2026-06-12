---
title: "FFMPEG - FLV will not play completely through"
date: 2008-06-29
forum: Multimedia Software
---

### Post by c.wilson on 2008-06-29
I have been going crazy the last few days trying to get this to work. 

I'm using Ubuntu server and for some reason I can not get FFMPEG to convert the file correctly.

This maybe more of a FFMPEG help question but I can't seem to find a forum for FFMPEG. 

For some reason the video stops after playing a little bit more then half. Yet, if I encode the video from the server command line then upload the FLV it works fine. 

I'm at a lose. Any ideas?

Here is the code I am using.

```
    exec("/bin/cp {$file} {$file_orignal}");

    exec("/usr/bin/ffmpeg -i {$file_orignal} -ar 22050 -f flv {$file_converted_flv}");
    exec("/usr/bin/flvtool2 {$file_converted_flv}");
    exec("/usr/bin/ffmpeg -i {$file_orignal} -an -ss 0.010 -an -r 1 -vframes 1 -y -f mjpeg {$file_converted_jpg}");
```

---

### Post by radopenev on 2008-07-30
Hi,
install mencoder and try this:
$flash_temp="blabla/blabla.flv";
$flash="blabla/blablaEND.flv";
exec ( "/usr/bin/mencoder ". $uploadfile ." -o ". $flash_temp ." -of lavf -oac mp3lame -lameopts abr:br=56 -ovc lavc -lavcopts vcodec=flv:vbitrate=400:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -vf scale=".$_POST[width].":".$_POST[height]." -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames -srate 22050" );

 exec("/usr/bin/flvtool2 -Uv ". $flash_temp." ". $flash);

Hope this helps!
Good luck!:)

---

