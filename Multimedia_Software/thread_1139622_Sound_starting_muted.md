---
title: "Sound starting muted?"
date: 2009-04-27
forum: Multimedia Software
---

### Post by keirlawson on 2009-04-27
Whenever I load up Ubuntu the "front" volume slider is always at the bottom, meaning I dont hear anything, I have to manually adjust it every time I reboot, which is getting quite tedious.  Does any one have any idea what the problem could be? I'm using PulseAudio with Ubuntu Jaunty 64bit (though the problem was present in Intrepid 64bit as well).

---

### Post by Bakker on 2009-04-27
I am suffering from the same issue. 

Xubuntu 9.04 clean install
Creative Audigy 2 Value
Already tried storing the volume level manualy with *alsactl store*. 

Never tried Intrepid but i havent had this issue in other distro's.

---

### Post by stumpey on 2009-04-27
Hi

I had the same problem in Intrepid amd64 on now in Jaunty amd64 I must have tried every "fix" in the forums but none of them worked.

But here is how I resolved the problem

Create a file called soundstart.sh (or whatever name you like!) enter the script below and make the file executable.

This is the code for the script

```
#!/bin/sh 

sleep 30

/usr/bin/amixer -c 0 sset Master,0 unmute > /dev/null

/usr/bin/amixer -c 0 sset Master,0 50% > /dev/null
```

I used the sleep command because it takes a while for my desktop to load up compiz,awn etc and without the sleep the script starts before the volume applet has loaded but adjust to suite your desktop.I then have the volume set to 50% but this can be changed to whatever you need.

Now place the file in your home folder then go to System>Preferences>Startup applications then "Add" then "Browse" and add the file to the startup list.

Then next time you bootup the volume will be set and Bobs you Auntie :):)

I have used the forums a lot over the years so thought I had better post something that may be of use!

Steve

---

### Post by cornelis1 on 2009-04-28
I also spent de last week trying to find a solution to this problem. Your workaround is the only one that worked for me. 'Sleep 5' is long enough for me. Sound level is restored soon enough to hear the login sound.

Thanks.

---

### Post by waj1122 on 2009-07-02
Finally something that actually works without spending hours (maybe they'll get it right in 9.10).

Thank you very much.

---

### Post by Upkeep on 2009-08-20
Thank you

---

### Post by adam_kimber on 2009-11-02
Will give this a go! Been looking for a solution for ages to this really annoying problem!

---

### Post by Elviswind on 2009-11-13
I'm now running Xubuntu 9.10 and had the sound muting problem, but I was also suffering from crappy sound . . .  high frequencies did not sound correct.  I tried the edit to /etc/rc.local and that sort of worked to correct the muting problem, but the sound was still crummy.

What I found was, and I think this will work better in Xubuntu than other Ubuntu, that removing Pulseaudio solved all the problems.  

Look at post #4 in this [thread]("http://ubuntuforums.org/showthread.php?t=1313253") and give it a whirl.  Note: Becuase I'm running Xubuntu I didn't need to follow the last couple steps to install another mixer program . . . the one included with Xfce still works just fine.  :p

---

