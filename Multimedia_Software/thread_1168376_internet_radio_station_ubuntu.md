---
title: "internet radio station ubuntu"
date: 2009-05-24
forum: Multimedia Software
---

### Post by vapblack on 2009-05-24
Streaming radio station
Greetings all. I have 2 computers, both running Ubuntu 9.04. Both with dual processors. One has 32 bit and the other has 64. 
Tonight I'm upgrading the 32

To be more specific, here are the specs of my computers

1
Vostro 220
Intel® Core&#33922; 2 Duo E7400 (2.8GHz, 3M, L2Cache, 1066FSB)
3GB DDR2 SDRAM 800MHZ 
Integrated Video, Intel® GMA X4500HD
512 nvidia graphic card

2
AMD Athlon 64 X2 3800+ dual-core (2.0GHz, 35W)
- 1GB DDR2-533MHz dual channel SDRAM (2x512)
- 160GB 7200 rpm SATA hard drive
- Integrated NVIDIA GeForce 6150 LE

So..on to the problem. My mom is using #2 with Ubuntu x64 9.04. She likes a specific radio station in NYC but we don't get it up here. They do stream it online. Located [here]("http://wbls.com/pages/3874639.php")

Neither of the computers can run it though. It starts loading and just hangs there. I've  tried firefox, ie4linux, and windows firefox in wine. I also tried usung the beta flash x64 driver. none of those work. My last option is getting rid of ubuntu and putting windows on my mom's comp. I really don't want to, she is comfortable with ubuntu and I don't want to expose her to windows again. On top of that, I don't want the headache! So if any of you cool ubuntites can tell me how to make that site work, I'll be very appreciative.

in closing,
help a brotha out. 
peace

---

### Post by sofasurfer on 2009-05-24
On the radio stations web site, click on "stream help". It says you need adobe flash player. I though I had adobe install from the "multimedia how-to" but I was wrong. This is the only station I can not play right now. I went to adobe's site and downloaded the player but on installation it said that I had the wrong architecture.

So, we're waiting for someone to solve this.

---

### Post by ad_267 on 2009-05-24
It looks like it's a bug in the mp3 player they're using. It must work in Windows but they haven't bothered to test in Linux. When I try to play a song it starts buffering to about 9% then goes back to 1% and just sits there doing nothing. If only they used a proper internet radio stream, rather than a flash player. Unfortunately I don't think there's a way around this.

---

### Post by gandaran on 2009-05-24
probably the only firefox plugin that can play this stream is the xine-plugin, I haven't tried it on this stream but I know from past experience xine-plugin is the best for radio streaming. 
if you install xine-plugin you have to remove totem and any other player firefox plugin for it to take over firefox video/audio online streams

---

### Post by ad_267 on 2009-05-24
> **gandaran said:**
> probably the only firefox plugin that can play this stream is the xine-plugin, I haven't tried it on this stream but I know from past experience xine-plugin is the best for radio streaming. 
if you install xine-plugin you have to remove totem and any other player firefox plugin for it to take over firefox video/audio online streams

That won't work because the stream has to play through the embedded flash player. If it didn't then there wouldn't be a problem.

---

### Post by ad_267 on 2009-05-24
Weird, it's working for me now.

Does it never work for you? Or does it occasionally work.

Edit: Cleared all my cookies, restarted Firefox and it's still working. Doesn't seem to have any problems now.

---

### Post by vapblack on 2009-05-24
> **ad_267 said:**
> Weird, it's working for me now.

Does it never work for you? Or does it occasionally work.

Edit: Cleared all my cookies, restarted Firefox and it's still working. Doesn't seem to have any problems now.

what did you change? 
Please tell me your settings and comp hardware.

edit: if xine is the answer, where do I download that?

---

### Post by Torgas Prim on 2009-05-24
I think it is gstreamer. I installed it last night to play an obscure song.
I checked your link and I can listen after allowing Noscript on the site.

---

### Post by wbee on 2009-05-24
Try this:

[http://linux.wareseeker.com/free-wbls-radio/](http://linux.wareseeker.com/free-wbls-radio/)

---

### Post by cybrsaylr on 2009-05-24
I like listening to Last-FM which is built right into Rhythnbox Music Player. Just select an artist and their music and related music are streamed in.

---

### Post by ad_267 on 2009-05-25
> **vapblack said:**
> what did you change? 
Please tell me your settings and comp hardware.

edit: if xine is the answer, where do I download that?

I didn't change anything. I'm not sure why it's working now. I'm using Ubuntu 9.04 with the Adobe flash player installed from the ubuntu-restricted-extras package (adobe-flashplugin package). Don't think it's a hardware thing, I've got a pretty basic Intel motherboard. I tried it at University today on Fedora 9 with the flash player from the Adobe website, not sure how old that version is, and it played one ad then wouldn't play the next song. 

I don't think xine is the answer. There's no way to play the stream that I can find other than through the flash player on the website.

---

### Post by rudy.b on 2009-05-25
You can play the stream for WBLS through other media applications (e.g. Rhythmbox, VLC, Banshee, etc.) by using the following URL: [http://cmn-ice.spacialnet.com/wbls](http://cmn-ice.spacialnet.com/wbls).  The flash plugin must be installed first, of course.

---

### Post by ad_267 on 2009-05-25
> **rudy.b said:**
> You can play the stream for WBLS through other media applications (e.g. Rhythmbox, VLC, Banshee, etc.) by using the following URL: [http://cmn-ice.spacialnet.com/wbls](http://cmn-ice.spacialnet.com/wbls).  The flash plugin must be installed first, of course.

Doesn't look like it needs flash at all, it's running using gstreamer. That's great, looks like the problem is solved. :)

---

### Post by vapblack on 2009-05-25
> **ad_267 said:**
> Doesn't look like it needs flash at all, it's running using gstreamer. That's great, looks like the problem is solved. :)

yep. problem solved on this end! 
Thanks

---

### Post by Mortus Pryde on 2009-05-25
ad_267, another possibility is that the stream source(s) were down or a routing issue. This happens occassionally and your only real solution is to wait for it to come back up, or the issue to be resolved. This can be agrovating when you are trying to troubleshoot streaming issues.

---

