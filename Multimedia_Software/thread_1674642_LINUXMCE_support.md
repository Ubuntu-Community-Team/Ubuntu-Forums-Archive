---
title: "LINUXMCE support"
date: 2011-01-24
forum: Multimedia Software
---

### Post by bryan.sailer on 2011-01-24
I have been using Linux for over a year now and I am very comfortable with the OS. In the near future I am planning on building a home media center. I currently have a media server running Ubuntu 10.4 Server Edition. I am thinking about building a LINUXMCE but the only information I find is about a year old. What is the lastest version? Is LINUXMCE still supported? What version of Ubuntu do I need to have installed to run LINUXMCE?

---

### Post by nickleboyblue on 2011-01-24
LinuxMCE never really has been supported by the Ubuntu community.  I tried it out myself and discovered that, unless you have EXACTLY the recommended hardware (which usually either costs a lot or isn't even on the market any more), you will be spending months configuring everything to work.  Here are a few suggestions for the individual functions of a home automation system:

security:  Zoneminder.  As far as camera software goes, Zoneminder is one of the best linux has to offer.

media: Mythbuntu is a very configurable media center that can be controlled by a remote.  It does a much better job of this than LinuxMCE

X10:  at present, I am only aware of one utility for controlling x10 devices, and it can be found in the software center.  If you're good at writing your own scripts, you could configure it to turn on and off lights or whatever else you have connected to it.

Home automation is very possible to achieve under Linux, and especially Ubuntu.  With the up and coming switch to Unity, it's becoming an even bigger possibility to simply use the Ubuntu desktop as the automation interface.  But until someone puts together an easy-to-use system that includes all the tools that already exist, home automation under linux will probably only happen for programmers who are either too lazy to document what they have done or too worried that their system is unstable.

---

### Post by bryan.sailer on 2011-01-29
That is just the information I was looking for but when I looked at the zoneminder website the latest version is from June of 2009. Is this correct or can I find a newer version on a different website?

---

### Post by nickleboyblue on 2011-01-30
As far as I can tell, Zoneminder is not being actively developed, but that hasn't really done much to stop me from using it.  It's in the repositories for 10.10 along with a plug-in for myth.  You might have to look up what it's compatible with, but the Zoneminder wiki has some great how-tos for installing on Ubuntu, and that's how I got it working at a friend's office.  So far, it has worked like a charm, though it might take a little toying around to get it to do what you want.

---

### Post by L3mce on 2012-11-14
> **nickleboyblue said:**
> LinuxMCE never really has been supported by the Ubuntu community.  I tried it out myself and discovered that, unless you have EXACTLY the recommended hardware (which usually either costs a lot or isn't even on the market any more), you will be spending months configuring everything to work.  Here are a few suggestions for the individual functions of a home automation system:

security:  Zoneminder.  As far as camera software goes, Zoneminder is one of the best linux has to offer.

media: Mythbuntu is a very configurable media center that can be controlled by a remote.  It does a much better job of this than LinuxMCE

X10:  at present, I am only aware of one utility for controlling x10 devices, and it can be found in the software center.  If you're good at writing your own scripts, you could configure it to turn on and off lights or whatever else you have connected to it.

Home automation is very possible to achieve under Linux, and especially Ubuntu.  With the up and coming switch to Unity, it's becoming an even bigger possibility to simply use the Ubuntu desktop as the automation interface.  But until someone puts together an easy-to-use system that includes all the tools that already exist, home automation under linux will probably only happen for programmers who are either too lazy to document what they have done or too worried that their system is unstable.

Hi.

The only HW requirements really had to do with GPUs, needed a certain range of nVidia GPUs. That has changed now. We can work with anything that is supported in 1004 and then some.

LinuxMCE does X10, KNX, zwave, etc. As to "using a remote" the whole point of LinuxMCE is that anything can control anything. Any remote, or orbiter, or keyboard, or game pad can control anything in the system. Everything communicates in DCE.

We have a completely different install experience now, and the system works on just about anything, with notable exceptions... for instance ivy bridge video is a problem for us still... etc.

Feel free to give us a spin, or drop into irc if you have any questions. The system is designed so that you don't have to tweak things... though of course with the mad array of "stuff" we do prevents that from always being the case.

---

### Post by wildmanne39 on 2012-11-14
Old thread closed.

---

