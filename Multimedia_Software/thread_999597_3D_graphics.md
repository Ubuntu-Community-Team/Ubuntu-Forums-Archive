---
title: "3D graphics"
date: 2008-12-02
forum: Multimedia Software
---

### Post by thehada on 2008-12-02
Hi,

I have a serious issue with graphics on my 8.04, I'm programming small 3D applications with freeglut the latest version 2.4.0-6..
The problem is that most of the time it is working fine, but sometimes when starting the application it takes 50% of the CPU, the freeglut gives out a message:

freeglut (./test1): Unable to create direct context rendering for window 'Test1'

This may hurt performance.


The applications that I'm running are both my (with not so optimized code) and others example code witch are running great. When they are working properly they don't use the CPU more then 2-4% in total. The most confusing part of this is that when this starts to happen, running the application from terminal takes 50% of the CPU but double clicking on it in Nautilus works fine.

I have tried to run others apps first and not running my at all. The same error comes up.. 

glxgear (when running fine) takes less then 5% and gives me about 4800 FPS,
(when running after the error) it takes 100% of one core = 50% CPU like the other apps and still gives me about 4800 FPS.

Because glxgear is not running with freeglut, this would have to do with drivers, right?

My theory is that after the error, both GPU and CPU are doing the same job..


Could anybody help me with this??


Some information:
Centrino Duo
ATI X1600

---

