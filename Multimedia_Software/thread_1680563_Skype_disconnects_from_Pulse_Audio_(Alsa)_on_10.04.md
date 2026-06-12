---
title: "Skype disconnects from Pulse Audio (Alsa?) on 10.04"
date: 2011-02-02
forum: Multimedia Software
---

### Post by chicle2en1 on 2011-02-02
Hi!
When using Skype, the sound suddenly stops working, both ways (about 4-5 min into the communication). The message "connection failed: connection terminated" is displayed and when I click OK, Pulse Audio closes and Skype freezes. Actually, and I just realized this, the sound suddenly stops working on Firefox  as well. (The Alsa plugin in Pulse Audio 'Playback' just disappears). However this occurs after a long period of use. I've just watched about 30 continuous minutes of live soccer through Espn3, before the audio stopped working. No message was displayed though, and just refreshing the page fixed it. 

All this makes me think this is some type of Alsa-Pulse Audio  problem. I really don't understand well what they are, although I believe Alsa is a driver and Pulse Audio a sound server? Sorry, I started using Linux very recently...

I am using Ubuntu-Studio 10.04 and the rt Kernel (2.6.33-29-realtime). Sometimes I use Pulse Audio in Jack and vice-versa, using pactl load-module module-jack-sink and source respectively, but my problem seems to occur even if I unload the modules before using Skype. I believe all this started happening after I started using the rt kernel and/or the module-jack-sink/source.

Thanks in advance, and let me know if more information is required.

---

### Post by chicle2en1 on 2011-02-03
Hi again,
So, I dug further on the issue and I got to the file home/.xsession-errors, where I tracked the error and it says:
** (gnome-settings-daemon:1858): WARNING **: Connection failed, reconnecting...

Does that shed any light?
Any help will be greatly appreciated!

---

### Post by xyclo on 2011-02-05
OK. I tried with the generic kernel and it works just fine. Next, I will try the low-latency kernel, since I need the better performance for my audio apps, and I am not willing to be rebooting and switching kernels each time I want to make a Skype call...
I hope this monologue of mine is useful for somebody in the future. If so, please drop a line!

---

### Post by vangop on 2011-11-03
I think I have the same problem with ubuntu/kubuntu 11.10 and default kernel.
During the conversation in smth under 30min the sound stops working. Skype UI is still responsive but it cannot be closed. During this no sound works on the system. Killing skype brings back the sound.
Here's the [syslog]("http://pastebin.com/ZLnZNx9P").

---

### Post by bailunrui on 2011-11-03
I have the same problem as vongop. :(

---

### Post by tuxonapogostick on 2011-11-04
I am experiencing a similar problem as well. 2 min into audio chats, sound thing both playback and mic input disaapears during which sound icon turns >-- . I noticed that this thing started after I installed quite a few audio software in Ubuntu. I am wondering if a static skype install might solve the problem.

P.S.: my ubuntu is 10.10

---

### Post by tuxonapogostick on 2011-11-08
I just removed pulseaudio, and skype is working fine now. This is not an elegant solution though.

---

