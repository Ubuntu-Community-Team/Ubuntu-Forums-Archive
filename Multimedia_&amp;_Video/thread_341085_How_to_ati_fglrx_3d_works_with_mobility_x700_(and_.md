---
title: "How to ati fglrx 3d works with mobility x700 (and others)!!"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by mirr0r on 2007-01-18
Yeah! I spent a lot of time but now my 3d works very well!!! :p :p 

My hardware: notebook msi m635, with ati mobility x700.

(sorry for my bad english)

It was a lot of time that my xorg.log report no error but command:```
fglrxinfo
```
inform me that I use mesa driver instead of fglrx.. 
First of all, follow this how-to (method 2)  and install fglrx:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Pre-Installation_Checks]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Pre-Installation_Checks")

Second **most imporant!!!**:

in a console write:
```

cd /usr/lib
sudo  ls -la *GL*

```

pay attention! you must have this link:
```
 libGL.so.1 -> libGL.so.1.2
```
not:
```
 libGL.so.1 -> libGL.so.1.5.060501 
```
because first (correct!!) is a symbolic link to fglrx, second (wrong!!!) link to mesa dri!!!

If you have second, then write:
```
ln -s libGL.so.1.2 libGL.so.1
```

I found this error thanks to this [link]("http://www.thinkwiki.org/wiki/Problems_with_fglrx#Known_Troubles_and_Solutions")
They are my heroes!!!!!!!!

In attachment my xorg.conf. Attention to:
```
Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection
```

I read a lot of post with same problem in this and other forum, I hope this post help someone!
ByeZ

Mirr0r

PS Great community.

---

