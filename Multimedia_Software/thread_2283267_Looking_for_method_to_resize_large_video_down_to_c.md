---
title: "Looking for method to resize large video down to certain file size."
date: 2015-06-20
forum: Multimedia Software
---

### Post by Rytron on 2015-06-20
Hi.

Is it possible to resize a video of e.g. 1.3GB to about 900MB via a terminal command or GUI way?

For example, I'd like the command to figure out the proper aspect ration and bit quality in order to reduce the video size down to 900MB.

Thanks.

---

### Post by SeijiSensei on 2015-06-20
You can do it with ffmpeg, but it takes some work: [https://trac.ffmpeg.org/wiki/Encode/H.264](https://trac.ffmpeg.org/wiki/Encode/H.264)

---

### Post by Rytron on 2015-06-21
> **SeijiSensei said:**
> You can do it with ffmpeg, but it takes some work: [https://trac.ffmpeg.org/wiki/Encode/H.264](https://trac.ffmpeg.org/wiki/Encode/H.264)

Hi SeijiSensei.

Those command in your link look very tricky.

I may just stick with commands such as these:
[LIST]
[*]ffmpeg -i input.mp4 -vf scale=720:576 output.mp4
[*]ffmpeg -i input.mkv -vf scale=576:-1 output_576.mkv
[*]
[*]ffmpeg -i input.mkv -vf scale=-1:720 output_720.mkv
[*]ffmpeg -i input.mp4 -vf scale=iw/2:-1 output.mp4
[/LIST]

---

### Post by FakeOutdoorsman on 2015-06-21
See the Two-pass example in the link provided by SeijiSensei:

[https://trac.ffmpeg.org/wiki/Encode/H.264#twopass](https://trac.ffmpeg.org/wiki/Encode/H.264#twopass)

Using two-pass method can allow you to achieve a desired output file size. (In the vast majority of all other cases, and if file size is not a priority, I recommend just using single pass with -crf).

If you don't feel like doing the math you can use a simple [bitrate calculator](https://www.3ivx.com/support/calculator/). You just need to tell it the duration and the desired output file size.

Example if your input is 1 hour long and you want an output of approximately 900 megabytes:

```
ffmpeg -y -i input -c:v libx264 -preset slow -b:v 1918k -pass 1 -an -f mp4 /dev/null && \
ffmpeg -y -i input -c:v libx264 -preset slow -b:v 1918k -pass 2 -c:a libfdk_aac -b:a 128k -movflags +faststart output.mp4
```
I'm not sure why someone added audio encoding to the first pass example in the wiki, but I've never needed to do that, so I omitted it.

---

### Post by Rytron on 2015-06-21
> **FakeOutdoorsman said:**
> See the Two-pass example in the link provided by SeijiSensei:

[https://trac.ffmpeg.org/wiki/Encode/H.264#twopass](https://trac.ffmpeg.org/wiki/Encode/H.264#twopass)

Using two-pass method can allow you to achieve a desired output file size. (In the vast majority of all other cases, and if file size is not a priority, I recommend just using single pass with -crf).

If you don't feel like doing the math you can use a simple [bitrate calculator](https://www.3ivx.com/support/calculator/). You just need to tell it the duration and the desired output file size.

Example if your input is 1 hour long and you want an output of approximately 900 megabytes:

```
ffmpeg -y -i input -c:v libx264 -preset slow -b:v 1918k -pass 1 -an -f mp4 /dev/null && \
ffmpeg -y -i input -c:v libx264 -preset slow -b:v 1918k -pass 2 -c:a libfdk_aac -b:a 128k -movflags +faststart output.mp4
```
I'm not sure why someone added audio encoding to the first pass example in the wiki, but I've never needed to do that, so I omitted it.

Hi FakeOutdoorsman.

So I will try a video of about 2h50m. I want it reduced to 900 MB from 1.6 GB. Do I run 2 lines or 1?

---

### Post by Rytron on 2015-06-21
Are the values in my commands for kiloBytes or kiloBits?

---

### Post by FakeOutdoorsman on 2015-06-21
> **Rytron said:**
> So I will try a video of about 2h50m. I want it reduced to 900 MB from 1.6 GB. Do I run 2 lines or 1?
You run two commands with two-pass encoding. Your commands may look something like this:

```
ffmpeg -y -i input -c:v libx264 -preset slow -b:v 592k -pass 1 -an -f mp4 /dev/null
ffmpeg    -i input -c:v libx264 -preset slow -b:v 592k -pass 2 -c:a libfdk_aac -b:a 128k -movflags +faststart output.mp4
```

> **Rytron said:**
> Are the values in my commands for kiloBytes or kiloBits?

The -b option takes a value in bits, so you have to add a "k" to make it kilobits (as shown in the example above).

---

### Post by Rytron on 2015-06-23
@FakeOutdoorsman I went with Handbrake in the end. But I will keep your info for future reference. Cheers.

---

