---
title: "No Sound on thinkpad T530"
date: 2012-10-18
forum: Multimedia Software
---

### Post by Ben2r25 on 2012-10-18
I just got a new Thinkpad T530 and put ubuntu 12.10 on it (64-bit) Everything seems to be working fine except for the speakers (headphones work if they are plugged in) Ubuntu says the sound is all the way up. In the terminal, alsamixer confirms this. Any ideas?

---

### Post by edm1 on 2012-10-19
I have the same problem on my Thinkpad X230. But strangely, can hear the drums when lightdm loads.

I think [this could be the same problem]("https://bugs.launchpad.net/ubuntu/quantal/+source/linux/+bug/992087").

---

### Post by Simanek on 2012-10-20
Same here with my T530. It worked for a little while after installing the Audio Team Developer Driver: [http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/) but after booting up this morning I am back to no audio out of the built-in speakers, but audio works fine with headphones.

@edm1 Thanks for the link.

UPDATE: I see a comment on that bug ticket you linked to stating that the bug is specifically for the Vostro 3450. So I created a new bug ticket for ThinkPad T530 (would make sense if it included ANY ThinkPad running the Intel chipset): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1069114](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1069114)

---

### Post by bubukind on 2012-10-20
Same here, but on a Dell XPS 15z.
Also found this:
[http://ubuntuforums.org/showthread.php?t=2063728](http://ubuntuforums.org/showthread.php?t=2063728)

And already tried all the approaches there to no avail.
So far I have:


[LIST]
[*]No Sound from internal speakers
[*]Headphones work finde
[*]Muting/unmuting does not change situation
[*]selecting/reselecting audio source does not help
[*]restarting alsa does not help
[*]killing pulse (which seems to automatically restart it) does not help
[*]restarting pc will sometimes work
[*]sound does not work after resume
[/LIST]

---

### Post by bawss on 2012-10-20
Same with my X230. Headphones work fine, but the speakers do not. Most of the time the speakers just flat out don't work, but sometimes after restarting they do, and then die after the computer goes to sleep and wakes.

edit: just installed xmonad and I'm no longer using unity. The sound situation has now reversed. Only sound through the internal speakers works..

---

### Post by Simanek on 2012-10-22
Hi! 

I actually got a helpful response on this ticket:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1069114](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1069114)

After installing the upstream kernel as Joseph Salisbury described my built-in speakers and headphones work again! Hopefully this will solve your problems also.

---

### Post by edm1 on 2012-10-23
Kernel v3.7-rc2 fixed my sound but caused frequent freezes for me. I have downgraded to 12.04 for now. 12.10 didn't really have any new features I wanted anyway.

---

### Post by mafi127 on 2012-11-05
Got the same problem.  headphones work just fine. I did reinstall my ubuntu and now sound is gone.

---

### Post by ntzrmtthihu777 on 2012-11-28
[FONT=Courier New]Different machine, similar issue. just thought I would put in my 2 zenny.
Sound just stopped working, noticed when I was trying to play a .wav in audacity. No sound, sound settings showed no form of output or input, whether or not headphones or mic was plugged in.
I killed pulseaudio via system monitor, and it restarted and all sound worked fine.
[/FONT]

---

### Post by Mikeb85 on 2012-11-28
Some kernels seem to have issues with sound...  I had problems with several 3.6 kernels.  The 3.7 kernels seem to have fixed the sound issues, 3.7 rc7 has been good to me.

I'm also on a T530 btw...

---

### Post by nibot on 2013-01-21
I'm having the same problem, on a Thinkpad T410.

Sound worked fine until December 2012.  Not sure what prompted the failure.  Since then I've updated to Ubuntu 12.10 and it remains a problem.

In Ubuntu: no sound from the speakers, but the headphones work fine.

What is strange is that I am ALSO having sound problem when I dual-boot into Windows.  There the speaker audio works *intermittently*.  The sound will come on for a few seconds after I change the volume using the +/- buttons above the keyboard, but then it stops working again.

---

### Post by nibot on 2013-01-24
It turns out that doing "killall pulseaudio" is a (temporary) fix.  If I kill pulseaudio and then use the command line speaker-test program, it *works*.  

Found here: [http://askubuntu.com/questions/132577/no-sound-in-ubuntu-12-04](http://askubuntu.com/questions/132577/no-sound-in-ubuntu-12-04)

Next question: what's wrong with pulseaudio?

---

