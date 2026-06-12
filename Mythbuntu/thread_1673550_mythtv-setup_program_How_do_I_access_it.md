---
title: "mythtv-setup program How do I access it?"
date: 2011-01-22
forum: Mythbuntu
---

### Post by nhtrader on 2011-01-22
I installed a nonfunctional tuner card (AverMedia TVHD Duet) and replaced it with another (WinTV HVR-1250). But I get this error message from MythTV Frontend ....

MythTV has no capture cards define. Please run mythtv-setup program.

When I exit mythTV using ESC and enter Ubuntu, I can't find mythtv-setup program in Applications Menu or sub-menus. Secondly, while I'm in mythTV I selected Utilities/Setup | Setup and followed the prompts. This didn't "discover any TV Cards". I can't find a menu option that will discover a TV card.


Where/How do I find/use mythtv-setup progam?

---

### Post by gyussz on 2011-01-22
Try to run it from terminal, it will bring up an UI anyway (if I remember right).

---

### Post by newlinux on 2011-01-22
You can run it from a terminal

```

mythtv-setup

```

or from mythtbuntu-control-centre.

---

### Post by nhtrader on 2011-01-24
Thanks for the tip.

1. Note for future newbies like myself, you can't access "Mythtv-setup" from Mythbuntu Control Centre.
2. from terminal mode: mythtv-setup <E>
    This works, but it brings up a message: "MythTVbackend must be closed before contining. Is it OK to close any currently running mythbackend processes?"

    I answered yes. Then entered my username's password and not the mythtv database password. Then saw this menu:
 1.General 
 2.Capture Cards 
 3.Video Sources
 4.Input Connections
 5.Channel Editor


3. Here's the menu approach to running "mythtv-setup"...
      Applications|System|MythTV Backend Setup


As a note to developers, It would be more user friendly if the error message from MythTv's frontend would clearly state that the MythTV Backend Setup needs to be used. "mythtv-setup" is too vague.

---

### Post by nickrout on 2011-01-24
But the documentation is very clear on what to run:

[http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend#Running__mythtv-setup](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend#Running__mythtv-setup)

or

[http://www.mythtv.org/docs/mythtv-HOWTO-9.html#ss9.1](http://www.mythtv.org/docs/mythtv-HOWTO-9.html#ss9.1)

Both say to run mythtv-setup, what is counter-intuitive about that?

---

### Post by newlinux on 2011-01-24
> **nhtrader said:**
> Thanks for the tip.

1. Note for future newbies like myself, you can't access "Mythtv-setup" from Mythbuntu Control Centre.
...


Yes you can. It's on the mysql page in mythbuntu-control-centre (Launch mythtv Setup)

---

### Post by nhtrader on 2011-01-24
nickrout, 

Nothing if you know where to look.

I'm glad you responded to this and shared what you know. However, think about this. You load a something new - mythbuntu. You dive into it. And the first thing you encounter are numerous error messages. Where do you begin? As you are well aware of documentation is sparse and lacking, so I tread on here in this forum.

So the hunt begins for newbies such as myself to find the resources that matter (and thank you for the links that you posted). Plus, I didn't know at the time which half of the program I'm dealing with - frontend or backend. When you see MythTV appear for the first time it doesn't say you're in the frontend. Plus you think that you could go to Utilities/Setup to make the changes that the program wants you to make. But no. This is not the place.

And secondly, why should I expect the program to refer me to another program? The setup that I'm "in" (when I boot up MythTV brings me into the frontend program) didn't finish due to an error; therefore this setup is incomplete. So I'm figuring that I need to re-enter it and start over. But no, the program that I'm in (frontend) is telling me to use another section of the program (backend) that I've never seem before. It assumes that I know to switch to another program (backend). I didn't know. Plus the program told me to run "mythtv-setup", but didn't tell me that I need to exit the program; enter ubuntu; and then enter terminal mode to execute a shell command "mythtv-setup". (also notice that this assumes that I know how to enter terminal mode and that I'm familiar with the new stripped down version of ubuntu and know what it is; and where to find terminal mode; and use it)

Third, when I exit MythTV I enter yet another world - a stripped down version of ubuntu.  At this point, I'm lost. I don't know where I am b/c I'm unfamiliar with ubuntu. Secondly, I'm unfamiliar with MythTV and I don't know how to enter either the frontend or the backend. At this point, all I know is to reboot/turn it off and turn it on again which only brings me back to the same cycle of events.

Lastly, let it be noted that accessing the two halves of MythTV aren't even in the same sub-menu. The frontend is accessed from APPLICATIONS|MUTLITMEDIA and the backend is accessed via APPLICATIONS|SYSTEM. So from a usability standpoint, how is a newbie to know?

So for those of you more experienced, please be patient with us who are trying to migrate away from something familiar and explore something foreign and way more complicated. I believe the time spent learning something new will pay off. But I have to say that learning how to use MythTV has a steep learning curve. I haven't even gotten to any of the thousands of settings yet.

Lastly, there are those that are "fearless" and dare to try and explore without worrying about damaging their equipment/system/settings. And there are those that are more cautious and don't want to spend the time to reinstall the whole thing. Trial and error will only get you so far, and then you're back to asking for help.

I'm in the camp of asking for help right away rather then spending 6+ hours googling for each thing. In the end, this approach will help document what was unclear, non-intuitive, problematic, etc.

---

### Post by nhtrader on 2011-01-24
newlinux,

thank you for being more specific. I of course was looking for a selection named setup and didn't think to look within MySQL. I clicked several of the other headings but not MySQL and I paid the price - ignorance. Please accept my apologies.


This goes with what I'm saying that the learning curve is steep. How's a newbie to know?

---

### Post by newlinux on 2011-01-24
> **nhtrader said:**
> newlinux,

thank you for being more specific. I of course was looking for a selection named setup and didn't think to look within MySQL. I clicked several of the other headings but not MySQL and I paid the price - ignorance. Please accept my apologies.


This goes with what I'm saying that the learning curve is steep. How's a newbie to know?

There is a learning curve, but that is what and other forums are for. We've all been there.  It's hard for me to gauge a user's expertise and level or experience (you can know plenty about Linux for instance, but still nothing about mythtv), so I don't always know how specific I need to be, but that's why I offered two ways of doing it.

You may find it frustrating but mythtbuntu has made things a lot easier than they used to be. I don't use mythtbuntu (I install mythtv on top of ubuntu) - but from what I've seen it's as easy as it gets. The best thing to do is to ask a few questions before getting started. Mythtv is highly complex in ways most users don't know, because few users use all of its features. This flexibility and # of features can make setup complicated and have a steep learning curve. there are some good setup guides out there and for newbies I recommend reading through those, the wikis, and asking questions before trying to set it up.

This forum can help you through 90% of the problems.

---

### Post by nickrout on 2011-01-24
> **nhtrader said:**
> nickrout, 



I'm in the camp of asking for help right away rather then spending 6+ hours googling for each thing. In the end, this approach will help document what was unclear, non-intuitive, problematic, etc.

I appreciate that you can muck around a lot on a myth system, buggering it complaetely.

But the setup instructions are pretty intuitive to find:

[www.mythtv.org](www.mythtv.org)

Click on "Support" then "Documentation"

Also [http://www.mythbuntu.org/support](http://www.mythbuntu.org/support)

Actually the pdf that used to be the mythbuntu install instructions seems to have disappeared - too much a moving target to maintain I suspect.

---

### Post by madam on 2011-01-25
You can extend a helping hand towards a card tuner expert.

[VPS Hosting](http://www.hostv.com/)

---

### Post by nhtrader on 2011-01-25
nickrout,

thanks for more links.

Here's another usability question that probably should go into another topic, but since there are a few experienced users in this topic...

Does anyone know where I should look to learn how to jump between MythTv and ubuntu without exiting MythTV?
Where are the keystroke shortcuts listed?
Is it possible to press a combination of keys to create a smaller window containing MythTV? 
Can MythTV exist in a window on the ubuntu desktop?

---

### Post by newlinux on 2011-01-25
> **nhtrader said:**
> nickrout,

thanks for more links.

Here's another usability question that probably should go into another topic, but since there are a few experienced users in this topic...

Does anyone know where I should look to learn how to jump between MythTv and ubuntu without exiting MythTV?
Where are the keystroke shortcuts listed?
Is it possible to press a combination of keys to create a smaller window containing MythTV? 
Can MythTV exist in a window on the ubuntu desktop?


Alt-Tab switches between running applications. If there aren't any running It won't switch. In Gnome (ubuntu) Ctrl-Alt-d will show the desktop, or you could use a virtual desktop and do Ctrl-alt-<arrow> where arrow is left, right, up, or down depending on how your virtual desktops are set up. Don't know where these are listed, but if you are running Gnome then googling should get you there. If you are running XFCE (mythbuntu default) then I'm not sure what the keyboard shortcuts are but google will get you there, and the ones I posted above might still work.

Not sure about a combination of keystrokes that will create a smaller window without writing up a script but you can start mythfrontend from a terminal and specify the geometry, or there is a setting in mythfrontend that determines the geometry and window mode (probably in appearance).

From terminal:

```
mythfrontend -geometry 1024x768
``` lets you specify the geometry (substitute your own values for 1024x768 ). then you can use the Ctrl-Click to move the window around even if it doesn't have a title bar.

```
mythfrontend -w
``` will put it in windowed mode.
```
mythfrontend -nw
``` for explicitly specifying non windowed mode.

```
mythfrontend -geometry 800x600 -w
``` will make it an 800x600 windowed app.

```
mythfrontend --help
``` will give your more info.

---

### Post by nhtrader on 2011-01-25
many thanks. 

At least I now know that I can't reduce its size while it is running.

As for the other keyboard commands, most helpful.

---

### Post by newlinux on 2011-01-25
I believe if you change the setting in the frontend it will restart mythfrontend on its own with the new settings - so that is sort of like changing it when it's running :)

best wishes.

---

### Post by larsolav on 2011-01-25
Another key combination that may be helpful when running the frontend and you have no other applications running (so Alt-Tab won't work as newlinux said) is _Ctrl-ESC_. That pops up the applications menu and you can from there select another application, such as f. ex. terminal. Then you can Alt-Tab between the terminal and the frontend

---

### Post by myth01 on 2011-01-25
I use Alt-F2 which brings up the 'Run Application' window, you can then alt-tab to that.  Different ways to cut the cake as they say.

As for the learning curve, it is indeed steep but well worth climbing.  I actually prefer to spend those 6 hours googling as I generally end up learning more along the way.  But to each their own.

The thing I love about mythtv and Linux in general is that you can actually test it to destruction as re-installing is easy and fast.  I've learnt so much more from re-installing multiple times that my production myth box was a breeze to setup and I'm confident making changes to it.  It helped me to look at the first installation as an experiment, not in any way intended to become permanent.  It lasted that way for 10 months before I setup the proper box.

Keep at it, and keep asking questions.  I still do.  It really irritates me the guys who just b1tch and moan about how mythtv isn't 'ready' for release and that the developers should halt all progress and fix it.  I just remind myself that it is free, and a damn sight better than any other offering, paid or otherwise.

:)

---

### Post by nhtrader on 2011-01-25
thanks to all for your helpful suggestions.

I'm now slugging it out in another topic.. trying to get my tuner card Hauppauge HVR-1250 to work. I'm almost there thanks to those helping me in that thread.

I hope to get this up and running by the end of the day. Thanks to all.

---

