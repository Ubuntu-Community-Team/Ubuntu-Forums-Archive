---
title: "Remote Desktop"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by RadioDave_FM on 2010-11-09
Greetings.

I've been an Ubuntu user now for the last 2 years, and I use it for all my photography, videography, and sound editing needs.  This is my first time posting to the forum.  Mainly, because I tried searching the forums and google, and I can't find what I'm looking for.  

I know there are various options to doing the remote desktop, and it is super easy from what I understand to set it up on the network at home.   

Here's my set up: I have a AMD Quad-core processor desktop with 8gb ram that is my main production PC.  My wife also uses it for her schoolwork for her goverment and German classes and also likes jump on Facebook.  I use it for Facebook and production use.  I also have an ancient laptop running LXDE flavored Ubuntu.  The specs on the laptop are 768mb ram and 1.3GHZ AMD-XP processor.  

What I would like to try to do with remote desktop is too either 1) Log on as another user while my wife is working on her schoolwork or 2) Log on as the same user, but use a different desktop space, so we're not interfering with each other's work.  Are there any suggestions that I could set up my remote log-in as such where either one would work.  

Oh, I'm running Ubuntu 10.04 on both machines.  

Thanks for any suggestions. BTW.

---

### Post by cgb on 2010-11-09
I typically use nxserver for remote connections.  This will allow you to connect as a new x-session so that you will not interfere with anyone else currently logged into the machine locally..  Some instructions I found are below.  

[http://ubuntuforums.org/showthread.php?t=941530]("http://ubuntuforums.org/showthread.php?t=941530")

---

### Post by CharlesA on 2010-11-09
FreeNX would work fine for that.

---

### Post by RadioDave_FM on 2010-11-09
Thanks, I'm trying NXMachine right now, and I'm following the step by step instructions.

---

### Post by RadioDave_FM on 2010-11-10
Okay, I gave it a try last night, and it works amazingly well.  What I need to figure out now is how to port the audio completely off the desktop and on to the laptop.  I tried the enable media support in the Environment options (at least that's where I think it was, I'm trying to do this from memory as I'm at work now).  Still no go...any other ideas?

---

