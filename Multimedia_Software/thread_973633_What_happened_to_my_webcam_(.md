---
title: "What happened to my webcam? :("
date: 2008-11-06
forum: Multimedia Software
---

### Post by Rovdjur on 2008-11-06
So here is the deal: I just recently (one month ago) purchased a new Lenovo Thinkpad X300. I do not like Windows all that much so I decided to put Ubuntu Hardy Heron on there and everything (and I mean everything) worked EXCEPT the sound. It turned out that the ALSA drivers did not work properly and no matter how many times I tried to compile new ones, it never got fixed, so I decided to install Windows and use that until Intrepid Ibex was released.

So now I am running Intrepid Ibex on my X300 and everything EXCEPT my WEBCAM works!

I do not know what happened to it! It worked fine before, but not it does not work at all! I don't use it to video conference, but I DO love to play around with it in Cheese! In Hardy Heron Cheese worked great! I had a lot of fun with that program, but now in Intrepid Ibex, Cheese does not get a picture and freezes every single time! The little green light goes on for a split second to tell me my webcam is being used, but then it goes off and Cheese dies and I have to force quit.

It is not the version of Cheese because I had it updated to the same version in both Heron and Ibex, so the drivers got messed up in the new Ubuntu update.

I am a complete newbie to Linux and I would love it if someone could help me out :) It is not deathly important, but it's nice to send a few pictures to my girlfriend every now and then through e-mail :)

Any help is appreciated!

---

### Post by cariboo on 2008-11-06
Just as a test have you tried you web cam using Ekiga? My webcam is now a v4l device, which cheese (as far as I know) does not support.

Jim

---

### Post by Rovdjur on 2008-11-06
Well, Ekiga crashes when I try to bring up the webcam as well! The weird thing is that the webcam WORKED in Heron, but not does NOT work with Ibex. So Cheese definitely supported my webcam. I think a driver update with Ibex crashed it :-/

Is there any way to revert back to old drivers for the webcam from Heron?

---

### Post by dvstin on 2008-11-10
I have the exact same experience as Rovdjur. My webcam worked great in 8.04 and doesn't work in 8.10. When I start cheese, the green light to indicate webcam activity goes on and then off again before any picture is displayed.

Also, as of 8.10, I am getting random kernel panics on the thinkpad x300.

---

### Post by kleeman on 2008-11-11
There is a general webcam problem in Intrepid. See the sticky in the General Help section. I have an X300 and skype webcam works but cheese and ekiga do not.

---

### Post by andresmh on 2008-11-25
I wonder if there is a bug report open for this. I am having the same problem.

---

### Post by hbj on 2009-05-06
The built-in camera and mic are working fine for me on an X300 running 9.04, AMD64.  Cheese and Skype work fine.

---

