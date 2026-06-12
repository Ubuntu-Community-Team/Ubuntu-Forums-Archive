---
title: "Speeding up rendering"
date: 2013-01-16
forum: Multimedia Software
---

### Post by Eklod on 2013-01-16
Hello:

I am runing 64bit Studio  12.10 on the following hardware
Gygabyte mb 970A-D3
AMD FX8120 cpu 
sapphire hd7770 video
24 Gig Kingston hyperX RAM

I use GIMP, OpenShot, Kdenlive extensively and those apps all  seem to render slowly (considering hardware resources) and fail to utilise on average more than 30 % of processors and 40% of RAM.  

To give you an idea, in GIMP, to render perspective effect on a 10Mb .jpg takes 3-4 minutes and it takes about 3 minutes to export the resulting file to .png.   

I recently upgraded RAM from 8 to 24 Gig hoping it would speed up rendering.   While it greatly improved responsiveness of OpenShot when editing, rendering speed has not improved in any of these apps.   

My system is otherwise extremly tolerant.  While it renders, I can use any other app without issues.  But I wish it would render faster,  I am seeking suggestion on how I could adjust my system so that it utilises more resources (CPU and RAM) when doing that).  

One note, when rendering, average total processor load sits between 30-40%, but in turns, individual processor usage hit 100% load. no more than one processor at the time, and for 30-60 seconds periods.  Perhaps this is causing slows downs.  Would not know where to look to investigate this further and if its is worth it.  Would running these apps in virtualisation environment reduce those hardware bottlenecks?    

I consider trying the following.  If you obtained improvements running these apps or tried any of the above, I would love your comments. 

-running OpenShot, Kdeblive and the GIMP as virtual machines.  Anyone obtaining better performance that way on a 64 bit system?   I suspect that a combination using 32 bit may run faster.  Given the many possibilities, I hesitate between using WINE, Playwith Linux, OracleVM and which OS to emulate and also 32bitvs 64).  

-Changing the priority for processor of these application from NORMAL to HIGH?  (never done that and I am concerned my sys becoming unstable).

-24Gig of RAM provides enough room to operate completly from within RAM.  Configure my system like that?    

-Overclock CPU/video? 

-All, or part of the above?


Thank you

---

### Post by lukeiamyourfather on 2013-01-16
> **Eklod said:**
> 
I am seeking suggestion on how I could adjust my system so that it utilises more resources (CPU and RAM) when doing that).


That's not how it works. Applications will use the resources they need. If an application is using only one or two processor cores out of many that means the algorithms the application uses are limited to one (or sometimes two) processor cores. Making software take advantage of many processor cores is not easy and sometimes is not possible at all (or provides no benefit). In time things that can benefit from running in parallel and are actually possible to run in parallel will eventually do so, but it will take time for software development to catch up with the hardware. More on that here if you're interested but a warning, it's kind of a bottomless pit that you could spend hundreds or even thousands of hours researching and not know everything about it.

[http://en.wikipedia.org/wiki/Parallel_computing](http://en.wikipedia.org/wiki/Parallel_computing)

> **Eklod said:**
> 
-running OpenShot, Kdeblive and the GIMP as virtual machines.  Anyone obtaining better performance that way on a 64 bit system?   I suspect that a combination using 32 bit may run faster.  Given the many possibilities, I hesitate between using WINE, Playwith Linux, OracleVM and which OS to emulate and also 32bitvs 64).  


Virtual machines will only make things worse because they use up resources on their own before you even start processing things with them.

> **Eklod said:**
> 
-Changing the priority for processor of these application from NORMAL to HIGH?  (never done that and I am concerned my sys becoming unstable).


Changing the process priority will have no affect unless the system is overloaded (which it isn't if you're saying there's typically 30% to 40% processor usage). 

> **Eklod said:**
> 
-24Gig of RAM provides enough room to operate completly from within RAM.  Configure my system like that?    


That will bring more headaches than anything else and it probably wouldn't improve performance in this case very much if any since the processor is doing all the work.

> **Eklod said:**
> 
-Overclock CPU/video? 


Overclocking the processor could improve performance a little but it comes with risks. Overclocking the video card will have no affect since the tasks you describe don't use the video card to process anything.

---

### Post by Eklod on 2013-01-17
Thank you for your comments and link,  Vast but very interesting field.  I understand that video production firms use multiple computers in conjonction.  Will explore further how they do it, as I like the fact that is would allow me to give a second career to currently unused systems.   

I think that perhaps a virtualisation may be faster although it adds a layer between the OS and the apps, is that it results in a sort of buffer zone, which may allow for a more evenly spreaded load on the processors.  (I hate to see a processor at 100% with 7 others simultaneously at 10-15% and it is the only visible bottleneck)  I also suspect that a 32bit emulation could not technically maxout a 64bit architecture CPU to 100% ?  Also, I can dedicate specific processors to the virtulised environments,  So if the 100% peaks create slows downs which affect the OS-or runninjg apps, and running my apps within virtualised environments removes those peaks, I would perhaps get better overal performance.   BUt maybe those peaks do not at all influence performance on a multiprocessor sys.  My knjowledge is restricted and practical experience running virtualisation inexistent, and also those peaks get possibly created at a lower layer that the OS anyway.   

Running from RAM would save the the cost of adding solid state drive, but would likely take me a few days and bring a few headaches I agree, and may not help in the current case (but my computer would be more quiet as I would spin the hard drives down and opening, saving larger files would be faster.)..

---

### Post by lukeiamyourfather on 2013-01-18
If you need to process a lot of tasks that use just one processor core each you can run many at the same time. The disadvantages are it uses more memory than a clever algorithm that would natively take advantage of multiple processor cores (not a problem if you have enough memory), and it only helps speed things up if you have a lot to process to run (won't help with just one). In the past I've written scripts to do this.

[http://www.whenpicsfly.com/multi-threaded-meshing/](http://www.whenpicsfly.com/multi-threaded-meshing/)

That was a very specific problem so it probably won't help you in this situation but it might give you some ideas for your own workflow. Basically the same as your virtual machine idea but instead just run multiple on the machine as is so you don't have the overhead of the virtual machines.

---

### Post by dblaies on 2013-02-02
I have just spent a lot of money building a video editing machine. Then I installed Ubuntu 12.04.1 LTS. Then I installed Openshot.

Here is what I found out. The sixteen cores are only used during rendering. The sixteen cores are not used for preview and editing--that makes this software dog slow. Horribly, painfully slow. So, I also noticed that during rendering, only 6% of my 32 GB of RDRAM are used. So why does this software lag and crash so often? I was researching this and found out why. Here is a quote from the Openshot author on this issue:

The video library we use (MLT) has some stuttering sound issues, even with really good quad-core computers.  Also, the MLT library doesn't suport multi-cores when previewing and scrubbing video... only when exporting videos.  So... if your intention is to use OpenShot (or Kdenlive), the faster the CPU the better.  Also, the more RAM the better, and the faster RPM hard-drive the better.  More cores won't help the performance...unfortunetely.
 Don't get me wrong.  I would love to support multi-core computers, but it really depends on the MLT library (and probably FFmpeg to some extent). Nothing I can do at this point. =)
 I don't have a specific clock speed in mind, but any decent computer made within the last year should be fine... just get lots of RAM.
 Thanks,
-Jonathan

He did mention recently that much will be fixed in the upcoming v.2.0 that may not use the MLT backend. Also, Blender is supposed to start using the Nvidia GPU also. But only if it's Nvidia. Same goes for Sony and Adobe, too. If you find out more, please leave a post.
-Dave

---

### Post by AstroLlama on 2013-02-03
i assume you adjusted your gimp environment settings in file -> preferences to match the number of processors on your system and the amount of ram? 3-4 minutes to render a perspective change on a 10 MB jpg does not seem normal given your hardware...

---

