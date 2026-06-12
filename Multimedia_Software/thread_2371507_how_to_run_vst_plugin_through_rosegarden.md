---
title: "how to run vst plugin through rosegarden ?"
date: 2017-09-15
forum: Multimedia Software
---

### Post by shantiq on 2017-09-15
***Edit: solution explained at bottom of thread*** *::*


i know it is possible to do that from articles i have seen  but how?
any of you managed it?

trying to run those amazing [plugins]("http://smatni.tripod.com/safwanmatnivstplugins/")

i know you need to have dssi-vst/dssi-vst-server and I have those


this is as far as I have got but not yet visible in Rosegarden  ....    any ideas ....    anyone done this before? thanx in advance

```
shan@shan-Aspire-XC-780:~$ /usr/lib/dssi/dssi-vst/dssi-vst-server.exe Oud.dll, .vst
DSSI VST plugin server v0.986
Copyright (c) 2004-2010 Chris Cannam
Loading "Oud.dll"... 
VST_PATH not set, defaulting to /home/shan/vst:/usr/local/lib/vst:/usr/lib/vst
dssi-vst-server[1]: found in /home/shan/vst/Oud.dll
done
Testing VST compatibility... 
dssi-vst-server[1]: VST 2.4 entrypoint "VSTPluginMain" not found in DLL "Oud.dll", looking for "main"
dssi-vst-server[1]: VST entrypoint "main" found
fixme:font:get_outline_text_metrics failed to read full_nameW for font L"POSTOFFICE"!
dssi-vst-server[1]: plugin instantiated
dssi-vst-server[1]: plugin is a VST
dssi-vst-server[1]: plugin has a GUI
dssi-vst-server[1]: plugin supports processReplacing
ERROR: Remote VST startup failed: Failed to open FIFO
shan@shan-Aspire-XC-780:~$ 


```

---

### Post by yoshii on 2017-09-16
Good Question!!! You might try contacting some people from the KXstudio project or ask at the AVLINUX forum.  Those are some folks who know alot about that kind of thing.

---

### Post by Bucky Ball on 2017-09-16
> **yoshii said:**
> Good Question!!! You might try contacting some people from the KXstudio project or ask at the AVLINUX forum.  Those are some folks who know alot about that kind of thing.

+1. Minimal help with this here. You will probably need to use WINE to run straight VSTs. Does Rosegarden claim to run them natively?

---

### Post by shantiq on 2017-09-16
Thanx for feedback
Got in touch With this guy [here]("http://www.penguinproducer.com/Blog/2011/11/making-music-in-the-rosegarden/") and you can see on his page there that he once managed it [do CTRL+f enter vst and see foryourselves]


[IMG]http://www.penguinproducer.com/Blog/wp-content/uploads/2012/02/screenshot1231.png[/IMG]

It was 7 years ago  ...   he says *probably   was on a 32-bit install*
Will give that a whirl soon on an older machine and report ...    I want  to use the [Oud and Kanun]("http://smatni.tripod.com/safwanmatnivstplugins/") since they have great sound  ....   will give  32 a go although I thought the process went on behind the scenes in Wine  which is 32 anyway i think
Do not know enough about tech side just trial and error
Want this to work tho

---

### Post by yoshii on 2017-09-18
I do know that 32-bit Ubuntu's tend to be a bit more supported than 64-bit for some things.  The WineHQ FAQ mentions this about 32-bit WINE vs 64-bit WINE.  
Also, in my experiences even running 32-bit WINE on 64-bit Ubuntu is sometimes less supported.  Anyways...

I've been trying Rosegarden and Carla, but Carla is buggy and incomplete on Ubuntu 64-bit and I can't get Rosegarden to notice any of my plugins of any type on this particular distro even though it worked on Ubuntu Studio (currently using Xubuntu with KXstudio repos).  

I'm stumped.

---

### Post by shantiq on 2017-09-19
oh did a 16.04 32-bit install and you can see them straight away  ..... so good there
  never used vst's on Ubuntu so all new to me  ....    but yes a 32 install solves it for visibility ...   installing dssi-vst is the key here


[[IMG]https://s26.postimg.org/qsd9wu6gl/safwan.png[/IMG]]("https://postimg.org/image/qsd9wu6gl/")

AND then it started to work!   Excellent  ...    wanted this for years :]

[[IMG]https://s26.postimg.org/4mq08eugl/image.png[/IMG]]("https://postimg.org/image/4mq08eugl/")


*** To summarize:***

&#10122;  ```
sudo apt install dssi-vst jack wine
```
&#10123;  store vst's in  /home/username/vst  or /usr/local/lib/vst or /usr/lib/vst or /home/username/.vst
&#10124;  make sure your Ubuntu is a 32-bit ; I cannot see these on a 64-bit install 
[please say if you know a way through on 64 there must be a way]
&#10125;  click on manage synths plugins drop-down box
&#10126; Fire qjackctl before you start rosegarden to activate jack
&#10127; no way to export natively to an audio file 
so use jack_capture [commandline software]
```
 sudo apt install jack-capture
```
then:
```
 jack_capture -b 24 -f flac
```


AND you end up with something looking thus >
[[IMG]https://s1.postimg.org/8czaa6xl4r/vst.png[/IMG]]("https://postimg.org/image/8czaa6xl4r/")

---

