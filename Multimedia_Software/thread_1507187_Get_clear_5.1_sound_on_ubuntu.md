---
title: "Get clear 5.1 sound on ubuntu?"
date: 2010-06-11
forum: Multimedia Software
---

### Post by Einstein86 on 2010-06-11
Hello here,
    I have problem to get clear sound through my 5.1 speakers. I can hear out sound from evry speaker, but it's kind of shrilly. How can fix it that if someone has the idea I'd be thankful very much.

---

### Post by lidex on 2010-06-13
That's a pretty subjective description, can you elaborate? And while you're at it...
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Einstein86 on 2010-06-21
Hi i think this is you need, it screen me all but my audio card, Realtek ACL850. I think this 'NVidia CK8S' is integrated. What do you think now? Thanks ahead

---

### Post by lidex on 2010-06-21
Interesting, as in Doh! Let's upgrade your kernel, then your alsa install. If you have alsa-backports installed, uninstall please.
OK. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Now reboot so we can work with the latest kernel. Follow the alsa-upgrade link in my sig to get v 1.0.23

BTW, can you post this output:
```
head -1 /proc/asound/card0/codec97#0/ac97#0-0
```
And what is the make/model of this computer?
Does it sound as if it's playing too fast?

---

### Post by Einstein86 on 2010-06-23
i did it all steps you wrote. still is same :( l'm using amd sempron 1.61GHz 64bits, hdd maxtor 80GB, audio card realtek alc850, graphical card ati readeon 9600 256MB..

if i set 5.1 in software, output sound is somethin like oscillates up and down but when i set only stereo it's totaly alright. you mignt know what's about?

thanks so far

---

### Post by lidex on 2010-06-25
Did you upgrade to alsa 1.0.23?

---

### Post by Einstein86 on 2010-06-25
yes sir, i did all your commandments :)

---

### Post by lidex on 2010-06-25
What is this output now:
```
cat /proc/asound/version

```

---

### Post by Einstein86 on 2010-06-27
this is that, i just don't know how to solve problem. but i want to because it's must be the way:(

---

