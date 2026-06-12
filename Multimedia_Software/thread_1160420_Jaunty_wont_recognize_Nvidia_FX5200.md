---
title: "Jaunty wont recognize Nvidia FX5200"
date: 2009-05-15
forum: Multimedia Software
---

### Post by Elitegroup on 2009-05-15
Hi all,
 I am a absolute newbie here but so far this forum has been very helpful. I have a very serious problem here and couldn't find solutions anywhere so i decided to post it.
  Jaunty does not recognize my card under the 'Hardware Driver' section but when I use Live CD i can totally see and update it. But then it asks me to restart and when i boot into jaunty i couldn't see the driver anymore. If i reboot in Live CD i see the driver but it asks me to activate it again. 

When i first tried to install XP and Jaunty together, I was able to install the driver in live CD and and when i restarted i got some errors which i cant remember exactly but i somehow successfully navigated through the errors and got the driver working. But i just want ubuntu in my so i reformatted and couldnt find the driver after that. :sad:.

I have tried the driver manual installation but i cant get past the X server warning. hope you guys can help me out. thank you.

---

### Post by ofb on 2009-05-19
Okay, first thing: unless I miss-read you, you have a misapprehension. When you say you update the driver with the LiveCD, that doesn't actually happen.

The LiveCD is an entirely separate Ubuntu from the one installed on your harddrive.

In the LiveCD session, you can detect and download the driver for the 5200, but you have to restart to finally enable it.

Catch-22 is that when your restart a LiveCD session, your old session is entirely gone, and the new session doesn't know anything about that driver you wanted.

It's doesn't do that to make you crazy. It's just a LiveCD is a fully functional Ubuntu session. If you install something that doesn't require a reboot, it'll install and work, as long as you have enough space in your RAM. But it won't be there next time you start the LiveCD again. Nothing is remembered between boots.

Back to your harddrive-installed Ubuntu, I'm not sure what the trouble is. What exactly happens when you go System -> Administration -> Hardware drivers? Perhaps give us a screenshot.

**
I must add I'm not having good luck with FX5200 in Jaunty here. With the recommended 173.x restricted driver, I only get about half the framerate I should. 

Backstory is that a while ago Nvidia dropped support for legacy hardware in its drivers. That's been improved a little since, but FX5200 support still appears bad. You may be better off upgrading to a newer or at least different card, than fighting with this one.

---

