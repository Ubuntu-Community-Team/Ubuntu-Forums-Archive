---
title: "How do I can switch graphics cards ? ATI/Intel"
date: 2014-07-08
forum: Multimedia Software
---

### Post by NoXon21 on 2014-07-08
Hello,

I'm new to Linux world

I have HP Pavilion DV6 with 2 graphics cards ATI/Intel

I searched around but it's huge information and I get confused

I tried to install fglrx and reboot but I get error messages [No desktop ... error msg at boot ... etc ] so I removed it 

I need a clean way to get switchable cards

I'm using Ubuntu 14.04 LTS 64bit

Thanks in advanced
 
best regards !

---

### Post by Bucky Ball on 2014-07-08
*Thread moved to **Multimedia & Video**.*

Welcome. You might have more luck here. As you're new, people will be gentle, and just ask if you don't understand. Good luck.

---

### Post by QIII on 2014-07-08
Hello!

I'm on my cell phone so I can't give you the link.  You need to have Catalyst 13.10 or later installed (install fglrx-updates and fglrx-amdcccle-updates to be sure) and may need to install fglrx-pxpress.  I think the last is not necessary with Trusty.

ATI has put a LOT of work in with the Linux community to get this running, but it's pretty new.

You switch using the Catalyst Control Center, but it is not dynamic like Windows.  You have to reboot.

Will get you a link when I can.

Edit:  let's see if this works...

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

---

### Post by NoXon21 on 2014-07-08
> **QIII said:**
> Hello!

I'm on my cell phone so I can't give you the link.  You need to have Catalyst 13.10 or later installed (install fglrx-updates and fglrx-amdcccle-updates to be sure) and may need to install fglrx-pxpress.  I think the last is not necessary with Trusty.

ATI has put a LOT of work in with the Linux community to get this running, but it's pretty new.

You switch using the Catalyst Control Center, but it is not dynamic like Windows.  You have to reboot.

Will get you a link when I can.

Edit:  let's see if this works...

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)


Sorry , but I told that I tried to install fglrx and reboot

I couldn't start my desktop , I've got an error message ( I forget it but something like low resolution press ok ... and nothing happened )

I went to text mode [ctrl + alt + F2 ] and removed fglrx package

any idea ?

---

### Post by QIII on 2014-07-08
Which driver did you try to install, how and what was the exact error message?

Can you tell us the exact models of the GPUs?

We will have to find out why you had problems with the fglrx driver.

---

### Post by NoXon21 on 2014-07-08
Ok,

I read [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics) before making this thread

and what I did is :

sudo apt-get install fglrx

and reboot

I get error message exactly like this one

( I searched for it ... but the different I'm not using VMbox )

See first attached screenshot. The message before it is in the second screenshot.

I googled for these photos, so like I said I forced to remove fglrx to restore my Desktop again .

Thanks for your fast replies :-)

---

### Post by QIII on 2014-07-08
OK.  What are the model numbers of the GPUs?

---

### Post by Bucky Ball on 2014-07-09
I have attached your large pics and edited the post accordingly. 

For future reference, please attach large pics rather than inserting them in the body of your posts by using 'Go Advanced' or 'Adv Reply' and using the paperclip icon. Spare a thought for those with slow connections or vision impairment. Good luck. ;)

---

### Post by NoXon21 on 2014-07-09
Oh sorry ... ATI Radeon 5650

and Intel HD , no idea what after HD numbers

---

### Post by NoXon21 on 2014-07-09
> **Bucky Ball said:**
> I have attached your large pics and edited the post accordingly. 

For future reference, please attach large pics rather than inserting them in the body of your posts by using 'Go Advanced' or 'Adv Reply' and using the paperclip icon. Spare a thought for those with slow connections or vision impairment. Good luck. ;)

Ok , sorry my mistake ... it's 7 AM in my country and I still awake :shock:

---

### Post by QIII on 2014-07-09
OK.

Did you do

```
sudo amdconfig --initial
```

immediately after installing the driver and *before *rebooting?

This is not *supposed *to be necessary any longer, but as many times as I have helped people get their graphics running I have found that this is often the problem.

So:

```
sudo apt-get install fglrx-updates fglrx-amdcccle-updates xvba-va-driver
```

When that has completed, immediately do

```
sudo amdconfig --initial
```

and then reboot.

With 14.04, this should be sufficient for you to use hybrid graphics.  The ATi folks have been very open with Canonical (at least -- hopefully with the whole Linux community) and Canonical officially supports hybrid graphics in 14.04.

The one thing that may be a problem, come to think of it, is if this is not a muxless setup.

---

### Post by NoXon21 on 2014-07-09
No I didn't do "[COLOR=#000000][FONT=Ubuntu Mono]sudo amdconfig --initial"[/FONT][/COLOR]

And I will do that your steps !

Thanks!

---

### Post by Bucky Ball on 2014-07-09
> **NoXon21 said:**
> Ok , sorry my mistake ... it's 7 AM in my country and I still awake :shock:

All good. ;) ... and I know the feeling!

---

### Post by NoXon21 on 2014-07-09
Ok, now I can't see my desktop

same error message again "Ubuntu is running low-graphics mode

what I did is :

sudo apt-get install fglrx-updates fglrx-amdcccle-updates xvba-va-driver

sudo amdconfig --initial

and reboot

:(

---

### Post by QIII on 2014-07-09
OK.  Yours must be a muxed system.

I'll have to do some research to be sure.

For the time being, let's get you back to the default condition.

```
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates 
```

```
 sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 
```

Give me the exact model of your computer so I can research if it is muxed/muxless.


EDIT:

Come to think of it, since you have an intel GPU you should also do the following:

```

sudo apt-get install --reinstall xserver-xorg-core xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx:i386 libgl1-mesa-dri:i386  
sudo dpkg-reconfigure xserver-xorg 
sudo reboot
```

---

### Post by NoXon21 on 2014-07-09
Ok I did this :

```
sudo apt-get install --reinstall xserver-xorg-core xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx:i386 libgl1-mesa-dri:i386
```

I get an error : libgl1-mesa-dri not located

so I deleted : libgl1-mesa-dri:i368

and everything works well with no error

then ```
sudo dpkg-reconfigure xserver-xorg 
```

reboot

the problem still exist :(

---

### Post by QIII on 2014-07-09
Did you first remove the fglrx driver?

---

### Post by NoXon21 on 2014-07-09
> **QIII said:**
> Did you first remove the fglrx driver?

No, I will do that again.
Thanks!

---

### Post by NoXon21 on 2014-07-09
I did what you told me :


```
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates
```


but seems like fglrx and fglrx-amdcccle-update not installed


so : ```
sudo apt-get purge  fglrx-amdcccle fglrx-updates
``` works fine and removed those 2 pkgs


I even checked for sudo apt-get purge fg[TAB button] but there's nothing


then ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```


I reboot and now I can logging into my Ubuntu GUI again


what now ?

Edit : My laptop exact model is HP Pavilion DV6 3150se

---

### Post by QIII on 2014-07-09
I'll have to do some research, but I can't say I can get right back to you.  I need to update the ATI wiki in my signature, so finding out will be helpful.

if your system is muxed, we may not be able to get this running so you can get your ATI GPU working with the fglrx driver.

---

### Post by NoXon21 on 2014-07-09
I did that too

```
sudo apt-get install --reinstall xserver-xorg-core xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx:i386 libgl1-mesa-dri:i386
```
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg-reconfigure xserver-xorg[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
```
sudo reboot
```[/FONT][/COLOR]

---

### Post by NoXon21 on 2014-07-09
> **QIII said:**
> I'll have to do some research, but I can't say I can get right back to you.  I need to update the ATI wiki in my signature, so finding out will be helpful.

if your system is muxed, we may not be able to get this running so you can get your ATI GPU working with the fglrx driver.


Oky,Thank you very much for your time :-)

PS : This issue happened to me with Fedora but the community didn't try to fix my problem.

I hate my laptop now

---

### Post by QIII on 2014-07-09
This is a problem for everyone in the Linux world, unfortunately.  The OEMs have not made this easy.  They make sure it works for Windows because they have sense enough to know where the market is.  Linux is too small a market to get full attention.

---

### Post by NoXon21 on 2014-07-11
So do I have to wait now?

---

### Post by QIII on 2014-07-11
I'm afraid I have not found any good news for you yet.  It is almost certainly the case that ATI/Intel hybrid graphics with the ATI GPU being an HD 5xxx series are muxed.

Because the multiplexer is actually the Intel GPU (it takes either its own signal or the one from the ATI GPU and outputs to the monitor/screen), what I was hoping for vis-a-vis switching with the fglrx driver installed will not be possible.

However, if you are willing to stick with the Radeon driver, you may be able to use [vga_switcheroo]("https://help.ubuntu.com/community/HybridGraphics").  The Radeon driver has improved by leaps and bounds in the last 18 months or so -- which means it will likely work just fine for you.

It looks like a pain and the information there is a little dated.  I can't guarantee it will work with 14.04.

If you are asking if you have to wait for the OEMs to fix this, then I suspect you will have a long wait.  As I said, Linux simply does not command the market share for them to make a sound business decision to spend too much time on making this work.

I wish I had better news.

---

