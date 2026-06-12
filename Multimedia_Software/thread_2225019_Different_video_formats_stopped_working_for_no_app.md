---
title: "Different video formats stopped working for no apparent reason"
date: 2014-05-19
forum: Multimedia Software
---

### Post by Ben_Cook on 2014-05-19
I just put xubuntu on my inlaws computer that was previously running a virus ridden windows.  All they use it for is streaming shows and checking email which xubuntu handled fine just a week or so ago.  They watch netflix, which still works, but cannot watch any of the networks that make their shows available for streaming.  Incidentally, youtube works fine as well.  So, I'm assuming it is a particular video format it won't play (html5 possibly?).  I got them to reinstall the restricted extras program, but to no avail.  So, without being able to access their computer, I'm at a loss.  Did the latest update cause it to somehow lose the ability to watch certain formats?  I really have no clue what to tell them to do.  I'm still pretty new to linux, and my inlaws have only been using it for a little over a week.  So, if you could, please answer accordingly:oops: so I can send this link to them.  As always, thank you in advance for any help/suggestions!

---

### Post by Yellow Pasque on 2014-05-19
Try this: [http://www.webupd8.org/2014/03/get-firefox-and-phonon-gstreamer-to.html](http://www.webupd8.org/2014/03/get-firefox-and-phonon-gstreamer-to.html)

---

### Post by Ben_Cook on 2014-05-23
I have been busy so sorry for not replying sooner.  I will not be able to see if this works until I am in front of their computer...I think it would be difficult to explain over the phone.  I will let you know how it goes

---

### Post by monkeybrain20122 on 2014-05-23
> **Ben_Cook said:**
> I have been busy so sorry for not replying sooner.  I will not be able to see if this works until I am in front of their computer...I think it would be difficult to explain over the phone.  I will let you know how it goes

Well not really the best solution but if you want a quick fix and avoid explanations over the phone just tell them to install Chrome/Chromium. h264 will work out of the box:)

---

### Post by SeijiSensei on 2014-05-23
It would help if you give us an example of something they cannot play.  Hulu, for instance, works fine here  since it uses Flash.  Can you post a non-working URL for us to consider?

Amazon Instant is a bit tricky to get working on Linux.  I finally gave up since my new TV has an Amazon app built in.

---

### Post by Ben_Cook on 2014-05-28
Haven't had the chance to get on here to reply, but an example of what doesn't work is CTV.CA.  If you're not in Canada, you won't be able to stream from this (without some clever workarounds haha).Also, global tv, which is also a Canadian only site.  They are the only sites they stream from other than netflix.  But I assume they would be the same format as CBS or NBC, since those are the networks where they get their shows from.  I will try and reply sooner next time.  Thanks!  And I might tell them to try chromium.

---

### Post by monkeybrain20122 on 2014-05-29
> **Ben_Cook said:**
> Haven't had the chance to get on here to reply, but an example of what doesn't work is CTV.CA.  If you're not in Canada, you won't be able to stream from this (without some clever workarounds haha).

It works on Chrome. It appears that CTV requires newer flash than 11.2, there are a few news sites like that and also Yahoo videos.  

Right now your options are Chrome (pepper flash) or Pipelight  flash on Firefox (it is Windows flash through wine). 

Then there is a project to get pepper flash to work in Firefox, but still pre-alpha though so I imagine it will take a while for it to work properly, I will test it out on Fedora over the weekend.[http://www.webupd8.org/2014/05/fresh-player-plugin-pepper-flash.html](http://www.webupd8.org/2014/05/fresh-player-plugin-pepper-flash.html)

Edited: Ok, some videos on CTV appear to be drmed in addition to requiring up to date flash so they don't work on Chrome either (pepper flash, while up to date, does not support drm). But work perfectly with pipelight flash on Firefox [http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html) Don't you love it? Flash is such a pain on Linux. :)

---

### Post by Ben_Cook on 2014-05-31
It is just strange that it worked before the last update.  But, I should have the computer tomorrow so I can try things out then, and hopefully I can get it working.  As I said, netflix is still working on firefox...and I thought that used pipelight.

---

### Post by Ben_Cook on 2014-06-01
OK,so I've tried what you said monkeybrain -  [http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html) - but I can't get it to work.  I feel like I'm in a bit over my head. CTV just gives me a black screen, global tv plays the ads but then just says buffering when the show is about to start :( . I'm at a loss

---

### Post by Ben_Cook on 2014-06-01
OK, I just went ahead and installed chrome and ctv worked but not global (???).  Again it plays the ads but just buffers and won't play

---

### Post by monkeybrain20122 on 2014-06-01
Did you install pipelight flash? Pipelight is a sort of umbrella thing that allows you to install different plugins. For netflix you install silverlight, but that won't work with global tv which doesn't use silverlight.

Since you already have pipelight installed, now just close all browsers and type
```
pipelight-plugin --enable flash
```

Now start firefox and wait for pipelight-flash installer to do its things.

You need to tell Firefox to switch between pipelight-flash and system flash.

The easiest way to switch would be to use a gui called galternatives
```
sudo apt-get install galternatives
```

If you are on 14.04 galternatives is broken, you need one more step to get it to work.
In the terminal type
```
sudo ln -s /usr/bin/update-alternatives /usr/sbin/
```

(Thanks to stinkeye's workaround [https://bugs.launchpad.net/ubuntu/+source/galternatives/+bug/1309709](https://bugs.launchpad.net/ubuntu/+source/galternatives/+bug/1309709))

Now open galternatives (type "alternatives" in the dash, it goes under the name 'alternatives-configurator'), go to mozilla-flashplugin and click add
then choose /usr/share/pipelight/libpipelight-flash.so (you can choose it from the menu in case there are typos)

Now you just click the a button to choose between the version of flash you use in FF. You need to restart Firefox for the switch to take effect.

You may consider replacing system flash with pipelight-flash and that would save your troubles of switching back and forth (choose pipelight flash in galternatives and forget about switching back, or simply remove system flash) but in my experience when both versions work (that is for 95% of the web) native flash performs a little better and that pipelight-flash has little glitches like buttons don't work on some sites. So do some testings and decide whether to switch permanently to pipelight or switch back and forth.

Also note that pipelight doesn't work in Chrome/Chromium so all I said above applies only to Firefox.

---

