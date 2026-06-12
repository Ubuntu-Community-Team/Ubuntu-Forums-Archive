---
title: "Ardour + JACK error?"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by Prosis on 2007-06-29
Hello

When I start Ardour-GTK I get a message box that reads:

```
ardour: unplugged

Ardour could not connect to JACK
There are several possible reason:

1)JACK is not running.
2)JACK is running as another, perhaps root.
3)There is already another client called "ardour".

Please consider the possibilities, and perhaps (re)start JACK.
```

What can I do.  I know that, when I tried Audacity I was unabled to install my microphone.  But I have no audio problems normally.

Thank you :D

---

### Post by christhemonkey on 2007-06-29
You need to start JACK before you start Ardour.

I would recommend you use Qjackctl to control JACK.

```
sudo apt-get install qjackctl 
```

Then launch it from "Applications" >> "Sound and Video" >> "Jack Control"
And click the start button to get it going.

Then you can launch Ardour.

---

### Post by Prosis on 2007-06-29
Alright I'll try this.  Thank you very much

Do you think that had anything to do with my microphone troubles with Audacity?

---

### Post by christhemonkey on 2007-06-29
Frankly no i dont think it does!

---

### Post by Hanj on 2007-06-29
It probably has nothing to do with the microphone problems. Jack is a program that lets you connect audio applications to each other in a quite advanced way (some applications, like Ardour, can only run via Jack). It's really powerful but can take a while to get used to. More info [here]("http://jackit.sourceforge.net/docs/faq.php").

As christhemonkey said, QJackCtl is the easiest way to deal with Jack. If you plan to record stuff using Ardour, you will probably need a real time kernel as well. Check out the repos for [Ubuntu Studio]("http://ubuntustudio.org").

---

### Post by Prosis on 2007-06-30
UbuntuStudio screwed up my Ubuntu.  Now I don't have splash screens and my wireless connection has disapeared.  It's no longer available.  I'll have to reinstall everything now...great.

---

### Post by lyceum on 2007-06-30
I am having the same problem. How do you load JACK? I sudo apt-get install jack and it is installed, but I do not know how to turn it on. I cannot find it on any lists. Another program said I needed jackd, whick I also loaded, but do not know how to start. I am very confused. 

:confused:

edit - I am not attaching any instruments to my PC, it is all just electronic sound with wave files I created. Does this matter?

---

### Post by christhemonkey on 2007-06-30
Install Qjackctl!


```
sudo apt-get install qjackctl 
```

Then launch it from Applications > Sound and Video > JACK Control.

Electronic sounds are fine with jack it just deals with routing audio from one place to another (like a porgrams output to your speakers or another programs input) with no added latency.

---

### Post by lyceum on 2007-06-30
You know what, I loaded that. Then I did a forum search and found this thread and load it again, but still could not find it. You reply and magically it is there. Either my computer is out to get me or I need more sleep. :lol:

Thanks!

---

### Post by christhemonkey on 2007-06-30
No worries!


Know the 'need more sleep' feeling!!
Never mind, il sleep tomorrow....

---

### Post by iamaqbot on 2007-10-08
i had a problem but fixed it and don't know how to delete

---

### Post by Sawman on 2007-10-09
I don't want to hi-jack (no pun intended) this thread, but can someone please help this total noob get Ardour to run? After spending an entire day downloading and compiling and getting dependencies, I thought I finally made it . . . :confused:  But when I tried to run ardour I get :

mike@mike-laptop:~$ ardour
The program 'ardour' is currently not installed.  You can install it by typing:
sudo apt-get install ardour-gtk
Make sure you have the 'universe' component enabled
bash: ardour: command not found

When I did "make" and "make install" it seemed to build fine (after getting the dependencies).
Please remember, I am borderline clueless on what I'm doing ! :frown:

Thanks in advance
Mike

---

