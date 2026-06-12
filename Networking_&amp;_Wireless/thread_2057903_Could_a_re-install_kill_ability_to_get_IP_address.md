---
title: "Could a re-install kill ability to get IP address?"
date: 2012-09-14
forum: Networking &amp; Wireless
---

### Post by silbar on 2012-09-14
Greetings,

My machine seems unable to connect with the internet.  I assume this is really a Comcast problem, although their techs can't see, remotely, why I can't.  So a tech will make a house call on Sunday, three days from now!!

Anyway, I am wondering if the problem might have arisen because I have just now re-installed Ubunut 8.04 (on the way to upgrading to 10.04 and then 12.04).  Not at all clear to me, as there HAVE been moments in the past 28 hours when an internet connection has been established.

Is this too ridiculous?

Richard Silbar

---

### Post by raja.genupula on 2012-09-14
here i am not getting one point . thats why you have to install 8.04 LTS to upgrade to 12.04 LTS ? 

You installing 8.04 LTS , so why can't you install 12.04 LTS directly ?

---

### Post by kaytrance on 2012-09-14
Yeah, well, you should give more info on what kind of connection you are using (LAN, WiFi, PPP..).
I cal also be hardware related problem if 8.04 doesn't have any drivers for you network adapter, or the default one is buggy.

---

### Post by silbar on 2012-09-14
The reason I installed 8.04 is because (I'm ashamed to say) I seriously messed up the install of 12.04 from a liveUSB and eventually got to the point where I could not boot into anything, even from the liveUSB (!).  Unfortunately, I had never made a 10.04 start-up disk, but I did have an 8.04 startup disk.  Needless to say, this was not my finest hour (actually 30+ hours).

My connection to the net normally is by ethernet through the Comcast modem.

At the moment I am now making a 12.04 startup CD (LiveCD) here at work, as I suspect my LiveUSB that I used earlier (or some graphics configuration file) is corrupted.  But, I won't be able to try that until I get back home.

Fortunately, I can make these postings since I at the Lab (which does not go through Comcast).

   RRS

---

### Post by silbar on 2012-09-14
Update from the previous posting:

I shouldn't probably be blaming Comcast for my troubles getting to the net from 8.04.  On using the 12.04.1 LiveCD I created at the Lab, I was, in the Try Ubuntu mode (live session), able (and immediately) to be connected with the net.  So, as kaytrance suggests, the problem may have been with the 8.04 installation.

The installation of 12.04 went smoothly.  After some help from this forum on my "grub error 15" error. I was then unable to log in using what I thought I set up as my password. I was finally able to reset my login password (after getting past the "authentication token manipulation error", also with the help from the forum) -- all this in recovery mode at the root prompt.  So, this posting is being sent to you from 12.04 (finally!).

Rico Silbar

---

