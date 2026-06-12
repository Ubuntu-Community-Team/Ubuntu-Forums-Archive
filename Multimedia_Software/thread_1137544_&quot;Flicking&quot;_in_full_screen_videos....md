---
title: "&quot;Flicking&quot; in full screen videos..."
date: 2009-04-25
forum: Multimedia Software
---

### Post by BuhSnarf on 2009-04-25
Hi,

I'm not quite sure how to describe this problem, but I shall do the best that I can. It also only seems to of happened fairly recently (worked fine when I was on 8.10 but has definitely happened for most of the 9.04 betas.) Basically whenever I am playing something full screen in any movie player (have tried Totem, Kaffeine and flash) if I move the cursor which usually brings up the menu bar along the bottom as I do it I get a brief flash of whatever desktop wallpaper I have as well. This is quite distracting, for example, when libnotify displays something (im buddy coming online or whatever) as it will flicker the video with my background as it pops up and then gets rid of the box.

Is anyone else experiencing this? I tried turning off Compiz but that didn't seem to help.

I have a GeForce 8400 card with the binary nVidia driver installed (recommended one under Hardware drivers - 180 I think)

Thanks in advance.

---

### Post by sports fan Matt on 2009-04-25
I have noticed it as well..Im not sure if it did it in the betas..youre probably right...but I definately have noticed it....

---

### Post by BuhSnarf on 2009-04-28
Does anyone know why? As I use Ubuntu plugged into my HDTV and it's really annoying to have the desktop background keep showing while I'm watching movies or TV!

---

### Post by xc3RnbFO8P on 2009-04-28
If you are using Compiz, try in settings/preferences/compiz config settings manager under general tab uncheck Unredirect fullscreen.

---

### Post by shayguitarra on 2009-04-28
This was happening to me in 8.10. I posted about it [[COLOR="Sienna"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1116647").

Since upgrading to Jaunty I've switched to an nVidia 9500GT 512MB video card, due to the problem with the FGLRX driver for ati cards. I'm using the open source driver for nvidia. This behaviour has completely stopped.

---

### Post by BuhSnarf on 2009-04-28
I wonder if it's a Ubunutu problem and not a Kubuntu problem. Would make sense as I used to have Kubuntu installed before this beta. I think I might go back to Kubuntu and see if that helps as a reinstall of Ubuntu didn't.

OK, also the unredirect full screen from Compiz worked - is there any functionality lost by unchecking that box? What does that do?

---

### Post by shayguitarra on 2009-04-28
> I wonder if it's a Ubunutu problem and not a Kubuntu problem. 

Well, I only started having the problem after I installed the Kubuntu desktop. I'm still running it now but with no problems.

I think it's possibly an issue with the proprietary drivers and certain video cards.

---

### Post by iconfat on 2009-05-03
Thanks, I was having this problem too.
I unchecked Undirect Fullscreen and it fixed the problem.

---

