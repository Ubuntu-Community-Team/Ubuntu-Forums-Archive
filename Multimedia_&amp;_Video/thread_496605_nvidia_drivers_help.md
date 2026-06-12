---
title: "nvidia drivers help"
date: 2007-07-09
forum: Multimedia &amp; Video
---

### Post by MightyGaz on 2007-07-09
Hi folks, 

OK from the begining.  i've just installed feisty, and have never used any form of linux before.  so any answers here, please explain it to me like i'm an idiot!  

here's the problem.  i installed, updated and what not, then tried to install the nvidia driver as a prelude to maybe doing some gaming at some point.  i rebooted as required, but upon rebooting, when i get to the login screen, i get a black screen.  more accurately, the screen turns off.  

For the record, this is a dell inspiron 8200 with a geforce 440mx go.  

its as if i had pressed the power button on the monitor on a desktop.  i can log in if i type my user name and password as i can hear it logging in, i just cant see anything.  

Now, my problem is that being clueless as i am, my only method of fixing this was to reinstall feisty. 

so i suppose my question is is there a way to switch off the nvidia driver and go back to the default from the recovery whats its name thing? i'm gonna try again, but would like a method of fixing the problem if it happens again that doesnt involve a full OS reinstall.  

anyone got any help for the idiot who hasnt got a clue what he's doing?? 

Cheers!

---

### Post by dreadlord_chris on 2007-07-09
> **MightyGaz said:**
> Hi folks, 

OK from the begining.  i've just installed feisty, and have never used any form of linux before.  so any answers here, please explain it to me like i'm an idiot!  

here's the problem.  i installed, updated and what not, then tried to install the nvidia driver as a prelude to maybe doing some gaming at some point.  i rebooted as required, but upon rebooting, when i get to the login screen, i get a black screen.  more accurately, the screen turns off.  

For the record, this is a dell inspiron 8200 with a geforce 440mx go.  

its as if i had pressed the power button on the monitor on a desktop.  i can log in if i type my user name and password as i can hear it logging in, i just cant see anything.  

Now, my problem is that being clueless as i am, my only method of fixing this was to reinstall feisty. 

so i suppose my question is is there a way to switch off the nvidia driver and go back to the default from the recovery whats its name thing? i'm gonna try again, but would like a method of fixing the problem if it happens again that doesnt involve a full OS reinstall.  

anyone got any help for the idiot who hasnt got a clue what he's doing?? 

Cheers!

When you get to that blck screen - press Alt-F1 - this will bring you to a text-mode login. Log in. Now enter:
```

sudo dpkg-reconfigure xserver-xorg

```
leave everything as is **except** when it asks for the *driver* - choose **vesa**. Tell it to save the file at the end.
Now enter:
```

sudo /etc/init.d/gdm restart

```
You should have your GUI back again...

---

### Post by MightyGaz on 2007-07-09
ok, just to confirm, pressing Alt-F1 will reactivate my screen?  sorry if this is a silly question, i just want to avoid another reinstall from scratch.

---

### Post by MightyGaz on 2007-07-09
nope, didnt work.  the drivers that is.  and pressing Alt-F1 to open a text login didnt work either.  had to boot into recovery mode and enter those commands there.  also had many questions to set, everything from video to mouse, type of card, type of monitor, i was expecting questions about the style of underwear i was wearing! 

either way, doesnt work.  

anyone have any advice on trying to get this driver to cooperate? 

Cheers

---

### Post by dreadlord_chris on 2007-07-09
so, you chose **vesa** at the driver section and it didn't work?
if Alt-F1 doesn't work try Control-Alt-F1 to get to a console

---

### Post by MightyGaz on 2007-07-09
> **dreadlord_chris said:**
> so, you chose **vesa** at the driver section and it didn't work?
if Alt-F1 doesn't work try Control-Alt-F1 to get to a console

cant get the console up under any circumstance once the screen turns off.  and sorry, yes, reconfiguring and selecting vesa brings the screen back, but it doesnt achieve getting me a driver working with 3d acceleration. 

i've got hold of a driver from the nvidia site.  trying to install it but i think its become sentient and is now just taking the piss out of me.  

first, it doesnt like running alongside the x server.  fine.  i reboot into recovery mode and from the command prompt run the thing.  says i'm running on level 1 (or something to that effect, cant remember the exact term) and i should "initlevel3" or something like that as it would be better.  something to do with a daemon and making things easier for the installer.  sorry for the vagueness, this is driving me insane!  i'm hoping you get the idea here.  well i did that, it took me back to the graphical log in screen.  reboot again, ignore that warning.  and it doesnt work.  reason why escapes me, gonna go through it again and will come back and post why.

---

### Post by MightyGaz on 2007-07-09
ok, update.  was runlevel 1 i was on about earlier.  thing itrs complaining about now is that there is no precompiled kernel module i think.  asked if i wanted to download one, none of those either.  do i want to make one, well yes i do.  but it wont do that either lol apparently i've no libc header files.  i've to download the libc developement package.  now as i stated earlier, when it comes to linux i'm about as clued up as goats are on nuclear physics.  

can someone please save my sanity and explain whats going on here?  i am learning, and dont intend to be as big a pain for long lol  but if i cant make this driver install i may unspool entirely! 

thanks in advance for any advice!

---

### Post by Scotty1982 on 2007-07-09
have you tried going back to where the command prompt was working and entering:  nvdia-xconfig   ? that's how i get my nvidia card to work in linux. you have to be root though, so either log in as root, or type:  su   then when asked for the password enter it then type:   nvidia-xconfig  .

also if you haven't set up a password for root, log in and enter:   sudo passwd root   then it'll ask you to enter a new password.

hope you get it working.

---

