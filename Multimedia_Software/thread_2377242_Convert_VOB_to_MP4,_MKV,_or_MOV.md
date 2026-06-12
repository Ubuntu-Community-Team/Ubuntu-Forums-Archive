---
title: "Convert VOB to MP4, MKV, or MOV"
date: 2017-11-10
forum: Multimedia Software
---

### Post by AbleTassie on 2017-11-10
I have some video files that are MOV, and I want to convert them to  MP4, MKV, or MOV so that they work with a certain device I have. MP4 would probably be best, since I am most familiar with that. Almost all the files in the folder in question that I want to convert are MOV files and range in size from 1 GB down to 100KB. There are a few BUP and IFO files that are smaller and range from about 50 to 16 KB. I'm not sure of the significance of these .BUP and .IFO files.

QUESTION: Is there software to make the conversion?

Thanks,

A.

---

### Post by shantiq on 2017-11-11
Please see what is in these files 

Place all VOBs in a folder then >>

```
 sudo apt install mediainfo
```

```
 mediainfo   *VOB*
```

so to convert keeping highest possible values shown by mediainfo
to use for a "bulk convert"  [change the values you found for audio and video and lower if you want smaller size]


```
for f in *.VOB ; do ffmpeg -i "$f" -b:v 3000k  -b:a 128k "${f%.*.VOB}.mp4"; done


```

---

### Post by YuiDaoren on 2017-11-11
**Handbrake** will do that, easy peasy with a GUI. It's in the repositories.

---

### Post by Yellow Pasque on 2017-11-11
@shantiq: I believe the OP wants to convert VOB's (as the title says) and accidentally said s/he wants to convert MOV's to MOV's/MP4/MKV, as that wouldn't make sense.

---

### Post by shantiq on 2017-11-11
> **Temüjin said:**
> @shantiq: I believe the OP wants to convert VOB's (as the title says) and accidentally said s/he wants to convert MOV's to MOV's/MP4/MKV, as that wouldn't make sense.


you are so right here T ...   and changed the line therefore
she is describing what is in a VIDEO_TS folder obviously ....     and the penny dropped for you before it did me  ...    i thought something was odd :]

---

### Post by VanillaMozilla on 2017-11-14
I second the suggestion to use Handbrake.  As I recall, you just import the whole directory, not the individual files, and Handbrake will begin to analyze it and present yo with sections to choose from.  If it doesn't appear to work instantly, persist in the effort and check back here.

I do not suggest using ffmpeg or avconv as suggested by shantiq.  That is an excellent method for some cases, but it is likely to be very inappropriate in your case.  VOB files from a DVD could well be a horrible mess internally.  That's just the way a DVD is put together.  Handbrake will sort that out neatly and simply, but ffmpeg will not.  You could get lucky, but you might as well just do it the easy way with Handbrake.

---

### Post by shantiq on 2017-11-14
> **VanillaMozilla said:**
> I second the suggestion to use Handbrake.  As I recall, you just import the whole directory, not the individual files, and Handbrake will begin to analyze it and present yo with sections to choose from.  If it doesn't appear to work instantly, persist in the effort and check back here.

I do not suggest using ffmpeg or avconv as suggested by shantiq.  That is an excellent method for some cases, but it is likely to be very inappropriate in your case.  VOB files from a DVD could well be a horrible mess internally.  That's just the way a DVD is put together.  Handbrake will sort that out neatly and simply, but ffmpeg will not.  You could get lucky, but you might as well just do it the easy way with Handbrake.


Totally right Vanilla !    i did not realize it was a DVD folder   so yes Handbrake is by far the best tool here  ....    i Leave the earlier info anyway but yes use handbrake   pick mp4 or mkv

---

### Post by AbleTassie on 2017-11-14
Thanks to everybody. I had composed a previous post acknowledging that yes, there is a typo in the original post, as was picked up. But somehow it was never actually posted -I'm not sure why. I have downloaded and installed handbrake and will give it a try and report back. 

Thanks again,

A.

---

