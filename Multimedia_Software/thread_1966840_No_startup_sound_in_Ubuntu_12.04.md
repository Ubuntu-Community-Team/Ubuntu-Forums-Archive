---
title: "No startup sound in Ubuntu 12.04"
date: 2012-04-27
forum: Multimedia Software
---

### Post by mgt2000 on 2012-04-27
I installed Ubuntu 12.04 yesterday on two different systems (32 & 64 bit) but none of them have startup (login) sound!!. Of course its beta 2 version didn't have startup sound neither. is it a bug or what is the problem?

I solved the problem by adding this startup item to the startup applications and now it works. I hope it can be useful for those who have the same problem.

Name: GNOME Login Sound
Command: /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
Comment: Plays a sound whenever you log in

---

### Post by Lamukra on 2012-04-28
> **mgt2000 said:**
> I installed Ubuntu 12.04 yesterday on two different systems (32 & 64 bit) but none of them have startup (login) sound!!. Of course its beta 2 version didn't have startup sound neither. is it a bug or what is the problem?

I solved the problem by adding this startup item to the startup applications and now it works. I hope it can be useful for those who have the same problem.

Name: GNOME Login Sound
Command: /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
Comment: Plays a sound whenever you log in

I have the same problem on 12.04 x64, dunno what it is, but I will try your solution. Thx

---

### Post by madnag4u on 2012-04-28
> **mgt2000 said:**
> I installed Ubuntu 12.04 yesterday on two different systems (32 & 64 bit) but none of them have startup (login) sound!!. Of course its beta 2 version didn't have startup sound neither. is it a bug or what is the problem?

I solved the problem by adding this startup item to the startup applications and now it works. I hope it can be useful for those who have the same problem.

Name: GNOME Login Sound
Command: /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
Comment: Plays a sound whenever you log in

Yep. I too had the same problem. There was no startup sound and when i checked the startup applications, there was no entry regarding Login Sounds. Will try your fix though.

---

### Post by Lamukra on 2012-04-28
It does work indeed like a charm, my favorite sound is back :) Thanks man!!!

---

### Post by chemtut on 2012-04-28
Thank you --- worked for me also

---

### Post by mgt2000 on 2012-04-28
> **madnag4u said:**
> Yep. I too had the same problem. There was no startup sound and when i checked the startup applications, there was no entry regarding Login Sounds. Will try your fix though.

You can use this command to show up all startup application again:

sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop

---

### Post by TedinOz on 2012-04-28
Yes it worked for me too...and the 'drum roll' is back also! Havin' a ball with Precise...it is brilliant! And well named :)

---

### Post by kadrlica on 2012-04-29
Looks like the login sound was removed by default:

[http://www.omgubuntu.co.uk/2011/12/ubuntu-12-04-login-sound-to-be-disabled-by-default/](http://www.omgubuntu.co.uk/2011/12/ubuntu-12-04-login-sound-to-be-disabled-by-default/)

---

### Post by Lamukra on 2012-04-30
THX kadrilica, nice nice to know, thought it was was mistake made!

---

### Post by MutantJohn on 2012-04-30
Ha ha ha, I was wondering about that too. Apparently it's supposed to be faster, eh? I haven't really noticed a difference, tbh.

---

### Post by wallaby34 on 2012-04-30
> **mgt2000 said:**
> I installed Ubuntu 12.04 yesterday on two different systems (32 & 64 bit) but none of them have startup (login) sound!!. Of course its beta 2 version didn't have startup sound neither. is it a bug or what is the problem?

I solved the problem by adding this startup item to the startup applications and now it works. I hope it can be useful for those who have the same problem.

Name: GNOME Login Sound
Command: /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
Comment: Plays a sound whenever you log in
Thank you VERY MUCH for that advice - it worked a charm !. I am one of the "old fashioned" weirdos who happens to like the distinctive Ubuntu login sound. Remember the old addage? "If it ain't broke, don't fix it" !!

---

### Post by rookcifer on 2012-05-01
I have the same issue, so it apparently is a bug.  I don't really care, though.  My big problem is my music will just stop playing at random times.  I will check syslog and see a bunch of Pulseaudio tracebacks.  I have no idea how to report those to the devs in any readable format.

---

### Post by rplantz on 2012-05-01
My Startup Applications already had the canberra-gtk-play command in there, but I still did not get a startup sound. I read in another post that somebody had to use the -V 5 option to turn the volume up. I tried that and it worked. But it was loud, so I changed it to 3. Did not turn the volume down. So I removed the -V 3 option (thus restoring the command back to its original value), and it still works. I guess I just needed to let it know that a human is here.

---

### Post by chromatica86 on 2012-05-01
Yes. It worked. Thanks. This has really been bugging me about 12.04:guitar:

---

### Post by Zakhafr on 2012-05-09
That does **NOT** work for me.

A hint could be that on a non-english Ubuntu, identifiers of files have been changed. Launching the command on a terminal, I get a "file not found" message.

Anyway I managed to get the same effect with a simpler command:
```
paplay /usr/share/sounds/ubuntu/stereo/desktop-login.ogg
```


About the reason of the suppression of this "feature"... I find it a pity. My desktop has a slow BIOS. The BIOS itself needs around 40sec for a "cold start" (when disk are stopped), prior it tries to boot any O.S.
So even if Ubuntu buts in less than 15 secs, it's still around a minute.
So, usally turn on the PC and do something else -for example change from my work clothes to my home clothes-, and the sound is nice to alert me that I can come back and start using the PC.

---

### Post by roelpaulo on 2012-05-12
> **mgt2000 said:**
> I installed Ubuntu 12.04 yesterday on two different systems (32 & 64 bit) but none of them have startup (login) sound!!. Of course its beta 2 version didn't have startup sound neither. is it a bug or what is the problem?

I solved the problem by adding this startup item to the startup applications and now it works. I hope it can be useful for those who have the same problem.

Name: GNOME Login Sound
Command: /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
Comment: Plays a sound whenever you log in

It worked for my 12.04! Thanks!

---

### Post by Tranlm on 2012-05-19
> **rplantz said:**
> My Startup Applications already had the canberra-gtk-play command in there, but I still did not get a startup sound. I read in another post that somebody had to use the -V 5 option to turn the volume up. I tried that and it worked. But it was loud, so I changed it to 3. Did not turn the volume down. So I removed the -V 3 option (thus restoring the command back to its original value), and it still works. I guess I just needed to let it know that a human is here.

Weird. I had the same issue and this fixed it for mew too. Thanks a lot!!!

---

### Post by StewartM on 2012-05-20
I've tried both, and nothing works for me. The command:

paplay /usr/share/sounds/ubuntu/stereo/desktop-login.ogg

works from the terminal but not in startup applications. The command:

/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

Does nothing, even in the terminal.

-StewartM

---

### Post by rjsec4ever on 2012-05-23
Doesn't work on a **new install**...

HOWEVER, got to Terminal and do the command
/usr/bin/canberra-gtk-play --id="desktop-login"
...it works.

EDIT: It works! Make sure your quotes are **NOT** the TILTED ones. If you must, go to the quotation marks and type them in manually. Also, remove the description: **_COPY & PASTE_** the above.

---

### Post by satish_j on 2012-06-03
> **StewartM said:**
> The command:

/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

Does nothing, even in the terminal.

-StewartM
For me,this command worked from terminal on a fresh install.I added the command in startup applications and got the login sound working,but then,may be after some updates,this same command stopped working.
And,now,there is no login sound even though it is still in startup Apps.](*,)
Running from terminal does not show any error as such,it seems like it is playing something,but it is not audible..

---

### Post by 3vilStar on 2012-11-11
/usr/bin/canberra-gtk-play --id='desktop-login' --description='GNOME Login'

The problem is in the quotes

---

