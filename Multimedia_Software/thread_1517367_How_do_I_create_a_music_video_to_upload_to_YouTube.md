---
title: "How do I create a music video to upload to YouTube?"
date: 2010-06-24
forum: Multimedia Software
---

### Post by fredbird67 on 2010-06-24
I've got another dumb question.  I've been looking for how to do this within Ubuntu Forums and I can't seem to find a HowTo guide for this one.  It seems like hundreds of people have taken MP3s or whatever of their favorite music and uploaded them to YouTube, either having a still photo or slide show as the video, and I'd like to learn how to do that within Linux.

Can anyone help get me started here?

Thanx in advance,
Fred in St. Louis

---

### Post by OxentroT on 2010-06-24
Most of these programs are easy to learn how to use. For uploading the footage you have to create a youtube account and go to your area and there you will be able to upload your file(s)

The link I have provided you below may help you in finding the right software for you.

[Click Here]("http://techcityinc.com/2009/02/04/top-10-free-video-editors-for-ubuntu-linux/")

:guitar:

---

### Post by Kenjitamura on 2010-06-25
I was looking for opensource software for creating music videos a little over a year ago in linux and I gotta say everything I tried at the time felt like a flop.  Back to Ubuntu after an unpleasant affair with Windows (lost my own computer) and there is a program that article doesn't list.  It's super simple and reminds me of the video editing software apple comes with and is called Openshot.  I created an AMV (Animated Music Video, taking clips from cartoons and having them go along with the song) and everything went great.  Not saying it's better than any of the listed programs (especially as most of them have worked out their bugs in the past year)but I think it'll easily do what you need it to do, here is it's interface 
[IMG]http://i698.photobucket.com/albums/vv346/kenjitamura/openshot.jpg[/IMG]
The best part is encoding the resulting file is super easy in Openshot.

---

### Post by ron999 on 2010-06-25
Hi
The OpenShot program in the post above looks impressive.:p

I have used a command-line program called **dvd-slideshow**.

And here is a cheap and cheerful command using ffmpeg:-
```
ffmpeg -loop_input -i foo.jpg -i foo.mp3 -shortest -acodec copy foo.mp4

```

Here's one I prepared earlier:-[http://www.youtube.com/watch?v=kYRkjpZhoEE&fmt=18]("http://www.youtube.com/watch?v=kYRkjpZhoEE&fmt=18")
:guitar:

---

### Post by fredbird67 on 2010-06-28
Ah...sounds good.  I'll get around to trying that out whenever I get the chance.  Thanx, y'all! :-)

---

