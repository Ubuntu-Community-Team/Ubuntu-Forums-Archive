---
title: "Pass Xvfb directly to ffmpeg"
date: 2018-01-08
forum: Multimedia Software
---

### Post by mario90yxz on 2018-01-08
[FONT=arial]I'm trying to pass Xvfb buffor directly to ffmpeg inside Docker. This is approach give me really big performance benefits. [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]This is how I'm doing it:[/FONT]

[FONT=arial]Xvfb write the screen output:[/FONT][FONT=arial]`sudo Xvfb $DISPLAY -ac -screen 0 1680x900x24 -fbdir /tmp/screen/test.xwd > /dev/null 2>&1 &`[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]ffmpeg read command: [/FONT]
[FONT=arial]`[/FONT]
[FONT=arial]ffmpeg -hide_banner -loglevel debug -loop 1 ' \
    '-re -i /tmp/screen/test.xwd ' \
    '-f alsa -i default -strict -2 -ac 2 -preset ultrafast -f ' \
    '-c:av copy ' \
    'output_file.mkv'
[/FONT]
[FONT=arial]`[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]The problem is: ffmpeg missed many frames and the video should be 3 minutes long, but is half of expected time (video accelerates at some point). [/FONT]
[FONT=arial]On following video you can see the problem: [https://drive.google.com/file/d/1HWjEqrtPfZCRSndxpUpY1iXsrfMNWdp7/view](https://drive.google.com/file/d/1HWjEqrtPfZCRSndxpUpY1iXsrfMNWdp7/view)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I guess there is a problem with ffmpeg command and it requires some tweaks, but no idea how to configure it properly. [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thanks![/FONT]

---

