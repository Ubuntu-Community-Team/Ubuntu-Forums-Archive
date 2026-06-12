---
title: "Java ???"
date: 2010-11-24
forum: Multimedia Software
---

### Post by steven198807 on 2010-11-24
OK after many people on the web telling me it is very unlikely that I will ever need to touch command I seem to be having problems first day.

Today I plug in my tablet and had to install the driver by command,  fixed that with some luck.

Now I go to websites that need flash and Java, flash player was easy install very nice btut Java big no no.

For example I went to minecraft website and needed Java, its a pain in the butt i have tried some things from what I saw on you-tube but no luck.

For a system which is meant to be for humans its bloody confusing.

---

### Post by sikander3786 on 2010-11-24
It is not confusing, it is simple.

Go to Applications > Software Center, search for ubuntu-restricted-extras and install that package. It would give you an open source alternative for java, flash, codecs and some fonts.

And then you'll know that it is truly "meant for human beings" :-)

You can also install the official sun-java package but it would need some plugins to be added manually.

I would recommend ubuntu-restricted-extras as it always sets up everything nicely for me.

Good Luck!

---

### Post by steven198807 on 2010-11-24
> **sikander3786 said:**
> It is not confusing, it is simple.

Go to Applications > Software Center, search for ubuntu-restricted-extras and install that package. It would give you an open source alternative for java, flash, codecs and some fonts.

And then you'll know that it is truly "meant for human beings" :-)

You can also install the official sun-java package but it would need some plugins to be added manually.

I would recommend ubuntu-restricted-extras as it always sets up everything nicely for me.

Good Luck!

only one problem when i search for that it says its already installed , yet i still can get java websites to work ?

---

### Post by sikander3786 on 2010-11-24
> **steven198807 said:**
> only one problem when i search for that it says its already installed , yet i still can get java websites to work ?
Type this in your firefox address bar.

```
about:plugins
```

And it should list an entry for

> IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.1 (6b20-1.9.1-1ubuntu3))


If it doesn't, try installing the plugin (I'll use command line this time :-) ) by,

```
sudo apt-get install icedtea6-plugin
```

Does it say it is already installed?

Do that command from Applications > Accessories > Terminal and if you are doing a sudo command for the 1st time, you won't see your password return any characters or *, just type it blindly and hit Enter.

---

### Post by steven198807 on 2010-11-24
> **sikander3786 said:**
> Type this in your firefox address bar.

```
about:plugins
```And it should list an entry for




If it doesn't, try installing the plugin (I'll use command line this time :-) ) by,

```
sudo apt-get install icedtea6-plugin
```Does it say it is already installed?

Do that command from Applications > Accessories > Terminal and if you are doing a sudo command for the 1st time, you won't see your password return any characters or *, just type it blindly and hit Enter.

Yes it is listed in about:plugins, thanks for the help so far you seem to be the only person trying to help me today :)

---

### Post by steven198807 on 2010-11-25
Can any one help me please, I would really like to be able to play mine-craft and other Java games

---

### Post by steven198807 on 2010-11-26
> **steven198807 said:**
> Can any one help me please, I would really like to be able to play mine-craft and other Java games

Looks like its back to windows for me but i hope this is fixed for future versions.
I don't see any reason why any OS cant have flash and java pre-installed so you don't have too!.
Mostly all the time you will run into some webpage that needs flash or java installed, in my eyes this is a must have!.

Also a pre-installed  Pdf Reader would be great (i have not seen one i could be wrong).


Make Ubuntu for Humans!, heres a example video for some ideas.
I will keep it installed only for gimp as my tablet seems to work better in ubuntu
[http://www.youtube.com/watch?v=BM2NBDTbRQI](http://www.youtube.com/watch?v=BM2NBDTbRQI)
This is very true even the first 5 secs i did not even know.

---

### Post by a-user on 2010-11-26
> **steven198807 said:**
> Looks like its back to windows for me but i hope this is fixed for future versions.
I don't see any reason why any OS cant have flash and java pre-installed so you don't have too!.
the reason is already shown during installation. despite of that you get the possibiliy to install flash and other already duing te installation.
> 
Mostly all the time you will run into some webpage that needs flash or java installed, in my eyes this is a must have!.

in yours only!
> 
Also a pre-installed  Pdf Reader would be great (i have not seen one i could be wrong).

like on your previous claims you are wrong here too.
> 
Make Ubuntu for Humans!
it is. only because you are used to get things working in the manner windows does, hence you have difficulties with different behaviours does not mean it is not for humans!

for me it is 100 times easier to handle ubuntu than windows ever was. and i am/as a long time windows user. last time my doctor checked me i was human (just in case you ask).

if you start asking question instead of flaming everything that does not work like you used to know from window you may get more help.

---

### Post by steven198807 on 2010-11-27
> **a-user said:**
> the reason is already shown during installation. despite of that you get the possibiliy to install flash and other already duing te installation.

in yours only!

like on your previous claims you are wrong here too.

it is. only because you are used to get things working in the manner windows does, hence you have difficulties with different behaviours does not mean it is not for humans!

for me it is 100 times easier to handle ubuntu than windows ever was. and i am/as a long time windows user. last time my doctor checked me i was human (just in case you ask).

if you start asking question instead of flaming everything that does not work like you used to know from window you may get more help.

Im not flaming or a troll, ubuntu is nice but like that video i posted its not easy.
In my opinion a OS should be so easier to use that you don't have to know how it works, it should be so easy that some one who is very poor at computers can do his/her job with out panic.

Come on i installed a tablet just by pluging it in to windows, but ubuntu i have huge problems, my brother installs and has wifi and sound problems.
I can't even get a java to install but yet on windows its just click and point, you can't go give some one a command line if they dont even know what a url bar is.

Decided maybe its just me but my brother gave it a try and my mother, they both said its confusing.

If you want to have utouch how you gonna type command with out a keyboard ?.

Yes i love gui's but thats only because they are super easy to use.
I don't need to look up a bunch of commands to install a app, no i just point and click and it works.

Look at android a very much loved phone and why because its got no command, no because its easy to use !.

If you need a manual to use the system from day 1 then guess what something is wrong!, instead its got to be ready out side the box.

And PDF are ebooks and a big part of the PC World, so every one needs it really.

---

