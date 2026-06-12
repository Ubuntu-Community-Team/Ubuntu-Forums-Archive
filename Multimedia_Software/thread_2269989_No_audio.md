---
title: "No audio"
date: 2015-03-19
forum: Multimedia Software
---

### Post by michele-baravelli on 2015-03-19
Hi everyone; I'm desperate!!:cry: I've tried every solution on internet, but nothing: audio doesn't want to come out.
I think because my laptop it's too old (2006), but I saw many old pcs in this forum..could anyone help me, please?

---

### Post by michele-baravelli on 2015-03-19
-Computer-
Processor        : Intel(R) Celeron(R) M processor         1.40GHz
Memory        : 961MB (196MB used)
Operating System        : Ubuntu 14.10
Audio Adapter        : ICH - SiS SI7012

---

### Post by dino99 on 2015-03-19
welcome michele  ):P

it's easier to know a bit about the user's config for helping ;)
anyway i will try to give the first steps:

sudo apt-get install pavucontrol

then from the menu, select 'pulseaudio volume control' inside the 'sound' submenu. There you will see 2 tabs: 'configuration' & 'output devices'
Let play something: either a song on your hdd, or a streaming radio
Then you will see sound activity (or not), you will then need to select the good options for your hardware (into both tabs above)

---

### Post by michele-baravelli on 2015-03-19
Nothing happend: there is sound activity (bar changes color) but the sound doesn't come out from speakers

---

### Post by tgalati4 on 2015-03-19
Try testing sound using headphones.  If you don't hear any sound, it could be that the output amplifer of the sound chip is burned out.  If you see activity bars, then sound is being sent to the sound chip.

Is this machine dual-boot?  Did sound work in Windows?

---

### Post by dino99 on 2015-03-19
you have to test which options are good, both inside 'configuration' tab  and then into 'output devices' tab
as you are seeing the sound bar activity changing, then it is only the options selected you need to change; nothing else.

---

