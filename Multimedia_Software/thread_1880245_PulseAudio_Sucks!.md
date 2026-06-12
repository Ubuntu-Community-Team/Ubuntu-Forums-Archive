---
title: "PulseAudio Sucks!"
date: 2011-11-13
forum: Multimedia Software
---

### Post by Joshwaa on 2011-11-13
Whenever I restart my computer all my hardware disappears from the PulseAudio Audio Settings and the sound indicator disappears from the top bar. Whenever I run aplay -l my sound devices are listed.
I have no idea what's going on, I've tried purgeing and reinstalling both alsa and pulseaudio and reinstalling but that only works until I restart next.

Any help?

---

### Post by MoreOrLess on 2011-11-13
You'll have to look in dmesg to see why the kernel module isn't loading.
Note: this has nothing to do with pulseaudio. That's like downloading/installing the wrong sound driver in Windows and declaring, "Device Manager sucks!"

---

### Post by Joshwaa on 2011-11-14
Can someone please help? This is urgent, I'm close to just removing Ubuntu altogether right now.

---

### Post by MoreOrLess on 2011-11-14
...
> **MoreOrLess said:**
> You'll have to look in dmesg to see why the kernel module isn't loading.

This might make it easier: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Joshwaa on 2011-11-14
> **MoreOrLess said:**
> ...

It'd help if I knew what I was looking for..

Here's the output of aplay -l anyway
[http://pastie.org/2862392](http://pastie.org/2862392)

---

### Post by Joshwaa on 2011-11-14
[http://www.alsa-project.org/db/?f=5d2368dfafd2110db8f488f52c670f7f0e664a2c](http://www.alsa-project.org/db/?f=5d2368dfafd2110db8f488f52c670f7f0e664a2c)

That's what I got back

Oh derp, after reading it "Pulseaudio Running: No"
I've just added PulseAudio to startup applications, hopefully this will fix it.

---

### Post by inobe on 2011-11-14
it's a way to diagnose the problem.

simply open terminal, then paste **cd ~/** in terminal and hit enter.

now paste 

```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
``` and hit enter, type **y** to upload your results.

once it's done, it will provide a link, you can paste that link on next post.

---

### Post by Joshwaa on 2011-11-14
> **inobe said:**
> it's a way to diagnose the problem.

simply open terminal, then paste **cd ~/** in terminal and hit enter.

now paste 

```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
``` and hit enter, type **y** to upload your results.

once it's done, it will provide a link, you can paste that link on next post.

I just did that above, PulseAudio wasn't running for some weird reason, it was my understanding that it opened automatically on boot but I probably broke it.

Thanks for your help!

---

### Post by inobe on 2011-11-14
i found this method, get confirmation before trying it!

[https://wiki.ubuntu.com/PulseAudio#PulseAudio_does_not_start_automatically](https://wiki.ubuntu.com/PulseAudio#PulseAudio_does_not_start_automatically)

> PulseAudio does not start automatically
If PulseAudio does not start at login time, you can try to set the gconf value of /desktop/gnome/sound/enable_esd to true.

---

### Post by inobe on 2011-11-14
notice the thread is solved, may i ask what solved it?

---

### Post by Joshwaa on 2011-11-14
> **inobe said:**
> notice the thread is solved, may i ask what solved it?

I just added the pulseaudio command to startup applications, seems like a cheap fix.

---

### Post by inobe on 2011-11-14
review post **#9** if you have any problems.

glad you solved it.

---

### Post by MoreOrLess on 2011-11-16
> **inobe said:**
> review post **#9** if you have any problems. glad you solved it.

I don't think that's applicable to modern versions of Ubuntu. IIRC, Ubuntu has used libcanberra for system sounds since Jaunty.

---

