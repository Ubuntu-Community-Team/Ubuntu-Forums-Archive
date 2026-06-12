---
title: "Getting fast upload speed"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by PaulM1985 on 2011-02-12
Hi

I am not sure if this is the correct forum to post my question, but here goes..

I am looking host an application I have written.  Clients connect to the server (which I will be hosting) and each client needs to be able to download from the server at a maximum of 40-50KB/s.

My current internet connection is only capable of uploading at 40KB/s so in theory I could only support one client well.  Does anyone know how I can get better upload speeds?  There seem to be plenty of web hosting companies out there, so they must be able to get this sort of connection from somewhere.

Any ideas?

Paul

---

### Post by dmizer on 2011-02-12
> **PaulM1985 said:**
> Hi

I am not sure if this is the correct forum to post my question, but here goes..

I am looking host an application I have written.  Clients connect to the server (which I will be hosting) and each client needs to be able to download from the server at a maximum of 40-50KB/s.

My current internet connection is only capable of uploading at 40KB/s so in theory I could only support one client well.  Does anyone know how I can get better upload speeds?  There seem to be plenty of web hosting companies out there, so they must be able to get this sort of connection from somewhere.

Any ideas?

Paul
Why not host it on [sourceforge]("http://sourceforge.net/") or Ubuntu's own [launchpad]("https://launchpad.net/")? Until your project gains enough momentum and following, making it available it on an unfamiliar host will be a deterrent to many.

With Launchpad and Sourceforge, you get secure project hosting for free with lots of benefits like project tracking, bug tracking, managing teams and contributions etc.

Hosting a project on your own connection would be a huge mistake security wise (both for you and your users).

---

### Post by PaulM1985 on 2011-02-12
I am not looking to host the project.  Part of the application is to connect clients together, much in the way that there must be some Skype server running somewhere for clients to connect to.  So it is not the hosting of the project, but the hosting of the server side of the application I am interested in.

Paul

---

### Post by dmizer on 2011-02-12
You'll probably want an unmanaged VPS then. I use [http://bluemilecloud.com/](http://bluemilecloud.com/) for mine. Here's another one that looks pretty good: [http://www.vpsville.ca/ubuntu-vps](http://www.vpsville.ca/ubuntu-vps)

---

### Post by PaulM1985 on 2011-02-13
> **dmizer said:**
> You'll probably want an unmanaged VPS then. I use [http://bluemilecloud.com/](http://bluemilecloud.com/) for mine. Here's another one that looks pretty good: [http://www.vpsville.ca/ubuntu-vps](http://www.vpsville.ca/ubuntu-vps)

The Ubuntu one sounds exactly what I need, but one thing I am struggling to find is how these things work.  Do I remotely log on to the server and work at it as if it is my PC?  There seem to be endless amounts of detail about how much the services cost but not how I use them.

---

### Post by dmizer on 2011-02-13
> **PaulM1985 said:**
> The Ubuntu one sounds exactly what I need, but one thing I am struggling to find is how these things work.  Do I remotely log on to the server and work at it as if it is my PC?  There seem to be endless amounts of detail about how much the services cost but not how I use them.

The Ubuntu one offers an extremely easy to use point an click web management panel called cPanel: [http://www.cpanel.net/](http://www.cpanel.net/) It's pretty straight forward, but it appears to be more costly.

The value plan appears to offer direct command line access via SSH. According to [this]("http://www.vpsville.ca/vps-plans"), you're allowed to do pretty much anything you like as long as you have the technical capability of managing the server from the CLI. You'll log in via an SSL link, and you'll be presented with this control panel: [http://www.vpsville.ca/images/screen1.png](http://www.vpsville.ca/images/screen1.png) once you're there, then you can click to enter the secure shell (SSH).

---

### Post by PaulM1985 on 2011-02-13
Thanks for all of your help dmizer.

Once my app is a little closer to being a finished product I will look into this.

Paul

---

### Post by Laen on 2011-04-19
I'm having the same issue as you (upload speeds for residence internet connections) and I'm probably going to go with Amazon's EC2.

It may be something you want to consider.
It's fully customizable and the prices are also pretty good.

They also give you an year free for a micro instance, so you can experiment as much as you want for free and only pay/upgrade if you need to.

Here's a quick tutorial on how to setup a ubuntu image on amazon:
[https://help.ubuntu.com/community/EC2StartersGuide](https://help.ubuntu.com/community/EC2StartersGuide)

I've played with it in the past and successfully setup and imported a couple of Wordpress blogs. Everything went pretty smoothly!

---

