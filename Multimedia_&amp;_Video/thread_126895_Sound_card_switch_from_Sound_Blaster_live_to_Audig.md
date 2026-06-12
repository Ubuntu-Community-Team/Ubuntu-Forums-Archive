---
title: "Sound card switch from Sound Blaster live to Audigy produces distortion"
date: 2006-02-07
forum: Multimedia &amp; Video
---

### Post by ceilingfish on 2006-02-07
hi,
I have just changed my sound card from a Sound Blaster Live! to an Audigy, and it hasn't quite worked as I had hoped.

I didn't change any system settings to prepare for the hardware swap just turned off the computer and changed the cards over, and I now have a rather strange output from the Audigy which is basically the original sound but very heavily distorted and alot quieter.

I have looked around a bit so far and am I right in thinking that the Sound Blaster Live uses the driver emu10k1 and the audigy uses a driver entitled ca0106. I may be talking absolute rubbish however, so please correct me if I am.

Would it work if I removed the sound card altogether and started again, or is that not necessary?

Cheers,
Tom

---

### Post by FarEast on 2006-02-08
Hi,
According to the web below, your new sound card is driven by 'snd-emu10k1'.

[http://www.alsa-project.org/alsa-doc/index.php?vendor=.%23vendor-Creative_Labs.1.1.1.1](http://www.alsa-project.org/alsa-doc/index.php?vendor=.%23vendor-Creative_Labs.1.1.1.1)

Execute the command below to know the sound chip.
$ lspci -v | grep audio

---

### Post by ceilingfish on 2006-02-09
Sorry for the slow reply I forgot to put on email notification.

Output of command is:

```

tom@cod:~$ lspci -v | grep audio
0000:00:0d.0 Multimedia audio controller: Creative Labs SB Audigy LS

```

I shall read more on that link, but if there is anything else you could tell me I'd be really appreciative. How do I change the sound card driver?

Edit: It appears that I have an Audigy LS. Is this different to the standard Audigy?

---

### Post by FarEast on 2006-02-09
Thanks for the info.

> It appears that I have an Audigy LS. Is this different to the standard
> Audigy?

I am not sure...  How about consulting the topis starter below?
[http://ubuntuforums.org/showthread.php?t=117265](http://ubuntuforums.org/showthread.php?t=117265)

---

### Post by ceilingfish on 2006-02-10
Turns out I really should have checked the HCL before I bought. I have got an Audigy LS and those don't appear to work in linux according to the asla:

[http://www.alsa-project.org/black.html]("http://www.alsa-project.org/black.html")

They are not the same as other Audigy cards and as such none of the existing drivers work.

Back to the shop I think.

---

### Post by FarEast on 2006-02-10
Oh, that is too bad...
But sparky says: "Playback of sound works just fine".

---

### Post by Rekoil on 2007-09-21
I have the same problems as the OP, however in Debian its fine. Any ideas whats happening here?

Sorry for reviving an old thread but I thought thats at least better than creating a new one :P

```
rekoil@Rekoil:~$ lspci -v | grep audio
01:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
01:0d.0 Multimedia audio controller: Creative Labs SB Audigy LS
```

---

### Post by nero_86 on 2007-09-21
Is your kernel module correct for your audio card? If not change the module whiit the correct one. You can retrive the correct module in debian whit a lsmod command.
If the module is correct you can try whit an alsaconf in the terminal.
Here there are the driver for your card:

[http://us.creative.com/support/downloads/]("http://us.creative.com/support/downloads/")

Good luck!

---

### Post by Rekoil on 2007-10-05
Sorry for not replying earlier, I switched back to Debian again (running Lenny, working really well).

```
Rekoil:/home/rekoil# lspci -v | grep audio
01:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
```

That's what Debian says. (I have the built in SBLive! 24-bit disabled as the Audigy is working again)

So it seems Ubuntu was using the right module which is really weird. Only thing I can think of is that the module in Ubuntu is faulty, but I'm probably just doing something wrong in Ubuntu.

Anyway I think I'm just gonna stick to Debian anyway, it works perfectly fine for me. I actually only bothered with Ubuntu for compiz-fusion as I couldn't find a repository for 64-bit Debian. But with 32-bit Debian theres a tuxfamily one and its working fine so yeah, I'm sticking to Debian.

Thanks for the help though nero_86. If I use Ubuntu again before I get a new sound card (this one is getting a tad old :P) I'll try alsaconf and post the result here.

---

