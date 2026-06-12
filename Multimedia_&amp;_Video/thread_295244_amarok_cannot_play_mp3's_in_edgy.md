---
title: "amarok cannot play mp3's in edgy"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by eastern_strider on 2006-11-07
Hi,

When I upgraded to edgy from dapper I found my amarok music player deleted. Ok, I reinstalled it using synaptic and it works but it cannot play mp3 files. In dapper it was playing without any problems.

I made a quick search and one link suggests to do the following but it doesn't work:

sudo apt-get install gstreamer0.10-plugins-ugly libxine-extracodecs

apt-get says I already have those packages installed!

So, I was wondering what can I do to be able to listen mp3's using amarok again?

Thanks,
eastern_strider

---

### Post by eastern_strider on 2006-11-08
Instructions in this link solve the problem:

[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

However, before running the apt-get command there please check the "Multiverse" checkbox in the repositories option of synaptic.

Cheers,
eastern_strider

---

### Post by Michal77 on 2006-11-08
Hi,
I have the same problem Amarok doesn't play mp3. I have installed all codecs from repositories but still no progres ](*,) 
Any suggestions?
M.

---

### Post by eastern_strider on 2006-11-09
Doesn't the suggestion in the previous post solve this problem?

It did in my case..

---

### Post by vloris on 2006-11-12
No, it does not in my case. Amarok doesn't use gstreamer, so it has no effect to install those codecs.
The libxine-extracodecs package is already installed, and amarok doesn't recognize mp3's... :(

O, I'm sorry, ignore what I said above.. I had another problem, amarok does play mp3, it doesn't put them in my collection. But that's probably my fault somewhere...

---

### Post by insulae on 2006-11-12
i solved my problem, i use AmaroK with Xine Engine.

try to run a mp3 file with Xine-ui or Kaffeine, if you have the same problem, is the Xine update, i resolved the problem removing my .xine/ directory:

```
rm -r /home/insulae/.xine/
```

Regards
insulae

---

### Post by gua on 2006-12-05
```
rm -rf ~/.xine
```
did the trick for me.

Thanks a bunch.

---

