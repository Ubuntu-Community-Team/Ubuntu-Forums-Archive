---
title: "no sound at mp3 and avi"
date: 2008-03-14
forum: Multimedia &amp; Video
---

### Post by swotie on 2008-03-14
I have no sound when I play mp3 and avi-files ... but I have sound when I play internet games ...

---

### Post by xc3RnbFO8P on 2008-03-14
Intall this:

> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
> sudo apt-get install w32codecs

---

### Post by swotie on 2008-03-14
Thanks

---

### Post by swotie on 2008-03-15
Then I use these codes and reboot my pc ... I have sound at mp3 and  avi ... but the day after, the sound  is gone :-( .... and now is the internet sound gone too :-( .... 
If I go into the sound settings and try some different settings, I got the message "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Ressource optaget eller ikke til rådighed." (resource busy or not avaible)

---

### Post by xc3RnbFO8P on 2008-03-15
I found this:

> sudo lsof |grep /dev/snd/

It should show witch program is causing this error.

Then use System monitor to kill it. (It is in System> Administration)

---

### Post by swotie on 2008-03-15
I got this message, when I write the code: 

mixer_app  6132     Swotie   19u      CHR      116,7               15487 /dev/snd/controlC0

I removed "mixer_app" from system monitor ... but no sound on mp3 and avi

---

### Post by xc3RnbFO8P on 2008-03-15
Dont remove mixer_app, try to play something and run **sudo lsof |grep /dev/snd/** again.

---

### Post by swotie on 2008-03-16
I have rebooted my PC ... I play a mp3 ...sound OK ....close file down ....  I play a avi .... sound OK ... close file down .... I play whist at [www.komogvind.dk](www.komogvind.dk) ..... sound OK ..... I play mp3 or avi while I play whist .... NO sound at mp3 or avi ..... I close my whist game .... wate few seconds ... mp3 and avi play again .... Result  .... I can't play whist at [www.komogvind.dk](www.komogvind.dk) and mp3 at the same time :-(


 Then I write sudo lsof |grep /dev/snd/ now ... I get no answer

---

### Post by xc3RnbFO8P on 2008-03-16
Do you have Pulseaudio?

---

### Post by swotie on 2008-03-16
nope ... must I install this program ?

---

### Post by eye208 on 2008-03-16
> **swotie said:**
> I can't play whist at [www.komogvind.dk](www.komogvind.dk) and mp3 at the same time :-(
Is that a Flash-based browser game?

Try playing a YouTube video and some MP3 file at the same time. If that doesn't work either, then you probably have a very old version of the Flash plugin that uses OSS emulation instead of ALSA. Before installing PulseAudio I'd recommend to update the Flash plugin to the latest version and see if that helps.

---

### Post by xc3RnbFO8P on 2008-03-16
> must I install this program ?
No

---

### Post by swotie on 2008-03-16
1) Games at komogvind is java games

2) I can play youtube  video and mp3 at the same time

---

### Post by eye208 on 2008-03-16
> **swotie said:**
> 1) Games at komogvind is java games

2) I can play youtube  video and mp3 at the same time
There is already a bug report related to that problem.

[https://bugs.launchpad.net/sun-java/+bug/82099](https://bugs.launchpad.net/sun-java/+bug/82099)

It seems you can work around it by using the ALSA wrapper for OSS applications, but that's not exactly a satisfying solution. :-k

---

### Post by 6205 on 2008-03-16
That looks like Flash site...Do you have Flash installed ? [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

Or is it Java ? 

sudo-apt get install [COLOR="Blue"]sun-java6-plugin[/COLOR]

---

### Post by swotie on 2008-03-16
it must be a java problem ... if I start A media player before a java application, I can play anything ... but not java sound

 I have installed the ALSA wrapper for OSS applications .... but how can start this application ?

---

### Post by 6205 on 2008-03-16
Hmm...i'm affraid i can't help you with this issue, but meantime you can play games at [www.miniclip.com](www.miniclip.com)

---

### Post by swotie on 2008-03-16
I open a mp3 and paused it .. then I can hear all my music ... and play my game wiout sound ... this is a solution for me ... 


Thank YOU all of, who have use a lot of energy on my question ...

---

