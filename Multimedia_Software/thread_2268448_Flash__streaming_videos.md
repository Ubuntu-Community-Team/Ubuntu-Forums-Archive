---
title: "Flash / streaming videos"
date: 2015-03-09
forum: Multimedia Software
---

### Post by dan163 on 2015-03-09
Hello all,

New to the forums here. Ive been able to resolve my technichal issues so far by doing some quick online research, although my latest issue has not been the easiest to resolve. I was hoping someone who is well versed in the art of "ubuntu" could point me in the right direction.

i have ubuntu 14.04 LTS installed on a dell optiplex 720 im (trying) to turn into an entertainment center box of sorts.

As this is going to be an entertainment center box, i really need to be able to run flash on this bad boy. Youtube, as well as any streaming site you can name is useless without it. Im particularly interested in comcast dot net as i do the majority of my streaming there.

so i got chromium installed, and updated, as well as selected the options which allow for the use  of third party apps in system settings (multiverse). Im not sure if it was necessary or not, but i also installed - pepperflashplugin-nonfree

the website no longer informs me that i need flash, and interestingly enough, the ads load. However when it comes to playing the feature film, the webpage becomes stuck on buffering and will not play the actual content.

has anyone experienced this issue? Any help would be greatly appreciated.

---

### Post by kerry_s on 2015-03-09
your better off with real google chrome, it has flash built in, it's the only app that can do netflix, the only app that can handle the drm crap correctly.
plus being able to make web apps(launchers) for any site is a huge benefit, instead of opening the browser & going to site.

---

### Post by dan163 on 2015-03-09
Thanks for the response. I was up all night playing around with my setup. I got DVD working with copywright protection. That took more research than i expected.


downloaded chrome, taking my computer to work with me. I left my keyboard at work so ive been doing everything with the on screen keyboard. Very frustrating at times lol.

if theres any chance you could keep an eye on my post im guessing i might need a little help :)

that goes out to anyone who feels like lending some knowledge!

---

### Post by kerry_s on 2015-03-09
no problem i'm already subscribed, my email checks every 5min's, so if i'm at my pc i see it right away.

---

### Post by monkeybrain20122 on 2015-03-09
So does Chrome work or not?  It is not clear from your last post. If it still doesn't work it may be because Comcast content is drmed and Chrome's flash on Linux while up to date, doesn't work with drmed streams. In that case you may try using pipelight flash (Windows flash under wine)

[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)
After installing pipelight, close firefox and run

```
pipelight-plugin --enable flash
```

to revert back to system flash

```
pipelight-plugin --disable flash
```

(you don't need sudo to run these commands, even though it is in the instructions)

Edited: You may also need the user-agent-overrider addon for Firefox [https://addons.mozilla.org/en-us/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/en-us/firefox/addon/user-agent-overrider/)

---

### Post by dan163 on 2015-03-12
chrome works, but when i try to play a video, it will play the ads, and starts to play the video, but immediately freezes.


ahh! wine! i forgot all about that, really good idea. ill give that a try and let yall know how it goes (incase anyone finds this information useful)

---

### Post by SeijiSensei on 2015-03-12
If the Optiplex has Intel motherboard video, you're not going to be happy trying to watch HD videos on that machine without a video card upgrade.  Even something as cheap as a [$30 NVIDIA 8xxx card]("http://www.newegg.com/Product/ProductList.aspx?Submit=Property&N=100007709%208000%20600030348&IsNodeId=1") will be a big improvement.  These adapters have special circuitry to decode the H.264 codec that is used for most HD video.  Otherwise the CPU has to handle the decoding and often cannot keep up.

While AMD has improved its support for Linux, I still recommend NVIDIA.  Install the adapter, then use the "Additional Drivers" application in Ubuntu to download and install the proprietary driver.

---

### Post by monkeybrain20122 on 2015-03-14
My laptop has an old intel card (ironlake) I have no problem watching HD video with h.264 using vaapi. Another with AMD HD6310 using vdpau with the open driver also play HD h264 smoothly.

---

### Post by amrabdi on 2015-03-16
I have htpc with the 5th gen Intel 5500 gpu(but it should work with the 3rd and 4th gen too from what I have read), running Gnome Ubuntu 14.10 with the latest kernel, and Netflix works well with sound under the latest Chrome and chrome beta.

---

### Post by darin5 on 2016-02-14
> **dan163 said:**
> chrome works, but when i try to play a video, it will play the ads, and starts to play the video, but immediately freezes. ahh! wine! i forgot all about that, really good idea. ill give that a try and let yall know how it goes (incase anyone finds this information useful)


Did you ever resolve your problem with Chrome and Xfinity videos?  It's the same problem that I'm currently having but in Xubuntu.

-Darin

---

### Post by yoshii on 2016-02-15
try and see if you can view lower-resolution videos before you try to play the larger HD ones.  try 140 and 240 and 360 before 480 and 720 and 1440.  it could be the limits of your ISP connection.

---

