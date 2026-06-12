---
title: "Sound on Ubuntu 9.10 not working"
date: 2010-04-20
forum: Multimedia Software
---

### Post by LucasJA on 2010-04-20
Hello.

I was using Ubuntu 9.04 and my sound was working perfectly. Then, I upgraded my system to the 9.10 version. Now, my sound does not work.

I tryied to search on the Internet, found many solutions, but none worked for me.

The output for **lspci |grep -i audio** is:

[I]00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

[/I]The output for **aplay -l** is:

[I]aplay: device_list:223: no soundcards found...

[/I]On my sound preferences, Hardware tab, there is no hardware to select. The sound output is selected to Dummy Output.

Please, someone help.

Thank you for reading :KS

---

### Post by LucasJA on 2010-04-20
Here is a screenshot showing that there is no audio device to configure.

---

### Post by lidex on 2010-04-20
Do this for me please, in a terminal="Applications>Accessories>Terminal":
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Now reboot and post the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by LucasJA on 2010-04-21
Hello lidex.

I did what you asked. There is no output for the command you said to run. Should it have something?

---

### Post by lidex on 2010-04-21
> **LucasJA said:**
> Hello lidex.

I did what you asked. There is no output for the command you said to run. Should it have something?

Yes. Try it again. Did you do the first part?

---

### Post by LucasJA on 2010-04-28
Sorry that I took a long time to answer.

I tried many things here. But none worked. I installed 9.04 again, it is normal now. I will keep it, get some more experience with linux and then I will try to upgrade it.

Thanks so much for your help ^-^

---

