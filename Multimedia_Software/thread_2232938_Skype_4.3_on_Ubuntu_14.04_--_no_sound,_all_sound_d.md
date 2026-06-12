---
title: "Skype 4.3 on Ubuntu 14.04 -- no sound, all sound devices say &quot;virtual device&quot;"
date: 2014-07-05
forum: Multimedia Software
---

### Post by miles6 on 2014-07-05
I just installed the new Skype update and now the sound isn't working in skype but it is for everything else. In the drop downs to select sound devices, my only option is "virtual device". Do I need to create a virtual audio device? and if so how do I go about doing that cus I tried following a bunch of tutorials and they just didn't work. Also please bear in mind that I'm a bit of a noob. Thanks in advance :3

okay just now the "make a test sound" worked, but still nothing else is working

[ATTACH=CONFIG]254485[/ATTACH][ATTACH=CONFIG]254484[/ATTACH][ATTACH=CONFIG]254483[/ATTACH][ATTACH=CONFIG]254486[/ATTACH]normal audio stuff

---

### Post by xc3RnbFO8P on 2014-07-05
Try Terminal:
> PULSE_SERVER=127.0.0.1 skype

---

### Post by miles6 on 2014-07-05
Didn't work :/ thanks though

Solved here: [http://ubuntuforums.org/showthread.php?t=2232684&highlight=skype+4.3](http://ubuntuforums.org/showthread.php?t=2232684&highlight=skype+4.3) thank youuuuuu

---

### Post by marco56 on 2014-08-06
> **miles6 said:**
> okay just now the "make a test sound" worked, but still nothing else is working

Hey

had the same problem, tried many solutions offered in several threads. in the end it helped to install pavucontrol and therein change from analog duplex to e.g. digital back and forth several times to finally stay with default setting (analog duplex). A latte machiato ubuntu user may explain this phenomenon. I am still chewing coffee beans. However, now it works fine with Pulseaudio.

;)

---

### Post by martinr on 2014-08-23
See this thread for: [how to keep using your old Skype version]("http://ubuntuforums.org/showthread.php?t=2240954&p=13105799#post13105799").

---

### Post by thienai on 2014-08-31
Hello, sorry my english very bad, i use ubuntu 10.... and skype 4.3 but i use web hear music online okay, but skype i not hear
i enter skype \ options\sound devices :
 microphone : virtual device
 speakers : virtual device
 ringing :virtual device
make test sound not work
please help me, thanks

---

### Post by Martin_Kuemmel on 2014-09-05
Here's what helped me and what I did not explicitly find in other posts/threads:
- install 'paprefs' (Pulse Audio Preferences), open it ('./paprefs' on terminal or via dash)
- on 'Network Access" tick "Make discoverable PulseAudio...."
- on 'Network Server' tick "Enable network access to local..."
- there also tick "Dont require authentification" (not really sure whether this is necessary)

Then it skype worked for me. Here screenshots:
[ATTACH=CONFIG]256166[/ATTACH][ATTACH=CONFIG]256167[/ATTACH]

---

### Post by Light-kun on 2014-10-06
After trying all fixes from this thread still have no sound in skype at all.
Linuxint17 fresh installation with retained /home from LM15.

---

### Post by Qd64erK on 2014-10-15
I got it to work by installing libpulse0:386, just followed [this answer on Ask Ubuntu]("http://askubuntu.com/questions/506259/skype-shows-virtual-device-for-microphone-speakers-and-ringing/507083#507083")
Hope it helps
Cheers
**Asensio**

---

### Post by leti2 on 2015-02-13
install and it works
sudo apt-get install gstreamer0.10-plugins-ugly gxine libdvdread4 totem-mozilla icedax tagtool easytag id3tool lame nautilus-script-audio-convert libmad0 mpg321 gstreamer1.0-libav

---

### Post by Georgi_Karpov on 2015-02-24
The best solution for me: find skype 4.2 .deb and install it over installed skype 4.3, as priveously log in skype 4.3 and enable autologin on startup (after installation of 4.2 over 4.3 there could be problems with login). Skype sound is back.

---

### Post by pkohout on 2015-07-22
i had to run skype as root, now it just works fine

---

### Post by Aberts10 on 2015-09-13
> **Martin_Kuemmel said:**
> Here's what helped me and what I did not explicitly find in other posts/threads:
- install 'paprefs' (Pulse Audio Preferences), open it ('./paprefs' on terminal or via dash)
- on 'Network Access" tick "Make discoverable PulseAudio...."
- on 'Network Server' tick "Enable network access to local..."
- there also tick "Dont require authentification" (not really sure whether this is necessary)

Then it skype worked for me. Here screenshots:
[ATTACH=CONFIG]256166[/ATTACH][ATTACH=CONFIG]256167[/ATTACH]

Worked Flawlessy, but i had to use Alt + F2 to enter paprefs

---

### Post by tedy58 on 2015-09-15
[Here]("http://ubuntuforums.org/showthread.php?t=2232684&p=13188664#post13188664") is the solution for me.
Thanks @  'svenmeier'
I install the pulse adudio library that skype still stick on it, 
and all works now. 

Installing the 32bit pulseaudio library helped here on 14.04.3.:

```
$sudo apt-get install libpulse0:i386 

```

---

### Post by strelook70 on 2015-10-26
> **Martin_Kuemmel said:**
> Here's what helped me and what I did not explicitly find in other posts/threads:
- install 'paprefs' (Pulse Audio Preferences), open it ('./paprefs' on terminal or via dash)
- on 'Network Access" tick "Make discoverable PulseAudio...."
- on 'Network Server' tick "Enable network access to local..."
- there also tick "Dont require authentification" (not really sure whether this is necessary)

Then it skype worked for me. 


[COLOR=#000000]This solution works great on a laptop eMashines eM350 the system Lubuntu 14.04 32bit version Skype 4.3.[/COLOR]
[COLOR=#000000]Thank you so much![/COLOR]
[COLOR=#000000]To install paprefs[/COLOR]
[COLOR=#000000]In the terminal, dial:
[/COLOR]
```
 sudo apt-get install paprefs
```

---

### Post by mauro-annarumma on 2015-12-19
I had same problem and I solved installing paprefs and opening it with ALT + F2... tks so much! (skype  on lubuntu )

---

### Post by Lalo_Mercado on 2016-02-29
> **Martin_Kuemmel said:**
> Here's what helped me and what I did not explicitly find in other posts/threads:
- install 'paprefs' (Pulse Audio Preferences), open it ('./paprefs' on terminal or via dash)
- on 'Network Access" tick "Make discoverable PulseAudio...."
- on 'Network Server' tick "Enable network access to local..."
- there also tick "Dont require authentification" (not really sure whether this is necessary)

Then it skype worked for me. Here screenshots:
[ATTACH=CONFIG]256166[/ATTACH][ATTACH=CONFIG]256167[/ATTACH]

This was the solution for me, on Lubuntu 15.10 and Skype 4.3.

Thank you so much!!

---

### Post by gebebkebeb on 2016-04-09
> **Martin_Kuemmel said:**
> Here's what helped me and what I did not explicitly find in other posts/threads:
- install 'paprefs' (Pulse Audio Preferences), open it ('./paprefs' on terminal or via dash)
- on 'Network Access" tick "Make discoverable PulseAudio...."
- on 'Network Server' tick "Enable network access to local..."
- there also tick "Dont require authentification" (not really sure whether this is necessary)

Then it skype worked for me. Here screenshots:
[ATTACH=CONFIG]256166[/ATTACH][ATTACH=CONFIG]256167[/ATTACH]

spasibo, comrade

---

### Post by estelondono on 2016-08-19
> **Martin_Kuemmel said:**
> Here's what helped me and what I did not explicitly find in other posts/threads:
- install 'paprefs' (Pulse Audio Preferences), open it ('./paprefs' on terminal or via dash)
- on 'Network Access" tick "Make discoverable PulseAudio...."
- on 'Network Server' tick "Enable network access to local..."
- there also tick "Dont require authentification" (not really sure whether this is necessary)

Then it skype worked for me. Here screenshots:
[ATTACH=CONFIG]256166[/ATTACH][ATTACH=CONFIG]256167[/ATTACH]

I just install 'paprefs' without opening and configuring it and Skype 4.3 started to work just fine in my Lubuntu 14.04

---

