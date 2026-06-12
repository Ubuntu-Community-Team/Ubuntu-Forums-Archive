---
title: "watching in line videos from pbs/nova"
date: 2009-07-31
forum: Multimedia Software
---

### Post by gsociology on 2009-07-31
I'm trying to watch some in line videos from NOVA
[http://www.pbs.org/wgbh/nova/](http://www.pbs.org/wgbh/nova/)

apparently i need to install something like a media player.  I just installed ubunto a few weeks ago on a windows computer, compaq laptop, have not installed anything else on it.

So, my question is, what do I need to install, and hopefully are there instructions on how to install, for a ubuntu dummy.

Thanks

Gene

---

### Post by ad_267 on 2009-08-01
Go to system - administration - synaptic package manager and install the ubuntu-restricted-extras package. This will isntall the adobe flash player required to view flash videos on websites as well as codecs for mp3 and other media formats.

---

### Post by gsociology on 2009-08-01
Thanks for the suggestion. As far as I can tell, adobe flash player is already installed.  Is there some way to install windows media player or quicktime?

thanks

gene

---

### Post by silverdulcet on 2009-08-01
> **gsociology said:**
> Thanks for the suggestion. As far as I can tell, adobe flash player is already installed.  Is there some way to install windows media player or quicktime?

thanks

gene

I just tested the pbs.org video with the totem-mozilla package. It is a video plugin for firefox and works for most videos/media. Use Synaptic to install it by searching for totem-mozilla or from a Terminal type
```
sudo aptitude install totem-mozilla
```

You will be asked for your user password to install the package. 

Once it has completed installing restart firefox if you have it running and type
```
about:plugins
```

You should see various plugins listed. Just confirm that you have ones mentioning Totem. Then try going to the pbs site and see if you can now view the videos.

---

### Post by nacho32 on 2009-08-01
odd I just get waiting for video when I try to play them

---

### Post by burgundy on 2009-10-05
I found this thread:
[http://ubuntuforums.org/showthread.php?t=1161693&highlight=pbs+video](http://ubuntuforums.org/showthread.php?t=1161693&highlight=pbs+video)
and didn't have the same dumb luck the other guy had...

I have a feeling this problem isn't very common because my other ubuntu desktop systems work fine with pbs video beta programs.

For some reason the flash videos at PBS.org just don't play on my laptop anymore... how do we debug this?

Flash in general is working in Firefox and every other web browser I try.. (Opera/Chrome) but when I go to pbs.video.org nothing works.  All I want to do is watch the News Hour and that new National Parks series, but something about the way PBS does flash in my browser is broken.

---

### Post by Lars Noodén on 2009-10-06
> **burgundy said:**
> 
For some reason the flash videos at PBS.org just don't play on my laptop anymore... how do we debug this?


Whatever your solution, part of it includes contacting PBS and letting them know they need to modernize to open formats.  

1) The squeaky wheel gets the grease  aka ask and ye shall receive, and all that.

2) *public* broadcasting should be independent from any single company or campaign donor.

---

