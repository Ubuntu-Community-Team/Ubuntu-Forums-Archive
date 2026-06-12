---
title: "I disconnected and then"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by Darris on 2011-04-27
Okay, every night at 11 the router turns off because the building I am in decided to connect the router to the same path as the lights which they turn off to save energy. When they turn it off, my ubuntu starts going crazy and continually tries to find the networks and it obviously doesn't work.
Every time I closed that stupid network window it would pop up again in 10 seconds and disrupt what I was doing, so I clicked disconnect. Now this morning I try to connect and it sees the different connections, but I cant access them. I click them and it acts as if nothing was clicked. 
This is really frustrating. 

tl;dr:
I disconnected my wireless and now it won't reconnect.

---

### Post by Darris on 2011-04-27
I feel like this could be solved with a simple command. I just don't know what it is. 
P.S.
could you also tell me how to keep it from popping up over and over in the future?

---

### Post by Darris on 2011-04-27
Also, if I open network editor from the panel's notification area, there are no wireless connections, but if I open it from System>Preferences>Network Connections (which, I assumed opens the same editor) it does show all of my previous connections.

This is really confusing me. I don't know what to do. 
How do you reconnect after you have clicked disconnect?

---

### Post by Darris on 2011-04-27
It works on the login screen. I have set up my firefox to be openable from the login screen- so the internet works there. 
but as soon as I login it doesn't work. 

If I right click the network applet on the panel, the options "enable wireless" and "enable networking" are greyed out and I am unable to tick them either on or off. 

I have run the command 
> sudo killall NetworkManager
and it seems to work, but if I try to restart it with
> sudo NetworkManager
It says it's already running, which doesn't make any sense because I just did the killall.

I ran
> sudo lshw -C network
and on *network it says DISABLED. 

I just don't know how to reenable it. 
There is a hardware switch on my toshiba satellite for wireless, and it is certainly turned on. 

I've enclosed some screenshots of the Network editor problem. The empty one is the one from the panel, obviously.

I'm trying to think of any other information you may need, but I think that's all I have.

---

### Post by Darris on 2011-04-28
bump

---

### Post by Darris on 2011-04-29
bump

---

### Post by Darris on 2011-04-30
bump

---

### Post by Darris on 2011-05-01
please guys, any feedback would at least give me some confidence.
do you have any idea at all?
what could be wrong with it ?
i have no internet and i really need it for school

---

### Post by Rasa1111 on 2011-05-01
damn..
Im sorry no one has replied to you yet. :(
Respect for your patience! 

Im also sorry that im not sure how to remedy your problem.

 I will subscribe though and attempt to attract others here.

just a note,
when running a "killall" you don't need 'sudo'. 

just
killall followed by the app name is all you need. 

I will look around for anything that might help.

Sorry again no one has answered..
than can be very frustrating and discouraging.
and can even be enough to push some people away. 
which is understandable.

 Good luck mate <3

---

### Post by Darris on 2011-05-01
I think you may have spoken too soon because, in an attempt to fix it, I tried to reinstall network manager and now its gone entirely
I'm going to be without access to another computer for 1 week starting tomorrow and I know this thread is going to die if I am gone so i'm trying to fix it before I leave.

I have the deb file for network manager, but after running it, I now have no applet on the top. I still have the notification thing on my panel, but the network is not inside it.
and now it's gone on other users too from me having done this.

this has gone from bad to worse. 
I am about to upgrade to 11.04 to see if maybe that would fix the problem by reinstalling the network manager, lol
Do you think that will work?
it sounds a little foolish to me, but I am getting kind of desperate.

Thank you for replying to me.

---

### Post by Darris on 2011-05-01
I fixed it by upgrading. However, after checking the functionality, I have learned that WINE no longer plays my games. It just opens for a half second then closes.

---

### Post by Rasa1111 on 2011-05-01
well that's good news! :D
Good job!

 I don't play games though, so that'd be the last of my worries and the last thing i could help with. 

I'd just be glad the main stuff is fixed! lol

Good luck. 
Glad you got it fixed.

---

### Post by Darris on 2011-05-07
it's okay, I just had to reboot, it was a silly problem. it works now.

---

