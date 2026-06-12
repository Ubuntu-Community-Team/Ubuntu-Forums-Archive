---
title: "Help With Flash"
date: 2009-02-09
forum: Multimedia Software
---

### Post by gt8ost4l on 2009-02-09
I really need help i just installed adobe flash and i still cant watch anything it says i need to download the plugin can anybody help me please

---

### Post by redroad55 on 2009-02-09
In your browser go to tools > add ons > plug ins and list what you have back here .. Best to you

---

### Post by snowpine on 2009-02-09
This has always worked well for me:

1. Close any open browser windows
2. Open the terminal and enter the following:
```
sudo apt-get install flashplugin-nonfree
```
3. Restart the browser.

Good luck! If you get any error messages, post them here.

---

### Post by itang sanjana on 2009-02-09
Perhaps this is a suit place to start
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
HTH

---

### Post by gt8ost4l on 2009-02-09
well i did wat yu told me n still nothing

---

### Post by wolfen69 on 2009-02-09
do
```
sudo apt-get remove flashplugin-nonfree
```
then
```
sudo apt-get clean && sudo apt-get autoremove
```
then go [here]("http://get.adobe.com/flashplayer") and download the .deb for ubuntu 8.04+
click to install. restart firefox.

---

### Post by gt8ost4l on 2009-02-09
can yu just give me your screen name for we can talk about this issue

---

### Post by gumbald on 2009-02-09
This is a forum, people are helping... Which bit didn't you manage to do?

---

### Post by gt8ost4l on 2009-02-09
its a complicated matter either way it takes to long here for yus to comment back so why not instant messaging

---

### Post by redroad55 on 2009-02-09
Because there are many people reading a thread and if we help you and they have the same problem we help them also .. I know it can be tedious sometimes but be patient and be willimg to learn as you go and it will all work out .. Best to you 

It sure beats the windows forums .. HaHaHa

---

### Post by gumbald on 2009-02-09
We're not personal slaves. Posting here allows other people with the same problem to get a solution. What was the terminal outputs to **wolfen69**'s commands?

---

### Post by gt8ost4l on 2009-02-09
hahaha speaking bout windows the files got corrupted so i transfered to ubuntu and its real hard i try real hard installing thr flash plugin and each time nothing happens by the way how did yu install it i did what they told me and still nothing i really think its my computer

---

### Post by gumbald on 2009-02-09
> **gt8ost4l said:**
> hahaha speaking bout windows the files got corrupted so i transfered to ubuntu and its real hard i try real hard installing thr flash plugin and each time nothing happens by the way how did yu install it i did what they told me and still nothing i really think its my computer

1) Open a terminal.

2) Enter:

```
sudo apt-get remove flashplugin-nonfree
```

then

```
sudo apt-get clean && sudo apt-get autoremove
```

3) Go to [here]("http://get.adobe.com/flashplayer") and download the .deb for ubuntu 8.04+ to your Desktop.

4) Close Firefox.

5) Double-click the file on your desktop and allow it to install.

If you get errors during step 3, paste them in here and people can help. Just saying "it doesn't work" doesn't allow anyone to help you...

---

### Post by gt8ost4l on 2009-02-09
well ur method still didnt work but i updated the system and noticed shockwave got installed but i have one small issue no sound dammit came so close

---

### Post by redroad55 on 2009-02-09
Try this guide to see if you can resolve sound issue..[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")
Post back..

---

### Post by k3ttc4r on 2009-02-09
> **gt8ost4l said:**
> well ur method still didnt work but i updated the system and noticed shockwave got installed but i have one small issue no sound dammit came so close

no sound from flash, or no sound in general?

---

### Post by gt8ost4l on 2009-02-09
thanks i finally got it to work ha lol

---

### Post by crjackson on 2009-02-09
> **gt8ost4l said:**
> thanks i finally got it to work ha lol

And what was the solution for the benefit of the other readers?

---

### Post by gt8ost4l on 2009-02-09
well if they get no sound with the shockwave player they just go to that page that redroad55 gave me and install that alsa program using the terminal its really simple

---

### Post by gumbald on 2009-02-10
> **gt8ost4l said:**
> well if they get no sound with the shockwave player they just go to that page that redroad55 gave me and install that alsa program using the terminal its really simple

There we go, forums can be useful...

---

