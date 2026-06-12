---
title: "fish-eye/barrel distortion correction for video"
date: 2011-10-04
forum: Multimedia Software
---

### Post by ghat on 2011-10-04
hi

I have a Canon Vixia AVCHD camcorder, and recently purchased a Opteka Fisheye lens for the camera...

[http://www.youtube.com/embed/1lAhP3BOi6k](http://www.youtube.com/embed/1lAhP3BOi6k)

I have successfully used ffmpeg with Canon M2TS files, before and was wondering if there is a way in ffmpeg to apply a barrel-distortion correction filter to remove the fisheye effect of the lens... 

Ideally want to apply this correction in a batch script to all video clips which have used the fish-eye lens, and am not looking for a full-video-editor solution...

Ghat
> 
I understand that conceptually one piece of information would be missing in the setup is the angle of view, which would be variable as the camera moves... 
the camera is a 2D camera, so that information in not really grabbed in the capture... not sure how the avisynth defish works... in windows... 


---

### Post by FakeOutdoorsman on 2011-10-05
I'm not sure if FFmpeg can provide the solution for this, but your best bet with FFmpeg is probably [lenscorrection](http://frei0r.dyne.org/gallery?filter=lenscorrection) from frei0r. You will have to compile FFmpeg to support frei0r because the version from the repository has no filtering capability last I checked:
```
sudo apt-get install frei0r-plugins-dev
```
Then install FFmpeg: [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Add to the FFmpeg configure line:
```
--enable-frei0r
```
Then use it:
```
ffmpeg -i input -vcodec libx264 -preset medium -crf 24 -vf frei0r=lenscorrection:0.5:0.5:0.5:0.5 -acodec copy output.mp4
```
I didn't test this and I'm unsure of the proper values for lenscorrection. See the [code](http://frei0r.dyne.org/gallery?filter=lenscorrection) for the filter to get a better idea, specifically:
```
{
        case 0:
                info->name = "xcenter";
                info->type = F0R_PARAM_DOUBLE;
                info->explanation = "";
                break;
        case 1:
                info->name = "ycenter";
                info->type = F0R_PARAM_DOUBLE;
                info->explanation = "";
                break;
        case 2:
                info->name = "correctionnearcenter";
                info->type = F0R_PARAM_DOUBLE;
                info->explanation = "";
                break;
        case 3:
                info->name = "correctionnearedges";
                info->type = F0R_PARAM_DOUBLE;
                info->explanation = "";
                break;
        case 4:
                info->name = "brightness";
                info->type = F0R_PARAM_DOUBLE;
                info->explanation = "";
                break;
}
```

If that doesn't seem to work or if you're more familiar with AviSynth see:
[HOWTO: AviSynth video processing with WINE](http://ubuntuforums.org/showthread.php?t=1333264)

---

