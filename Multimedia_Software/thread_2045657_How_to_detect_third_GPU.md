---
title: "How to detect third GPU?"
date: 2012-08-21
forum: Multimedia Software
---

### Post by kivig on 2012-08-21
Hi,
Ubuntu (12.04) sees only two of three GPUs (all Nvidia gxt580, were working fine under windows).
Is there a way to help it?

---

### Post by kivig on 2012-08-28
Anyone?

---

### Post by Sylos on 2012-08-28
Hello.

Im by no means the man to give you a solution but, to get the ball rolling, have you done "lspci" to see if your card is being detected at all?

If not you could also check dmesg after you boot to see if there are any problems initialising the card etc.

It should be possible to get three cards working I would have thought. The NVIDIA driver appears to have (or had) support for it:

[ftp://download.nvidia.com/XFree86/Linux-x86/177.70/README/chapter-25.html](ftp://download.nvidia.com/XFree86/Linux-x86/177.70/README/chapter-25.html)

Cheers

EDIT: Might have spoken to soon - [http://www.geforce.co.uk/hardware/technology/sli/faq](http://www.geforce.co.uk/hardware/technology/sli/faq)  it says only windows for tripple sli. But the driver doc does say "2 or more" so it does make me wonder....

EDIT2: It also says on "min system requirements" for sli that you need windows - but says elsewhere on the site linux is supported. So I guess their infor isnt worth much. Maybe email them...

---

### Post by kivig on 2012-08-28
At least they're alive - lspci shows all three.
And there seems to be no problems according to linked document as I can see two of them.

> **Sylos said:**
> EDIT2: It also says on "min system requirements" for sli that you need windows - but says elsewhere on the site linux is supported. So I guess their infor isnt worth much. Maybe email them...

I will right now.
Thanks a lot!

Edit: hahah.. Anyone had a chance to get Nvidia email to write to? Their support is mastery of redirections to clueless third parties. Will try forum..

---

### Post by kivig on 2012-08-28
I should have made it clear though, that I don't need SLI (I use only the CUDA computational power for rendering in Blender).

---

### Post by Sylos on 2012-08-28
> **kivig said:**
> I should have made it clear though, that I don't need SLI (I use only the CUDA computational power for rendering in Blender).

Hmmm... thats me well and truly out of my depth then.

I would have thought if you are using them in tandem then you would need the SLI but I suppose if you are just getting each core to do independent tasks then you wouldnt need it.

It would appear you know far more than me about this area so I fear I may have to bow out.

Maybe try checking the blender documentation for how you set up 3 cards?

Cheers (and sorry to bail but really - I was stretching my knowledge with my first post - anything now would be pure guessing).

Good luck.

---

### Post by kivig on 2012-08-28
> **Sylos said:**
> Hmmm... thats me well and truly out of my depth then.

I would have thought if you are using them in tandem then you would need the SLI but I suppose if you are just getting each core to do independent tasks then you wouldnt need it.

It would appear you know far more than me about this area so I fear I may have to bow out.

Maybe try checking the blender documentation for how you set up 3 cards?

Cheers (and sorry to bail but really - I was stretching my knowledge with my first post - anything now would be pure guessing).

Good luck.

GPUs isn't a big area to have knowledge about, at least from consumer perspective nor am I specializing on them :)

It seems to be more of a problem because of my lack of experience with Linux (I didn't know lspci command until you mentioned it). More reading probably will help it.
Thanks a lot!

---

### Post by kivig on 2012-08-28
Solved!

After search for what it is possible to o I found this:
[http://manpages.ubuntu.com/manpages/natty/man1/alt-nvidia-173-xconfig.1.html](http://manpages.ubuntu.com/manpages/natty/man1/alt-nvidia-173-xconfig.1.html)

and tryed
-a option for etecting all GPUs, but got an error:

WARNING: Unable to use the nvidia-cfg library to query NVIDIA hardware.

reason of which appears to be the cause of all problems.
Next I found this:
[http://ubuntuforums.org/showthread.php?t=1684460](http://ubuntuforums.org/showthread.php?t=1684460)

```
sudo pico /etc/default/grub
```
and modify this line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vmalloc=256M"
```
Save, then
```
sudo update-grub
```
reboot

That was enough, GPUs got detected straight away.

Being newbie some questions remain - 
what exactly "vmalloc=256M" means?
Is it RAM or real memory on GPU?
Is it still usable afterwards?
If no - can I experiment with lowering the value?
Every megabyte counts for my applications...

Edit: Strangely, coolbits=5 seems still to work only for first GPU. That's kind'a important too, as I don't want to burn some of videocards while on long render.

---

