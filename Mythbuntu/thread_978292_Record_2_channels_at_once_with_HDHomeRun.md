---
title: "Record 2 channels at once with HDHomeRun?"
date: 2008-11-11
forum: Mythbuntu
---

### Post by toddk111 on 2008-11-11
I have a Myth set up which has been working well for me with one small problem, when I attempt to record four shows at the same time, the fourth show appears as a conflict in the upcoming recordings.  

I have four tuners, two Dvico USB Gold tuners and an HDHomeRun.  When I go to Information Center > System Status > Tuner Status, it shows that I have four tuners.  In the upcoming recordings screen, the successful recordings show that they use tuners 1-3.  Since the Dvico tuners are tuners 1 and 2, I wonder why I'm not able to record two shows at once on the HDHomeRun.  

Does anyone know how to get my HDHomeRun to record two shows at once?

Thanks,
Todd

---

### Post by newlinux on 2008-11-11
Maybe you have your input groups somehow setup to disallow your second HD homerun tuner from working at the same time as the other tuner. What are your input group settings?

Also, are you able to use your 4th tuner at all (what happens when you specify that a recording use the 4th tuner when the other tuners are idle?)

---

### Post by foxbuntu on 2008-11-11
> **toddk111 said:**
> I have a Myth set up which has been working well for me with one small problem, when I attempt to record four shows at the same time, the fourth show appears as a conflict in the upcoming recordings.  

I have four tuners, two Dvico USB Gold tuners and an HDHomeRun.  When I go to Information Center > System Status > Tuner Status, it shows that I have four tuners.  In the upcoming recordings screen, the successful recordings show that they use tuners 1-3.  Since the Dvico tuners are tuners 1 and 2, I wonder why I'm not able to record two shows at once on the HDHomeRun.  

Does anyone know how to get my HDHomeRun to record two shows at once?

Thanks,
Todd

Even with the conflict does the show record? I have seen this as well, many of my shows show conflict but record anyways because it polls the tuner to check if it is active or not before skipping the recording due to a conflict.

---

### Post by toddk111 on 2008-11-13
When it shows the conflict, it does not record.  Also, when I attempt a test recording (without doing other recordings at the same time) and specify tuner 4 as the preferred tuner, it just ends up using tuner 1.  Any help would be greatly appreciated.

Thanks,
Todd

---

### Post by novellahub on 2008-11-14
Do you have the recording source set for the second tuner for the HDhomerun?

---

### Post by toddk111 on 2008-11-18
> **novellahub said:**
> Do you have the recording source set for the second tuner for the HDhomerun?

Yes, it is the same as the other tuners.  Do you have any other ideas of where I can look for a possible problem?
Thanks,
Todd

---

### Post by novellahub on 2008-11-19
1.  Check the cables.  Maybe you have a bad cable on Tuner 1.
2.  Delete all tuners on the Master Backend, then re-add them and assign back the input connnections.  Then test the tuners via live TV.  You can change inputs via live TV by pressing the "M" key and then navigating to another tuner.
3.  If all else fails, look for clues on:

[https://help.ubuntu.com/community/HDHomeRun](https://help.ubuntu.com/community/HDHomeRun)

[http://www.mythtv.org/wiki/index.php/Silicondust_HDHomeRun](http://www.mythtv.org/wiki/index.php/Silicondust_HDHomeRun)

---

