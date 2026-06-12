---
title: "Why can I not watch video using Quicktime?"
date: 2008-05-13
forum: Multimedia Software
---

### Post by lesliek on 2008-05-13
I'm using Ubuntu v 8.04 with the supplied Firefox browser. When I check for Firefox plugins, I'm told I have both Flash and Quicktime.

I go here: [http://www.nfb.ca/duneculturealautre/toutvoir_vis.php?film=&_onfplr_sel=plr&mediaid=666145&mcid=&full=](http://www.nfb.ca/duneculturealautre/toutvoir_vis.php?film=&_onfplr_sel=plr&mediaid=666145&mcid=&full=)

I'm said to have the choice of watching the video in either Flash or Quicktime format.

If I select Flash, a start button appears for the video. If I select Quicktime, it doesn't.

That's the reason for the question in the title to this post.

Thanks for reading this.

Leslie

---

### Post by aeiah on 2008-05-13
i cant test right now, but have you ruled out a website error by seeing if you can view apple trailors or something? they use .mov

---

### Post by lesliek on 2008-05-13
Thanks for replying so quickly aeiah.

Unfortunately, I'm so ignorant that I don't know where to find Apple trailers to test!

---

### Post by aeiah on 2008-05-13
[http://www.apple.com/trailers/](http://www.apple.com/trailers/)

---

### Post by lesliek on 2008-05-13
Thank you very much. I had no trouble watching a trailer at the site you sent me to, so that suggests a problem with using Quicktime at the National Film Board site.

Can I ask you something else related?

What I really want to do is to capture the video that I can watch at the URL I mentioned originally.

It seemed to me that I had to install Mplayer to do that, so I did. I also found through Googling a list of URLS from which one could stream video through Mplayer. I tried a couple of those in Real Media format and they worked properly.

However, I couldn't stream the URL I mentioned originally. Is there some way for me to convert that URL into a form that would allow me, for instance, to stream the Flash format of the film I want?

Thanks again for your help.

Leslie

---

### Post by gandaran on 2008-05-13
streaming a flash url, I think can only be done in the vlc-player and maybe totem, also plays .flv formats.

---

### Post by aeiah on 2008-05-13
i think the quicktime file is at [http://helix.nfb.ca/collection/films/300_10605.mov](http://helix.nfb.ca/collection/films/300_10605.mov)

you should be able to grab the flash with a firefox plugin designed to get the .flv files. i cant do it right now because im at work on IE7. egh.

download either of them and try and convert with mencoder or ffmpeg, or see if you can play them straight with mplayer or vlc

---

### Post by lesliek on 2008-05-13
Thanks to Gandaran and thanks again to aeiah.

aieah, you were right about the Quicktime file. I downloaded it and then ran "mplayer http://helix.nfb.ca/collection/films/300_10605.mov" and it worked! May I ask how you were able to arrive at the correct filename? I can't find any hint of that name in the URL itself.

Also, I'll try to find a Firefox plugin of the type you mentioned, but is there a particular one you have in mind?

Thanks again,

Leslie

---

### Post by cor2y on 2008-05-13
do you hve the mplayer mozilla plugin installed for firefox or the totem mozilla plugin?
A quick check via Synaptic should tell you if you do (search for totem-mozilla and mozilla-mplayer).
Replace totem with mplayer's plugin.
I visited the page in question and the video played for me using flash.
It may be that you have the alternative open source flash plugin installed, i am on firefox 3b5 with the closed source flash plugin. Check in Synaptic to see if flashplugin-nonfree is installed if not remove libflash-mozplugin,swfdec-mozilla or gnash if installed (these are the open source flash plugins) then install it.

---

### Post by lesliek on 2008-05-13
Thanks for your reply cor2y.

I apologise for this, but I obviously didn't express myself properly at the start. I CAN watch in my browser the Flash version of the film I wanted to see, but what I can't do is watch it by using the command "mplayer <filename for Flash file>". I want to be able to do that as a step to capturing via mplayer the Flash version of the film.

Of course, in order to stream or capture either the Quicktime or the Flash version of the film using mplayer, I have to know the URL to use with mplayer and I don't know how to find that out.

aeiah gave me the URL for the Quicktime version of the film, but I don't know how he figured it out. If I knew that, I could also stream/capture other films at the site using mplayer.

Thanks again,

Leslie

---

### Post by cor2y on 2008-05-13
If you want the ability to get streaming media captured with mplayer, let the video in question play for in while in the browser with the plugin, then right click and select copy url then you can use that for playback in mplayer itself.
If you want to download then use the download helper plugin for firefox it gets most but not all video streams.
There is no easy to use stream url capture software like say urlsnooper in linux yet.
You could always monitor your web connections with tools like the firestarter or wireshark to capture the url address a bit of work there though.

---

### Post by lesliek on 2008-05-13
Thanks again cor2y.

Maybe I'm just out of luck here.

Right-clicking on a video at the National Film Board of Canada site when it's playing in Flash format doesn't give me the "copy url" option. I can't even try the same when the video's playing in Quicktime format, because, for whatever reason, I can't get videos at that site to play in Quicktime format. (However, I was able to get Apple trailers playing, following aieah's instructions.)

Also, I installed DownloadHelper, but the NFB site isn't one supported.

If you have any other ideas, I'd be happy to try them.

Thanks again,

Leslie

---

### Post by cor2y on 2008-05-13
using the mplayer plugin with firefox i was able to get the stream address.
I just right clicked and selected play
its rtsp://helix.nfb.ca/collection/films/300_10605.mov however according to mplayer, vlc and totem no stream at that address is available.
I am going to try the wine ie browser next with a quicktime plugin see if its shoddy protocol work on the part of the web designer or if there is no stream there.

EDIT
Its shoddy webdesign it works in windows the stream is not absent/missing.
How to fix i don't know

---

### Post by lesliek on 2008-05-13
cor2y, this is really all above my head. One thing I did notice though is that aeiah said the protocol for the video was http, while you said it was rtsp.

When I used wget and the filename with the rtsp protocol, I couldn't download the file, but when I used wget and the filename with the http protocol, it began to download quite happily.

---

