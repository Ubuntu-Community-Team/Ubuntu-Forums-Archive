---
title: "SLI in linux ..!?!?!"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by mrazster on 2006-08-10
I was wondering about SLI in linux. Is there anything in particular to think about, or do I just slap in the cards and make sure I get the driver reinstalled/reconfigured..??

Any buggs or any other thing to watch out for..??

---

### Post by mrazster on 2006-08-11
OK,,,I read up a little bit on it....shouldn't be to much hasstle, disable the exisiting driver, slap in the cards and reconfigure drivers with SLI option enabled.

However I'd still like some user input and thoughts...if there is anyone here using SLI..?!?!?

---

### Post by tseliot on 2006-08-11
I know that you can use it with Nvidia cards

---

### Post by mrazster on 2006-08-11
Yeah..SLI can ONLY be used with Nvidia cards...if you wanna go multigpu with Ati cards. it's called crossfire.
AFAIK crossfire isn't supported yet in ati linux drivers....but I'm not 100% sure about this, as I don't use Ati cards.

Got a pretty good deal on 2 7600GT cards...so I thought I'll give it a go. Should give a pretty desent game perfromance.

---

### Post by tseliot on 2006-08-11
When you get the two cards you will have to:

Plug in the new cards then boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

Then install the Nvidia driver (use Method 1):
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)


After you do all that you can enable SLI:
```
sudo nvidia-xconfig --sli=Auto
```

---

### Post by mrazster on 2006-08-11
OK eliot...thnx buddy. Help much appreciated.

One question thou...I'm runing a custom compiled 2.6.17.3 vanilla kernel from kernel.org, so I guess I'm stuck with method 2. Will your script for method 2 work in my case..?
Or du I have to do it manually like in your howto in [*THIS*](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)  link ??

---

### Post by tseliot on 2006-08-11
> **mrazster said:**
> OK eliot...thnx buddy. Help much appreciated.

One question thou...I'm runing a custom compiled 2.6.17.3 vanilla kernel from kernel.org, so I guess I'm stuck with method 2. Will your script for method 2 work in my case..?
Yes, it works.

I use that kernel and installed the driver thanks to my script

---

