---
title: "Where to get flashplayer 10r42_34 .deb?"
date: 2010-06-19
forum: Multimedia Software
---

### Post by Naggobot on 2010-06-19
Yes there are probably about 10 000 security flaws with the old one but the performance of 10.1 just does not cut it for me. I was much happier with the old version and I was stupid enough to let it get upgraded. 

[Official adobe archive]("http://kb2.adobe.com/cps/142/tn_14266.html") contains only tarballs.

---

### Post by howefield on 2010-06-19
Your choice knowing the security risks... 

[http://www.linuxinet.com/free-linux-software/adobe-flash-player-10-0-42-34-play-files-created-flash-linux.html](http://www.linuxinet.com/free-linux-software/adobe-flash-player-10-0-42-34-play-files-created-flash-linux.html)

Not a .deb but simple enough to extract the .so file to /usr/lib/mozilla/plugins eg,

Extract to the Desktop, open a terminal and type

```
cd Desktop
sudo mv libflashplayer.so /usr/lib/mozilla/plugins
```

---

### Post by Naggobot on 2010-06-19
Interesting. There is a link

```
/usr/lib/mozilla/plugins/flashpluginalternative.so
```

to

```
etc/alternatives/mozilla-flashplugin
```

which links to 

```
/usr/lib/adobe-flashplugin/libflashplayer.so
```

Now since I obviously want to mess this up more :p I renamed the last file and copied the old player version th the last location. 

Now next thing to do is to decide if the performance is better. Now of course I may experience better performance but is it really better. I'll post my experiences.

---

### Post by Naggobot on 2010-06-19
It may be that I am kicking wrong bucket here. It seems that performance is the same with old plug-in. 

Previously when whatching Flash videos the videos hogged up about 70-90% of CPU and now the number is 85-100% causing stuttering. Obviously something else has happened too. 

Since my original question was answered I mark this thread as solved.

---

