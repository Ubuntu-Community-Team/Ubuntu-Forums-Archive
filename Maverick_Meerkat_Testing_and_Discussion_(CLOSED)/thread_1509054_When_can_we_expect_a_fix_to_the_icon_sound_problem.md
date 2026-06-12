---
title: "When can we expect a fix to the icon sound problem?"
date: 2010-06-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-13
Every time i start Ubuntu the icon of the sound is in mute mode now i know that there is a way to fix it from a previous thread but when would an official fix would be released for it?

Thanks in advance.

---

### Post by ranch hand on 2010-06-13
There is an easy fix for that.  I don't know where the thread is right off the top of my head but if you run a search for "mute" on the "search this forum" tool you will find it.

---

### Post by Atermoon on 2010-06-13
Lol this seems to happen with every release while it's in alpha/beta. At least with the last 3, can't remember if Jaunty had it too.

---

### Post by TerminX on 2010-06-13
Try configuring things how you want them and run "sudo alsactl store" to see if that gets the settings to stick.  I think it's supposed to happen during shutdown but the script that controls it could have blown up at some point without immediately being noticed.

---

### Post by ktp on 2010-06-13
If I remember correctly...this seems to happen if pulseaudio had crashed for one reason or another.  At least that is the pattern I have seen.

---

### Post by jerrylamos on 2010-06-21
> **TerminX said:**
> Try configuring things how you want them and run "sudo alsactl store" to see if that gets the settings to stick.  I think it's supposed to happen during shutdown but the script that controls it could have blown up at some point without immediately being noticed.

"sudo alsactl store" doesn't do it for me.

Maverick defaults to "mute", with alsamixer "Master M" reset to absolute zero on every reboot.

It doesn't stop the computer just something I have to do on each and every boot.

Anyone know how to automatically run a script on boot that turns on the speaker?

Thanks, Jerry

---

### Post by ranch hand on 2010-06-21
There is an easy fix for this.  If folks would run their very own search in the hard to find "search this forum" option at the top of this page they would have found that this is already dealt with and did not need another thread.

I couldn't remember where it was but a complex search using the hard to think of word "mute" in the search box turned it up.

[http://ubuntuforums.org/showthread.php?t=1490373&highlight=mute](http://ubuntuforums.org/showthread.php?t=1490373&highlight=mute)

Literacy is something that we all need to consider as a possible option.

---

### Post by aviramof on 2010-06-21
I did managed to fix it before but because of the xorg breakage i was forced to reinstall ubuntu and i didn't had the time to fix it again it was 
something about commenting or uncommenting a line in some file i'm sure i can find it if i search but fixing it via an update would be of course much better.:)

---

### Post by ranch hand on 2010-06-21
It most certainly would.  It has, as can be seen on the post date of the thread I linked, been a problem for some time.  I am sure it will be fixed eventually but I can see why it would not be a high priority.

Not being a person capable of writing code I have no idea what may be involved.  They may want to wait until closer to the final kernel version for all I know.

I do know that commenting that line has fixed it for me in all my installs.

---

### Post by 23dornot23d on 2010-06-21
I submitted a bug report on Sound Problems with Maverick ......

How do I get it back onto their list to have another look at it  ...... at the moment it is marked incomplete

but I have added as much information that is possible to add about this problem now ......

They seem to have marked it as incomplete ....... yet I have spent a lot of time trying to
sort this out today ..... and this thread would probably have solved part of it ......

The fact the volumes are automatically set to ZERO ...... but even when adjusting them
there is no sound OUTPUT .... at all.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/596882](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/596882)

Do these get looked at again ..... at some point ...... any help here would be good  ....

or is there a way to bump them ...... into view again after information has been added ....
to them .......

---

### Post by ranch hand on 2010-06-21
Well, I am ashamed of myself.  This appears to be the only bug filed on this.  I hope others jump on board so they know it really is a problem rather than specific to your hardware.

Should have been filed weeks ago, I never even checked.  Sorry.

Anyone reading this should join this bug if it effects you too.  I know it effects more than 2 of us.

---

### Post by 23dornot23d on 2010-06-21
Thanks for looking at it ranch hand - and adding to it .......
I am sure there will be more people that have this problem 
hopefully it will get solved
I have always had to recompile the alsa source code in the past and the drivers
to get sound to work ....... but this time it will not let me compile the code
headers are missing according to the error ...... but as far as I know I have the
latest of everything needed to compile them ....

If it gets sorted I will not have to worry about this anymore though .......

---

### Post by jerrylamos on 2010-06-21
> **ranch hand said:**
> It most certainly would.  It has, as can be seen on the post date of the thread I linked, been a problem for some time.  I am sure it will be fixed eventually but I can see why it would not be a high priority.

Not being a person capable of writing code I have no idea what may be involved.  They may want to wait until closer to the final kernel version for all I know.

I do know that commenting that line has fixed it for me in all my installs.

Commenting out the line fixed it - if the fix is that simple why hasn't it been done?  Is there some problem with commenting out the line?

Thanks, Jerry

---

### Post by aviramof on 2010-06-21
I'm still hopping that it would be fixed in an update if not eventually i would fix it my self by commenting out the line.

---

### Post by 23dornot23d on 2010-06-21
> **jerrylamos said:**
> Commenting out the line fixed it - if the fix is that simple why hasn't it been done?  Is there some problem with commenting out the line?

Thanks, Jerry


It would be a fix if it made the sound work ..... it does not ...... and it is different problem ..... to that .....

The Sound does not play ...... at all ........ even after doing the above edit .....

---

### Post by ranch hand on 2010-06-21
> **23dornot23d said:**
> It would be a fix if it made the sound work ..... it does not ...... and it is different problem ..... to that .....

The Sound does not play ...... at all ........ even after doing the above edit .....
Now that is a real bummer.  Mine is fine but  I am using an old audigy1 5.1 card and the gnome-alsamixer so it is probably not like too many boxes this new.

This probably hasn't been fixed because we were all waiting for someone else to file the bug.  They can't fix it if we don't file the bugs.  Join the bug and help get it verified.  Geeze I feel like a moron.

---

### Post by 23dornot23d on 2010-06-21
Just a Recap of what has happened today ....... 
My first day trying to make sure that a Bug gets fixed ........
1.......  Timed out on putting a bug report in ..... so after spend time typing it all out the information was lost
2........ The first person sees the minimum information on the second Bug report - marks it as incomplete
3 ........ With all the information added to this now ..... the second person sees it and marks it as incomplete
4 .......  Next I add a file outlining the two files one from Linux Mint that Works and one from Maverick that does not
5 .......  The next person looks at it and says its a duplicate to one where the Sound levels are decreased to zero Wrong
6 .......  I do the edit as the previous person believes they think this is the solution ...... it is not .........
7 .......  But I will continue ...... as it does not work yet
Except of course when I  go into  Linux MINT or Zorin .....which are working fine and I have posted the results from these too
8 .......  I will go through the differences file that I posted as the solution must lie there ......... this needs updating as the
           levels were at Zero here ...... but even after altering them I have posted the latest maybe I need to do another
           difference file ..........
[http://sites.google.com/site/centraltube3dsfiles/files-for-system-config/differencesMavandMint.txt?attredirects=0&d=1](http://sites.google.com/site/centraltube3dsfiles/files-for-system-config/differencesMavandMint.txt?attredirects=0&d=1)

I did get it working in Lucid by re-compiling the ALSA drivers ..... but have not been successful here as it reports
that headers are missing ...... 

I will try to solve it and get back back with the solution ......  or reduce the Difference file to the lines I think may be the cause
but I am not a programmer ....... although I have dabbled in my past .......

**My challenge is to see if I can get this one bug fixed and implemented and fixed in the next release ...... **
(I know that I can fix it as I did it in Lucid ...... and even now I can drop back into Lucids old ,22 Kernel and the sound works fine)

---

### Post by cariboo on 2010-06-21
@23dornot23d

Your problem is different from everybody else in the thread, our sound works, it is just muted on a restart, commenting out the line in /etc/pulse/default.pa just leaves the sound in the same state as it was when the system was shutdown, if it was muted on shutdown, it will be muted on start up.

---

### Post by 23dornot23d on 2010-06-21
Cheers ....... that seems to be the case ...... how do I go about highlighting this (Newer) problem though and getting it fixed ........

Should I start another thread ..... or will the Bug report be sufficient as that is where we should see a solution.

I will work on tying the information down to something more specific .... too ..... as it still is not obvious why its not
working ......

It even displays the right info in the Sound mixer for the correct card ..... bizarre ..... it will be something simple ....
I hope .....

I will keep all my updates on my homepage as I do not want to take over this thread ...... this thread seems to be solved

My information and updates will now be posted here ...... [My Homepage in UBUNTU FORUMS]("http://ubuntuforums.org/member.php?u=953253")

---

### Post by cariboo on 2010-06-22
I'd suggest starting a new thread, make sure you let us know what hardware you are running, especially the sound card.

---

### Post by 23dornot23d on 2010-06-22
Ok thank you ..... I have done that now the link is here 

[http://ubuntuforums.org/showthread.php?p=9494219#post9494219](http://ubuntuforums.org/showthread.php?p=9494219#post9494219)

---

### Post by aviramof on 2010-06-22
I think i can say that the problem is fixed now with the new kernel and all the other updates i just downloaded and also there is no blutooth icon and etc so everything is 
fine for now thread solved.:)

---

### Post by aviramof on 2010-06-22
Problem still exist.

---

### Post by andrewabc on 2010-07-02
I have same problem. Alpha 2 +updates installed.

Link to older thread with solution works.

> 
load-module module-device-restore in /etc/pulse/default.pa  with #load-module module-device-restore


---

### Post by aviramof on 2010-07-05
To be honest i still have this problem and i still didn't took the time to fix it manually as i did before i still hope that an update would fix it. 

But it's also don't bother me much because i don't use speakers in my computer my sound card is connected to my TV and amplifier  and only when i 
turn on the tv and set them in the HDMI channel i can hear sounds usually from hdmi movies but sometime i use it for mp3 files or skype and etc so i 
don't worry about this too much.

---

### Post by 23dornot23d on 2010-07-08
I have just done a full update and THIS problem is definitely still here ..... for me too ....


Now there is a nice graphic " LOCK " on the sound icon though ..... 

[IMG]http://sites.google.com/site/23dornot23d/home/desktop10.png?attredirects=0[/IMG]

So at the very least I know the OS does not want me to have the sound turned on at  start-up ...... 

**Will this stay like this until the Final release ..... **

seems we do not need to keep commenting on something that should be fixed ...... 
is it being incorporated the way the fix says here in this thread ? 
....... or is there still a problem with the fix stated ?


(My main problem is the Grub2 ........ what a mess it seems to be ......
each time it goes to 640x480 on my 32" monitor it is very impressive and it also removes my background - giving a very plain Black and White Menu ...... in very big letters which I appreciate as my eyes are not so good ..........
 
(But my thoughts - We might as well have kept with Grub 1 at least that was easy to sort out and it stayed as you set it up ....... this GRUB2 I feel the computer is in control !!!
and has a random setting built into it ..... this time I will MESS the Graphics up the next time I will Mess the Sound up ........ where do I look it used to be one of two places ....
now I find that the safest option is to re-install ......... just to get my menu back )

I cannot stop the Safe Upgrade overwriting my modified GRUB2 list ..... even though it asks me twice to keep  the modified one I have (default setting keep the modified one) .... as for the second USB drive and boot options - it seems that it has no idea how to set them up ......... so it FAILS ..... on each and every one I select it says there is no kernel ....  )

So I .....

Re-install the old Grub 2  from a clean LINUX MINT 9 install and it sets everything back up as it should be in around 30 mins .............. there is clearly a big difference between
MINT and UBUNTU - GRUB2 ..... you seem to solve the problems here ...... but what then happens to the fixes ...  

Strange way to go about things ...... but whatever  ...... 

( Finish on a good note ..... The latest Nvidia Driver is working great and is giving the lowest Thermal readings I have ever had ..... even on these HOT HOT days .....  )

And the music played on  .....   :guitar:   ... after the UN mute ..... and the next time UN Mute ...... and the next time Un Mute ...... alter the code ...... then the next upgrade ...... UN Mute ......... Alter the code .......

Too hot today 'I just finished cutting the grass' ...... but it is a nice day ....... 

I am really looking forward to the Final release in October - the Majority of things do work well ...... Would be nice if the USERS could choose the GRUB 2 Menu they want to use though ......... especially if they spend a lot of time setting it up ......

---

### Post by VastOne on 2010-07-08
> **ktp said:**
> If I remember correctly...this seems to happen if pulseaudio had crashed for one reason or another.  At least that is the pattern I have seen.

Same pattern seen here...

---

### Post by VMC on 2010-07-09
> **ranch hand said:**
> There is an easy fix for this.  If folks would run their very own search in the hard to find "search this forum" option at the top of this page they would have found that this is already dealt with and did not need another thread.

I couldn't remember where it was but a complex search using the hard to think of word "mute" in the search box turned it up.

[http://ubuntuforums.org/showthread.php?t=1490373&highlight=mute](http://ubuntuforums.org/showthread.php?t=1490373&highlight=mute)

Literacy is something that we all need to consider as a possible option.

Thanks for the link. It did fix mine as well. I wasn't too worried and knew in time it would get fixed.

---

### Post by MacUntu on 2010-07-09
Nitpicking: that's rather a workaround than a fix.

---

