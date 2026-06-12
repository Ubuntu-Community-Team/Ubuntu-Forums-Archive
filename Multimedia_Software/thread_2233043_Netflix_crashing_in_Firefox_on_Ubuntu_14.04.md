---
title: "Netflix crashing in Firefox on Ubuntu 14.04"
date: 2014-07-05
forum: Multimedia Software
---

### Post by mcweb2 on 2014-07-05
Hi folks,

I'm new to Linux so bear with me. I installed Ubuntu on to an older system that will just be used to watch Netflix, YouTube and possibly surf the web.

[LIST]
[*]Intel Core 2 CPU 6400 @ 2.13 Ghz
[*]3.25 GB DDR RAM
[*]ATI Radeon Sapphire X1950 Pro Graphics Card
[*]500 GB Seagate Barracuda Hard Drive (the hard drive has an issue, we have to press "enter" when Ubuntu is loading but we won't be saving anything to it)
[/LIST]
 
I then followed this [YouTube video]("http://youtu.be/Fx7X79Arvlc"), which directed me to install Pipelight, enable Silverlight and add the User Switcher to Chrome. This didn't work for me but I found another [page on the Pipelight site]("https://answers.launchpad.net/pipelight/+faq/2351") that suggested using Firefox and adding the Add On, User Agent Overrider 0.2.4. And changing the user agent to 

Firefox 15/Windows: Mozilla/5.0 (Windows NT 6.1; WOW64; rv:15.0) Gecko/20120427 Firefox/15.0a1

Then selecting the option "Firefox 24/Windows" from the User Agent Overrider tab in Firefox.

This worked for me. Firefox loaded Netflix and played my movie full screen. The problem is it only lasted about 4 minutes before the picture froze. The sound kept playing, my mouse could move, but nothing on the window was clickable and the keyboard didn't work. I had to manually turn off the computer and turn it back on. 

I have since tried the following user agents:
[LIST]
[*]Firefox 26/...
[*]Firefox 15/...
[/LIST]

Unfortunately they all crash after approximately 5 minutes. I really need to get this working, my natives are getting restless does anyone have any other ideas I can try?

---

### Post by yancek on 2014-07-05
Which Ubuntu release are you using, 14.04 or earlier?  What version of firefox do you actually have installed?  I have firefox 29 on 12.04 and use it on Netflix.  I tried User Agent Switcher but for some reason, I could not play Netflix.  I installed the User Agent Overrider and also use Firefox 24/Windows and am able to play full movies.  Go to the pipelight diagnostic site below and select your plugin.  See if you get any error messages.  If it is installed correctly, you should just see OK for the different options.

[http://fds-team.de/pipelight/](http://fds-team.de/pipelight/)

Chrome version 34 and higher will not work.  Other than seeing what the diagnostic says, perhaps upgrading firefox would be an option if it is an older version.

---

### Post by SeijiSensei on 2014-07-05
I'm guessing the video card isn't up to decoding HD video.  Are you using the proprietary driver?  

Cards of that vintage do not have hardware decoding for H.264 streams, which I'm pretty sure Netflix uses.  So all the decoding has to take place in the CPU.  Try opening a terminal and running the program "top".  Leave it open while you start up Netflix.  Does it pin the CPU at 100% or close to it?  Hit the "1" key to see both cores.  How're they doing?

What if you turn off HD in the Netflix player?  Any better?

---

### Post by mcweb2 on 2014-07-06
Finally I think I have fixed the problem!

Thank you so much for your help guys. But I think it's just a simple fix, tonight anyway. 

I went into the Ubuntu Settings and selected the Security & Privacy icon. [INDENT]Under the first tab 'Require my password when:' I un-clicked both 'Waking from suspend' and 'returning from blank screen' then I changed 'if screen has been blank for' to '1 hour'. Then returned to All Settings.

Next I selected the Power Icon and under 'suspend when inactive for' I changed it to '2 hours'.
 [/INDENT]

I'm sure I don't need all of these changes but the movie is playing and it's not crashing my system. I'm going to bed. But I will definitely look into both your posts as well tomorrow. Thank you!

---

### Post by mcweb2 on 2014-07-06
Rats I played that movie for 30 minutes last night with no problem. This morning it's back to crashing after 1-3 minutes. Back to the drawing board. I did try playing it in full screen and not in full screen, they both crashed. I also unchecked sharing info with conical in the security tab but it still crashed. So I have reversed all the changes I made in my last post. I will now move on to Testing the first reply above from yancek.

---

### Post by mcweb2 on 2014-07-06
Thanks for taking the time to help me. 


To answer your questions:
Ubuntu 14.04
Firefox 30.0-build 1-0ubunto0.14.04.3


Pipelight Diagnostic:
User agent okay
Silverlight 5.1 okay
Result okay

I'm going to switch over to SeijiSensei message now and do the CPU test before I try changing the user agent and Firefox version.

---

### Post by mcweb2 on 2014-07-06
> **yancek said:**
> Which Ubuntu release are you using, 14.04 or earlier?  What version of firefox do you actually have installed?  I have firefox 29 on 12.04 and use it on Netflix.  I tried User Agent Switcher but for some reason, I could not play Netflix.  I installed the User Agent Overrider and also use Firefox 24/Windows and am able to play full movies.  Go to the pipelight diagnostic site below and select your plugin.  See if you get any error messages.  If it is installed correctly, you should just see OK for the different options.

[http://fds-team.de/pipelight/](http://fds-team.de/pipelight/)

Chrome version 34 and higher will not work.  Other than seeing what the diagnostic says, perhaps upgrading firefox would be an option if it is an older version.

Thanks for taking the time to help me. 




To answer your questions:
Ubuntu 14.04
Firefox 30.0-build 1-0ubunto0.14.04.3




Pipelight Diagnostic:
User agent okay
Silverlight 5.1 okay
Result okay


I'm going to switch over to the  SeijiSensei message now and do the CPU test before I try changing the user agent and Firefox version.

---

### Post by mcweb2 on 2014-07-06
> **SeijiSensei said:**
> I'm guessing the video card isn't up to decoding HD video.  Are you using the proprietary driver?  

Cards of that vintage do not have hardware decoding for H.264 streams, which I'm pretty sure Netflix uses.  So all the decoding has to take place in the CPU.  Try opening a terminal and running the program "top".  Leave it open while you start up Netflix.  Does it pin the CPU at 100% or close to it?  Hit the "1" key to see both cores.  How're they doing?

What if you turn off HD in the Netflix player?  Any better?

Hi SeijiSensei, thanks for the help.

I haven't loaded any extra drivers for the card just whatever Ubuntu loaded. Should I? Any idea where to get them?

I ran the CPU test, the first line "my pluginload+" went between 79% and 101% then everything crashed at 91.7%. The 2nd one was compiz it only went to 13%.

Then I ran the movie in Netflix turned off HD it lasted longer up to 4 minutes then crashed the CPU number for the plugin load+ was only at 57.4%.

---

### Post by mcweb2 on 2014-07-06
> **yancek said:**
> Which Ubuntu release are you using, 14.04 or earlier?  What version of firefox do you actually have installed?  I have firefox 29 on 12.04 and use it on Netflix.  I tried User Agent Switcher but for some reason, I could not play Netflix.  I installed the User Agent Overrider and also use Firefox 24/Windows and am able to play full movies.  Go to the pipelight diagnostic site below and select your plugin.  See if you get any error messages.  If it is installed correctly, you should just see OK for the different options.

[http://fds-team.de/pipelight/](http://fds-team.de/pipelight/)

Chrome version 34 and higher will not work.  Other than seeing what the diagnostic says, perhaps upgrading firefox would be an option if it is an older version.


Yey! I changed the User Agent Overrider to Firefox 24/Windows as you suggested and I was able to play the complete movie over an hour. So that is great. It did crash again after the credits were done. Not a big deal but I would like to fix it any ideas?

---

### Post by Rob Sayer on 2014-07-07
That card isn't supported in linux by ATI anymore.  It isn't even supported in Windows anymore.

Which means: don't mess with video drivers.  The proprietary driver you'd dfind in "additional drivers" (fglrx I believe) will bork your video.  The open source driver (radeon) is the one you should be using now.  Don't change that.

To check which driver is being used put this into terminal:

```
sudo lshw -c video
```

and enter your password.

Personally it's absolutely beyond me why the user agent string or suspend settings would have anything to do with this.  I think you're taking shots in the dark and misinterpreting any perceived change with different videos.

For a start, you have a video card with no 3D hardware acceleration capability in linux.  If you're using the Unity desktop version that's hamstringing you right off.  Unity (or cinnamon or any gnome 3 based DE) requires 3D accel just by itself.  Asking it to play videos too slows things down even if your gpu *does* have 3D accel.

For a dedicated video machine I'd use xubuntu or kubuntu and turn off all effects and compositing in xfce and kde.  Even with 3D acceleration.

You could simply install the kubuntu desktop or the xfce one, but I think reinstalling is better.

However, you are *not* going to be able to play HD video very well, period, on a machine without 3D acceleration.  No amount of fiddling is going to change that.  And as sites like youtube migrate more to HD with higher fps (like 60 or more), this is only going to get worse.

I think your best bet is to get a modern video card.  It wouldn't have to be for cutting edge gaming.  Just about any card would be better.

---

### Post by mcweb2 on 2014-07-07
> **Rob Sayer said:**
> That card isn't supported in linux by ATI anymore.  It isn't even supported in Windows anymore.

Which means: don't mess with video drivers.  The proprietary driver you'd dfind in "additional drivers" (fglrx I believe) will bork your video.  The open source driver (radeon) is the one you should be using now.  Don't change that.

To check which driver is being used put this into terminal:

```
sudo lshw -c video
```

and enter your password.

Personally it's absolutely beyond me why the user agent string or suspend settings would have anything to do with this.  I think you're taking shots in the dark and misinterpreting any perceived change with different videos.

For a start, you have a video card with no 3D hardware acceleration capability in linux.  If you're using the Unity desktop version that's hamstringing you right off.  Unity (or cinnamon or any gnome 3 based DE) requires 3D accel just by itself.  Asking it to play videos too slows things down even if your gpu *does* have 3D accel.

For a dedicated video machine I'd use xubuntu or kubuntu and turn off all effects and compositing in xfce and kde.  Even with 3D acceleration.

You could simply install the kubuntu desktop or the xfce one, but I think reinstalling is better.

However, you are *not* going to be able to play HD video very well, period, on a machine without 3D acceleration.  No amount of fiddling is going to change that.  And as sites like youtube migrate more to HD with higher fps (like 60 or more), this is only going to get worse.

I think your best bet is to get a modern video card.  It wouldn't have to be for cutting edge gaming.  Just about any card would be better.

Hi Rob I think you are probably right my card is pretty old. However since I changed to the Firefox 24/Windows user agent all is good. I was able to watch Netflix all of last night. So for now I won't change anything and just thank my lucky stars! Thank you for taking the time to reply.

---

### Post by mcweb2 on 2014-07-07
> **mcweb2 said:**
> Yey! I changed the User Agent Overrider to Firefox 24/Windows as you suggested and I was able to play the complete movie over an hour. So that is great. It did crash again after the credits were done. Not a big deal but I would like to fix it any ideas?

The crash at the end of the movie credits only happened once. I watched Netflix the rest of the evening without any problems. Many thanks to all the folks that helped me out.

---

