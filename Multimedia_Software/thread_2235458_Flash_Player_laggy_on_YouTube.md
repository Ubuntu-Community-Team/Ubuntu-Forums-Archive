---
title: "Flash Player laggy on YouTube"
date: 2014-07-21
forum: Multimedia Software
---

### Post by alessio-popoli on 2014-07-21
Hello everybody. I'm having a problem with Trusty and Flash Player. Basically, some videos on YouTube are extremely laggy: they play one second, wait one second, then play another second. I figured it was something with Flash Player - if I remove it, some videos still play and the others ask me to install Flash - so I tried to purge and re-install flashplugin-installer and ubuntu-restricted-extras. Nothing changed, but I think I figured out where the problem originated.

I upgraded to 14.04 only about a week ago, because I hadn't been using Ubuntu in a while. Flash Player didn't work at all in 13.10 - I couldn't install it no matter what I tried. When I upgraded, some miracle happened and it began working fine. But then yesterday I tried to play a virtual piano keyboard on the Internet, and I noticed a big delay, at least one second, between the key being pressed and the note being played. Following some online tutorials, I re-installed pulseaudio, purging it in the process, and since then many things stopped working. First, the sound indicator disappeared, but this is kind of normal I guess - and easy to fix, reinstalling indicator-sound. Second, I noticed I didn't have Flash Player in my browser anymore, and installed it. Then, there was no audio in the videos, but somehow - I don't remember how - I managed to make it work again. This is the very last of the problems that I caused myself doing whatever that stupid tutorial - which didn't even fix the problem with the online keyboard, although I now have vmpk and it works like a charm - told me to do: like I said, Flash videos on YouTube lag although the grey line tells me that they have been correctly buffered - they lag even when the video is, in facts, 100% buffered.

What I tried so far:
-Re-installing flashplugin-installer (later I also tried flashplugin-downloader)
-Replacing it with adobe-flashplugin
-Downloading Flash from the official Adobe site and installing it manually
-Disabling hardware acceleration from Flash Player settings (why in this world does that damn checkbox only work in fullscreen mode?)
-Disabling hardware acceleration editing /etc/adobe/mms.cfg (neither the file, nor the /etc/adobe folder existed before I created them)
-Telling Flash to override GPU validation, again editing mms.cfg (this and the previous solutions were applied both singularly and together)
-Purging and re-installing Firefox (I'm not sure it was correctly purged, though - it kept my configuration intact without restoring the backup I had previously made)
-Using Chromium instead (I experience the same problem)

I'm desperate. I had switched back to Ubuntu because most bugs that had made me change my mind and go back to Windows were solved in Trusty, but now I experience this big problem...

Oh, one last thing. I didn't experience this bug before yesterday, so no, it can't be because Flash is generally crappy like that on Ubuntu. It wasn't until Saturday. I've seen many people claming that one will never solve this "bug" (which, to them, is not even a bug) on Ubuntu because Linux sucks and blah blah blah (what IT expert would ever say that Linux sucks?), but again, I began experiencing this bug only yesterday. I thought I had solved it by removing Flash Player, because one particular video that was lagging - this one: [https://www.youtube.com/watch?v=siKLBZdjtTc](https://www.youtube.com/watch?v=siKLBZdjtTc) (yes, I'm Italian, but I prefer posting in the English forum for many reasons) - worked afterwards. Instead, this one [https://www.youtube.com/watch?v=iUiTQvT0W_0&list=PLB31A13C3BE13A595&index=2](https://www.youtube.com/watch?v=iUiTQvT0W_0&list=PLB31A13C3BE13A595&index=2) told me to install Flash Player, and after installing it, it lags.

Thank you in advance. I'm really in the mood to shoot some Adobe programmers if I ever see them. Also, sorry if I made any mistakes - again, I'm Italian. Thanks!

---

### Post by frank18 on 2014-07-22
Install Google Chrome and you solve the flash player issue, it has it's own flash player

---

### Post by zteam2 on 2014-07-22
This ugly little trick does only work around the issue for youtube but....

Just visit this link and choose to use the HTML 5 version of youtube instead
[https://www.youtube.com/html5](https://www.youtube.com/html5)

---

### Post by uudruid74 on 2014-07-23
> **zteam2 said:**
> This ugly little trick does only work around the issue for youtube but....

Just visit this link and choose to use the HTML 5 version of youtube instead
[https://www.youtube.com/html5](https://www.youtube.com/html5)

There are other plug-ins that will convert nearly any flash video to html5.   I'm using one and it works great.  I had a horrible experience with trying to get Flash playing properly after recent system changes.  Everything played great - but disabling the flash player and converting to html5 on the fly works great.  I really don't see why YouTube doesn't use html5 by default.

---

### Post by monkeybrain20122 on 2014-07-24
For Youtube you don't need flash or html5 (html5 on Firefox is not easier than flash on CPU) Install the greasemonkey addon, restart Firefox and get [http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en)

There is a bug in greasemonkey (which they said will be fixed in the next release) so the script doesn't get updated automatically, if it stops working just go to the above link and install an updated version and then delete the old one (click greasemonkey icon > manage scripts)

---

