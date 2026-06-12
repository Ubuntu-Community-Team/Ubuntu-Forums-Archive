---
title: "White Noise?"
date: 2008-10-06
forum: Multimedia Software
---

### Post by nuzzynh on 2008-10-06
I've just installed Ubuntu and fear I may be over my head in trying to resolve a problem with white noise (WN) coming out of the speakers continuously.

My sound card is a SB Live! 5.1 and it seems to be working fine.  However, there is a constant WN that varies directly with changes to the volume setting.  That is, if I turn my speakers up, the WN gets louder and vice versa.  

I've played music (it nearly drowns out the WN) so I know that the sound card has been recognized and is functioning to some degree.

What could be causing the WN problem and how do I resolve it?  I will be happy to provide more specific info based on your suggestions/questions.  I just didn't want to put up a lot of irrelevant stuff and reveal the *complete *extent of my ignorance. ;)

---

### Post by JerryG78 on 2008-10-06
I can think of 2 possibilities -

1) You have a bad ground somewhere.

2) Go to your mixer, and one at a time, mute your input channels. I had a noisy TV tuner card, and I had to mute the (line-in) input when I wasn't using the card.

HTH,

-Jerry

---

### Post by minky311 on 2008-10-06
Have you tried double clicking the speaker icon located on the top panel and experimenting with that.
Edit:Try what the JerryG78 suggested.

---

### Post by Teefs on 2008-10-06
I am not sure if it is the same problem, but I was actually experiencing a similar effect earlier. I had my microphone boosted to maximum. When it wasn't connected i would get noise out of my speakers. I fixed it by turning down the mic boost setting. 

Hope this helps!

---

### Post by nuzzynh on 2008-10-07
[SIZE="2"]It turns out that on the volume control there's a tab called 'switches' and on it a box (SB Live Analog/Digital Output Jack) was checked off.  As soon as I removed the check, the noise stopped.  Problem solved!

Thanks for your insight and help, folks.

[/SIZE][FONT="Times New Roman"][/FONT]

---

### Post by JerryG78 on 2008-10-07
Glad to be of help!

Cheers,

-Jerry

---

### Post by bond17_007 on 2008-10-16
Hi, 
I have a similar problem. 
I am using dell inspiron 1525. it came with a built-in intel sound card. 
I hear white noise through the speakers as well as the earphones. 
Even when i have the audio in MUTE, the white noise is still present.
I tried all combinations in the alsa mixer but no luck. 
I am worried that it might ruin my soundcard. 
any help would be greatly appreciated.

---

### Post by jsschreck on 2008-10-24
I also have a Dell Inspiron 1525 and have the same static problem. 

Ive noticed that it is related to flash - before I start up a flash program, the sound will mute just fine with no static, but once flash is running, if I mute, I hear loud static coming out of the speakers (and also headphones if they are plugged in). This started happening when I upgraded to Intrepid-beta. Everything was fine in 8.04. I filed a bug report here - [https://bugs.launchpad.net/ubuntu/+bug/288386](https://bugs.launchpad.net/ubuntu/+bug/288386)

Any fixes would be greatly appreciated!

---

### Post by bond17_007 on 2008-10-24
I do a dual boot. Since I noticed that in Interpid, i checked on Vista.. same issue. I recently bought this PC so I had Dell replace the MB but this still exists.
So Dont think its software issue perhaps hardware?

---

### Post by clearshot on 2008-10-26
I use this;

Using Kernel 2.6.27-7-generic
Dell 1525N
Ubuntu 8.10

When it's muted, any sound playing on the OS makes the speakers crackle. Unmuted, sound works fine. I had to tweak and play with it in Hardy though.

---

### Post by zalmoxes on 2008-11-20
i muted both my line-in / capture-devices to temporarily fix the problem.

i'm still looking for a permanent solution to the problem.

---

### Post by gallo008 on 2009-02-27
Hello. 

I had this problem with my laptop DELL 1525 with ubuntu hardy, kernel 2.6.24-19-generic.

The solution for me came from an accident.

I had my amplifier connected to the lap, obviously with the white noise in the background. 
I was hurry cause I had classes, so I disconnected every USB from my computer. And... Voila!!!  The noise has gone.

The USB that was making the noise was my hp psc 1200 printer.

Now I  just disconnect it, and is fine!!!!!

I hope my experience helps.

cheers

---

