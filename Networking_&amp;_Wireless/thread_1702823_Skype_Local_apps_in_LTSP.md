---
title: "Skype Local_apps in LTSP"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by MikeUK on 2011-03-08
I've recently tried out Skype on my LTSP server (ubuntu 10.4LTS)with the current download from the repositories, and it appears to work on the server, with the result that it has created a user profile etc.
I tried installing this into the chroot for the LTSP terminals, The application seems to install and can be launched, but stalls and remains with X in the notification bar and is unresponsive, and can only be forced to close (doesn’t respond to the mouse or keyboard).
I have local apps and local dev enabled in the lts.conf, and I have the server set to bridge (NAT) between the thin client network side and the outside world (I have one pc sitting working on the thin client network side and it can access the internet).
I’m convinced I’m missing something stupid, Can anybody advise ??

---

### Post by MikeUK on 2011-03-08
Well it was something stupid..

I removed the original account from the server side setup in my "home" directory (.Skype) this was being accessed when Skype running as a local app and I believe causing the problem?
Once this was gone all the skype options became accessible and allowed me to login and change setting,test calls, etc

Down side is that running as a local app meant it shares bandwidth with the Thin client and all the network traffic that goes along with it

The sound quality was awful on the test call.

---

### Post by MikeUK on 2011-03-11
Well I thought with Skype now using PulseAudio I would try that as a possible solution to the bad audio,  Called up the chooser program and set about ensuring the right devices were active and any unwanted options switched off. Well it does help and it’s possible to get the audio sort of clean, but anything running at the same time as Skype will impact the sound quality. 
Considering this is an LTSP setup if these impacts are coming from applications running on the server and I’m assuming that its traffic simply between the terminals Xorg and the application server side that are generating the noise, Running Skype as a Local app just doesn’t seem to be a solution, 
I haven’t even tried to get a web cam working yet, I’d assume that would just add even more traffic to the system

---

### Post by gordintoronto on 2011-03-11
Why would you run Skype on your server instead of your client? This just makes it more likely to fail.

---

### Post by MikeUK on 2011-03-11
> **gordintoronto said:**
> Why would you run Skype on your server instead of your client? This just makes it more likely to fail.

It's trying to run on the client that's failing.... The reason I wanted to run on the client was to enable the web cam

If I choose to run on the server, without web cam, it works no issue, all I need to do is make sure PulseAudio links the right connections on the client to the server.

---

### Post by gordintoronto on 2011-03-12
I notice you have this thread marked as solved. Is it really? I'm still confused about what your problem is/was.

Your signature mentions "thin clients." How thin? In my experience, videoconferencing in Skype -- started with "bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'" uses lots of CPU.

---

### Post by MikeUK on 2011-03-12
I'm using two neoware Ca2's not much above a 800mhz cpu and about 256M of memory and couple of other devices

My problem was that every time i tried to use Skype on the client it stalled, my problem IMHO was a previously set up the server side .skype folder in the home directory, this seemed to block the client from being able to login, once removed my login problem, and access to setting options went away

My reason for moving Skype to a localapp was to try to get a working web cam, with such a deterioration in sound quality from running client side as opposed to the quality I get server side it doesn't seem worth the effort, i suspect that if the network traffic is enough to screw up sound adding a web cam feed into the mix won't help. 

I run one instance of ice-cast, at least two additional music streams across my net along with two independent Viop units (spa3000's), its not really busy for a gig, but its not empty either.

---

### Post by gordintoronto on 2011-03-14
> **MikeUK said:**
> ...my problem IMHO was a previously set up the server side .skype folder in the home directory, this seemed to block the client from being able to login, once removed my login problem, and access to setting options went away ...


I'm sorry, but I can't figure out what you are trying to say.

In any case, I think your clients are too thin for what you want to do. Not enough memory, not enough CPU.

---

### Post by MikeUK on 2011-03-14
I'd set up skype on the server to try it out. I'd run the application on the server using the user's account.
This resulted in a skype profile being created for the user.
This profile in the user home directory prevented a smooth login and caused skype to lock up if the application was run on the client.
Once this .skype directory was removed from the user's home directory the problem loging in went away.

For a thin client the neoware Ca2 may be too thin to run Skype as a local app, but its more than sufficient for running LTSP and playing a variety of media feeds on. I can understand 'maybe' CPU speed at 800mhz but memory? 256M isn't enough..actually on checking the client has 500M and with about 200M of that unused (not even used for buffers). Its basically just an Xorg server and pulse audio which between them is using 10% of the CPU.

---

### Post by gordintoronto on 2011-03-14
In Ubuntu, 512 MB is a completely different story from 256 MB. Should be adequate for most things, including Skype.

For Skype with video, 800 MHz is marginal. Should work OK with text and audio, though.

---

### Post by MikeUK on 2011-03-15
> **gordintoronto said:**
> In Ubuntu, 512 MB is a completely different story from 256 MB. Should be adequate for most things, including Skype.

For Skype with video, 800 MHz is marginal. Should work OK with text and audio, though.

Thats what i thought.

I suspect my issue isn't driven by the CPU or memory, but by all the network traffic going between the thin client and server, 
One of Skype's recommendations for poor sound is to shut down other network applications,

---

