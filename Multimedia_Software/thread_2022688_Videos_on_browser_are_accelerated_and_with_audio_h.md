---
title: "Videos on browser are accelerated and with audio hiccups"
date: 2012-07-11
forum: Multimedia Software
---

### Post by ggg83 on 2012-07-11
Video reproduction in browsers is not working.

Whatever video (youtube, dailymotion or various newspapers) has accelerated video and audio hiccups. Same thing happens with Chrome, Chromium, Firefox and Opera. 

This happens every now and then and it solves when I reboot, but I want to understand what's going on, and not reboot every time.

Videos on the laptop and banshee audio are ok.

I'm on Ubuntue 12.04 32-pit, Pangoline from System76

---

### Post by mikewhatever on 2012-07-11
Hm..., to understand how Adobe Flash works, you'll need to, at least, convince Adobe bosses to let you look at the source, and probably provide someone to help you study it. Are you sure there aren't better things to do or to spend money on?

Have you tried disabling hardware acceleration in flash settings? It's blocked on Linux anyway, so no harm would be done.

---

### Post by ggg83 on 2012-07-11
I'd rather get as far as possible from Adobe, honestly..

Anyway, hardware acceleration is off, thanks for the hint. This thing happened like twice this week, it just goes like that at startup.

---

### Post by caravaggisto on 2012-09-23
> **ggg83 said:**
> Video reproduction in browsers is not working.

Whatever video (youtube, dailymotion or various newspapers) has accelerated video and audio hiccups. Same thing happens with Chrome, Chromium, Firefox and Opera. 

This happens every now and then and it solves when I reboot, but I want to understand what's going on, and not reboot every time.

Videos on the laptop and banshee audio are ok.

I'm on Ubuntue 12.04 32-pit, Pangoline from System76
ggg83,

I've been having the same recurring issue on 12.04 Ubuntu. My hardware is a X220 Thinkpad, i7 cpu.

Have you found a solution since you first posted about this issue?

Thanks,
Caravaggisto

---

### Post by caravaggisto on 2012-09-23
I did more research on this and it appears that Pulseaudio has a problem with certain versions of Flash. Either change the plugin you’re using or change to HTML5 content, and you’re good to go.

Possible solutions:

[LIST]
[*]It could be an issue with Flash, if that’s where your audio is coming from. [These guys]("https://bugs.freedesktop.org/show_bug.cgi?id=50324") point out that enabling the [HTML5 trial in youtube]("youtube.com/html5") solves the audio issue (worked for me as well), so Flash probably has something to do with it. The specific pulseaudio problem that’s leading to the accelerated audio or video is that, when Flash is the source, pulseaudio continuously creates and then drops new audio streams every half second. You can see this happening if you run the command `pacmd list-sink-inputs` over and over when the audio is messed up. Look for the `index` value; it changes continuously, representing a new audio stream. If you change youtube to HTML5, you’ll notice that the `index` value remains constant.
[*]Related to the previous, Chrome has two Flash plugins, and if you’re in Chrome, the default one might be causing the issue. This sounds odd, but check for yourself under [chrome://plugins]("chrome://plugins"). (thanks to [Dennis Schridde]("https://bugs.freedesktop.org/show_bug.cgi?id=50324#c3") for pointing this out.) Dennis reports that if you disable the PepperFlash plugin (usually the first one listed, located at `/opt/google/chrome/PepperFlash/libpepflashplayer.so`), then the problem is solved.
[*]Pulseaudio might be setting the output incorrectly. [Lars Scheithauer (derlars)]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/630134#yui_3_3_0_1_1348379473650638") mentions this on an Ubuntu bug page. For him Pulseaudio was incorrectly routing the audio stream to HMDI instead of headphones, so nothing was coming through on the headphones. Somehow he manually rerouted the audio to fix it, but how he did this, I'm not sure. [This page]("http://askubuntu.com/questions/71863/how-to-change-pulseaudio-sink-with-pacmd-set-default-sink-during-playback/72076#72076") might show how. Whether or how this is connected to the Flash plugin problem, I don’t know. 
[/LIST]

Links cited in order of appearance:
[LIST=1]
[*][https://bugs.freedesktop.org/show_bug.cgi?id=50324](https://bugs.freedesktop.org/show_bug.cgi?id=50324)
[*][http://www.youtube.com/html5](http://www.youtube.com/html5)
[*][chrome://plugins]("chrome://plugins")
[*][https://bugs.freedesktop.org/show_bug.cgi?id=50324#c3](https://bugs.freedesktop.org/show_bug.cgi?id=50324#c3)
[*][https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/630134#yui_3_3_0_1_1348379473650638](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/630134#yui_3_3_0_1_1348379473650638)
[*][http://askubuntu.com/questions/71863/how-to-change-pulseaudio-sink-with-pacmd-set-default-sink-during-playback/72076#72076](http://askubuntu.com/questions/71863/how-to-change-pulseaudio-sink-with-pacmd-set-default-sink-during-playback/72076#72076)
[/LIST]

hth,

caravaggisto

---

