---
title: "indicator-weather does not launch..."
date: 2011-03-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by shantiq on 2011-03-25
ok so installed it this way


```
sudo add-apt-repository ppa:weather-indicator-team/ppa

``````
sudo apt-get update
```
```
sudo apt-get install indicator-weather
```

and it simply does not launch

any ideas?

---

### Post by Iehova on 2011-03-25
There is a bug, it probably has launched but it doesn't display any icon until you configure it. Go to your panel and click one of the indicators. Mouse left along the indicators and you should find the weather indicator hiding up there, you can then configure it and it will thenceforth behave as expected.

---

### Post by mc4man on 2011-03-25
Two things - 
the current indicator-weather doesn't _work here _as well as the previous one that didn't use couchdb though it may be fine for you (only 9 locations
[https://bugs.launchpad.net/ubuntu/+source/indicator-weather/+bug/741482](https://bugs.launchpad.net/ubuntu/+source/indicator-weather/+bug/741482)

 do a restart or logout/in after install - if it isn't showing then there is a little trick to get it to show  - it it has to be configured first

Easiest way to configure if it isn't showing - 

Click on an icon in the right side group - the envelope one is good. Move the mouse into the dropdown so it highlights the first option.
Then use your left arrow button, a few presses should expose the setup for the weather indicator, press enter on keyboard or click on and you should be into the setup

Edit I see Iehova has shown you the 'trick. - would be curious if you get more than 9 locations

---

### Post by shantiq on 2011-03-25
got it configured using 

> Click on an icon in the right side group - the envelope one is good. Move the mouse into the dropdown so it highlights the first option.
Then use your left arrow button, a few presses should expose the setup for the weather indicator, press enter on keyboard or click on and you should be into the setup


  =============================

used to be on maverick if you hovered on time display it would pop up  

  it is working...   but it is no longer linked to the time display with the flashing little window whch was quick


or am i confusing two different things here?   was the pop-up weather thing on the clock in maverick different from indicator-weather?

**Anyway** thanx guys indicator-weather now works

---

### Post by rburkartjo on 2011-03-25
tks for sharing since the last few updates it sometimes loads and sometimes doesnt

---

### Post by Anduu on 2011-03-26
Maybe I am missing something here...

I can find my way into the configuration and add locations etc...however...it is still just a blank space with no info.

---

### Post by mc4man on 2011-03-26
> **Anduu said:**
> Maybe I am missing something here...

I can find my way into the configuration and add locations etc...however...it is still just a blank space with no info.

Here it's always blank but clicking on the 'get cities' does return some locations. Unfortunately I only 'get' 9 locations, none even remotely useful

Have returned to using the 11.02.13+repack-... version which works ok, though not as good as the gnome-panel applet did

---

### Post by shantiq on 2011-03-27
ok what i was looking in the first place has reappeared see image

simply had to right-click on the clock preferences weather and location


sure it was not there last week

but anyway now found out about indicator-weather so bonus

---

### Post by SevenMachines on 2011-03-27
I had the same thing, but due to a stale pid. so, if there are no running processes
```
 $ ps -e |grep indicator-weather
```
but you still get
```
$ indicator-weather 
Another instance of this program is already running
```
then you might want to try
```
 $ rm .cache/indicator-weather.pid
```

---

### Post by rburkartjo on 2011-03-27
seems that my problem was fixed with the last weather indicator upgrade

---

