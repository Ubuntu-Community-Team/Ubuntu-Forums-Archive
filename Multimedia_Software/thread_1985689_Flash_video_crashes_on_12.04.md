---
title: "Flash video crashes on 12.04"
date: 2012-05-23
forum: Multimedia Software
---

### Post by forza.stiinta on 2012-05-23
every time I am playing flash video in google chrome or firefox, flash crashes. This happens on youtube and on any other flash video websites.

I am using ubuntu 12.04 on a Thinkpad T61 with NVIDIA Quadro 140NVS and latest drivers installed.

---

### Post by gordintoronto on 2012-05-23
Is your 12.04 32-bit ot 64-bit? Did you install Flash as part of the "restricted extras"?

---

### Post by bombaklat on 2012-05-24
> **gordintoronto said:**
> Is your 12.04 32-bit ot 64-bit? Did you install Flash as part of the "restricted extras"?
 
I'm running 12.04 64bit. "ubuntu-restricted-extras" are installed. and I have exactly the same issue.

---

### Post by bombaklat on 2012-05-24
my problem was:
there is a bug in flash which is causing all youtube videos to be blue.  this appears only if you have nvidia card. following this quick fix:
[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)
I could solve the colour problem. but afterwards the flash player started crashing.

my solution:
 I opened this file /etc/adobe/mms.cfg 
and deleted the first line from there so the only thing left is this entry: 
OverrideGPUValidation=true

now my flash player is not crashing any more.

---

### Post by bbb13 on 2012-05-24
try this:

```
sudo apt-get purge flashplugin-installer
```
and then install flash player through firefox extension [Flash Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")_ , using wizard mode and selecting only "override GPU validation"._

---

### Post by mrmorris on 2012-05-30
> **bbb13 said:**
> try this:

```
sudo apt-get purge flashplugin-installer
```
and then install flash player through firefox extension [Flash Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")_ , using wizard mode and selecting only "override GPU validation"._

Thanks for this tip, it worked... establishing proper Flash video playback both in Firefox and Chrome!

---

### Post by finny388 on 2012-06-05
> **bombaklat said:**
> my problem was:
there is a bug in flash which is causing all youtube videos to be blue.  this appears only if you have nvidia card. following this quick fix:
[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)
I could solve the colour problem. but afterwards the flash player started crashing.

my solution:
 I opened this file /etc/adobe/mms.cfg 
and deleted the first line from there so the only thing left is this entry: 
OverrideGPUValidation=true

now my flash player is not crashing any more.

Well, this worked for me. I changed "EnableLinuxHWVideoDecode=1" to 0 instead. But without using my nvidia card, 240p is as high as I can go or everything is choppy/can't see people's mouths move, etc. But it's something. <sigh>

---

### Post by az_s_za on 2012-06-07
> **bombaklat said:**
> 
my solution:
 I opened this file /etc/adobe/mms.cfg 
and deleted the first line from there so the only thing left is this entry: 
OverrideGPUValidation=true

now my flash player is not crashing any more.

I was going crazy with flash continually crashing.  This fixed it for me.  Now rock solid.  Thanks!
(I only had one other line n that file and commented that line out)

---

### Post by mteppo on 2012-09-29
Had plenty of crashing of Flash-plugin, some sites were completely unusable.
This article helped me out - now my mms.cfg says:
"
EnableLinuxHWVideoDecode=0
OverrideGPUValidation=true
"
And flash works just nicely.
I have 12.04 with Flash from extras and AMD AM2 4400+ cpu (so it is not lightning-fast) and NVidia display adapter with proprietary drivers. 
The lack of acceleration seems to have some impact - though - on fullscreen SD material the CPU consumption is increased with this setup (85% of a single core taken by the browser/plugin).
Still - there is enough CPU to run it smoothly and the crashing is gone, so this -to me- is resolved.

---

### Post by mteppo on 2012-09-30
> **mteppo said:**
> 
...
"
EnableLinuxHWVideoDecode=0
OverrideGPUValidation=true
"
And flash works just nicely.
...
Still - there is enough CPU to run it smoothly and the crashing is gone, so this -to me- is resolved.

Yes - does not crash but there is smurf invasion on Youtube. Got that resolved with the help of this thread [http://ubuntuforums.org/showthread.php?t=1974037](http://ubuntuforums.org/showthread.php?t=1974037). 
Now I think this should be ok.

---

### Post by Lili on 2013-03-16
This solved the problem in one second. Thank you, great answer!!

However, I preferred to comment out the first line instead of deleting it, so my mms.cfg looks like this:

[FONT=Lucida Console]#EnableLinuxHWVideoDecode=1
OverrideGPUValidation=true[/FONT]

Newbie hint: you can edit the file with root privileges (sudo)

---

### Post by silbar on 2013-03-16
Interesting, but I cannot find any directory like /etc/adobe, much less a file called mms.cfg.  
The Adobe flash I have installed is 11.2.202.275ubuntu0.12.04.1, installed from the
Ubuntu Software Center.

Richard Silbar

---

### Post by Lili on 2013-03-17
Hi, you can create the /etc/adobe directory and the /etc/adobe/mms.cfg file with [FONT=Lucida Console]EnableLinuxHWVideoDecode=1[/FONT] content. 
This can be undone deleting the mms.cgf file
Source: [Enable Flash Player hardware video decoding]("http://askubuntu.com/questions/117127/flash-video-appears-blue")

Or you can try one of the methods below which are also reported working.

---

### Post by markackerman8@gmail.com on 2013-07-19
sudo apt-get remove --purge adobe-flashplugin flashplugin* nspluginwrapper
&#8728; WORKED with NO REINSTALL of any adobe-flashplugin or  flashplugin*

---

