---
title: "Two Kernels"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by Sheik Yerbouti on 2006-06-26
I wanted to share something that I thought might be helpful. I went through the process of compiling the realtime kernel from scratch and had no problems due to the wikis excellent guide. So thanks for that by the way. 

I did run into one major problem. And that is that the Vmware modules will not compile while running a kernel with the realtime patch a quick look at the planet ccrma forums confirms this not to mention I tried everything under the sun to make it work and it simply won't. I use vmware quite a bit for certain windows apps like Macromedia Director and Macromedia flash etc... So this was a big problem for me a show stopper in fact.

So then I decided why not simply run both kernels and just use my realtime kernel for audio work only. This seemed like a reasonable solution to me. 
Then I ran into the issue that every time I would reboot X would complain about my nvidia kernel module being wrong for that kernel. What I would end up having to do is rerun the Nvidia installer again to recompile the kernel module. And everytime I would do this it would uninstall the other module This obviously is far from ideal. 

Then I found a post on the Internet tonight about the -K option for the nvidia installer. If you have the module installed in one kernel then boot into the other kernel and run the nvidia installer with the -K option that will compile the kernel module without removing the other module. Thus allowing you to boot into two kernels easily. It works really well so I am pretty happy now. Running the command would looks like this.

```
sudo sh NVIDIA-Linux-x86-1.0-8762-pkg1.run -K

```

---

### Post by dolson on 2006-06-27
If you build the [slightly older] NVIDIA driver how the wiki advises, this is not an issue at all. But thanks for the tip, for those of us who want to use the non-Ubuntu version NVIDIA drivers.

---

### Post by zettberlin on 2006-06-27
[QUOTE=Sheik Yerbouti]
I did run into one major problem. And that is that the Vmware modules will not compile ...
So then I decided why not simply run both kernels and just use my realtime kernel for audio work only. This seemed like a reasonable solution to me. 
Then I ran into the issue that every time I would reboot X would complain about my nvidia kernel module being wrong for that kernel. ....
[/QUOTE]

More reasons for me to stuck with the binary standardkernel of dapper.

Have you got much better results for latency and stability with the RT-Kernel now?

---

### Post by dolson on 2006-06-28
If you require VMware, then maybe you should have two kernels, one for audio work, and one for emulating a PC. The fact is that the RT patch currently does not work with VMware. You do have source code to fix it if you want.

Also, the RT patch is over a megabyte of code! With that many changes to the kernel, you can't expect it to be more stable than a kernel that is closer to a much more well-tested vanilla kernel. That is the entire reason why the RT patch is not merged yet.

Latencies will be better with a RT kernel, yes. Well, not really. It is possible. But if you have a fast enough system, you won't notice the difference - UNLESS you have a load on your system. See any number of previous posts for my experience with Xruns and the RT kernel.

As I wrote in the wiki, regarding the stock kernel:
*It might suffice for your purposes, so try it out, and if your latencies are good enough for your purposes, then you can move on to the next section.*

Don't fix what isn't broken.

---

### Post by Sheik Yerbouti on 2006-06-28
That was one question I had for everyone about the realtime kernel. If you use a realtime kernel how many frames do you set in jack? And do you ever see Xruns. 

Right now I have mine set at 256 all though I can set it lower all the way down to 32. Maybe even lower than that. However I still do get Xruns not a lot just one or two especially when starting up or stopping certain audio apps like rosegarden. 

For example if I have jack running and I close rosegarden that is a garaunteed xrun regardless of what my frames are set to in jack. However if jack is running and rosegarden is running and I am just using it I don't get xruns. Is this normal? 

One thing I do not like about the realtime kernel is that a poorly behaving audio app will kill your box since it is running uninteruptible. And unfortunatley even though I think jack and alsa at this point are pretty stable up the application chain at the audio application level it can be real hit or miss at this point in terms of stability. A lot of these apps are in fact beta.

Cheers

---

### Post by dolson on 2006-06-28
How would you define "beta"? Linux itself it still in development, and it will never be finished. So is Linux 1.0 beta? Or is 2.2? 2.4? There is a huge difference in featuresets between Linux 1.0 and 2.6, just as there will be between Linux 2.6 and Linux 4.2. So where do you draw the line, when something is or isn't a "beta"? If you think an app is too beta that it causes stability issues, you might wanna not use it. Stick with the better apps out there, or wait it out/find workarounds/help code on it. Which apps cause you problems, exactly?

Anyhow, to answer your question, set the JACK settings as low as you can without getting Xruns. During use.

Starting up applications will always cause Xruns. I don't know why, and I hope that goes away someday real soon. But for now, it's a normal thing. The only time Xruns matter are in the middle of playback, or recording. Especially recording, since the Xrun will result in a loss of sound data.

---

### Post by Sheik Yerbouti on 2006-06-29
I would define beta as the developer says it's in beta. It's not a knock dude many linux audio apps are in beta not according to me according to the devs. I believe if it's less than 1.0 it's beta. Just look at many of the version numbers their beta.

Based on what you are telling me a few xruns when starting stopping audio apps can be considered normal. Based on that I now understand I was getting decent performance under the stock Ubuntu kernel down to 256 frames or something like 5.2 ms.  I think I will just use the stock kernel that way if a program goes off into lala land I can just kill it. 

I think the wiki should be more clear about what acceptable performance is. I was under the impression you should never see xruns. But it sounds like even with the RT kernel you will ocaisonally see xruns when starting and stopping apps. But when your apps are up and running is when you should not see more xruns is this correct?

Cheers

---

### Post by dolson on 2006-06-30
I will add a note to the wiki about Xruns at application startup, but I am not the one who can judge what "acceptable performance" really is. It is going to be different for every individual. Some people are fine with 40ms latency. Myself, I use 1.33ms. So it's not really fair to say one or the other. Besides this, the -RT kernel's advantage is not that it can achieve smaller latencies, but that applications can run in 99% realtime as opposed to 50% realtime.

The different pre-emption options are already listed here, and I think most people don't read it:
[http://www.ubuntustudio.com/wiki/index.php/Preemption](http://www.ubuntustudio.com/wiki/index.php/Preemption)

---

