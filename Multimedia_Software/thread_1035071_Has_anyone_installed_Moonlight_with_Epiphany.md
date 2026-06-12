---
title: "Has anyone installed Moonlight with Epiphany?"
date: 2009-01-09
forum: Multimedia Software
---

### Post by DJ_Peng on 2009-01-09
I recently switched from using Firefox 3 to Epiphany 2.24.1 and I'd like to add the Moonlight plugin. I know there's a thread for [installing it from source code]("http://ubuntuforums.org/showthread.php?t=992635") but I have the pre-compiled code from [Novell]("http://www.go-mono.com/moonlight/"). Has anyone gotten it to work with epiphany-browser? I can compile it if I need to, but I'd still need to know how to get it installed so Epiphany will recognize it.

---

### Post by directhex on 2009-01-09
> **DJ_Peng said:**
> I recently switched from using Firefox 3 to Epiphany 2.24.1 and I'd like to add the Moonlight plugin. I know there's a thread for [installing it from source code]("http://ubuntuforums.org/showthread.php?t=992635") but I have the pre-compiled code from [Novell]("http://www.go-mono.com/moonlight/"). Has anyone gotten it to work with epiphany-browser? I can compile it if I need to, but I'd still need to know how to get it installed so Epiphany will recognize it.

Assuming you mean Epiphany-Gecko, not Epiphany-Webkit, you could use packages, rather than a .xpi file.

Try
```
deb http://ppa.launchpad.net/directhex/ubuntu intrepid main

```
Package is moonlight-plugin-mozilla. (tested quickly on AMD64 Intrepid; minor focus problem w/ right-click menus on Epi; packages may not have built yet on the PPA - be patient)

---

### Post by DJ_Peng on 2009-01-10
You're right, I did mean epiphany-gecko. Sorry I wasn't more clear. I keep forgetting there's an epiphany-webkit since i looked at it and was kind of thrown by how different some of the pages looked. Thanks for that PPA. I've added it to my 3rd party repos, and I'm snagging moonlight-plugin-mozilla and its dependencies right now. I definitely owe you a brew, directhex, and I'll keep my eyes open for the Epiphany-gecko package.

This? Is why I love the open source community. You can look for something, evidently miss the one thing you're looking for, and then post a question to the boards. Almost every time there's someone smart enough to know what you missed seeing and they don't just tell you what you need, they show you where to find it. The Windows community was never quite *this* helpful. :D

---

### Post by DJ_Peng on 2009-01-10
I see on about:plugins that Moonlight is seen by Epiphany-Gecko, but trying both the [video page for MLB.com](http://mlb.mlb.com/mlb/radio/) and a [local classic rock radio station](http://www.wrornothinbutthe70s.com/) only to see that I'm unable to see the Silverlight content. Did I miss installing something? I know the Moonlight beta were missing the media codecs or something but wven I checked the MLB video page in Fx3 on a clean profile I still get a message that I need Silverlight to see the content (with your package, not the xpi from the Moonlight site). I'm going to see if a system restart helps any, although I doubt it would be much different since I completely closed Epiphany after installing the package.

---

### Post by directhex on 2009-01-10
It's possible the sites you use require Silverlight 2.0 (Moonlight only has 1.0 support at the moment). My usual SL1 demo page is:

[http://miguelmoreno.net/sandbox/Silverlight_0/](http://miguelmoreno.net/sandbox/Silverlight_0/)

which is tested as working on Epiphany in Intrepid

---

### Post by DJ_Peng on 2009-01-10
Animusic! Now that's a cool test page! :8) It's weird, I was able to see the pages for MLB.com before I did my recent reinstall but it isn't working now. I see on the [Moonlight project page]("http://www.mono-project.com/Moonlight") that it recommends having ffmpeg to see the media content, and I just installed it so I'll restart Epi and let you know if that helped.

Ok, now it's ticking me off. With both your package and the extension installed, checked in just about every permutation under the sun, an MLB video in Fx3 insists that I need to install Silverlight. This wouldn't be nearly as frustrating if I hadn't been able to successfully see the MLB's Silverlight content in the past.

/me growls in the driection of Redmond

---

### Post by directhex on 2009-01-10
> **DJ_Peng said:**
> Animusic! Now that's a cool test page! :8) It's weird, I was able to see the pages for MLB.com before I did my recent reinstall but it isn't working now. I see on the [Moonlight project page]("http://www.mono-project.com/Moonlight") that it recommends having ffmpeg to see the media content, and I just installed it so I'll restart Epi and let you know if that helped.

Ok, now it's ticking me off. With both your package and the extension installed, checked in just about every permutation under the sun, an MLB video in Fx3 insists that I need to install Silverlight. This wouldn't be nearly as frustrating if I hadn't been able to successfully see the MLB's Silverlight content in the past.

/me growls in the driection of Redmond

It probably needs SL2 then

---

### Post by DJ_Peng on 2009-01-10
Thanks for all the assistance

---

