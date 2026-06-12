---
title: "Wierd Problem with 3D games"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by Achetar on 2007-11-18
Alright, so I just upgraded to Gutsy from Fiesty (I am running Xubuntu BTW). In 3D games, it looks like they are just below, like, flowing water or something. I would do a screenshot, but my computer refuses to take screenshots of direct rendered stuff. Anyway, Beryl, Compiz, and Compiz Fusion all work fine. What is wrong here?

Games also have slower performance than normal, while Compiz Fusion (what I am using right now) runs far faster than it used to! Odd...

---

### Post by gsiliceo on 2007-11-18
I disable compiz for playing games as there are several known bugs, including fps dropping and sudden turning off of fullscreen mode.

---

### Post by garyj1972 on 2007-11-19
I have a similar problem. Could you advise how to turn off Compiz? .. and then how you turn  it back in again? Thanks from a newbie

---

### Post by garyj1972 on 2007-11-19
I thought I'd advise anyone facing a similar problem what I did to resolve this. It's not a perfect solution but it does allow me to do what I want.

On a fresh Gutsy i386 install with "GARY" as Admin user defined during install
Installed all hardware (wifi) in my case
Installed all Ubuntu updates
Installed ENVY  and ran it to update ATI driver
Installed Compiz Fusion Settings Manager from this link >   
       [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)
BUT DIDN'T ENABLE ANYTHING - JUST INSTALLED IT AT THIS STAGE

Now created a second Admin authorised user, for me called GAMER

Now in the original Admin account "GARY" for me I enabled the 3D cube, wobbly windows, etc... that I wanted.

These settings did not transfer to the "GAMER" account, so as long as I never enable Custom Effects on this account all my 3D games still run perfectly.

I appreciate this doesn't cure the proble but for me is a satisfactory work-around - hope it helps someone else. Gary

---

### Post by Achetar on 2007-11-19
Whoops, sorry, I forgot to mention, I used Beryl for awhile before, and learned to turn it off when doing graphics/memory intensive stuff. I forgot to say that I turned it off when I was doing that.

---

### Post by Achetar on 2007-11-19
Actually quite oddly, when I play 3D games in windowed mode, I don't have that problem...

---

### Post by Achetar on 2007-12-18
Aha! I found the problem (kinda)!

When I play games in fullscreen, I have to set them to 800x600. Hopefully 1268x1024 will work as well, but I havent tested it.

---

### Post by gsiliceo on 2007-12-18
I have 2 icons in my gnome-panel to disable and enable the desktop effects.
Disable uses this command
> metacity --replace
And after im done with tremulous i enable the effects back with this command
> compiz --replace
And that does it, im searching for a script that does this automatically, im not sure if a script can "detect" when a program exits and then executes a string.

---

### Post by Achetar on 2007-12-19
> **gsiliceo said:**
> I have 2 icons in my gnome-panel to disable and enable the desktop effects.
Disable uses this command

And after im done with tremulous i enable the effects back with this command

And that does it, im searching for a script that does this automatically, im not sure if a script can "detect" when a program exits and then executes a string.
I think you can do that, but I am not sure how. I am stuck in a tougher boat. xfwm won't replace another WM, I have to manually kill compiz, then start xfwm4, then reverse the process when I am done.

---

