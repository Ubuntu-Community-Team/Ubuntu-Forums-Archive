---
title: "alsamixer only contains master control"
date: 2008-11-14
forum: Multimedia Software
---

### Post by XeroXer on 2008-11-14
I installed ubuntu yesterday and just now ran into some problems.
I have installed Wine and I am running Ventrilo through it.
I can hear the people in Ventrilo and I can talk just fine.
The problem is that my microphone volume is a bit low.

Well no biggie I thought and entered alsamixer, and there I found one control for the master volume.
[IMG]http://xeroxer.xeroxer.com/?file_id=104[/IMG]
I have used alsamixer before and then I had micboost and microphone volume and everything.
I thought that maybe ubuntu couldn't recognize my driver and went looking for some guides, but found none that helped me.
I have a SoundBlaster Live card.

I was just hoping that someone here could help me with this, if you need the output of any command just say the word.

---

### Post by m121212 on 2008-11-16
I just encountered the same problem myself, with an ASUS u6 laptop.  I just installed 8.10.  Your screenshot is identical to mine (card is listed as pulseaudio).

I remember having a problem like this on a previous install, and was able to fix it by selecting more controls under System|Preferences|Sound|Default Mixer Tracks.  That doesn't seem to help in this case.

---

### Post by skrap on 2008-11-16
Same thing for me,  Upgraded from 8.04 via the internet as reccomended.
Using X86_64 bit version Kernel 2.6.27-7  Sound works in rhythmbox but when I open alsamixer only have the master.  It also says pulseaudio for the card and the chip.  I actually have nvidia card with a realtek chip.
I had problems with the OS shutting down.  It would hang on a black screen and the last line said alsa.  Like it was trying to shut down alsa and couldn't.  I found a work around for that in the sticky.  If we find an answer to this I should be set.  Intrepid seems to be much better than hardy.  Gutsy was my first and best experience with ubuntu so far.  Hoping intrepid works as good as I think its going to.

---

### Post by wadubois on 2008-11-16
I just installed 8.10 this morning and discovered the same thing that you gentlemen did.  After browsing here for a bit (that's how I came upon this thread), and finding no quick solutions, I went back and messed around a bit more and found, if not a fix, at least a workaround.

I too, have a SB 5.1 Live.  it's listed in my /proc/asound/cards as:
```
wdubois@Leviathan:~$ cat /proc/asound/cards
 0 [Live           ]: EMU10K1 - SB Live 5.1
                      SB Live 5.1 (rev.7, serial:0x80641102) at 0xa800, irq 18

```

I found that if you invoke alsamixer with the -c option, you can force it to talk to a specific card or device, in this case, my live card.  

Try something like this: ```
 'alsamixer -c 0' 
``` substituting your card # from the output of the cat command above and see if that helps.

 - w

---

### Post by skrap on 2008-11-16
Thank you Sir.  That did the trick for me.

---

### Post by wadubois on 2008-11-16
Awesome, skrap! Glad to hear it.

 - w

---

### Post by aparigraha on 2009-01-16
Works like a charm wadubois
Thanks

---

### Post by Chris_Z on 2009-09-20
@wadubois

This did the trick! 

Greetings from Sweden.

---

### Post by syrag on 2010-01-25
Thanks, Wadubois! That did it for me, too.

---

