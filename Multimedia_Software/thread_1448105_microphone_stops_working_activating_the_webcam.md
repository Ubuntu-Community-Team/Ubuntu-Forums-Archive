---
title: "microphone stops working activating the webcam"
date: 2010-04-06
forum: Multimedia Software
---

### Post by kila84 on 2010-04-06
Hi all,

I've just installed Ubuntu Karmic on a HP pavilion AMD 64 bit.

I've a weird problem: the microphone works good,  but using skype 2.1 beta, it stops working when I activate my webcam. Even after restarting skype, the microphone doesn't work. To make the microphone work, it seems to me that I've to reboot.

How can I use both the microphone and the webcam without problems?

Thanks

---

### Post by ajgreeny on 2010-04-06
Does your webcam have a mic as well as the one that stops working, ie, have you got two mics?

If so you may need to use "mic select" in the pulse configuration, or even in alsamixer.

---

### Post by kila84 on 2010-04-06
Hi,

I've just one mic: The only mic that I have is the one integrated with the webcam.

---

### Post by zampes on 2010-04-14
Hi there!
This may lead you somewhere: 
[http://forum.skype.com/topic/495591-skype-2-1-0-47-on-kubuntu-9-10-with-kde-4-4-beta-1/](http://forum.skype.com/topic/495591-skype-2-1-0-47-on-kubuntu-9-10-with-kde-4-4-beta-1/)

I know it talks about KDE, but I have both U and Kubuntu and have the same issue, it is definitely related to flash because the same happens when you open a web browser. In may case, I can run Skype fine; as soon as I open a web browser, the mic dies.
Let's work on it :) I'll follow this post, here's my description if you're interested and gives you some clues as to how to proceed:
[http://wwww.ubuntuforums.org/showthread.php?t=1452145](http://wwww.ubuntuforums.org/showthread.php?t=1452145)

---

### Post by Toews91 on 2010-05-28
I had a similar problem with my netbook running the UNR.  I downloaded the Pulse Audio device chooser (it will put a couple of programs on your machine) and then if you find your input device under the audio chooser, make sure that its only a single stream, most built in mics aren't multi channel.  So unlock them and then figure which channel its working on, and thats how i fixed my problem.  If the other solutions presented don't work you can try that, it worked for me.

---

