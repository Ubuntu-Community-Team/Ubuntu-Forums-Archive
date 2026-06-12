---
title: "[SOLVED] Why is Flash not working ?"
date: 2008-11-25
forum: Multimedia Software
---

### Post by Linux4theWin on 2008-11-25
I am getting sick of this. 
The thing is that I have being using Ubuntu now for some time. 
But i have never got flash to work.  
Well it can play YouTube videos on the internet but thats it!
YouTube is the only flash video thing that i am able to play. 
Well at least i always get in trouble playing something else. 
I have a "no sound" problem with YouTube flash and it it just not working well. 
I have been using Google. . Yes i have and i have tried it all. 
Nothing works. . 
It always gives me the same or similar problem.  
I have tried a couple of browsers but no.  Not working. 
The flash player that i have been using is flash player 10 

Am i the only one heaving this big flash problem with Ubuntu ?

---

### Post by Therion on 2008-11-25
You don't mention what version of Ubuntu you're using but you're using the Adobe plugin to handle Flash, correct?

Have you checked to see if you still have Gnash player installed?  Search for it using Synaptic and, if it's installed, remove it; leaving the Adobe plugin as the sole plugin installed for Flash duty.

---

### Post by gandaran on 2008-11-25
> I have a "no sound" problem with YouTube flash and it it just not working well. 
for the no flash videos sound problem you have to fix pulseaudio, see this thread [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
can you post the link where flash doesn't work?

---

### Post by Linux4theWin on 2008-11-25
> **Therion said:**
> You don't mention what version of Ubuntu you're using but you're using the Adobe plugin to handle Flash, correct?

Have you checked to see if you still have Gnash player installed?  Search for it using Synaptic and, if it's installed, remove it; leaving the Adobe plugin as the sole plugin installed for Flash duty.

Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

yes i am using Adobe plugin. 

I checked for Gnash but it is not installed.

sorry for my bad english but ,What does
"leaving the Adobe plugin as the sole plugin installed for Flash duty." mean ? 

> **gandaran said:**
> for the no flash videos sound problem you have to fix pulseaudio, see this thread [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
can you post the link where flash doesn't work?

I can hear sound from youtube if i have no musicprogram playing sound, even if i have mute turned on.
Like songbird and programs like that.
The instructions on the site you gave me . . they are not working well.

"bjarni@Linux-320i:~$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
cp: cannot stat `/home/bjarni/.asound*': No such file or directory
"

---

### Post by gandaran on 2008-11-25
> The instructions on the site you gave me . . they are not working well.

"bjarni@Linux-320i:~$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
cp: cannot stat `/home/bjarni/.asound*': No such file or directory
it says on the thread not to worry if you don't have these files, just read the thread carefully first

---

### Post by cariboo on 2008-11-25
Type about:plugins in firefox's address bar and check what version of flash you are running. I get this:

   ```
 File name: libflashplayer.so
    Shockwave Flash 10.0 d20
```

when I type the above command.

Jim

---

### Post by Linux4theWin on 2008-11-25
> **gandaran said:**
> it says on the thread not to worry if you don't have these files, just read the thread carefully first

I followed the steps.  
The problem is still the same. 
Well i can look at the video at youtube.  But no sound.
here is my about:plugin in the flash section.
[IMG]http://i38.tinypic.com/ego7rm.png[/IMG]

Here is my settings in firefox
[IMG]http://i38.tinypic.com/ealgfl.png[/IMG]

And allso. 
lot of flash object have this annoying gray "play botton" on them at first.

---

### Post by gandaran on 2008-11-25
you have two flash packages installed, adobe flash and swfdec flash, you need to remove the swfdec, open synaptic package manager scroll down to mozilla-swfdec-plugin. mark for complete removal and click the apply button
about the flash sound problem,  you can find many fixes here on the forum but I think that link is the best and easy to follow, search for others if you like

---

### Post by Linux4theWin on 2008-11-25
> **gandaran said:**
> you have two flash packages installed, adobe flash and swfdec flash, you need to remove the swfdec, open synaptic package manager scroll down to mozilla-swfdec-plugin. mark for complete removal and click the apply button
about the flash sound problem,  you can find many fixes here on the forum but I think that link is the best and easy to follow, search for others if you like

I did what you said.
Now sound and video is working and i am not seeing this stupid play botton anymore.
May God bless you whether you are Christians, Hindus, Muslims, or Buddhists, ...
And you all.  
That helped me here.  
tanks alot.
I was going to start using windows if i would'nt be able to get help :S . .

---

