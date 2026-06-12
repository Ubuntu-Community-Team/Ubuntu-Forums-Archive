---
title: "eSpeak: Connection refused (111)"
date: 2009-04-25
forum: Multimedia Software
---

### Post by AwesomeTux on 2009-04-25
Hello,

I recently upgraded to Ubuntu 9.04 (Jaunty Jackalope) and now when I run "espeak" in a terminal I receive this error:

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

And eSpeak, doesn't speak the text I input. I suspect it's a small problem, but, I don't know how to fix it. Please help. Any suggestions?

---

### Post by AwesomeTux on 2009-04-27
Really? No one can help me on this one? :(

---

### Post by zpreston on 2009-04-28
I have this same problem too and am still looking for an answer...

---

### Post by psyke83 on 2009-04-29
If you're using Ubuntu (i.e., the GNOME environment), the problem is most likely to be a PulseAudio misconfiguration. See my tutorial to ensure you have a clean configuration, and there are troubleshooting steps you can use.

P.S. espeak works fine here.

---

### Post by AwesomeTux on 2009-04-29
> **psyke83 said:**
> If you're using Ubuntu (i.e., the GNOME environment), the problem is most likely to be a PulseAudio misconfiguration. See my tutorial to ensure you have a clean configuration, and there are troubleshooting steps you can use.

P.S. espeak works fine here.

Thank you for help. But my eSpeak is still broken.

I did notice if I stop pulseaudio, then run "sudo espeak" it still tells me... 

```
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
```

But, it works, I hear speech when I input text. So I think it has something to do with permission/privileges.

---

### Post by zpreston on 2009-04-29
> **AwesomeTux said:**
> Thank you for help. But my eSpeak is still broken.

I did notice if I stop pulseaudio, then run "sudo espeak" it still tells me... 

```
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
```

But, it works, I hear speech when I input text. So I think it has something to do with permission/privileges.

Similar thing here, I tried some troubleshooting things when I googled the error message, but they didn't work. I still haven't had a chance to try Awesome's tutorial yet though. When I am Root, I will hear what I type, but still get the error message.  Strange, but it works I guess.  I will try that tutorial and then report the results.

---

### Post by froller on 2009-05-09
Same problem here after upgrade.  I turned my bluetooth services back on:

System -> Administration -> Services

and it cleared the problem up.  Turn them back on and they return. Config bug with bluetooth?

I am on an aspire 7520 amd64 build in gnome.

---

### Post by AwesomeTux on 2009-05-09
> **froller said:**
> Same problem here after upgrade.  I turned my bluetooth services back on:

System -> Administration -> Services

and it cleared the problem up.  Turn them back on and they return. Config bug with bluetooth?

I am on an aspire 7520 amd64 build in gnome.

THANK YOU SO MUCH! The error is gone.

But, still, when I type "espeak Hello" I hear "Hehl-" and it cuts out before he can finish saying "Hello." It's not quite fixed.

---

### Post by pdc124 on 2009-09-12
did you ever fix this ? 
Im still struggling

---

### Post by Ter Rymon on 2009-10-21
Espeak that is currently in repos for Jaunty has a bug in that it is speaking words incorrectly (i.e. way too fast or speaking only the first few words)

Espeak is not broken entirely just a bit buggy.

Two current work-a-rounds are as follows (choose the one that best fits your use):

1) pipe espeak output through aplay in a bash script

```
%words = "hello world"
espeak --stdout %words | aplay 
```

or 2)install Gnome Espeaker front-end:

[http://gespeaker.googlecode.com/files/gespeaker_0.6_all.deb](http://gespeaker.googlecode.com/files/gespeaker_0.6_all.deb)

I use both.

---

### Post by outi on 2009-11-02
This solution works like espeak in readline mode

```

while [ 1 ]; read i; do espeak --stdout -v pl "$i" | aplay; done

```

exit - ctrl+c

---

### Post by myspacejmagenst on 2010-01-21
Works for me  and I greatly appreciate it! Here's the gespeak website 

[http://code.google.com/p/gespeaker/](http://code.google.com/p/gespeaker/)

---

### Post by Wizzu on 2010-02-15
About the bt_audio_service_open: connect() failed: Connection refused (111) errors, in case someone is still looking for a solution (and doesn't want to enable bluetooth):

This might fix them:
[FONT=monospace]s[/FONT]udo apt-get purge bluez-alsa

From [https://bugs.launchpad.net/ubuntu/+source/supertux/+bug/486287](https://bugs.launchpad.net/ubuntu/+source/supertux/+bug/486287) and [http://www.digitalbuz.com/2009/11/03/solved-using-espeak-error-bt_audio_service_open-connect-failed-connection-refused-111/](http://www.digitalbuz.com/2009/11/03/solved-using-espeak-error-bt_audio_service_open-connect-failed-connection-refused-111/)

---

### Post by fooey on 2010-05-07
> **Wizzu said:**
> About the bt_audio_service_open: connect() failed: Connection refused (111) errors, in case someone is still looking for a solution (and doesn't want to enable bluetooth):

This might fix them:
[FONT=monospace]s[/FONT]udo apt-get purge bluez-alsa

From [https://bugs.launchpad.net/ubuntu/+source/supertux/+bug/486287](https://bugs.launchpad.net/ubuntu/+source/supertux/+bug/486287) and [http://www.digitalbuz.com/2009/11/03/solved-using-espeak-error-bt_audio_service_open-connect-failed-connection-refused-111/](http://www.digitalbuz.com/2009/11/03/solved-using-espeak-error-bt_audio_service_open-connect-failed-connection-refused-111/)

yes. purging bluez-alsa fixe dit for me. thanks man.
*(wasn't using espeak but had the error doing something else...either way, still fixed it)*

---

### Post by ensenadaubuntulover on 2010-05-12
> **AwesomeTux said:**
> Thank you for help. But my eSpeak is still broken.

I did notice if I stop pulseaudio, then run "sudo espeak" it still tells me... 

```
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
```

But, it works, I hear speech when I input text. So I think it has something to do with permission/privileges.

for me the sudo option works 

also if I use [COLOR="Red"][SIZE="4"]/usr/bin/espeak[/SIZE][/COLOR]

i still get 
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)[/CODE]

but works (without sudo)


and I can not find [COLOR="Red"]SYSTEM->ADMINISTRATION->SERVICES[/COLOR]

---

### Post by c.realkiller on 2010-06-25
[http://ubuntrucchi.wordpress.com/2010/06/16/empathy-parlami/](http://ubuntrucchi.wordpress.com/2010/06/16/empathy-parlami/)
speaks with empathy gespeaker

---

### Post by andthewicked on 2010-07-26
I don't know if this helps but I keep getting the same error message when I use flight gear, and they say it has to do with the plus audio configurion file, it says to change it to drivers = oss or drivers = alsa but I've tryed that for fg and it still didn't work. also I tryed to use epeak and it doesn't work if I just type something into the line but if I use -f it will read the entire file...its a little fast but its better then nothing. hope this helps some.

---

### Post by mdhtr on 2011-04-22
> **froller said:**
> Same problem here after upgrade.  I turned my bluetooth services back on:

System -> Administration -> Services

and it cleared the problem up.  Turn them back on and they return. Config bug with bluetooth?

I am on an aspire 7520 amd64 build in gnome.

Wow, this really fixed that error message.
I guess BT meant BlueTooth after all.

---

