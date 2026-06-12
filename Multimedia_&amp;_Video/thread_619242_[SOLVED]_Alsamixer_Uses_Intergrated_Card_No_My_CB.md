---
title: "[SOLVED] Alsamixer Uses Intergrated Card No My CB"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by MofoVideo on 2007-11-21
My sound card is a [SB Live! Value] EMU10k1X came with my Dell 4600. My sound works in Windows xp. But My sound doesnt work with Ubuntu....
If i have my Speakers plugged in to my integrated sound card It works and I have sound.
When I do alsamixer in terminal i get 

 Card: Intel ICH5                                                             &#9474;
&#9474; Chip: Analog Devices AD1980                                                  &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00, 0.00]
I want the card To be creative =[


Oh yah im using 7.10

---

### Post by pedx1ng on 2007-11-21
Take a look at this site:

[https://help.ubuntu.com/community/DebuggingSoundProblems]("https://help.ubuntu.com/community/DebuggingSoundProblems")

I had a similar issue.

This section is what solved my problems:

> If you have no sound and you have a regular sound card type "lsmod | grep snd" in the terminal and see if there is more than one card listed. It's possible that you have a motherboard sound chip that is interfering. Add it to the bottom of the blacklist file. For example, sudo nano /etc/modprobe.d/blacklist then add "blacklist snd_via82xx" to the bottom.

Your onboard sound is different so I guess you'd need to use a different entry for blacklist.

---

### Post by MofoVideo on 2007-11-21
ok I blacklisted it now when I try to do alsamixer it gives me 



alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by pedx1ng on 2007-11-21
When you run the command ```
cat /proc/asound/cards
``` do you see your Creative card listed?

Something I forgot to mention is that after making the changes I ran this command:

```
sudo /etc/init.d/alsa-utils restart
```

But I assume you just rebooted which would have been another way to apply the changes.

Anyway, I'm afraid I won't be much help if it remains a problem because I'm fairly new myself.  It's just that your issue sounded similar to one I had so I thought I could point you to that link and hopefully take care of it.  If not, you'll have to wait until some gurus arrive. ;)

---

### Post by MofoVideo on 2007-11-21
Yeah I just reset after i did it


and yes Its listed

$ cat /proc/asound/cards
 1 [Live           ]: EMU10K1X - Dell Sound Blaster Live!
                      Dell Sound Blaster Live! at 0xdf20 irq 22

---

### Post by MofoVideo on 2007-11-21
I got alsamixer to use the card now 
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: Dell Sound Blaster Live!                                               &#9474;
&#9474; Chip: SigmaTel STAC9708,11                                                   &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00, 0.00


[EDIT]


Fixed!!!! Yes =] 

First Alsamixer wasnt using the card as the default so I had to add 
> 
pcm.!default {
    type hw
    card 1
}
ctl.!default {
    type hw
    card 1
}

and save it as asound.conf and put it in etc

then i 

In the ALSA mixer GUI use arrows to go right to the Audigy Analog/Digital Output Jack

In my case I had to TURN OFF the Audigy Analog/Digital Output Jack switch.

Thanks for the help pedx

---

