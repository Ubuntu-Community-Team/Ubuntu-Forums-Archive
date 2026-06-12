---
title: "Pulseaudio problem"
date: 2010-09-26
forum: Multimedia Software
---

### Post by Colo2 on 2010-09-26
Hello everyone

I am setting up ubuntu studio on my dad's PC. He has 2 x Delta 1010 audio cards for his recording studio.

My current problem is: > Waiting for sound system to respond

I'll explain what's happend here.

First of all, the Delta drivers wouldn't work. So I did some googling and found out that Delta 1010s don't work with pulseaudio. So I went ahead and followed a tutorial to remove it. This one:
[http://ubuntuforums.org/showthread.php?t=963914&highlight=pulseaudio+audiophile](http://ubuntuforums.org/showthread.php?t=963914&highlight=pulseaudio+audiophile)

Since then, the audio works, but the "Sound" control in the preferences returns the error: 
> Waiting for sound system to respond

does anyone know what to try? 

thanks

---

### Post by cchhrriiss121212 on 2010-09-26
The sound entry in the preferences menu is designed for Pulse only so you may as well remove it. Envy24control is the GUI to control these cards, I think it comes installed on Studio, if not it is in the alsatools package.
Have you had jack running yet with both cards going? I'd be interested to see your settings if so.

---

### Post by Colo2 on 2010-09-26
> **cchhrriiss121212 said:**
> The sound entry in the preferences menu is designed for Pulse only so you may as well remove it. Envy24control is the GUI to control these cards, I think it comes installed on Studio, if not it is in the alsatools package.
Have you had jack running yet with both cards going? I'd be interested to see your settings if so.

Hey, thank you for your reply.
I'll check this out tomorrow. 

Jack? what's that. I got a jack error once when opening audour butw when I tried the next time there was no error. To be honest with you, I dont know much about the sound side of things, that's my dad's business :P

Is there something I should know related to the functionality of the cards in Linux?

Thanks

Tom

---

### Post by Yellow Pasque on 2010-09-26
This PPA has a few packages for those not running pulse: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)
After you install them, you can logout/in, and then you should be able to add a volume control applet to your panel. Media keys (if you have them) should work again too.

---

### Post by cchhrriiss121212 on 2010-09-26
> **Colo2 said:**
> 
Jack? what's that. 
Jack is the sound server that your Dad will be using if he wants to make/produce music. It works on top of ALSA just like Pulse, but unlike pulse it is professional quality and has low latency audio mapping.
I wondered what your settings were because you may need to do extra tweaking to get both soundcards working at the same time (which I assume is what you want?). I have heard that it should work fine if both cards are the same type, but I have not tried it myself.
If I were you/your Dad I would get it all set up with one card, and add another when you understand how it all works. Try posting a thread about it in the [studio forum]("http://ubuntuforums.org/forumdisplay.php?f=335"), which is where all the jack-knowledgeable users will see it.

> 
Is there something I should know related to the functionality of the cards in Linux?
You know about pulse already, so the only other thing is that you need to set the volume when you install, as these cards are always muted by default. You set volume in the analogue volume tab of envy24control, DAC means outputs and ADC means inputs.
Once they are set up they work great, you should aim for <5ms latency with jack.

---

### Post by Colo2 on 2010-09-26
> **cchhrriiss121212 said:**
> Jack is the sound server that your Dad will be using if he wants to make/produce music. It works on top of ALSA just like Pulse, but unlike pulse it is professional quality and has low latency audio mapping.
I wondered what your settings were because you may need to do extra tweaking to get both soundcards working at the same time (which I assume is what you want?). I have heard that it should work fine if both cards are the same type, but I have not tried it myself.
If I were you/your Dad I would get it all set up with one card, and add another when you understand how it all works. Try posting a thread about it in the [studio forum]("http://ubuntuforums.org/forumdisplay.php?f=335"), which is where all the jack-knowledgeable users will see it.


You know about pulse already, so the only other thing is that you need to set the volume when you install, as these cards are always muted by default. You set volume in the analogue volume tab of envy24control, DAC means outputs and ADC means inputs.
Once they are set up they work great, you should aim for <5ms latency with jack.

thank you very much for your reply. I'll show him this thread tomorrow morning :)

---

