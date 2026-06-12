---
title: "Plugging an electric guitar into my laptop?"
date: 2008-05-04
forum: Multimedia Software
---

### Post by WBL on 2008-05-04
I've got the Ubuntu pre-installed Dell Inspiron 1525N.  It's running Ubuntu 8.04 (flawlessly).  A friend loaned me an electric guitar so I can learn the guitar. I notice that I have a microphone jack on my laptop.

I plugged the guitar in, but nothing happened.  Is there software I can install, or will plugging the guitar into my laptop never work?

-WBL

---

### Post by Stochastic on 2008-05-04
Chances are you have your levels in alsa-mixer turned down or muted on your mic input (run alsa-mixer from the command line).  As for recording your guitar through the mic input, be careful with the levels, as a guitar can output a much higher signal volume than a microphone can.  Try audacity or rezound as beginner software for recording.

---

### Post by WBL on 2008-05-04
> **Stochastic said:**
> Chances are you have your levels in alsa-mixer turned down or muted on your mic input (run alsa-mixer from the command line).  As for recording your guitar through the mic input, be careful with the levels, as a guitar can output a much higher signal volume than a microphone can.  Try audacity or rezound as beginner software for recording.

"command not found" when I type alsa-mixer into the command prompt...

-WBL

---

### Post by Stochastic on 2008-05-04
my bad, no hyphen in the command: alsamixer

---

### Post by WBL on 2008-05-04
> **Stochastic said:**
> my bad, no hyphen in the command: alsamixer

OK, everything in alsamixer is turned up to 100, except for a few things which say "MM" and don't allow me to adjust them...

-WBL

---

### Post by cb951303 on 2008-05-04
BTW, plugging in a guitar directly from mic or line in will sound terrible. You need a DI box to get rid off impedance differences (which you can find from 10$ to 200$ in any guitar store)

edit: I'm planning to buy a "toneport gx" myself. it's a DI box + usb sound device (it helps you get rid off the latency so that you can add realtime effects, cabin or amplifier simulations to the sound). I'm not sure that it will work in linux but I'll try it anyway...

---

### Post by WBL on 2008-05-04
> **cb951303 said:**
> BTW, plugging in a guitar directly from mic or line in will sound terrible. You need a DI box to get rid off impedance differences (which you can find from 10$ to 200$ in any guitar store)

edit: I'm planning to buy a "toneport gx" myself. it's a DI box + usb sound device (it helps you get rid off the latency so that you can add realtime effects, cabin or amplifier simulations to the sound). I'm not sure that it will work in linux but I'll try it anyway...

I don't really care how bad it sounds at this point, since I'm just learning.  I'd just like for it to work...

-WBL

---

### Post by cb951303 on 2008-05-04
> **WBL said:**
> I don't really care how bad it sounds at this point, since I'm just learning.  I'd just like for it to work...

-WBL

It may be noisy and really unclear. It may sound like your speakers are broken. So if you want to learn I suggest you to get a cheap DI box :)

---

### Post by WBL on 2008-05-04
I guess my question essentially boils down to this-do I need to install software to hook up the guitar to the laptop, or is it just not working in my Ubuntu setup for whatever reason?   Is it not plug 'n play?

-WBL

---

### Post by cb951303 on 2008-05-04
> **WBL said:**
> I guess my question essentially boils down to this-do I need to install software to hook up the guitar to the laptop, or is it just not working in my Ubuntu setup for whatever reason?   Is it not plug 'n play?

-WBL

it should work without any software
it looks like simple mixer configuration error

---

### Post by WBL on 2008-05-04
> **cb951303 said:**
> it looks like simple mixer configuration error

Any ideas on how to fix it?

-WBL

---

### Post by Stochastic on 2008-05-05
what exactly are you attempting to do by plugging the guitar in?  record the sound? hear it? add effects? analyze your playing & have the computer teach you songs? by simply plugging in and putting sound into the card nothing will happen, some software (such as Audacity for recording) will be needed to get any result.  Plug'n'play is only a term used for digital equipment, not plugging an analog signal into your soundcard and playing.  If you merely want to hear yourself then your mixer may be setup right as not all systems have input monitoring as default.

---

### Post by WBL on 2008-05-05
> **Stochastic said:**
> what exactly are you attempting to do by plugging the guitar in?  record the sound? hear it? add effects? analyze your playing & have the computer teach you songs? by simply plugging in and putting sound into the card nothing will happen, some software (such as Audacity for recording) will be needed to get any result.  Plug'n'play is only a term used for digital equipment, not plugging an analog signal into your soundcard and playing.  If you merely want to hear yourself then your mixer may be setup right as not all systems have input monitoring as default.

All I wanna do is *hear* the electric guitar.  If anyone could tell me what to install/do, it would be GREATLY appreciated.  :)

-WBL

---

### Post by loganp82 on 2008-05-05
get a program called guitarfx you can install the free trial from guitarfx.net

---

### Post by WBL on 2008-05-05
> **loganp82 said:**
> get a program called guitarfx you can install the free trial from guitarfx.net

That program is for Windows.  :(

Anybody know of any Linux software I can use?

-WBL

---

### Post by djbon2112 on 2008-05-05
As a guitarist with a history of recording, I hate to tell you, but basically it doesn't work that way. Amps/DI boxes greatly amplify the signal from the guitar which is VERY weak by computer mic input standards. You NEED some sort of signal booster. Either a DI box or some sort of all-in-one effects pedal with a headphone out (which can then be plugged into the input jack).

---

### Post by dchurch24 on 2008-12-01
> **cb951303 said:**
> BTW, plugging in a guitar directly from mic or line in will sound terrible. You need a DI box to get rid off impedance differences (which you can find from 10$ to 200$ in any guitar store)

edit: I'm planning to buy a "toneport gx" myself. it's a DI box + usb sound device (it helps you get rid off the latency so that you can add realtime effects, cabin or amplifier simulations to the sound). I'm not sure that it will work in linux but I'll try it anyway...

Hi, did you ever get the toneport working in Ubuntu? I'd be very interested in one of these myself.

---

### Post by cb951303 on 2008-12-01
> **dchurch24 said:**
> Hi, did you ever get the toneport working in Ubuntu? I'd be very interested in one of these myself.

nope, toneport series don't work in linux. Instead, now I use a semi-pro pci card + cheap DI box

---

### Post by dchurch24 on 2008-12-01
Thanks for that - I'll have a hunt round and see what works in Linux and what doesn't before I buy.

Cheers.

---

### Post by frederick2809 on 2011-06-08
Sthat orry Guys but you are all wrong, the only device on the market is a line 6 product and it sells for around $99.00 dollars but you can only record guitar or voice with it at one time unless you invest a little more and go to its big brother ux model and it sells for 149.00 and then you can record both because of the issue of delay the time it takes to play and have it come out at the same exact time and anyone worth there weight in the recording business knows that only the equiptment be it amixer or sound board will already address these issues so that is my advice 40 years of playing guitar. Frederick

---

