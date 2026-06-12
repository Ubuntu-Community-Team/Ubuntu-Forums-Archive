---
title: "Serious help Ubuntu Ardour &amp; Jack"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by caseyg on 2008-01-24
Hey all, I need some serious help with Ardour and Jack. This post will be limited. I will provide any info needed for help. I have an M-audio 1010LT card but have no clue how to configure it with JACK and ARDOUR, basically I think I have patch panel issues. I figured out how to set the default to the M1010 card and make sound through ALSA drivers. This is as far as I have got. I for the life of me can not get sound to record through ARDOUR. If there is a good resource to documentation please advise.

caseyg

---

### Post by Emblem Parade on 2008-01-24
It's not that easy, I agree. I'm not sure exactly what your problem is, but here are some quick tips:

1. Consider installing Ubuntu Studio. It has everything pre-configured for you. Otherwise, it's just regular Ubuntu. If you don't want to do that, try the rest of these tips...

2. Make sure you are running a kernel that supports realtime! In Gutsy, it's as easy as installing the linux-rt meta-package, and then choosing to start the ...-rt kernel in GRUB when you reboot.

```
sudo aptitude install linux-rt
```

(Note that there are a few minor issues when adding another kernel. Gutsy's packages for VirtualBox, for example, don't include the appropriate modules for the realtime kernel, so you'll need to reboot to the non-realtime kernel for VirtualBox to work. Also, if you manually install a kernel module, such as a hardware driver, you need to do it separately for every kernel you normally use.)

3. Make sure that audio has permission to use those realtime extensions! This was a pain for me to figure out... again, once of those things that simply works with the default installation of Ubuntu Studio. In any case, here's what to do:

```
sudo gedit /etc/security/limits.conf
```

And add the following lines at the end:

```
# For jackd
@audio - rtprio 99
@audio - memlock 250000
@audio - nice -10
```

Reboot to get this accepted.

4. I recommend using JACK Control (sudo aptitude install qjackctl) to start/stop JACK. It shows you a status of JACK, and also the (rather unhelpful) JACK log messages. It even has some basic JACK patching capabilities, including MIDI patching (which isn't really related to JACK, but convenient to have all in one location). JACK Control can also work with Patchage (sudo aptitude install patchage) for even nicer patching capabilities. With either JACK Control or Patchage you'd be able to see all the JACK ins and outs registered by Ardour when it runs. I have a feeling your problem would be visible there.

(I also recommend installing JACK Rack. JACK Rack lets you chain LADSPA effects together, load/save the configuration, and patch the whole chain in JACK between ins and outs. You can use LADSPA effects on individual tracks in Ardour, but it can sometimes be cleaner to manage the effects externally to Ardour when recording, and have Ardour simply accept the effected signal as a raw input.)

5. On Ardour's side of things, you want to look at the mixer (ALT+M). There you should be able to see what how the various JACK ins and outs are related to Ardour's tracks. I had a lot of trouble until I figured this out! Note that the mixer interface (like all of Ardour's interface, if you ask me) is not very intuitive. Try right-clicking on various things until you learn what they do.

If you find out what your problem was, please post the solution here! There's a dearth of good support for getting it all to work together.

---

### Post by caseyg on 2008-01-27
I'm currently running Ubuntu Studio, probably shouldn't have left that out. Do you feel I should still install linux-rt meta-package? I feel I'm not connecting the patch bay in Jack correctly.

---

### Post by Emblem Parade on 2008-01-27
Well, I hope someone will find my -rt advice useful. :)

I don't think you need to install the linux-rt package. But, easy way to find out: when you boot Ubuntu, in the GRUB menu, you should see a list of kernels to start. The kernel you usually use should have an "-rt" appended to its name. That means it includes the realtime extensions.

However, realtime or not, it does sound like your problem is different. It's hard to help you out without seeing all the patching. As I said in #5, though, I think your issue may be the internal routing in the Ardour mixer. That has nothing to do with JACK patching, but with how Ardour matches its various tracks to each other. Somewhere there you can make your track record from a certain input. I suggest going slowly through the Ardour documentation and making sure you understand how everything in Ardour works. It's not very intuitive!

---

### Post by caseyg on 2008-01-27
I really appreciate your efforts and wanted to post this link as it is full of useful info on this configuration. Couple of other things to anyone looking for support on this matter. 
1> Ardour needs to be connected to JACK (which I knew)
2> As you configure the Ardour Mixer (alt -m) your patch bay in JACK is automatically configured. I think here may have been my issue as I was trying to manually set my patch bay and didn't need to. Let Ardour do it for you, just set your inputs and outputs in the Ardour mixer.
3> You also need to turn up the levels on your channels in Alsamixer. This is listed lastly in the link below and needs to be done. There is a gui interface called _Alsamixergui_ just search for 'alsa' in your Synaptic Package Manager. Hope this helps someone else. And yes I finally can record sound with my M1010LT card and Ardour!:guitar:

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/")

---

