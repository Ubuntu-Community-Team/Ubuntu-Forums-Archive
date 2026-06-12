---
title: "lcdproc client question"
date: 2010-10-23
forum: Multimedia Software
---

### Post by toadleyb on 2010-10-23
I have been reading and playing for two days now trying to get my LCD display working on my Antec Fusion Black HTPC.

Here is where I am at.  Using the resources here and reading relentlessly I have LCDd and lcdproc installed.  I also have lirc installed and my remote and even volume knob work.

My problem is this.  The lcdproc client will only work if I run it in the foreground either by running lcdproc -f from terminal or if I change the Foreground=true in the lcdproc.conf file.  When I do this it works great.  If I run it in the background it does nothing.  I have tried it by running sudo LCDd -f -r 4 to run LCDd in the foreground to see what is happening.  When I do this and run lcdproc in the background it says "client on socket 5 disconnected".  If I run it with the -f flag everything looks fine.

I have also gotten the lcdproc-plugin for rhythmbox to work and it displays artist and title just fine on my LCD.

Once I get this sorted out how do I get lcdproc client to run at system startup?

I also do not understand how the menus are supposed to work.  I have the menu key set to "escape" in the LCDd.conf file.  How do I actually use the menus?

Thanks for any help anyone can give.  I am a newb to ubuntu (about 1 month of tinkering now)  I am running 10.10 on a Asus P7H55-M pro motherboard with a core i3 processor and 2 GB of ram.

---

### Post by toadleyb on 2010-10-24
Anyone?

---

### Post by mal205 on 2010-10-31
Don't know about why it won't run in the background, perhaps you could post the command your using. Have you checked to see if there's anything in the system logs?

As to starting LCDd and lcdproc on startup, I followed this post:

[http://ubuntuforums.org/showthread.php?t=664306]("http://ubuntuforums.org/showthread.php?t=664306")

Adding the link into rc2.d didn't work. Of course the link really needs to be added into every run level, including the shutdown and reset levels.
There's a tool to do that, described here:
[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/]("http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/")

Using the defaults added lcdproc in as process 20. But LCDd was installed as process 60, so lcdproc was started before LCDd, and so it didn't work. Added lcdproc as process 61 on the way up and 59 on the way down, now works.

I used the command  &#8220;sudo update-rc.d lcdproc defaults 61 59 &#8221;

Let us know how you go.

---

### Post by K_Light2003 on 2011-03-25
Just a thank you for the info on LCDproc. I got my LCD working after about 5 hours messing around. If anyone's looking to install LCDproc both server (LCDd) & client ( LCDproc) on 10.10 I have written up how I did it on my [blog]("http://linuxserver2011.wordpress.com/2011/03/25/getting-the-lcd-to-work-with-lcdproc/").   \\:D/

Thanks again.

---

