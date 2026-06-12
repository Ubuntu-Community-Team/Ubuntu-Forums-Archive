---
title: "Sound only works for one application at a time?"
date: 2010-05-28
forum: Multimedia Software
---

### Post by Jarthur121 on 2010-05-28
Hey Everyone, I have quite a strange problem with my sound.

I recently did a new install of Kubuntu 10.04 LTS, and I  installed updates using:

```
sudo apt-get update
```And got Kubuntu restricted Extras using:

```
sudo apt-get install kubuntu-restricted-extras
```
Now, say for example I open Amarok and play some music it'll play. But, if I want to watch a youtube video (on Firefox) or someone chats to me on Facebook (on Firefox) the sound will cut out from Amarok (It will still be playing) and go to the Facebook Chat. To listen to anything on Amarok I have to close both applications and run Amarok again.


My question is, is this normal for Kubuntu? If not, how do I go about setting up my sound correctly so that it works across multiple applications without cutting out?

Edit: This is not just an issue with Firefox and Amarok, it's the same with any other applications.

Thanks for your time :).

---

### Post by lovinglinux on 2010-05-28
I don't use Amarok, but sound works for me using multiple applications.

Go to "System Settings >> Computer Administration >> Multimedia" and move [pulseaudio](apt:pulseaudio) to the top of all lists. That's works for me, but I use kde-minimal installed over a command-line only Ubuntu, not Kubuntu.

---

### Post by Jarthur121 on 2010-06-01
> **lovinglinux said:**
> I don't use Amarok, but sound works for me using multiple applications.

Go to "System Settings >> Computer Administration >> Multimedia" and move [pulseaudio]("apt:pulseaudio") to the top of all lists. That's works for me, but I use kde-minimal installed over a command-line only Ubuntu, not Kubuntu.

I don't have pulseaudio in any of those lists... Could that be the problem?

---

### Post by lovinglinux on 2010-06-01
> **Jarthur121 said:**
> I don't have pulseaudio in any of those lists... Could that be the problem?

Yes. I'm not sure if Kubuntu uses pulseaudio by default, but sound only works for me when I install it.

---

### Post by Jarthur121 on 2010-06-01
So I just install it through terminal and move it to the top of all my lists in Multimedia and it should work? Thanks, I shall test it when I get home.

---

### Post by lovinglinux on 2010-06-02
> **Jarthur121 said:**
> So I just install it through terminal and move it to the top of all my lists in Multimedia and it should work? Thanks, I shall test it when I get home.

Yes. That's how I do it. Nevertheless, I don't use Kubuntu. I use KDE minimal installation over a command-line only Ubuntu system.

---

### Post by Jarthur121 on 2010-06-06
Thanks for that, it worked a charm :)

---

### Post by coljohnhannibalsmith on 2010-08-07
I have a similar problem, but I am using Ubuntu Lucid Lynx x64, not Kubuntu, so my sound settings are not located in the same place.  In fact I'm not even sure I can even access the settings you describe, without adding another application.     I'm also using ALSA.  Does that matter?


Thanks, Hannibal

---

