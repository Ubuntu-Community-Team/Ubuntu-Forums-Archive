---
title: "CNBC Live TV not working on 13.04"
date: 2013-09-30
forum: Multimedia Software
---

### Post by mike114 on 2013-09-30
Hi, I am trying to load CNBC live TV using both Mozilla and Chrome with U 13.04 and I'm not getting anything. It says "one moment please" and nothing ever shows up. It works fine on the windows side. Does it work for anyone else? Thanks
[http://www.cnbc.com/live-tv](http://www.cnbc.com/live-tv)

---

### Post by gordintoronto on 2013-09-30
Did you install the Restricted Extras? Can you watch youtube videos?

I am in Canada, so CNBC won't let me watch live-tv or any programs, but I see the ads which precede the programs.

---

### Post by mike114 on 2013-10-01
I did install the restricted extras and while I can watch the pre-recorded shows, I can't watch the live stream. Oh, yes, I can view youtube videos.

---

### Post by mike114 on 2013-10-01
I googled around a little bit and found this (I followed directions but it still doesn't work - when I clear the directories does it confirm or just go back to the commande prompt?)

[COLOR=#333333][FONT=myriad-pro-1]For Ubuntu 10.04 or later, ensure that the Hardware Abstraction Layer module is first installed using apt-get.
(Watch carefully for &#8220;hal&#8221; install errors, as a damaged package install can continue to affect video playback.)[/FONT][/COLOR]
[COLOR=#333333][FONT=myriad-pro-1][FONT=Courier New]sudo apt-get install hal[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=myriad-pro-1]After the "libhal" (HAL) library install completes, close the browser and clear the Adobe Access directories by executing the following shell commands:[FONT=Courier New][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=myriad-pro-1][FONT=Courier New]cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2[/FONT][/FONT][/COLOR]

---

### Post by gordintoronto on 2013-10-02
One of the down sides of the Internet is that there is a lot of obsolete information. A solution for 10.04 might work in 13.04, but probably not.

Since I'm in Canada, I can't help with CNBC -- even though I often watch CNBC World on my TV. Oh, I was able to watch CNBC India....

---

