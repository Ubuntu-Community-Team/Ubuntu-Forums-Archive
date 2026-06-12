---
title: "Microphone not working in Lenovo G50-70"
date: 2015-03-19
forum: Multimedia Software
---

### Post by rakesh343 on 2015-03-19
After installation the microphne of my Lenovo G50-70 Series laptop is not working. Any guidance on it?

---

### Post by DarkSapphire on 2015-03-19
Did you check the additional drivers page in Ubuntu?  Normally they tell you if a device is working properly.  If the actual driver doesn't work, Ubuntu will recommend their own.  My wi-fi driver didn't work, but Ubuntu's did.

---

### Post by mörgæs on 2015-03-21
No, it's unlikely that sound drivers need special care. Mostly they are OK by default.

In stead try to run the command

```
sudo apt-get install pavucontrol
```

After that open the application, check that nothing is muted and play around with the settings. Surprisingly often it solves the problem.

---

### Post by rakesh343 on 2015-03-26
Dear Morgaes,

Thanks. But it still does not work. Anything else?

---

### Post by Vladlenin5000 on 2015-03-27
> **rakesh343 said:**
> But it still does not work.

Dear rajesh343,

A little bit of info instead of a laconic "doesn't work" is welcome.
Was something muted? No? What other settings have you tried?
And perhaps a screenshot is a good idea...

---

### Post by Bobses on 2015-04-18
I have exactly same situation: the microphone doesn't work on Lenovo G50-70 and Ubuntu Mate 14.04.02. I tried with Pulse Audio Volume Control and Alsamixer, but nothing changed: only undecipherable noise.
It is not hardware problem, because the microphone works well on Windows 10.

---

### Post by aleolivat on 2015-05-25
Did any of you guys find a fix for the problem?   I recently got the a lenovo notebook B50-70 and it looks like it has the same problems.

---

### Post by kuba6 on 2015-08-14
Type in Terminal
 Sudo apt-get install pavucontrol
pavucontrol
In opened window go to input devices, click lock icon and then move left-right sliders to different positions. I put 45% and 60%.
It seams that stereo channels cancel each other

---

### Post by dario.ghersi on 2015-08-31
Thanks for your suggestion. Moving the left and right sliders to different positions worked for me as well.

---

### Post by Pavel_D. on 2015-10-10
Thanks kuba6, your suggestion worked for me. However I chose higher levels (80% and 100%)

---

### Post by Morazi on 2016-05-18
Dear [**[COLOR=#000000]kuba6[/COLOR]**]("http://ubuntuforums.org/member.php?u=1996290")
Thank you very much .. your advice worked for me . I had tried almost everything in web without result. 
I once again thank you .. 
:D

---

