---
title: "Subwoofer doesn't work"
date: 2012-07-31
forum: Multimedia Software
---

### Post by Uvunter on 2012-07-31
Hello.

I have problems with my subwoofer in Ubuntu. I configured my sound system in the sound icon upper right. Now it's analog surround 4.1. Y checked if there is sound from every dispositive, and yes, there is sound, even from the subwoofer.

But when I open rhythmbox and play music, or when I play videos, there is no sound from the subwoofer. I don't know why.

This problem only happens on Ubuntu/Linux Mint, on other distributions I don't have such problem, and it works perfectly.

---

### Post by kingtiger01 on 2012-07-31
Thats easy, you dont have lfe(Subwoofer) Remixing enabled...

Youre Talking lfe Crossover, which Pulseaudio doesnt do by Default for a reason...

Honestly, a Good Speaker Setup has a Crossover built-in to the Amplifier to prevent 120hz and lower Frequency's going to the Satilite speakers... Blowing there Mid's(And high's if there higher-end speakers)

But, by Default, PulseAudio does not do this via Software... Because its not Application Specific, once you set it, its active in EVERY Application...

So Games and 5.1/7.1 Dolby content Will also send the Low-Frequency(Subwoofer) sound to LFE from the front speakers. Rather than just doing it.

------------------------------

There is Two ways of doing this.

1. System Wide:

If you dont mind a System Wide Configuration Change, that effects ALL users.

Just Edit /etc/pulse/daemon.conf and add "enable-lfe-remixing = yes" to it.

hold "Alt" and type ```
gksudo gedit /etc/pulse/deamon.conf
```

2: User Configuration:

Alternatively you can just set the Users Private Configuration to do LFE Remixing instead...

Personally id suggest this method if you use Mythbuntu or Xbmcbuntu as well as Ubuntu, as it wont interupt youre Movie's Quality...

this is a 3 step process....

 - 1: Open a Terminal ```
gnome-terminal
``` 
       
 - 2: Type ```
cp /etc/pulse/daemon.conf ~/.pulse/daemon.conf
```

 - 3: then Type ```
echo enable-lfe-remixing = yes >> ~/.pulse/daemon.conf
```


----------------

And ofcourse Restart after doing so, to ensure all pulseaudio sessions are ended.

---

