---
title: "you tube"
date: 2009-07-11
forum: Multimedia Software
---

### Post by chethan.md on 2009-07-11
:guitar:


is there any software to download you tube videos  as  we did  in windows

---

### Post by Marlonsm on 2009-07-11
There are many extensions for Firefox that do it.
I think DownThemAll can do it.
A [quick search]("https://addons.mozilla.org/en-US/firefox/search?q=youtube&cat=1%2C38") shows lots of them.

---

### Post by Hamchan on 2009-07-11
You don't need any software to download youtube videos. After your computer has completely loaded the video, just check the /tmp folder and you'll find the video sitting there. Move the video to any other place (or else it gets automatically deleted) and you have your video.

---

### Post by d_liebscher on 2009-07-11
Hi,

another nice plugin for Firefox is "Video DownloadHelper".

---

### Post by lovinglinux on 2009-07-11
> **d_liebscher said:**
> Hi,

another nice plugin for Firefox is "Video DownloadHelper".

+1

You don't need to look into the tmp folder, since Firefox 3 has a feature that allows you to downloaded the media embedded on a web site. Click the site icon next to the address bar, then click "More Information" then "Media".

---

### Post by vinutux on 2009-07-11
Best thing is after complete the streaming..you can get flv in temp folder

copy video besfore closing window or tab of video.........

temp folder is here..../home/yourusername/.mozilla/firefox-3.5/xschkijc.default/


Youcan download highquality mp4 

for this just bookmark this script

[COLOR="Red"]javascript:if(document.location.href.match(/http:\/\/[a-zA-Z\.]*youtube\.com\/watch/)){document.location.href='http://www.youtube.com/get_video?fmt=18&video_id='+swfArgs['video_id']+'&t='+swfArgs['t']}[/COLOR]

copy this script and paste it in location of new bookmark

after selecting any youtube video click on this bookmark and download mp4 file......................):P

---

### Post by vinutux on 2009-07-14
> **desertfish said:**
> [SIZE=3]This **[YouTube downloader]("http://www.leawo.com/youtube-download/")** can also download videos from other websites like Google Video, iFilm, Myspace, Daily Motion, etc.
[/SIZE]

Itz a Windows app ...not working under linux (may be with wine)

.

---

### Post by lisati on 2009-07-14
*cough* isn't that against the YouTube terms and conditions?

From [http://www.youtube.com/t/terms](http://www.youtube.com/t/terms)

> B. You may access User Submissions solely:

    * for your information and personal use;
    * as intended through the normal functionality of the YouTube Service; and
    * for Streaming.

"Streaming" means a contemporaneous digital transmission of an audiovisual work via the Internet from the YouTube Service to a user's device in such a manner that the data is intended for real-time viewing and not intended to be copied, stored, permanently downloaded, or redistributed by the user. Accessing User Videos for any purpose or in any manner other than Streaming is expressly prohibited. User Videos are made available "as is."

edit: also see [this thread]("http://ubuntuforums.org/showthread.php?t=116516")

---

### Post by kerry_s on 2009-07-14
i use greasemonkey & a userscript.

---

### Post by vinutux on 2009-07-14
Check this FF extension realy very helpfull one.........

**[https://addons.mozilla.org/en-US/firefox/addon/10137]("https://addons.mozilla.org/en-US/firefox/addon/10137")**

.

---

### Post by duleep on 2011-05-26
FireFox 4 don't store flv video file in home/temp folder anyone can know ubuntu 11.04 where is temporarily keep flv files

---

### Post by nothingspecial on 2011-05-26
They are stored in your ram.

---

### Post by duleep on 2011-05-31
> **Hamchan said:**
> You don't need any software to download youtube videos. After your computer has completely loaded the video, just check the /tmp folder and you'll find the video sitting there. Move the video to any other place (or else it gets automatically deleted) and you have your video.
i can't find flv file in temp folder in ubuntu 11.04 so anyone can tell where that temporary file store in firefox 4 ubuntu 11.04

---

### Post by nothingspecial on 2011-06-04
Type this

```
f="$(ls -l  /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && echo /proc/$(pgrep -f flashplayer)/fd/"$f"
```

The video is the number.

You are not legally allowed to copy it to your hard disk.

---

### Post by beew on 2011-06-04
Why are there so many complicated solutions? Just install the downloadhelper addon for FF, problem solved.
[https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/](https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/)

Umplayer, minitube and Acetoneiso also have options to record/download Youtube videos. But the FF addon is simplest and works for other video sites as well.

---

### Post by nothingspecial on 2011-06-04
> **beew said:**
> Why are there so many complicated solutions? Just install the downloadhelper addon for FF, problem solved.
[https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/](https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/)

Umplayer, minitube and Acetoneiso also have options to record/download Youtube videos. But the FF addon is simplest and works for other video sites as well.

Your post doesn't answer the question, which is not 'how do I illegaly download youtube videos?', but where are they stored?



> **duleep said:**
> i can't find flv file in temp folder in ubuntu 11.04 so anyone can tell where that temporary file store in firefox 4 ubuntu 11.04

The reason my answer is "complicated" is that, to stop it being so easy for linux users to copy the temporary files to their hard disc, firefox has changed things. 

My "complicated" answer finds them. It doesn't copy them, against youtube's terms and conditions :roll:

---

### Post by beew on 2011-06-04
> **nothingspecial said:**
> Your post doesn't answer the question, which is not 'how do I illegaly download youtube videos?', but where are they stored?

Why should I answer your question? OP asked how to download video from Youtube and I gave the most direct answer.

As to legality, I am not sure how saving it from tmp would make it more or less legal so get over yourself.

---

### Post by lovinglinux on 2011-06-04
> **beew said:**
> As to legality, I am not sure how saving it from tmp would make it more or less legal so get over yourself.

Even Google distribute add-ons through Google app store that allows to download YT videos with Chrome.

---

### Post by beew on 2011-06-04
Dowloading non copyrighted material for non commercial use appears to be legal.

[http://askville.amazon.com/legal-download-file-youtube-personal-media-converter/AnswerViewer.do?requestId=10331504](http://askville.amazon.com/legal-download-file-youtube-personal-media-converter/AnswerViewer.do?requestId=10331504)

---

### Post by nothingspecial on 2011-06-04
> **beew said:**
> Why should I answer your question? OP asked how to download video from Youtube and I gave the most direct answer.

As to legality, I am not sure how saving it from tmp would make it more or less legal so get over yourself.

When I said OP, I meant the one from this year. ;)

I've asked about this.

See here

[http://ubuntuforums.org/showthread.php?t=1767753](http://ubuntuforums.org/showthread.php?t=1767753)

---

