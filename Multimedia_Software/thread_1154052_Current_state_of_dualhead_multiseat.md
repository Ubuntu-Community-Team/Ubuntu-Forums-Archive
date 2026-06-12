---
title: "Current state of dualhead multiseat"
date: 2009-05-09
forum: Multimedia Software
---

### Post by bryonak on 2009-05-09
[i][color="green"]EDIT: I've made a [HowTo]("http://ubuntuforums.org/showthread.php?p=7448339#post7448339") that deals with pseudo-multiseating on one GPU and solves my question.
More information about multiseating in general is still very welcome here![/color][/i]


Could anyone offer some information on the current state of multiseat setups with one dualhead video card?

The most common setup seems to be using Xephyr, but most HowTo's I've read say that it loses OpenGL and 3D acceleration.
That's useless for me, because I want to play HD movies on one head (a beamer) and have Compiz enabled on the other (a standard LCD monitor).
There was lots of rumour about Xephyr supporting OpenGL, could anyone elaborate on the current state in Jaunty?

I've found an interesting [guide]("http://research.edm.uhasselt.be/~jori/page/index.php?n=Misc.DualSeatX") that claims to have dualhead multiseat *with* OpenGL via XGL/Xevdev... but [this article]("http://horky.wz.cz/en/multiseat/single-carded") uses the same method and claims the performance to be very bad.
Perhaps he just used older hardware, mine's an Athlon X2 with 2 GB RAM.
Again, somebody knows more?

Ideally, I'd like to be able to start two separate, non-nested X servers as if I had two distinct video cards. This is why I've bought another one (Radeon 2400 HD PCI).
After spending the whole day tinkering with it yesterday, it turns out my motherboard (Asus M2N-XE) only offers to activate one of them.
My other card is a GForce 8400 GS (I chose a Nvidia/ATI combo because I want to try out the radeonhd driver. And supposedly the proprietary nvidia driver might have trouble operating two cards, while the free ATI drivers are superior to the free Nvidia ones.)
Is there a way to accomplish this on one card?

Btw: I'm using Ubuntu 9.04 64bit.

---

### Post by bryonak on 2009-05-11
I just felt like spending some more time on this, but in vain... the XGL extension is deprecated in favour of AIGLX and has been removed from the X server.
When I feel adventurous again, I'll try replacing the XGL part in the HowTo above with AIGLX (maybe via Xnest, that is... can't find any useful info about AIGLX multiseating though).

Strangely I can't figure out if Xephyr has full OpenGL/acceleration support today... the best I can come up with is a blog post from 2007 saying that there was an experimental patch for it.

---

### Post by bryonak on 2009-05-15
Not much progress since my last post :/

Anybody knows more?

---

### Post by kacperpl1 on 2009-05-23
Hi there m8. I've been doing some research but the hardware resellers doesn't want to help me. What i know is that dualseat on one card is possible without nesting xservers only when u have card visible as two different devices on pci bus. Most possible is that cards with DVI + DSUB are visible as two devices but ive checked few of new nv cards and they doesn't. My old 6600GT is seen like this for sure but i didnt tried dual seat on it. Will you show me your lspci output? Its highly possible that your radeon is one of those cards. I'll update some info within two weekes because i have exams incoming.

---

### Post by kacperpl1 on 2009-05-24
Ive luckily found something on youtube that would be perfect for multiseat config: ```
http://www.youtube.com/watch?v=6o92RoCV8RU&feature=channel_page
```
I'm trying to reach the author of this config by private messages.
If he or anyone else would share the knowledge of running independend gdm sessions inside ratpoison we would have easy work to make a howto. With that knowledge configuration would look like this:
```

I. Requirements: 
1)any dual head card
2)two displays/mice/keyboards

II. Config: 
1) Xorg screen extended using both displays with twinview/xinerama
2) ratpoison splitscreen config(as our "screen" uses both displays)
3) running two independent gdm sessions inside ratpoison
4) forwarding inputs to correct gdm session

```

If there are any pro ratpoison users who would like to share with their precious knowledge - please go ahead :D. The main problem is running gdm with dri under another wm and forward input from correct devices. Will anyone help?

---

### Post by mkeuter on 2009-05-30
> **kacperpl1 said:**
> Ive luckily found something on youtube that would be perfect for multiseat config: ```
http://www.youtube.com/watch?v=6o92RoCV8RU&feature=channel_page
```
I'm trying to reach the author of this config by private messages.
If he or anyone else would share the knowledge of running independend gdm sessions inside ratpoison we would have easy work to make a howto. With that knowledge configuration would look like this:
```

I. Requirements: 
1)any dual head card
2)two displays/mice/keyboards

II. Config: 
1) Xorg screen extended using both displays with twinview/xinerama
2) ratpoison splitscreen config(as our "screen" uses both displays)
3) running two independent gdm sessions inside ratpoison
4) forwarding inputs to correct gdm session

```

If there are any pro ratpoison users who would like to share with their precious knowledge - please go ahead :D. The main problem is running gdm with dri under another wm and forward input from correct devices. Will anyone help?
I think I found the vendor of the solution in the video, somehow I don' t think we will get a quick howto..
[http://www.multiseatcomputer.be/index.php/en/](http://www.multiseatcomputer.be/index.php/en/) 

maybe it's worth a try

---

### Post by insane2600tt on 2009-05-30
[http://wiki.c3sl.ufpr.br/multiseat/index.php/Live-CD](http://wiki.c3sl.ufpr.br/multiseat/index.php/Live-CD)

did you try this ?

cheers,
marco

---

### Post by mkeuter on 2009-05-30
> **insane2600tt said:**
> [http://wiki.c3sl.ufpr.br/multiseat/index.php/Live-CD](http://wiki.c3sl.ufpr.br/multiseat/index.php/Live-CD)

did you try this ?

cheers,
marco
LiveCD works fine in my setup, problem is: I want to run a 64bit OS, there are no binaries and the compilation process requires me to spend a lot of time firguring stuff out without clear documentation (e.g. I can't even get started getting the repository system to work for c3sl).

---

### Post by bryonak on 2009-06-03
Hi altogether. It's good to see that I'm not the only one struggling with this... haven't had much success in the meantime.

@kacperpl1: I'll check my lspci when I get home this evening, but from memory I think it's just one device.
Can't watch youtube right now, I'll get back to that too.
That ratpoison idea sounds very interesting, yet as mkeuter said, they're trying to make money with this...

@insane2600tt: I haven't tested the liveCD, but I did compile mdm on my 64bit machine (took me about half an hour to track down stuff). Then I dropped it after seeing that only a Xephyr setup was possible... which I could do directly myself anyway.

Maybe I'll just have to live with Xephyr and hope that the performance hit isn't too hard.

---

### Post by bryonak on 2009-06-03
Both cards have only one entry (the Radeon has another one for audio, but that doesn't help much).

```
02:00.0 VGA compatible controller: ATI Technologies Inc RV 610LE PCI [Radeon HD 2400]
02:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]

03:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
```


Maybe I can spare some time next weekend and try out ratpoison, which seems to work very well (that Belgian guy shows off Compiz in his videos)... probably even better than Xephyr.

---

### Post by bryonak on 2009-06-11
OK, I've got a setup that is close to usable... after sorting out the last glitches (mouse separation/redirection) I'll post a summary.

---

### Post by kacperpl1 on 2009-06-12
I'm looking forward to it. Btw i'm searching for some dual head cards that have two pci bus identifiers so it'll run two instances of xorg.

---

### Post by bryonak on 2009-06-13
All right, [made a HowTo]("http://ubuntuforums.org/showthread.php?t=1186068"). Comments are welcome ;)

@kacperpl1: a list of those would be nice.

---

### Post by unavenged on 2009-07-02
Sorry if this has been asked before...

How do i find out if a card has Dual head... Im trying to set up a multiseat pc

It is a touchscreen panel pc with a VGA output and it has an Integrated intel graphics controller(82945G/GZ)

When i run lspci i get the following:

```
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```

And xrandr:

```
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1440 x 1440
VGA connected 1152x864+0+0 (normal left inverted right x axis y axis) 410mm x 256mm
   1440x900       59.9 +   75.0  
   1280x1024      75.0     60.0  
   1152x864       75.0* 
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
LVDS-1 connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9 
```

Will this work or should i try something else?

---

### Post by kacperpl1 on 2009-09-17
U've got two pci bus identifiers so should be ok for start. U can try just making two server layouts with different screens/inputs

---

