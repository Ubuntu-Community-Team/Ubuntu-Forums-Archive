---
title: "Need Help Diagnosing Crashes"
date: 2012-07-29
forum: Mythbuntu
---

### Post by johnvic on 2012-07-29
AMD Athlon 64 x2 dual core 4400+
Asus A8v mobo
2 gigs ram
120 gig hard drive
500 gig drive for sharing recordings
video card is Sparkle geforce 6200 256 mb AGP 8x 
I am running both backend and frontend on it for mythbuntu 12.04 /.25

I was finding that it would freeze up when I was not home. It seemed to coincide with days I was recording. I say freeze up because when I turned on my receiver and tv I would see the mythtv screen but the system would not respond, even to a ping or try to ssh into it. I had to force reboot. It seemed to happen on days I had more than one recording that was after one another, or at least while the first one was still looking for commercials. I decided to exit the mythtv fronted to see what would happen when I'm not watching and that is causing less crashes. It still happens but far less often. 

I'm not sure how to diagnose this problem. I don't mind exiting but I would like to eliminate crashes if possible. Any suggestions for diagnosing? I have checked the drives and they are passing tests and I periodically check the temperatures of the cpu and mono and both are fine.

Is this system on the low end for a mixed frontend/backend? My plan is to eventually build a quiet net top frontend and have a separate backend and possibly use this PC as a FreeNAS server.

Thanks!

---

### Post by klc5555 on 2012-07-29
Perhaps try disabling commflagging entirely for a while and record the bejeezus out of the machine to see whether it hangs. If it passes this test, try reenabling commflagging, but without logo detection. I've had installations of 0.24 where mythcommflag would peg out the CPU at 99% doing logo detection, but never complete or exit.

---

### Post by faginbagin on 2012-07-30
I assume when you reboot, you look at /var/log/messages, but nothing informative appears. Since the screen is visible when it locks up, here's an approach that might help you figure out why it's locking up:

1) Before you leave the system unattended, open a terminal window.

2) In the terminal window, become root. The command "sudo bash" should do the job.

3) Execute the command "tail -f /var/log/messages"

4) If the system is locked up when you return, there should now be up to 24 lines worth of messages. Hopefully, they'll give you a clue as to the problem.

One other thought. My experience may or may not be relevant, but in case it helps ...

I had a problem with a similar CPU, an AMD Athlon X2 4850e, an ASUS M3N78 PRO mobo, and a PVR-150, a PCI tuner card. The system didn't lock up, but the PVR-150 would sometimes stop working and the only fix was to reboot the system. The solution was to disable AMD Cool n Quiet in the BIOS. I also found that setting the CPU frequency governor to performance also worked. I don't fully understand why this worked, but apparently, when using Cool n Quiet and the CPU ondemand frequency scaling, it also slows down the PCI bus, which can affect the ability of a PCI based tuner card, like the PVR-150, to function properly. Apparently, it's a problem that was fixed in the Athlon/Phenom II CPUs.

---

### Post by QIII on 2012-07-31
```
sudo bash
```is not necessary.  Probably not even advisable.  Sure, it keeps you from having to type four letters before each command, but it also gives you greater opportunity to quickly bork things.  sudo limits the user to the permissions granted by the sudoers file.  sudo bash lets you go hog wild as root and subverts some of the security of sudo.

If you want to avoid the four letters, use ```
sudo -i
``` which is liable to play fewer reindeer games with environmental variables.  But even that is not necessary.  Stay in the habit of operating from a position of "least privilege/least exposure".

You can probably find all you want by looking at the last few lines of dmesg and syslog after you restart.  100 lines may be overkill, but you never know.

```
sudo tail -n 100 /var/log/dmesg
```might be the most informative, but you can also do

```
sudo tail -n 100 /var/log/syslog
```

---

### Post by johnvic on 2012-08-02
Okay, so I turned on commercial detection and did an insane amount of recording. I ran back to back on the two tuners for 6 hours. I had no crashes.

I will next try a different version of commercial detection. I already had Cool n Quiet disabled so that is not a problem.

Thanks for the tips about the log files. One problem about opening a terminal window is that I am running frontend and need to quit that to open a terminal window.

---

### Post by nickrout on 2012-08-02
> **johnvic said:**
> Okay, so I turned on commercial detection and did an insane amount of recording. I ran back to back on the two tuners for 6 hours. I had no crashes.

I will next try a different version of commercial detection. I already had Cool n Quiet disabled so that is not a problem.

Thanks for the tips about the log files. One problem about opening a terminal window is that I am running frontend and need to quit that to open a terminal window.

Easiest way is to ssh in from another computer, you can watch the logs scroll by on your laptop on the sofa as you watch myth crash on the TV :-)

---

### Post by klc5555 on 2012-08-02
> **johnvic said:**
> Okay, so I turned on commercial detection and did an insane amount of recording. I ran back to back on the two tuners for 6 hours. I had no crashes.

I will next try a different version of commercial detection. I already had Cool n Quiet disabled so that is not a problem.

Thanks for the tips about the log files. One problem about opening a terminal window is that I am running frontend and need to quit that to open a terminal window.

If this is a standard-ish Mythbuntu installation, the underlying desktop is XFCE. You should be able to alt+tab to your desktop environment while the frontend is running and then do other computery things without interrupting your frontend playback.

---

### Post by jksj on 2012-08-03
I have had similar problems ie a total system hang when the machine gets bored. I am running 0.25 fixes on 12.04. This only started happening recently so I suspect kernel 3.2. 
I am running a nvidia atom ion 1 platform 64 bit. 
After much googling I re-installed 11.10 / 0.25 32 bit which was rock solid.  Then 12.04 32 bit pae which has run for about 11 hours (a recent record) without problems. The 32 bit change may be a red herring as the recent 12.04 update to kernel 3.2.0-27 addresses some kernel hangs.
Also see [http://www.phoronix.com/scan.php?page=news_item&px=MTA4ODc](http://www.phoronix.com/scan.php?page=news_item&px=MTA4ODc) which recommends updating the nvidia driver to 295.49 from nvidia-current-updates.

---

