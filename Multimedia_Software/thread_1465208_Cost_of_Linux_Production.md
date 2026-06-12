---
title: "Cost of Linux Production"
date: 2010-04-29
forum: Multimedia Software
---

### Post by Alan James on 2010-04-29
I imagine this question is hard to answer and will get very few takers but I am hoping someone will be able to help.

Has anyone ever done a cost analysis of video production facilities that use Linux vs Windows vs OS X?

My company use Final Cut on OS X to edit video, Photoshop on Windows or OS X for photo editing and Nuke on Linux for visual effects composting. We have multiple computers running in this configuration but have not looked deeply into how to achieve maximum value for our money.

Mac's can cost up to four times as much as a comparable Windows machine but save on electricity over the course of their life and have better software for our workflow. Linux machines are even cheaper as they use the same electricity as Windows but the OS is free. Unfortunately, Linux does not have Photoshop, or a good video editor. Gimp does not support opening PSD files, which as used extensively in production environments.

Basically my question is has there been any studies done on this subject?

---

### Post by kbielefe on 2010-04-30
Well, this doesn't address cost specifically, but as this is a Linux forum, [here's]("http://www.linuxmovies.org/software.html") a really good resource on Linux software for movie production.

As far as open source options go, I would recommend checking out cinepaint instead of gimp.  As far as I remember, it does open psd files, although it may not always open them perfectly.

As a minor contributor to cinelerra, I just wanted to point out that a lot of its shortcomings are due to just plain not knowing what professionals need in a workflow.  I've seen the main developers be very responsive when they are educated, though.  One professional mentioned he needed to edit timecodes in a certain way and within days that feature was checked in and available.  It may be too far away from your needs to be usable, or it may be too much of a departure to implement your feature request or too much work, but it never hurts to ask.

The biggest hole on the open source side is color grading, although high end commercial software is available and cinelerra has some rudimentary functionality.  I've been toying with filling that hole myself as a standalone application.

---

### Post by conradin on 2010-04-30
I think its an interesting bias to say Linux but then refer to other product in terms of productivity. PSD files are proprietary photoshop components, which duely noted is not available in linux. To be more task specific (work flow analysis) one should ask what the tasks is. Are we editing images or video, ect. than appropriate a means of achieving that goal with software. If your goal is to use linux, focus on using systems designed for linux. 

I cant imagine there are general studies on this topic, work flow analysis is specific per site. Even if you go with linux computers, and linux software / support, you're going to have a learning curve to do things with linux. 

There have been studies into the average run time, of linux computers vs other systems, where linux typically had greater up time. Those which Ive read were pertaining to servers running similar loads and hardware.

---

### Post by Alan James on 2010-05-01
Thank you kbielefe  and conradin  for your reply. 

Conradin I have used Linux for several years and am very knowledgeable technically with it. Anyone working in a post production environment will, generally speaking, be able to adapt quickly to any technical situation, thus I am not terribly worried about the learning curve.

Kbielefe I have looked at cinepaint and cinelerra and both are not at the level they need to be at to be used in a professional workflow. I have asked developers how an entire workflow might be made on Linux and they have told me that &#8220;open source developers do what they want, not what their customers ask for.&#8221; I have seen this when talking to some of the developers of KDENLIVE to implement features professionals need. They have laughed at the idea of putting them in and continue to make a promising yet still unusable program. So, I am not concerned with using just Linux for production as I know right now that is very difficult if not impossible. The software is simply not up to snuff. 

What I am asking is how can I minimize the amount of money I spend on computers and software while still getting the same result I am now. It a very complicated question with nearly 1000 answers but I wanted to ask anyway. I bet the eventual answer will be &#8220;keep doing what you are doing now.&#8221;

Also, Kbielefe what exactly are you working on with color correction, it sounds like it could be promising.

---

### Post by kbielefe on 2010-05-01
I don't disagree with your statements about open source developers.  What is really needed for open source NLE on linux is a strong corporate sponsor.

You might look into virtualization or wine to help consolidate a little.  I don't use it myself, but photoshop is the #1 requested application for wine, and I understand it works fairly well.

My color correction software is still very much in the vaporware stage, just an idea I've been kicking around.  My one requirement is that I want to optimize for throughput.  Correcting one shot with cinelerra has definite room for improvement, but is doable.  Correcting 100 shots will drive you insane.  Noticing the distinction is where open source developers often fall short, and is why progress stops after a feature is "complete."

Anyway, my innovation (at least I'm not aware of anyone else doing this) is that I want to be able to plug in 3 cheap commodity trackballs to duplicate much of the user interface advantages of a $5000+ control surface.

I don't know when or even if it will get done, but if you have ever said, "I wish color correction software would work like this," I'd love to hear what you have to say.

---

