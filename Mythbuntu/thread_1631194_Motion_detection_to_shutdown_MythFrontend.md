---
title: "Motion detection to shutdown MythFrontend?"
date: 2010-11-26
forum: Mythbuntu
---

### Post by Morgennebel on 2010-11-26
Hi there,


my wife falls asleep while watching MythTV recordings or movies quite frequently. Sometimes I have to shutdown my energy-eating Plasma-TV and the computer few hours after she fall asleep...

I thought about adding motion detection to my MythFrontend. As long as motion is detected, no action are initiated. But if no motion is detected for about 30 mins - send warning via OSD to user and then shutdown the system to save energy.

Any ideas where to start?

Thanks, -MN

---

### Post by LowSky on 2010-11-26
I dont know about your wife but I move a lot in my sleep. so motion detection will not work well.

Your TV should have a sleep mode. usually 15, 30, 60 and 90 minute sleep times. Ask your wife to use it more often.

For the PC enable suspend or hibernation in the power management if there is no commands issued within 1-2 hours. Some TV will turn off if they detect the PC shutting down.

---

### Post by byronmyth on 2010-11-29
Try upgrading wife to v2.3 that might solve the issue but no doubt introduce a whole load of new ones. ;)

---

### Post by Morgennebel on 2010-11-29
Upgrading to Wife 2.3 is no choice, as there are kids v1.0 and v2.0 still running around in the system :-)

To be honest I think motion detection would solve the problem - the threshold trigger needs to be adjusted to avoid small movements during night to cancel a shutdown and allow a shutdown during sleep...

Go GREEN :)

---

### Post by matt_symes on 2010-11-29
Hi

What an interesting idea!!! Maybe motion detection using a web cam? Might give a starting place.

I have to agree though, i'm not sure it will work.

Kind regards

---

### Post by byronmyth on 2010-11-30
Not sure how much my other half would want a webcam pointed at her in bed, "of course darling, it's just for motion detection" LOL....

---

### Post by matt_symes on 2010-11-30
> **byronmyth said:**
> Not sure how much my other half would want a webcam pointed at her in bed, "of course darling, it's just for motion detection" LOL....

Yes good point :D Back to square one. Good luck with that one ;)

---

### Post by azmyth on 2010-11-30
There's a package called motion. You could probably do it with that. I think when it sees motion it starts taking pictures so it possibly could be too taxing on your system though. You could monitor the drive where the pics are stored and just check to see if it has been 30 minutes between pics and shutdown your FE.

---

### Post by ian dobson on 2010-11-30
Hi,

Why not just use mythtvosd so send a message to the display and then watch the ir and if the user doesn't press a key after 5 messages then shutdown the box.

hmmm, sounds like an interesting weekend project.


Regards
Ian Dobson

---

### Post by ian dobson on 2010-11-30
Hi,

Wow it didn't even take that long:-

OK the script is in 2 part, the first part is a bash script that can be called in a cron job, maybe between 9:00pm and 6:00am every 30 minutes, and a xml file that contains the message to be displayed on the screen.

Here's the code
```

#!/bin/bash
# Go to sleep if the viewer is sleeping
Count="0"

while [ $Count -lt 4 ];do
  /usr/bin/mythtvosd --template=/tmp/msg.txt > /dev/null
  Result=`timeout 15 irw|wc -l`
  if [ "$Result" -ne "0" ]; then
    Count="6"
  fi
Count=$[$Count+1]
done

if [ "$Result" -eq "0" ]; then
  echo User has fallen asleep do something - Add your code here
fi

```

And the xml message file:-
```

<mythnotify version="1" displaytime="10">
  <container name="news_scroller">
    <textarea name="text_scroll">
      <value>hello world press any key to abort the message display   </value>
    </textarea>
  </container>
</mythnotify>

```

The code displays the message 4 times (if the user doesn't press a key on the remote), waiting 15seconds between each message. If the user presses a key the script ends without doing anything. If the user doesn't press a key after 4 messages the line "Add your code here" is run.

Not as cool as a motion detection system, but K.I.S.S (keep it simple, stupid)

Regards
Ian Dobson

---

### Post by nickrout on 2010-11-30
```
<mythnotify version="1" displaytime="10">
  <container name="news_scroller">
    <textarea name="text_scroll">
      <value>hello world press any key to abort the message display, then take a baseball bat to the **** who put this annoying message on the screen.  </value>
    </textarea>
  </container>
</mythnotify>
```

---

### Post by ian dobson on 2010-12-01
> **nickrout said:**
> ```
<mythnotify version="1" displaytime="10">
  <container name="news_scroller">
    <textarea name="text_scroll">
      <value>hello world press any key to abort the message display, then take a baseball bat to the **** who put this annoying message on the screen.  </value>
    </textarea>
  </container>
</mythnotify>
```

Have you actually tried the code? The message is fairly unintrusive, it's just a message a the bottom of the screen.

Now show me your working solution..........

Regards
Ian Dobson

---

### Post by nickrout on 2010-12-01
Sorry I was making a poor attempt at humour. Should have included a smiley.

:)   :)

---

### Post by ian dobson on 2010-12-01
apology accepted ;)

Regards
Ian Dobson

---

### Post by azmyth on 2010-12-01
Here's my solution :)

[http://sleepzine.com/sleep-news/tv-automatically-turns-off-when-you-fall-asleep/](http://sleepzine.com/sleep-news/tv-automatically-turns-off-when-you-fall-asleep/)

What will they think of next?

---

