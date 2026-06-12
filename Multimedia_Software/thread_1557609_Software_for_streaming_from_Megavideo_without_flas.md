---
title: "Software for streaming from Megavideo without flash?"
date: 2010-08-21
forum: Multimedia Software
---

### Post by ZequeZ on 2010-08-21
Sorry for my english:

Well, I have this netbook, that can't handle the flash streaming from Megavideo, it get very low framerates... In the other hand, if I download the video, I can see it perfectly in a desktop player.
But: There is any plugin for Mplayer or VLC, or some else that allow you to view streaming videos bypassing the necessity of Flash?

Thanks in advance ^^

And again, sorry for my english xD.

---

### Post by cchhrriiss121212 on 2010-08-21
What I do is: start the flash video on whichever website I'm viewing, then press pause. Open up file manager and navigate to /tmp, where you will see the .flv file being downloaded. Open this file in whatever video player you like to use, it will keep playing like a stream does as long as you do not have to wait for buffering.

---

### Post by lovinglinux on 2010-08-21
I don't support Megavideo yet, but is on my todo list. See [https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

---

### Post by cchhrriiss121212 on 2010-08-21
> **lovinglinux said:**
> I don't support Megavideo yet, but is on my todo list. See [https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)
More good news! Any idea on when it will be ready? I have been trying out this plugin since the other day and it seems very stable, I will send you a contribution once you get megavideo working.
Out of interest, why is it that support for single websites needs to be added one-by-one?

---

### Post by ZequeZ on 2010-08-21
> **lovinglinux said:**
> I don't support Megavideo yet, but is on my todo list. See [https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

Yes, I already voted it :P.

Btw, you should make it compatible with Flash Blocker, and with no Flash at all. I don't want to install Flash in my netbook! Neither to disable Flash Blocker in my desktop! xD.

> **cchhrriiss121212 said:**
> What I do is: start the flash video on  whichever website I'm viewing, then press pause. Open up file manager  and navigate to /tmp, where you will see the .flv file being downloaded.  Open this file in whatever video player you like to use, it will keep  playing like a stream does as long as you do not have to wait for  buffering.

Nice TIP! I'll try now, thanks ^^

---

### Post by lovinglinux on 2010-08-21
> **cchhrriiss121212 said:**
> More good news! Any idea on when it will be ready? I have been trying out this plugin since the other day and it seems very stable, I will send you a contribution once you get megavideo working.

I haven't established a timeline yet. I'm currently working on the reported issues first, before adding more sites. Besides, Firefox 4 is going through a huge change and maintaining all my extensions is requiring more time than usual. As you can see, most of my extensions are already compatible with Firefox 4.b5pre, while 4.0b4 hasn't been released yet.

Additionally, I'm currently developing 3 more video related extensions. But I'm not stopping FlashVideoReplacer development. I have released a new version 5 days ago, to fix an issue with tabs loaded in the background.

> **cchhrriiss121212 said:**
> Out of interest, why is it that support for single websites needs to be added one-by-one?

Because each site has it's own method of authenticating the video links dynamically, and the flash object is usually coded in javascript instead of pure HMTL, so I need to figure out how to provide the proper link and how to detect the flash object to replace it. Additionally, in order to avoid running the extension code on every site you visit, which could cause performance issues, I need to match all supported video pages before running any code.

> **ZequeZ said:**
> Btw, you should make it compatible with Flash Blocker, and with no Flash at all. I don't want to install Flash in my netbook! Neither to disable Flash Blocker in my desktop! xD.

These are already on my todo list too. They have been reported in the [bug tracker]("http://code.google.com/p/flvideoreplacer/issues/list").

The extension is not compatible with Flashblock yet, but you can allow YouTube on Flashblock. This would allow the extension to work properly. Alternatively, you could use NoScript, which also block flash.

---

