---
title: "Reason-like program and useful guides"
date: 2007-05-13
forum: Multimedia Production
---

### Post by nerubian on 2007-05-13
Hello, I haven't used ubuntu studio apps too much yet.I learnt to run applications and jack configuration and other connections.I am pretty new and want to learn making music with a Reason -like program  in windows.I gave up using windows, now using Kubuntu 7.04 installed new studio packages.Do you suggest any program that has big sound bank like reason's factory?I liked the drum kit program but are there good programs for nice sounds and loops?I installed every program in ubuntu studio and need advice.

Also i need some documentation and guides for music making.Can you suggest me some sites and documents for these programs?

---

### Post by stijngysemans on 2007-05-14
you should take a look @ ubuntustudio

---

### Post by Pocadotty on 2007-05-14
yeah, and your not going to find a program like reason, Linux works on modularity, so rather then having a single program that tries to do everything, Linux has many programs that work together to do what you want.

If you are planing on doing music on Linux, first off you should be running the low latency kernel you get with Ubuntu studio, to do this do a full upgrade to Ubuntu studio by adding the fallowing packages in Synaptic package manager.

ubuntustudio-desktop
ubuntustudio-audio
ubuntustudio-audio-plugins
ubuntustudio-graphics
ubuntustudio-video

The graphics and video packages you may not need if you plan on doing just music, but they are there for you if you want.  ubuntustudio-desktop replaces ubuntu-desktop and contains the low latency kernel.  If you have any ristricted drivers (like video acceleration for nvidea) then you are going to nead this package.

linux-restricted-modules-lowlatency

Once you have your system up to Ubuntu studio with the low latency kernel your JACK server will run better.  I was able to get my latency down to 2.67ms (note the best I ever got it to on Reason and windows was 85ms), with virtually no Xruns.  This is a real and noticeable advantage of using ubuntu studio.

Anyway, I was a Reason user on windows, and I must say that I do miss the massive sound bank it had, however you can make your own sound bank.

check out [http://freesound.iua.upf.edu/](http://freesound.iua.upf.edu/) which is a project to provide royalty free samples to all for free.  Here you can download sounds that other people have posted, or start posting your own if you feel so inclined.  There is a lot there, so you are more or less bound to find something that suits your needs to the letter.

Personally I am an industrial musician, and am working on putting together an industrial drum bank to use on Hydrogen, which I have found to be my favorite drum interface (far easier to use then redrum on Reason) and find its only shortcoming the lack of a huge kit bank.  but with freesound you can help make this shortcoming go away by creating kits that match what your style is.

Or if you don't mind spending a little cash, you can pick up the rhythm galaxy sound bank here [http://sinevibes.com/soundware/rhythm-galaxy-1/](http://sinevibes.com/soundware/rhythm-galaxy-1/) it was made by a forum mod for Hydrogen last I heard.  There are likely patch libraries available for various synths on Linux, let me know if you find any.

I hope all that helps you out...

cheers:guitar:

---

### Post by nerubian on 2007-05-20
yes i installed the ubuntu-studio components and have jack running low latency.thank you Pocadotty, i really missed sound bank of reason.i am a little noob with producing my own samples but anyway producing is a good idea and i will try it.i was wondering is it possible to download or produce samples and then use it with a synthesizer (like zyn or another one) if there are guides of info about producing samples i would really like to know.thanks for replies.

---

