---
title: "nvidia restricted driver brokes text mode"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by Lo'oris on 2007-10-28
I'm using ubuntu 7.10 on a laptop.
most things worked like a charm, and for that I really have to thank all the community, I can't belive how much is usable even for newbs, it's really linux for human beings!

there's a problem though.

video card is geforce 6200, and since I installed restricted drivers, I can no longer use text mode.
It's not blank screen like I've noticed in other threads, nor it hangs (I can switch back to X).
Weird colors appear. And I DO mean weird, such as taken directly from an acid trip or from the sixties. This can be nice if intentional, but I'd like to remove this feature :P
This also happen if I logout for some seconds (I assume while X restarts).

Since these colors are sometimes REALLY strange, and remind too much of a broken monitor, I'm concerned they could actually do some damage.

Has anybody fixed that? Any idea?

```
looris@DoppioAllen:~$ lspci|grep geforce -i
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6200/6400] (rev a1)
```

---

### Post by Lo'oris on 2007-10-29
I also get a strange bug with games.

Games which run natively in fullscreen work ok.
Games that can run both in window or in fullscreen, doesn't handle fullscreen properly: image is vertically stretched, and I can't see what should be in lower part of the screen.

---

### Post by Lo'oris on 2007-10-30
come on!

I can't belive nobody knows ANYthing!!

please???

---

### Post by Stinger on 2007-10-30
Hi , try setting your driver up using the  nvidia tools ( comes with the restricted driver ) nvidia-xconfig and nvidia-settings , must be run as su (root) maybe thats your trouble ? 
In a terminal do:
```
sudo nvidia-xconfig
```
or
```
sudo nvidia-settings
```

Remember to reboot to activate the driver ( but it seems like you already done that ).

It worked for my monitor , couldn't get the new screenconfigtool to work with the nvidia driver, the refresh rates were much to low , but with nvidia-settings it worked fine , no flickering picture anymore.

---

### Post by Lo'oris on 2007-10-30
nope, I tried tweaking the full gpu scaling with every combination possible but nothing improved.

when I fullscreen, I get a stretched and cropped image.

and nothing changed about the text mode, it still goes totally mad. (I've just randomly tried to load nvidiafb, and then vesafb, but nothing changed)

---

### Post by kazuya on 2007-10-30
Are you in a gnome environment. if so, you can go to appearance> move through the tabs to one that is probably looks or effects> select  among the options for normal, extra, etc or no eyecandy, and the system auto configures itself with already existent video driver..


WARNING: This many not be applicable to you. What is your kernel?
type urname     in terminal..

Also are you using an RT kernel, i.e 2.6.22.rt image shows up when you boot-up computer? I know it does for me after I tried getting the ubuntu studio look.- 

Try doing this if you have the kernel like I mentioned here.
         sudo apt-get install linux-rt
 Alternatively, you could try booting to the previous kernel as that is still an option when you boot up your computer..
I hope that helps...

---

### Post by Lo'oris on 2007-10-30
realtime kernel didn't even boot, it crashed instantly and didn't even allow me to shift+pgup to see the whole error.

changing the effects level didn't improve anything.

sigh.

btw
```
root@DoppioAllen:~# uname -a
Linux DoppioAllen 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```

---

### Post by dabl on 2007-10-30
> **Lo'oris said:**
> come on!

I can't belive nobody knows ANYthing!!

please???

It sounds like there is a problem with your graphics card in "character mode", but it works OK in "graphics mode".

It may not be the driver.  If you're using the restricted driver, then you could do a little experiment to find out if your problem is the driver or the card itself. Remove the restricted driver (back up your xorg.conf file first), run the ```
sudo dpkg-reconfigure xserver-xorg
``` script, and choose the "nv" driver, and when you are done with the script, ```
startx
``` or Ctrl-Alt-Backspace to restart the X server. You won't have as good performance as restricted driver gives, but good enough for the experiment.  Now go find a full screen game or something else that runs in character mode, and see how it behaves.  If you still have the flashy colors, you will know there's a problem with the card.

:)

---

### Post by Lo'oris on 2007-10-30
problem is the nvidia driver, before installing it it worked, and when it failed to load due to a configuration error, it worked again.

now, just to mock me, it also started displaying the splash image "nvidia" even if it's turned off O_o
```
    Option         "NoLogo" "True"
```

---

### Post by Lo'oris on 2007-10-30
[here](http://video.google.it/videoplay?docid=-7716211293194450773) is the video of what happens. Sometimes it's longer and weirder, but I haven't been able to capture that :/
it happens if I switch to console, if I logout (before gdm reappears) and if I reboot or poweroff.

---

### Post by Lo'oris on 2007-11-04
still nothing?

---

### Post by Lo'oris on 2007-11-17
now it also randomly hangs if you leave it alone, no idea why.

do you really expect me to belive that no one here have got any clue on how to help me?

PLEASE?

at least tell me where to ask, I'm clueless!!

---

### Post by Malibyte on 2007-11-17
I don't have the acid-trip video problem, but I can't get into a CLI with Ctrl-Alt-Fx either.  I haven't been able to find a fix for it.  I'm running Gutsy with the 2.6.22-14 generic stock kernel and the Ubuntu package with the 100.14.19 nVidia driver.

The funny thing is, I have a dual-boot setup on this box...the other distro is Mandriva 2008 using the same nVidia driver - and it works fine.  So it seems to be an Ubuntu issue.

If anyone comes up with a fix for this...please post - thanks.

---

### Post by gvoima on 2007-11-19
Well, if it helps, I have exactly the same symptons.

The cause is the nvidia drivers, I still haven't found out why it does that. I've noticed that other drivers work and other does this acid-trip thing. 

My problem is that I need my current nvidia driver because it's the only one where suspend works.

And why it messes up the shutdown splash screen is because it's a console screen made with framebuffer and after startup when nvidia module is loaded it screws things up, so it affects the console only (ctrl+alt+Fx etc.).

I really don't have a huge problem with it (yet), but it damn is annoying.

I try to look into this matter later, at the meantime, try other nvidia drivers. They might work
I found that nvidia-glx from reposities 9631 works on my acer laptop. But I myself need the 160xx beta for suspend.

[EDIT]
Oh, and btw, I have the same gpu as you ;) 6200TC

...

Well I did some research, it seems that this is a nvidia driver problem and we should just wait for it to get fixed :(
I hope there will be a driver that fixes acid-tripping AND my suspend :P

On some drivers it works and some it doesn't, so basically it's already fixed.
Oh...and be sure to use agpgart.
[/EDIT]

---

