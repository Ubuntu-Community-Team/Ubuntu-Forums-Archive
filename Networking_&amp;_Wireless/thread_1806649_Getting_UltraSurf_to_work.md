---
title: "Getting UltraSurf to work"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by Theredbaron1834 on 2011-07-17
I have asked quite a few Q's for this forum as of late, so I guess I should give back a little bit.

Ultrasurf is a proxy server, originally wrote for Chinese people, but quite good everywhere. I have searched the forum and read every post I could about it, and couldn't get it to work. I found out, so I thought I would post it.

Start by making sure you have wine installed. I use wine1.3, but others might work too.
Then need to get 2 dll files, that I uploaded [here]("http://www.sendspace.com/file/kq6frh").
Extract the included dll files to your .wine/drive_c/windows/system and /system32 folder.
Go [here]("http://www.ultrareach.com/support.html") and dl the firefox addon, works with icecat too. DL and install. It places either an icon or words on the bottom toolbar.
Pick up the latest Ultrasurf too. U1016 as of this writing.
Run it. On my 900mhz cpu, it takes a while to start up, like 30sec. Once it does click options and check "Do not use IE". 

That is it, you are good to do. Works great far as I can tell. I hope you guys get some use out of it. Not as "nixy" as perhaps TOR, but I much prefer it, even with this set up it is more user friendly in my book.

---

### Post by djangkrix on 2012-06-27
i use Lucid then i try  to use U1017, and it works .thanks for your post ,that is help me a lot ... :)

---

### Post by orion188 on 2012-12-05
For those who still cannot run UltraSurf with Wine, I found something that might help:

I'm using Ubuntu 10.10 (the Marverick Meerkat), with wine 1.2. Copying the dll files did not work as it kept complaining about one of the dlls, while it was there. So I found this guys note and it really worked using 'winetricks':

[http://www.bytechip.com/2011/06/how-to-solve-dll-problems-in-wine/](http://www.bytechip.com/2011/06/how-to-solve-dll-problems-in-wine/)

Remember that you should first delete the dlls you've previously copied to the wine folder and then run the winetrick command.
Also if you don't have winetricks, you should run these commands:

```
wget http://winetricks.org/winetricks 
chmod +x winetricks 
```

---

