---
title: "Unity bar multiple app"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by piochelin on 2011-04-14
Hi there.

I have a problem with my unity bar, when i have 2 windows of the same program (for example 2 Firefox windows) the unity bar shows me a triangle in the right side for each window, but when I click I can't choose wich one is going to be up (it's always the same) and I'm tired of alt+tab.

I don't know if I dreamed it but I though when you have 2 or more windows of the same application and you click on the icon you can choose wich window you want.

Thanks in advance ;D

PD: Sorry about the bad English, as always trying my best :)

PDD: Sorry about the title too, it's not very clear, but I don't know how to make it.

---

### Post by texla on 2011-04-14
I have seen this feature work well for Gimp - But not at all for LibreOffice or Firefox or most other programs.  There are a lot of comments on this board about the problems unity has with multiple copies of the same programs open.  I really like the way unity handled working with two Gimp files by letting me choose between each one in a zoom-out screen. Wish every program worked that way - and the desktop switcher, too!  maybe someday soon...

---

### Post by seeker5528 on 2011-04-14
> **piochelin said:**
> Hi there.

I have a problem with my unity bar, when i have 2 windows of the same program (for example 2 Firefox windows) the unity bar shows me a triangle in the right side for each window, but when I click I can't choose wich one is going to be up (it's always the same) and I'm tired of alt+tab.

Click twice.

Later, Seeker

---

### Post by texla on 2011-04-14
> **seeker5528 said:**
> Click twice.

Later, Seeker
Whoah  - that's working... cool

---

### Post by FootySr on 2011-04-14
> **piochelin said:**
> 

I don't know if I dreamed it but I though when you have 2 or more windows of the same application and you click on the icon you can choose wich window you want.


That is exactly what happens for me when I click the application icon when using multiple Firefox windows.

I get 2 triangles on the left side of the icon in the bar to mark the number of windows open.

---

### Post by piochelin on 2011-04-14
> **seeker5528 said:**
> Click twice.

Later, Seeker

Didn't work :(, thanks anyways

---

### Post by cariboo on 2011-04-14
What happens when you double click the icon? Doesn't work, isn't a valid answer here. :)

---

### Post by piochelin on 2011-04-15
> **cariboo907 said:**
> What happens when you double click the icon? Doesn't work, isn't a valid answer here. :)

My bad, sorry :P 
When I double click in the icon happens nothing.

---

### Post by seeker5528 on 2011-04-15
Assuming this is Unity not Unity-2d....

If you are double clicking an app icon of an app with only a single window, a second click won't do anything.

If an app does have multiple windows a second click should give you a visual representation of all the windows that belong to that app.

In Unity this is provided by the Compiz scale plugin. If that plugin is not enabled, the second click will do nothing.

I believe if you open a terminal window and type

```
unity --reset
```

this is one of the things that will get reset.

Alternatively you could run CCSM (Compiz Config Settings Manager) to verify the scale plugin is enabled, if you have not installed CCSM in the past you will have to install it first.

Run CCSM, scroll down the the 'Window Management' section and make sure there is a check in the box next to 'Scale'. On my box when enabling/disabling plugins it seems to always cause compiz/unity to die, usually seems get to get restarted and back more or less to normal withing 20 to 30 seconds.

If you have Unity-2d, make sure you have a package named unity-2d-spread installed.

Later, Seeker

---

### Post by piochelin on 2011-04-16
> **seeker5528 said:**
> ...make sure there is a check in the box next to 'Scale'...

There was the problem, I haven't the scale box checked, Thanks you all for the help <3

Cheers

PD: Anyone can add the prefix [SOLVED] to the thread I don't know if i can/how to do it (first post solved lol)

---

### Post by seeker5528 on 2011-04-16
I believe the option to mark as solved shows up under 'Thread Tools' in threads that were started by you.

Later, Seeker

---

### Post by piochelin on 2011-04-17
You're helping me with everything, thank you seeker ;D

---

