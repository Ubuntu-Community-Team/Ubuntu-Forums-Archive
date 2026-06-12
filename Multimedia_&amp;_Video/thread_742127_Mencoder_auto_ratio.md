---
title: "Mencoder auto ratio?"
date: 2008-04-01
forum: Multimedia &amp; Video
---

### Post by Dark Severance on 2008-04-01
Currently I use a script that uses mencoder to convert my .avi to .flv files. The problem I encounter is when I have something that is 16:9 instead of 4:3 and then I have to manually convert it because I'm not sure how have the process auto detect the ratio of the source file.

Here is what I use when I'm working with the script, that converts my files. However the scale is only for 4:3 videos. 
```
nice mencoder $filename.avi -o $filename.flv -of lavf -oac mp3lame -lameopts abr:br=64 -ovc lavc -lavcopts vcodec=flv:vbitrate=400:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -vf scale=420:340 -srate 22050
```

Here is what I use when I wan to convert something that is a 16:9 aspect ratio so it does letterbox.
```
mencoder test.avi -o test2scale.flv -oac mp3lame -lameopts cbr:mode=2:br=64 -af resample=44100 -srate 22050 -ofps 20 -ovc lavc -lavcopts vcodec=flv:mbd=2:cbp:trell:vbitrate=400 -vf scale=420:276 -vf-add expand=:240 -ffourcc XVID
```

Is there some option in Mencoder that knows if it is 16:9 to do letterbox otherwise use 4:3 aspect ratio?

---

### Post by disturbed1 on 2008-04-02
man mplayer
> 
scale[=w:h[:ilaced[:chr_drop[:par[:par2[:presize[:noup[:arnd]]]]]]]]
              Scales the image with the software scaler (slow) and performs a YUV<->RGB colorspace conversion (also see -sws).

                 <w>,<h>
                      scaled width/height (default: original width/height)
                      NOTE:  If  -zoom  is  used,  and underlying filters (including libvo) are incapable of scaling, it defaults to d_width/
                      d_height!
                          0:   scaled d_width/d_height
                         -1:   original width/height
                         -2:   Calculate w/h using the other dimension and the prescaled aspect ratio.
                         -3:   Calculate w/h using the other dimension and the original aspect ratio.
 -(n+8): Like -n above, but rounding the dimension to the closest multiple of 16.

Try
-vf scale=420:-11,expand=:340

---

### Post by Dark Severance on 2008-04-03
That did work although it placed a border around the whole video that I didn't like in the playback. However I found out the real issue. Apparently mencoder was doing the autoaspect properly. However when it is playing back on the net it wasn't doing it in letterbox. It was in my testing just not  when it was being used on the actual site.

This was how it should look at playback:
[http://www.pcxvideo.com/test.htm](http://www.pcxvideo.com/test.htm)

This is how it is looking on playback:
[http://www.pcxvideo.com/forum/index.php?autocom=video&CODE=details&id=22](http://www.pcxvideo.com/forum/index.php?autocom=video&CODE=details&id=22)

It looks like in the embed code the "flashvar" variables are what is messing it up. Originally I had:```
flashvars="linktarget=_self&repeat=list&shuffle=false&linkfromdisplay=true&file={$this->ipsclass->base_url}autocom%3Dvideo%26CODE%3Dplaylist%26id%3D{$out['id']}&recommendations={$this->ipsclass->base_url}autocom%3Dvideo%26CODE%3Drecommendations%26id%3D{$out['id']}"
```

If I remove the playlist and recommendations part, it will playback in letterbox properly. But the issue is then a playlist or similar videos submitted by that ID no longer appear at the end. So that leaves the issue of how to keep the recommendation playlist in but not have it affect the aspect ratio on the playback.

---

