---
title: "Cannot change channels in MythTV - Remote is not working"
date: 2008-03-05
forum: Multimedia &amp; Video
---

### Post by tech9 on 2008-03-05
Hi all,

  I finally was successful with configuring MythTV for the Hauppauge WinTV PVR-150 tuner card that I installed. I was able to scan all of my cable channels, I just cannot change to any other channel from the starting channel that I set in the mythbackend. I have a remote receiver that I also connected up to the tuner card, brand new batteries installed in the remote; but the remote is not responsive. None of the buttons work. Are there some more configurations that I need for my remote? The remote is also a hauppauge remote that came with the card. 

I am currious to know if there is specific keys on the keyboard that will change the channels in the front-end? 

I am hoping that I can figure out how to get the remote working with someone's help.

Thanks in advance to anyone that can help or provide good suggestions,

T9

---

### Post by turlian on 2008-03-05
Howdy,

In short, your up and down arrow keys should change the channel.  For a full list, check out:

[http://wilsonet.com/mythtv/keys.txt]("http://wilsonet.com/mythtv/keys.txt")


As for the remote, are you using Mythbuntu and have you checked the control center?  for non-mythbuntu, check out [URL="http://www.mythtv.org/docs/mythtv-HOWTO-8.html"]http://www.mythtv.org/docs/mythtv-HOWTO-8.html
[/URL]

-J

---

### Post by tech9 on 2008-03-05
> **turlian said:**
> Howdy,

In short, your up and down arrow keys should change the channel.  For a full list, check out:

[http://wilsonet.com/mythtv/keys.txt](http://wilsonet.com/mythtv/keys.txt)


As for the remote, are you using Mythbuntu and have you checked the control center?  for non-mythbuntu, check out [URL="http://www.mythtv.org/docs/mythtv-HOWTO-8.html"]http://www.mythtv.org/docs/mythtv-HOWTO-8.html
[/URL]

-J

Thanks for the links Turlian!  :)

I thought this was the case with the infrared drivers.

---

### Post by tech9 on 2008-03-07
I was not able to change channels on the front-end interface with the up and down arrows. I haven't had time to looking into the remote problem.

---

### Post by wolfen69 on 2008-03-07
hi. i have the same tuner card as you and have no problems with remote. perhaps you could go back into mythtv setup and reconfigure your remote. you can change channels on the keyboard by just punching in (number keys) what channel you want.

---

### Post by tech9 on 2008-03-07
> **wolfen69 said:**
> hi. i have the same tuner card as you and have no problems with remote. perhaps you could go back into mythtv setup and reconfigure your remote. you can change channels on the keyboard by just punching in (number keys) what channel you want.

Hi wolfen69,

I have tried punching in different numbers, It will only allow me to hit one digit at a time and then the number disappears. This does make me think that I have not configured it properly. Which Backend configuration do I setup the remote under. I can't recall seeing those options?

Thanks for your help,

T9

---

### Post by tech9 on 2008-03-08
I was able to get my remote working, but the channel button only rewinds and forwards the live buffer. It does not channels. Also, when I hit the up and down arrows on the keyboard it does the same thing. I also noticed that the all channels show as unknown under the the scheduler. 

Any help would be appreciated... I'm almost there :

---

### Post by tech9 on 2008-03-24
> **tech9 said:**
> Thanks for the links Turlian!  :)

I thought this was the case with the infrared drivers.

ok, I have checked the control center, and I set the remote to hauppauge tv remote. I am still having problems even turning channels on the keyboard. The up and down arrows do not change the channels. Also, I am able to change the channels sometimes by hitting the return key. Something is not configured properly somewhere. 

Also, when looking under the scheduler, all my channels show as unknown.

Can anyone provide more suggestions or options to try to fix this?

---

### Post by turlian on 2008-04-24
Ok, so does it still rewind / ff when you hit the up / down arrow keys on your kybd?  The default behavior is that it should bring up a box at the bottom of the screen displaying what is on the next (or previous) channel for each press of the up / down arrow key.  Then you hit Enter to actually change.

I suspect that something else is going on, though.

As for the "unknown" channels, are you using Schedules Direct?

---

### Post by tech9 on 2008-04-28
> **turlian said:**
> Ok, so does it still rewind / ff when you hit the up / down arrow keys on your kybd?  The default behavior is that it should bring up a box at the bottom of the screen displaying what is on the next (or previous) channel for each press of the up / down arrow key.  Then you hit Enter to actually change.

I suspect that something else is going on, though.

As for the "unknown" channels, are you using Schedules Direct?

I am not using Schedules Direct because it is not free. Do you know of any free sites?

---

