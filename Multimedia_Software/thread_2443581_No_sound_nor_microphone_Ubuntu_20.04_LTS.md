---
title: "No sound nor microphone Ubuntu 20.04 LTS"
date: 2020-05-17
forum: Multimedia Software
---

### Post by lima-vaz-eduardo on 2020-05-17
Greetings,

I would like to kindly ask your help to troubleshoot my Dell G3 3590 notebook.

Default factory Ubuntu 18.04.2, sound and microphone work perfectly fine. 
After moving to 18.04.4, both sound and mic disappeared. 

I am now running Ubuntu 20.04 LTS.

Please see my config at:
[http://alsa-project.org/db/?f=7f4969c94b8b8652bdc5e7bb4317e674081198ca](http://alsa-project.org/db/?f=7f4969c94b8b8652bdc5e7bb4317e674081198ca)

Thanks in advance,

Eduardo

---

### Post by lima-vaz-eduardo on 2020-06-02
Greetings,

I have tried everything I can to fix speakers and microphone issues in my Dell G3 3590 with no success.

I decided to make a factory reset and go back to 18.04.2 where sound and microphone work flawlessly.

Here is the configuration for 18.04.2:
[http://alsa-project.org/db/?f=80821bb34cffa70096149ac8d54144bae7f9a85e](http://alsa-project.org/db/?f=80821bb34cffa70096149ac8d54144bae7f9a85e)

Here is the configuration for 20.04:
[http://alsa-project.org/db/?f=7f4969c94b8b8652bdc5e7bb4317e674081198ca](http://alsa-project.org/db/?f=7f4969c94b8b8652bdc5e7bb4317e674081198ca)

I would be glad if someone could find out what settings I need to change, because any time from now an update will come and I`ll loose sound and microphone again.

I have spent a great deal of time talking to Dell support, worst moments of my life, and I came to conclusion that Dell does not care about Ubuntu. I honestly did not expect to be treated as bad as I was by Dell customer service.

Hope the information above could be useful to troubleshoot this sound issue in Dell G3 3590 that perhaps could be happening in other users as well.

Thanks in advance,
Eduardo

---

### Post by asgard2 on 2020-11-29
> **lima-vaz-eduardo said:**
> Greetings,
I have tried everything I can to fix speakers and microphone issues in my Dell G3 3590 with no success.


Could you find a solution?

The solution from this post is not working (any more?).
[https://answers.launchpad.net/ubuntu-certification/+question/690183](https://answers.launchpad.net/ubuntu-certification/+question/690183)

```
cd /lib/firmware/intel/sof;sudo ln -s sof-cnl.ri sof-cfl.ri;reboot"
```


To prevent freezing after boot, I used the "snd_hda_intel.dmic_detect=0" boot option.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1899132](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1899132)

---

### Post by asgard2 on 2020-12-17
I bought an external microphone (phone connector) and it is also not working. Listed as unplugged at audio mixer, "input devices".

What could be the cause? 

... i need a microphone :(

---

### Post by pat944 on 2020-12-19
0

---

### Post by crpz41 on 2020-12-28
try to open alsamixer on command line.... 
after you selected with F6 your output device, you'll notice some double (MM) on the bottom of the bars... 
just press M and should it unmute.

I have another problem: I've been able to get audio in this way but once I reboot I have to re-do ... so frustating

---

### Post by asgard2 on 2021-01-02
> **crpz41 said:**
> try to open alsamixer on command line.... 
after you selected with F6 your output device, you'll notice some double (MM) on the bottom of the bars... 
just press M and should it unmute.

I can select two devices on F6:
On intel, it looks like this: Sound is working, microphone is not working, there is no Microphone to unmute.

[ATTACH=CONFIG]287666[/ATTACH]

If I select Nvidia, this option appears, not sure what to do here ...
[ATTACH=CONFIG]287667[/ATTACH]


Could you help?

---

### Post by crpz41 on 2021-01-02
no I didn't solved, once I reboot everything comes back as before

---

### Post by chrysanthemum2 on 2021-01-02
Install pavucontrol and see if that enables you to select the right device.

> sudo apt-get install pavucontrol

---

### Post by asgard2 on 2021-01-03
> **chrysanthemum2 said:**
> Install pavucontrol ...
It is installed, an internal microphone is selected but receives no input. Second option is "Microphone (uplugged)" without any input with plugged in headset.



[ATTACH=CONFIG]287676[/ATTACH]

---

### Post by chrysanthemum2 on 2021-01-03
> **asgard2 said:**
> It is installed, an internal microphone is selected but receives no input. Second option is "Microphone (uplugged)" without any input with plugged in headset.



[ATTACH=CONFIG]287676[/ATTACH]

I had a similar issue with it saying unplugged when I had a failed cable. Do you have a spare mic cable to try and see if that solves it being seen as unplugged?

---

### Post by asgard2 on 2021-01-03
I have a second headset which is not working on this dell notebook and the headsets are working on other devices. :/
Sound is working, but not the microphone, same problem as with the internal microphone.

---

