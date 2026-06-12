---
title: "amd64 and Vanilla Kernel with RT Preemption"
date: 2006-04-10
forum: Multimedia &amp; Video
---

### Post by aldous on 2006-04-10
I'm attempting to move from planetccrma/Fedora Core to Ubuntu.  One step I'm taking along the way is working to get a RT Preemption kernel.  I've tried following the directions to build one listed on the Dapper:Studio Preparation page, but each attempt has ended in a kernel that won't boot.  I suppose it doesn't help that I'm running compiling a 64bit Ubuntu kernel.

Any advice on how I can track down the problem?  64bit gotchas that I need to know about?  Am I insane to try to build a 64bit based Ubuntu Studio?

(By the way, I switched to Ubuntu because I could see that there were packages for all the apps I love to use, Hydrogen, Ardour, etc.  And I read somewhere that the main Hydrogen developer uses Ubuntu, so I figured this distrobution would be well supported.)

On another note (apropos phrase for the musicians), It seems it would be ideal if we could apply the RT patch to the kernel sources *after* all Ubuntu patches are applied.   Any work being done out there to produce a kernel package which is the cumulative Ubuntu patches plus the RT Preemtion patch?

---

### Post by dolson on 2006-04-10
It isn't as easy as you think, but yes, we have already done this for Dapper, albeit with an older version of the kernel. We stopped making updates when there was a new kernel released every 2 days, and will resume when the kernel freeze happens.

On top of those efforts, Mark said that there will be a multimedia-focused derivative of Ubuntu released with Dapper+1. I posted about this earlier.

As for your 64-bit issue, I can't help you, as I can't afford the jump off of 32-bit yet.

If PlanetCCRMA's kernel works, perhaps you could compile that for the time being, until we can release a Dapper kernel package that will work for you?

---

### Post by aldous on 2006-04-11
After two days of trying, I did finally get a bootable kernal with the RT Pre. patch.  I did an 'apt-get dist-upgrade' this time before I started and picked up a few new packages.  Perhaps I picked up something helpful...

I didn't see what I expected to see though when I launched Ubuntu Studio.  

The RT "light" in qjackctl never comes on.   What's the best way to confirm that the patch is in my kernel?  (Perhaps I made a mistake during configuraion...)  If I mimic the jack configuration here, setting input and output to my own card of course, my system locks up tight.  If I change frames/period to 128, I get sound, but for some reason my low end samples sound like they are clipping (distortion).  
Clearly something is still not right.

(Kudos for writing the launcher BTW!  The inability to launch everything at once has been a major headache for me in the past.  Now if there was only a way to take a 'state' snapshot of all of the applications before they shutdown...a difficult feature request I know.)

---

### Post by dolson on 2006-04-11
The RT light won't come on unless you meet two criteria.

1) You have the ability to request and receive realtime priority.

2) You tell QjackCtl to request realtime priority.

If you are using Dapper, then #1 is taken care of. If you aren't, then you need to follow the steps in the wiki. Any kernel from 2.6.12 and up have the necessary code in it to allow realtime priority. The -rt kernel allows complete pre-emption, allowing near-realtime performance. There is a big difference between the two.

#2 is simply an option in QjackCtl's GUI.

The launcher is just a small script I did up because it was easy. It doesn't work very well on Breezy, but on Dapper, it picks up most applications because a lot of work went into Dapper's missing menu launchers. LADCCA/LASH is probably going to be a much better solution, but LASH is not yet in debian/Ubuntu, and I'm not sure that apps that use LASH are all patched to use LADCCA. If they hadn't renamed LADCCA to LASH, then this wouldn't be much of an issue. But anyhow, you might wanna look into those anyhow.

---

### Post by aldous on 2006-04-12
The RT light has not come on for me yet since switching to Ubuntu.  After upgrading to Dapper it did not come on, and after compiling/booting the Vanilla Kernel with RTP it did not come on.  My processor is an AMD Athlon 64x2.  Any idea what I could be missing or is there a way to verify that my kernel is up to snuff?

I'm now using a 2.6.15-rt16 patched kernel.

---

### Post by dolson on 2006-04-12
Your kernel does not make a difference. Any kernel over 2.6.12 will support realtime-access.

Please follow this:
[http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#Real-Time_Support](http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#Real-Time_Support)

Also note that the Dapper section of the wiki is not ready for primetime yet, but this will solve your issue.

---

### Post by aldous on 2006-04-14
I followed the Real-Time support instructions here:
[http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#Real-Time_Support](http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#Real-Time_Support)

Observe the tail of limits.conf.  As far as I can tell I've done every possible thing that can be done to enable realtime.

# End of file
@audio - rtprio 99
@audio - memlock 250000
@audio - nice -10

...but my RT light is still dimmed when I run qjackctl.  I also get way too many xruns.

I don't believe that I'm really getting real-time access, the dimmed RT light being my biggest clue.  (Real time IS checked in the qjackctl preferences.)  

Does anyone know how I can prove that it does?  What can I check that would prove I have realtime access?

---

### Post by dolson on 2006-04-14
If you didn't have realtime capabilities, then you would not see the RT indicator at all.

You should really tell us what your settings are in JACK. If you're running the -rt kernel and you have RT enabled, then your periods and buffers must be too low for your sound card.

---

### Post by www.rzr.online.fr on 2007-02-18
> **aldous said:**
> I followed the Real-Time support instructions here:
[http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#Real-Time_Support](http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation#Real-Time_Support)



page down , maybe this help :

* [https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime)
* [http://rzr.online.fr/q/RT](http://rzr.online.fr/q/RT)

---

