---
title: "Confused noob please help!!!!!"
date: 2007-11-23
forum: Multimedia Production
---

### Post by aggrosplatt on 2007-11-23
Hi,

I am a music technician at a music specialist school and as part of this specialism we have been roped into doing some music production workshops at the local youth centre. 

Due to budget restraints we are not able to afford a full microsoft set up with music programs such as cubase and reason. For this reason we decided to explore the option of open source software for a solution and came across ubuntu studio. 

I have seen and used ubuntu operating systems in the past but am still a relative noob in regard to the workings of the system and have come across a couple of things that are really stumping me;:confused: 
1. Jack: I have been told that you need to run Jack to get sound out of programs such as ardour and rose garden. Why? I see no reason for this at all. I see the reason for the part of jack that allows you route any output of one programme to any input of another, in fact i think this is a really good idea. I have read around a bit trying to find out exactly what it is that jack is doing but i am still failing to understand, am i missing something? Can any one help?
2. When I launch the hydrogen drum machine on it's own without running jack it works fine but as soon as jack is launched you get no sound out of hydrogen at all, I have tried running jack first and then hydrogen but this still doesn't work, i have also noticed that launching jack stops ardour from playing i.e the play marker doesn't move unless you move it yourself.  :mad:

I am at the point now where, if I cannot figure out what is going on I am going to have to bite the bullet and find the money from somewhere for a microsoft setup, which I don't really want to do. So anybody out there that can offer some advice or point me in the right direction would be greatly appreciated.

---

### Post by mpgarate on 2007-11-23
Jack:

im not sure exactly, but I think it is very useful when you are running multiple audio programs at once. It allows you to connect program to program or hardware to program. It is also supposed to normalize the way the sound apps work. Rather than integrate audio card detection into every app, just have them all point to jack, which then controls the output. So in theory, you could use all your apps without a working soundcard while using jack

(feel free to correct me if im wrong, anyone)

---

### Post by aggrosplatt on 2007-11-23
Thanks for the reply mpgarate,  it mkaes a bit more sense now:)

I would still like bit more info with regard to the problems I am having with hyrdogen etc. Have I configured something wrong with in Jack? Also would I need to run Jack if I was running just one programme?

---

### Post by disturbed1 on 2007-11-23
Think of Jack as a virtual patch cage. You can wire any number of ins to any number of outs, change them on the fly, configure it how ever you want. This really helps in a studio situation when you have multiple tracks coming in, and you've created numerous sends going back out. You can pick which sends goto to which headphone monitors, route the auditioners to one set of monitors, the master to another, route your talk back to where you want etc.....  Jack doesn't make much sense if you have a home setup with something that only uses 2 or so inputs with just a couple of outputs. It's rather easy in this situation, but overkill for this type of application. Once you start having 8-10+ inputs with just as many outputs, there is nothing that comes close to Jack. Plus the real-time hooks that keep latency at a min. If you've ever attempted to record a simple 3 piece band on a system with latency, it can become a nightmare.

I always launch Jack Control first, then Adour2, then hydrogen. Tick Adour's time master to green, set the sync to Jack. In hydrogen make sure you're using Jack, not alsa/oss. Look to the bottom right of hydrogen for the blue Jack Transport. Now not only is hydrogen playing correctly, but you can control it with Adour.When you press play in Adour, what ever is loaded up in hydrogen will play.

---

### Post by Stochastic on 2007-11-23
Jack is a sound server, deals directly with your sound card (just like a driver in Win or Mac) and with the added feature of patchability and low latency.  See: [http://jackaudio.org/](http://jackaudio.org/)

Your Hydrogen problem should be fixable by going into the Preferences (Ctrl+P) and selecting JACK, you may then have to restart Hydrogen.  If this doesn't fix it let us know.

---

### Post by aggrosplatt on 2007-11-26
Hi,

Thanks for the explaination disturbed1 that has really helped and I think I have it all sussed in my head now.:)

Stochastic thank you as well, I had already read the jack site but it didn't make all that much sense to me at the time. I 'll test out both of your suggestion when I get a chance and get back to you if I have any more problems

Thanks again

Splatt

---

