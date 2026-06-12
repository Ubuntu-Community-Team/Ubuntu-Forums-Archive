---
title: "Midi in ?"
date: 2006-05-24
forum: Multimedia &amp; Video
---

### Post by Sandsound on 2006-05-24
Hi all

Been lokking everywhere for som info on midi-input. I have anything up and running except my midikeyboard, cant get any respond in any programs.

I'm a total newbie when it comes to Linux, so my aproaches might seam a bit odd to all of you experts. Anyway... here's what I have tryed :

Installed Dapper... Looks nice
installed my ATI Radon... Looks wery nice (cool penguinracer btw :-))
Installed misc. soundprograms sequencer and sutch... sounds nice
Followed every step given at [www.unbuntustudio.com](www.unbuntustudio.com)... COOL
Tryed to patch everything together... everything worked... amasing
But when I turned my MidiKeyboard on (always pluged in to my pc) there was no sound :-(
Tryed to patch every possible combination together in Jack-audio-connection-kit but still... nothing ?
Virtual keyboard works fine, but its just not the same playing with my mouse insted of all ten fingers.

I'd like to make the switch from MS, but can't survive without my midi-in, so please help a poor girl and free me from the Microsoft tyrany I have been living under for much to long.

My setup is a AMD64/1Gb RAM/2 80GbSata/ATI Radeon 9800/Audigy with breakout box and a standard MidiKeyboard

---

### Post by slugkilla on 2006-05-24
Hey man,
I got the same problem. Check it out.
[http://ubuntuforums.org/showthread.php?t=171829](http://ubuntuforums.org/showthread.php?t=171829)
hope that helps and hope someone helps us. BTW, What is your keyboard? Mine is a Yamaha PSR-195.

---

### Post by Sandsound on 2006-05-24
[QUOTE=slugkilla]I got the same problem. Check it out.
[http://ubuntuforums.org/showthread.php?t=171829](http://ubuntuforums.org/showthread.php?t=171829)
hope that helps and hope someone helps us. BTW, What is your keyboard? Mine is a Yamaha PSR-195.[/QUOTE]

Mine is an old Midi-only Roland pc-200.
It doesnt have a build in soundmodule, but that's never been a problem before.
It's the only thing stopping me from formatting my old MS-disk and making the switch to Linux, have tryed other dist. before, but noone compares to Unbuntu.

I'm sad to say that your link didnt help, but thanks anyway.

---

### Post by slugkilla on 2006-05-24
well maybe someone who knows a lot about midi and the sort will help us out.

---

### Post by bwanab on 2006-05-24
I don't know anything about the audigy, but I assume it has midi-in since you mention you've plugged your keyboard in. I haven't had any problem with my dapper system using my usb midi interface. 

What software are you running? Try running jack (use qjackctl), it has a Connect button. Click that and click on the Midi tab. Do you see your audigy as an in and out? 
If so, try running zynaddsubfx. It should connect itself to the audio out. Connect your audigy midi (readable), to zynaddsubfx midi (writable). Play the keyboard - you should hear or see some evidence that it's working.

---

### Post by Sandsound on 2006-05-24
[QUOTE=bwanab]What software are you running? Try running jack (use qjackctl), it has a Connect button. Click that and click on the Midi tab. Do you see your audigy as an in and out? 
If so, try running zynaddsubfx. It should connect itself to the audio out. Connect your audigy midi (readable), to zynaddsubfx midi (writable). Play the keyboard - you should hear or see some evidence that it's working.[/QUOTE]

I'm already running Jack. tryed all the examples at [www.unbuntustudio.com](www.unbuntustudio.com) and everything is working fine... except my midi-in.

I'm a bit confused about Jack thou, so I tryed all possible ways of conecting in the midi window of jack-connect. I know it might not be the optimal way, but trial and error has gotten me this far :-)

This is my options in the jack-connect window :
Left side :
62:Midi Through
64:Audigy MPU-401 (UART)

Right side :
62:Midi Through
64:Audigy MPU-401 (UART)
65:Emu10k1 WaveTable
127:ZynAddSubFX

What goes where and why... I still dont know, I have even tryed conecting everything on the left to everything on the right side :-)
I asume that 64:Audigy MPU-401 (UART) is the midi-in ?

---

### Post by bwanab on 2006-05-25
[QUOTE=Sandsound]I'm already running Jack. tryed all the examples at [www.unbuntustudio.com](www.unbuntustudio.com) and everything is working fine... except my midi-in.

I'm a bit confused about Jack thou, so I tryed all possible ways of conecting in the midi window of jack-connect. I know it might not be the optimal way, but trial and error has gotten me this far :-)

This is my options in the jack-connect window :
Left side :
62:Midi Through
64:Audigy MPU-401 (UART)

Right side :
62:Midi Through
64:Audigy MPU-401 (UART)
65:Emu10k1 WaveTable
127:ZynAddSubFX

What goes where and why... I still dont know, I have even tryed conecting everything on the left to everything on the right side :-)
I asume that 64:Audigy MPU-401 (UART) is the midi-in ?[/QUOTE]

Yes, the stuff on the left side is midi-in (from the perspective of your computer) and the stuff on the right side is midi-out. You mention that you've tried virtual keyboard. You lauch Vkeybd, and you see it on the left side. Then hook it to zynaddsubfx on the right side and you get sound? But when you hook audigy mpu-401(uart) from the left side to zynaddsubfx on the right side you get nothing?

---

### Post by Sandsound on 2006-05-25
[QUOTE=bwanab]Yes, the stuff on the left side is midi-in (from the perspective of your computer) and the stuff on the right side is midi-out. You mention that you've tried virtual keyboard. You lauch Vkeybd, and you see it on the left side. Then hook it to zynaddsubfx on the right side and you get sound? But when you hook audigy mpu-401(uart) from the left side to zynaddsubfx on the right side you get nothing?[/QUOTE]

Yes... have even tryed to use my husbands midikeyboard, still no luck.

I know that my hardware works, and I have used midi since the 80's so I have some expirience in this, but am an absolute beginner in Linux, I know it works internal thou, so maybe it's just that my soundcard isnt so happy running Linux ? have anyone tryed to play midi on an extern midi-keyboard via Audigy breakoutbox?
I also have a Prodigy 192 to try out, but it doesnt have a breakout box :-( and what happens when i install a new soundcard... will I have to recompile and all that ?

---

### Post by Sandsound on 2006-05-25
IT WORKS :-D 

I have found the solution to my problem... seams that the midi-in on my breakoutbox doesnt work under Ubuntu ???
Found an old midi-port-cable in the basement (the ones for joystick-ports) and mounted it to my the soundcard pcb. Now it finaly works.

Maybe this is a minor bug and maybe its more af a Audigy-problem, but can it realy be true that i cant use my breakoutbox ?
Not that I cant live without it, but the damn thing was pretty expensive when i bought it :( 

Well... I'm of to format my windoze partition... something a wanted to do for a long time :D

---

### Post by bwanab on 2006-05-25
Glad it's working for you. I'm perplexed about the breakout box. In the alsa soundcard matrix the audigy seems to be well supported with no caveats, but hey, there's lots of stuff going on there I guess. Best of luck to you with your newly freed disk space :)

---

