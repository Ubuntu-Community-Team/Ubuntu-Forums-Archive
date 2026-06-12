---
title: "Couldn't Open Audio"
date: 2006-01-20
forum: Multimedia &amp; Video
---

### Post by Kieffer87 on 2006-01-20
When a file is playing or sometimes not even playing, and I open it. Doesnt matter what app but I use xmms. I get a message saying
Couldn't open Audio figures now I cant get it to do it.
Anyhow it says 1.make sure you soundcard is configured properly 2. Make sure its not busy or somthing like it, and there is a third but I dont recall what it was. Ill post if it happens again. But any idea how to fix this? its annoying as hell

---

### Post by Kieffer87 on 2006-01-20
Ok I got it to do it. IT always does it when I dont have xmms open and double click ona file.

Couldnt open audio

Please check that:

1.Your soundcard is configured properly
2. You have the correct output plugin selected
3. No other program is blocking the soundscard

If I wait a few seconds then it will usually work.
I know its not blocked because if I hold the mouse over a file it still plays.

---

### Post by Kieffer87 on 2006-01-20
anybody?

---

### Post by FarEast on 2006-01-21
Hi Kieffer87;) ,

I want you to post the specs of your system,
particularly information regarding your sound card.

---

### Post by Kieffer87 on 2006-01-21
im pretty new to linux so anyhow the card is a SB Live! 24bit. I was using my onboard sound but I was having the same trouble if i recall correctly. Also maybe you can help me getting the rear speakers to work. I remember I did it on my onboard but I cant remeber now. Thanks

---

### Post by Kieffer87 on 2006-01-21
here is my lspci if that helps at all.
> 
0000:03:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs: Unknown device 1007
        Flags: bus master, medium devsel, latency 64, IRQ 17
        I/O ports at cca0 [size=32]
        Capabilities: <available only to root>


It works so Ive never really tryed to mess with it to get the live 24bit drivers for it. I guess that could possibly be my problem.

---

### Post by Kieffer87 on 2006-01-21
OK I narrowed it down to that if I open the file quickly i have no problem. However if I pause and its starts the preview for a file, then I open it, thats when i get the error.

---

### Post by Kieffer87 on 2006-01-23
I disabled that and it seems to help but I still ocasionally get the problem. Anyone hear of anything yet?

---

### Post by FarEast on 2006-01-23
I have not been able to access the forum for two days.
I am going to try to reproduce the problem here after I go back to home.

---

### Post by FarEast on 2006-01-24
> the card is a SB Live! 24bit. I was using my onboard sound but
> I was having the same trouble if i recall correctly.

Is the on-board sound chip disabled by BIOS?
What I am going to write is just a clue.  Anyway...
Below is the status of my system.

$ cat /proc/asound/cards
0 [Audio          ]: USB-Audio - USB Audio
                     C-Media INC. USB Audio at usb-0000:00:01.2-2, full speed
1 [YMF744         ]: YMF744 - Yamaha DS-XG (YMF744)
                     Yamaha DS-XG (YMF744) at 0xe9000000, irq 11
2 [SI7018         ]: SI7018 - SiS SI7018
                     SiS SI7018 PCI Audio at 0xd000, irq 11

$cat /etc/modprobe.d/sound
options snd-usb-audio index=0
options snd-ymfpci  index=1
options snd-trident index=2

If I start the system without USB sound apapter and try to play a sound
file with right-clicking it in the file manager(nautilus), I get the same error.

---

### Post by Kieffer87 on 2006-01-24
I recently did a reinstall of ubuntu, because somthing happened where it wouldnt requignize (sp?) any of my sound cards. Now everything is working fine, I have both onboard and the SB live card active and both work, and work well. I can even hear system sounds when listening to music as I never could before. The only thing I would still like is the 5.1 to work correctly. I havnt been able to get my center working yet.

---

