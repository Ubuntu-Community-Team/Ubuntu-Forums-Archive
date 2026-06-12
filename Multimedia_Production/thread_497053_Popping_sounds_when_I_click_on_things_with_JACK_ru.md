---
title: "Popping sounds when I click on things with JACK running."
date: 2007-07-09
forum: Multimedia Production
---

### Post by GregoryMA on 2007-07-09
I am having problems with popping sounds when I click on buttons/scroll/highlight things etc.  At first I thought it was the system sounds not knowing how to react to JACK because the pops would stop when  JACK was not running.  So, I turned off the system sounds and the amount of pops decreased, but they did not stop.  I still have pops occurring when I open menus or click on things.  Does anybody know what is going on?
Thanks, Greg.

---

### Post by GregoryMA on 2007-07-09
After listening to this more I have noticed that it is not happening when I click on things or highlight things but when the CPU is taxed.

---

### Post by fredj on 2007-07-09
Open the jack status window and see if you are getting xruns with each pop.

---

### Post by GregoryMA on 2007-07-10
I am getting x-runs with each pop.  This only happens with Ardour running as well as JACK.

---

### Post by fredj on 2007-07-10
What kernel are you using? Are you running Jack in realtime mode? What frames, periods and latency are you
using. You could try increasing the latency by altering frames or periods but remember xruns don't really
matter too much unless they occur while you are recording audio, so once you start recording don't click
on anything until you stop recording.

---

### Post by GregoryMA on 2007-07-11
I just installed ubuntu studio last week and I am using the 2.6.20-16-low latency kernel.  I wasn't running jack in realtime mode.  I am using 1024 frames/period and 0 input and output latency.  I am quite new to linux audio but I am guessing 0 latency is a bit idealistic.  Is an x run similar to clocking issues when you run two digital devices on different clocks?  Should I run Ardour off the Jack clock?

---

### Post by fredj on 2007-07-11
Forget about the input and output latency, those are specialist things that don't generally apply. 
The two things that contribute to the overall latency are the Frames/Periods and the Periods/Buffer.
The low latency kernel only provides a faster clock signal than the normal kernel, this is needed by 
many audio programs for accurate timing.
However to get really low latency (i.e. less than 10ms) you need to install the real time kernel and
adjust a few other things so that audio programs take priority over all other programs or processes.
What is latency? It's the time between a sound signal going into the computer and the same signal
coming out of the speakers or headphones. It is generally thought that 10ms (10 thousands of a second)
is the smallest acceptable value but 5ms is what you should aim for when you are recording audio.
To get these sort of low latencies you really need the real time kernel then you can run jack in realtime
mode.

---

### Post by GregoryMA on 2007-07-12
This begs the question, which real time kernel should I use and where do I get it?  Also what kinds of things do I have to adjust to give audio programs priroity?

---

### Post by fredj on 2007-07-12
If you look at the first message (first sticky thread) in this forum which asks for users to test the real time
kernel it will tell you how to get and install the real time kernel.

---

### Post by GregoryMA on 2007-07-14
I have the realtime kernel up and running.  Although I haven't had the time to play around in jack to get the xruns down.  How do I prioritize programs though? Is it with nice?

---

### Post by fredj on 2007-07-15
Open a terminal and type these commands (including the quote marks)
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'

You can then type 'cd /etc/security' and 'sudo gedit limits.conf' to check that these lines have been added to
the file.
Then go to System -> Administration->Users & Groups. The audio group already exists but it doesn't show up
in the list. Choose manage groups and select to add a new group called audio. Add the users that you want 
to use jack and other progams to the new audio group. In fact they will be added to the existing audio group.
Reboot to make sure the changes take effect and run qjackctl. You can now enter setup and select the
realtime box. Run jack and open the status window to monitor for xruns.

---

### Post by GregoryMA on 2007-07-16
Thanks a lot.  It is working great.  I have this set up on an ageing laptop and I am now getting 3ms latency.  I am throughly impressed.  Thanks again for all the help.
Greg.

---

### Post by fredj on 2007-07-16
Well done!

---

