---
title: "NVIDIA XServer Settings : Black Screen of Death"
date: 2010-12-11
forum: Multimedia Software
---

### Post by randomblink on 2010-12-11
Losing my mind here.
I had Ubuntu 10.04 running fine.
Then I got curious about NVIDIA XServer.

"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]" - Video Card

I opened it up, clicked a settings change, and said OK.
It said you need to update your blah blah blah.
Then it said blah blah blah doesn't exist.
Then it said it would create it for me.
Then I said REBOOT!

Now I get a black screen of death.
The only way I can get anything to happen on my monitor that comes from this computer is to boot into the Install Disk and say "TRY UBUNTU".

WTF?!

Can anyone point me in a direction that might help????

---

### Post by randomblink on 2010-12-11
screw it.
I am really starting to hate Linux.
The learning curve is fricking WAY up there.
I've picked up three programming languages over the last year, and complete about 6 or 7 college course, but getting Ubuntu 10.10 up and running without a glitch is apparently fricking beyond me...

Way frustrated...

I'm in the middle of wiping the drive and starting over.
I will never touch the NVIDIA XServer garbage again.
I had everything running just fine for two weeks until this...

Completely locked out... ridiculous.
And being able to get to the files through the CD "Try Ubuntu" option but NOT BEING ABLE TO FIX THE CHANGES??!?!?!?!

I consider myself an advanced computer user... In my opinion, Linux will continue to remain a fringe OS until things like this are fixed. I've NEVER been locked out of Windows or my Mac because of a single change...

Ridiculous...

---

### Post by amsterdamharu on 2010-12-11
If you get the black screen can you press control + alt + F1 to go to another tty? You should get a login prompt (non graphic).

After logging in you can try the following command:
```
sudo service gdm stop
sudo rm /etc/X11/xorg.conf
sudo service gdm start
```

Another way to try is use the "recovery mode" from the startup menu (press shift during bootup if you can't see it). Then those commands when you get to a prompt.

---

### Post by chewearn on 2010-12-11
A friendly word of advice to keep in mind next time:
Don't install nvidia driver when you have ati graphics card.

:popcorn:

---

### Post by Gato303co on 2010-12-14
Hello, I would like to ask a similar situation:  When I installed Ubuntu 10.04 now upgraded to 10.10, I installed it on my PC with a AGP 8x video card (nVidia),  It worked pretty well.
But now my video card died, had to remove it and work with the integrated - OnChip video card (VIA UniChrome).  So I basically made a hardware change.  And like Amsterdamharu, I got a black screen when I got prompted "casa login" and then password.  I can't get through this stage, I try to login but I got error message "login incorrect", and I don't know if recovery mode would be the solution, since I hid that option from the Grub 2 menu.  I will thank any help

---

### Post by Mad_Sunday on 2010-12-14
> **chewearn said:**
> A friendly word of advice to keep in mind next time:
Don't install nvidia driver when you have ati graphics card.

:popcorn:

Now that's funny, cruel, but funny. I think the comment "blah blah blah doesn't exist" was telling. rofl.


quote.....
I consider myself an advanced computer user... In my opinion, Linux will  continue to remain a fringe OS until things like this are fixed. I've  NEVER been locked out of Windows or my Mac because of a single change...[COLOR=Black]

Nvidia drivers with an ATI card works in Windows and Mac systems, that's truly amazing ;-)

 
[/COLOR]

---

### Post by amsterdamharu on 2010-12-14
[@Gato303co]("http://ubuntuforums.org/member.php?u=896676")
Can you press control + alt + F1 (or F2) and log in?

"Login incorrect" is what you get when the user name or password is wrong, just try again. I think the user name is case sensitive and the password is case sensitive for sure.

---

