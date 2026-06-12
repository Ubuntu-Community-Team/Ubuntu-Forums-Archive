---
title: "Anybody Else Having Problem With Sound On Ubuntu\Kubuntu, etc.?"
date: 2008-08-11
forum: Multimedia Software
---

### Post by SSVegito888 on 2008-08-11
I recently started switching from Windows Vista to Ubuntu Hardy Heron 8.04.

I like Ubuntu a lot better than Windows so far.

I do however miss some things about Windows.

One of the the things I miss is the sound quality.

For example, when I play my mp3s, I hear a lot of background noise.

I hope they fix this by the next Ubuntu release.


Until then, what can I do to make my sound better?


Also, what is the best multimedia system to use in Ubuntu 8.04, ALSA, pulseaudio, etc.?


Thanks,

SSVegito888

---

### Post by brujoand on 2008-08-11
Pulseaudio is the new and glorius, and combines all sound mech to one interface. However, it might just be that your sound settings are a litte of. try adjusting the level manually, it could be that the sound is amplified to high and then reduced again, making it sound like your speakers are broken. Sound about right?

---

### Post by SSVegito888 on 2008-08-11
That was one of the things I thought until I read that Linux doesn't always have the best sound drivers.

Also, I know the speakers aren't broken because I plugged in headphones directly into my pc tower.

So, you are probably right.


How would I go about manually changing all of the stuff you mentioned?

Remember I am a noob.


Thanks,

SSVegito888

---

### Post by brujoand on 2008-08-12
try to open a terminal (applications --> accessories --> termianal)
type in "alsamixer" , if its not installed type "sudo apt-get install alsamixer" to install it. And this will let you change the different volumes for your soundcard, given that it is supported by alsa. See, often the one volume like front can be set low and speakers set high making the sound loose quality. 

But for further instructions someone else better contribute because my knowledge pretty much stoppes here. But this procedure has helped me out in similar cases.

good luck

---

### Post by Ubuntaqua on 2008-08-12
In some cases, I've seen that the mike output was on by default, even if volume is set to 0 (or very low). Hope it helps.

---

### Post by Limbic on 2008-08-12
> **Ubuntaqua said:**
> In some cases, I've seen that the mike output was on by default, even if volume is set to 0 (or very low). Hope it helps.

I had this exact problem.  I was getting a lot of background noise (white noise normally, with a little humming when the volume was way up), then I went in to the Alsa Mixer and found that the Mic Boost was on.  Muted the Mic Boost and now everything sounds great; no background noise even when cranked up as loud as I'm willing to go.

---

### Post by bobpur on 2008-08-12
I don't know what your computers specs are, but if it is a dual core cpu you might try the 64-bit version of Ubuntu. Sound quality is better with the 64-bit version.
I use lower end Creative Labs sound cards (Audigy 2, 4, and SE)with the 64-bit Ubuntu v7.10 and the sound is great. Also, Diamond (5.1 or 7.1) makes a decent sound card that works in Ubuntu.
I seem to have less trouble with sound and video drivers if they are installed first after a fresh OS install. No proof to offer, just my way of doing it.
Check your Bios to make sure your Onboard sound is de-activated so as not to conflict with your  PCI soundcard. I'm not sure on this last point as I've got one computer that I use an X-fi card for WinXP and have to switch the plug to the mobo connection for sound in Ubuntu. I hear that there is an open source X-fi driver, but I haven't fooled around with it any.

Good Luck.

---

### Post by SSVegito888 on 2008-08-15
On my desktop pc, I have a pentium 4 processor, but I don't know if it is 64bit or not.


Also, on my notebook pc, I have a core2duo processor, but again I don't know if it is 64bit or not.


How do I find out?

Is there any kind of software that will tell me?



Thanks,

SSVegito888

---

### Post by SSVegito888 on 2008-08-15
I did a little more research and found this command:

cat /proc/cpuinfo

Here are the results when I run on my notebook pc under knoppix ver. 5.3.1:


processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
stepping        : 13
cpu MHz         : 800.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida
bogomips        : 3995.19
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
stepping        : 13
cpu MHz         : 800.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida
bogomips        : 3991.23
clflush size    : 64




Does the line "clflush size    : 64"  mean that I have a 64 Bit processor?




Thanks,

SSVegito888

---

### Post by markbuntu on 2008-08-15
Duo cores are all 64 bit. I think the pentium was the first 64 bit processor from intel but it may have been the last 32 bit processor. I forget, it was a long time ago.

---

### Post by Murdoc_of_puts on 2008-08-16
Does the line "clflush size    : 64"  mean that I have a 64 Bit processor?




I believe that it does. I did some research on it.  Also, my 32 bit system has an output of clflush size :32

---

### Post by SSVegito888 on 2008-08-17
Thanks.

---

