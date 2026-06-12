---
title: "Skype overload my cpu by using too much pulseaudio"
date: 2011-06-21
forum: Multimedia Software
---

### Post by mellouli on 2011-06-21
Like I said in the title skype takes more than 30% if the cpu usage with more than 25 % used by pulseaudio
to be sure pulseaudio was the problem Itried
```
cpulimit -p (pulseaudio PID) -l 1
```
then skype used only 1 % of cpu and the sound was horrible
please help

---

### Post by Lars Noodén on 2011-06-21
The longer term solution is to migrate to SIP.  There are a lot of good SIP clients out there.  They can all talk to each other.

[indent]
Blink
Ekiga
Empathy
Jitsi
Linphone
QuteCom
Twinkle
[/indent]

That doesn't help with the immediate problems with Skype, but Skype has a new owner and the prognosis for future linux support worsens.

---

### Post by mellouli on 2011-06-21
> **Lars Noodén said:**
> The longer term solution is to migrate to SIP.  There are a lot of good SIP clients out there.  They can all talk to each other.
[INDENT]
Blink
Ekiga
Empathy
Jitsi
Linphone
QuteCom
Twinkle
[/INDENT]That doesn't help with the immediate problems with Skype, but Skype has a new owner and the prognosis for future linux support worsens.
is it safe like skype no one can spy on me or something

---

### Post by Lars Noodén on 2011-06-21
> **mellouli said:**
> is it safe like skype no one can spy on me or something

They are much safer than Skype. It's hard not to be. ;)

Also, SIP is a bit more like e-mail in that there are different clients that can talk with each other.

---

### Post by mellouli on 2011-06-21
ok I solved the problem with just removing pulseaudio and choosing the name of my sound card

---

