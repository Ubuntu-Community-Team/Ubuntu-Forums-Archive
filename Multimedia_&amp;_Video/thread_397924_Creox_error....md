---
title: "Creox error..."
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by Drate on 2007-03-31
I am running Ubuntu Edgy + the Kubuntu Desktop installed.  I downloaded Creox, I plugged my stuff in, and I got what evidently is a fairly common problem: when I hit Play it gives me a very detailed error... it says exactly this: "Error".

Informative right?  I've tried it both in KDE and GNOME. So I have seen this one person saying something about starting it with a bit of terminal command involving this command "jackd" and I tried that and it said there is no "jackd" command.

So yeah... it'd really be cool if someone could help me out!

---

### Post by Drate on 2007-03-31
Wow, this is the first time nobody replied to me.

---

### Post by Drate on 2007-04-01
Okay, could I be redirected then to somebody that might could help?

---

### Post by sashaluda on 2007-10-12
> **Drate said:**
> Okay, could I be redirected then to somebody that might could help?

You have to launch jackd first (it's a kind of application to process sound a certain way) and then launch creox while jackd is running somewhere in another terminal window.
I've found an easy way to do two at once (besides that - with closing creox -- jackd ends it's work):
press Alt+F2 and type
jackd -d alsa -d hw:0 & creox

For some strange reason this command can not be added to the menu (maybe it's too complicated for the menu launcher)

Have nice playing time
Sasha:guitar:

---

### Post by prasadz8 on 2008-04-07
THANKS! yup this worked on my ALSA AMD64 Gutsy - eaaasy breeezy, lemon squeezy... Creox rrrrrrox!!

Look up Synaptic for more JACK applications, worth it.
-Jack beat
-Jack EQ
-Jack Rack

Q: How do we run Sound Recorder AND run Creox at the same time?
JACK doesn't allow this, why? I'm presuming it's ALSA. All my multimedia settings are set to ALSA. Some help needed on this.

---

