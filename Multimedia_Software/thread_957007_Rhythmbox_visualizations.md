---
title: "Rhythmbox visualizations"
date: 2008-10-23
forum: Multimedia Software
---

### Post by Sin@Sin-Sacrifice on 2008-10-23
I was wondering if there's a terminal command or something I can use to set up my lircrc and turn on the visualizations with the remote. I got shuffle and repeat buttons to work but I can't seem to find anything to put in for the visualizations.

---

### Post by Sin@Sin-Sacrifice on 2008-10-24
Come on peoples... I know there has to be a way. I got the repeat and shuffle working... Please.

---

### Post by Sin@Sin-Sacrifice on 2008-12-22
One last bump attempt....

---

### Post by nerver on 2009-02-16
Hey,

Hopefully this isn't too late to help you.

Now, I am not an expert in Lirc, but I have dabbled a bit seting up my mythbox.

The way to start the visualizations in Rhythmbox on a keyboard is to press "ALT+V" and then "V".

So as I see it you have 2 options for your problem.

1. Set up 2 new buttons on your remote in lirc. One to do the "ALT+V" and one for "V" and then after you start rhythmbox, press them in sequence on your remote when you want to turn on visualizations.

Example:

 begin
  prog = rhythmbox
  remote = Hauppauge_Gray
  button = Red
  repeat = 0
  config = ALT+V
  end

 begin
  prog = rhythmbox
  remote = Hauppauge_Gray
  button = Green
  repeat = 0
  config = V
  end

However this is awkward and less than ideal.

Option 2 is to setup a script to be executed by lirc when you press a specific button. This option is better, but slightly more complicated and I unfortunately do not know how to walk you through doing it as I have never needed to do this, but I do know that it is possible. 

If you're looking for a quick solution try option one and hopefully its not too cumbersome.

Cheers,
-Sean

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
Wow... going back through my old posts to mark solved from when it wasn't available is turning out to be gold. Now they just need to bring back the thanks button. Anyway... if you happen to come by this again thanks for the workaround. Works like a charm.

---

### Post by nerver on 2009-11-16
You're welcome, I'm happy I was able to help :)

---

