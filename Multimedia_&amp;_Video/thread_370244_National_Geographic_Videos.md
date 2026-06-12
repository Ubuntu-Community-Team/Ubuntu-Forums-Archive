---
title: "National Geographic Videos"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by mhenriday on 2007-02-25
With a little fiddling, I can manage to play videos from most sites, but ***National Geographic*** leaves me stymied. I've downloaded just about everything available in the video/multi media line from the Package Manager and/or Automatix 2, but no go : when I click on a ***NG*** video, i get a message saying «no video» in the pane where the video should play. What am I doing wrong ?...

Henri

---

### Post by chewearn on 2007-02-26
I have no problem with my ubuntu 6.10 system.  I see the National Geography is using flash video.  Did you install flash plugin for your Firefox?

---

### Post by mhenriday on 2007-03-05
**AstalaVista**, I was unable to find a flash plug-in for **Firefox** on the **Mozilla** site, so the first thing I did was to check my Package Manager to see if, as I thought, I had installed the flash programmes provided there. I found that **flashplayer-mozilla 6.0.79-0.2**, **mozilla-plugin-gnash**, and **swf-player 0.3.6-2ubuntu2** were indeed all installed. As despite this my troubles persisted, I then went to **Adobe**'s site, from which I downloaded the **9,0,31,0 tar.gz** to my desktop. I then followed the very clear installation instructions with the following result in my terminal :

[INDENT]Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 9 will be installed in your home directory.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.

NOTE: Please exit any browsers you may have running.

Press ENTER to continue...

----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/mhenriday/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.[/INDENT]

I then used the about:config command to take a look at the **Firefox** components directory, but was uable to locate any **xpti.dat** file there to remove. I'm still having the same problem with **NG** videos and, e g, with **NASA** videos as well. For example, if I try to watch the video of Cassini crossing Satrun's rings ([http://www.nasa.gov/mpg/170640main_pia08356-movie.mpg)](http://www.nasa.gov/mpg/170640main_pia08356-movie.mpg)), I get that «no video» message, which I find very odd, given that I have Real Player 10 installed. Any idea as to what I'm doing wrong ? I very much hope that these kinds of difficulties will be fixed in the **Feisty Fawn** release scheduled for next month ; I understand that I'm not unique in my problems with viewing videos and that these have been solved in the **Freespire** distro, which is based on **Ubuntu**....

Henri

---

