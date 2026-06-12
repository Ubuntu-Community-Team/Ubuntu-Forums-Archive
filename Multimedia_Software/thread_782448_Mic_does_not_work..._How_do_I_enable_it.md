---
title: "Mic does not work... How do I enable it?"
date: 2008-05-05
forum: Multimedia Software
---

### Post by Kdar on 2008-05-05
Ok.. My sound is working great.

But my mic sadly is not working.

I am using basic, logitech USB mic.

How do I enable it?

----
Also.. I am using 2.1 speaker system.. What do I have to enable?

Master, PCM (what does it mean?), Front, and Line-in (I guess if I will connect headphones..)
Or I need to and something else?

---

### Post by Kdar on 2008-05-05
bump.. can anyone help?

---

### Post by xc3RnbFO8P on 2008-05-05
Read this:
[http://www.linuxforums.org/forum/ubuntu-help/111002-installing-usb-mic.html]("http://www.linuxforums.org/forum/ubuntu-help/111002-installing-usb-mic.html")

---

### Post by Zorael on 2008-05-05
Are you sure you've unmuted it and set it to be your input device? There's a terminal application to manage volumes, and there's likely a graphical application in Gnome as well.
```
$ alsamixer
```

edit: See [http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/](http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/). Google is your friend.

---

### Post by Kdar on 2008-05-06
How can I restore original Speaker/Voice/Mic settings?

---

### Post by cespinal on 2008-05-07
same problem here... I usually see people in the forums talking about alsamixer features that I dont have!!! 

the big question is how do I get a version of alsamixer that shows me the rest of the features? 

thanks

---

### Post by pedro_orange on 2008-05-07
> **cespinal said:**
> same problem here... I usually see people in the forums talking about alsamixer features that I dont have!!! 

the big question is how do I get a version of alsamixer that shows me the rest of the features? 

thanks

Have you tried moving further to the right? 
Or hitting tab?

They're usually more options than that.
Just so you know; you're not alone; my mic is a pain in the ***. And it's not even USB.

To the OP: PCM means "Pulse-code Modulation" and is basically digital representation of an analogue signal.

---

### Post by cespinal on 2008-05-08
MMM NOPES! those are the only options I have got!, is there anyway to get another version of alsamixer with all the options? (I guess this one is the latest version tho).

Also, If I hit spacebar to try to open the capture options, nothing happens!! 

any hints??? this is starting to hurt right in my a$$ lol

---

### Post by hermes0710 on 2008-05-08
Have you tried clicking "Edit">"Preferences" and tick the components that will be present from there?

---

### Post by pbeesley on 2008-05-08
[http://ubuntuforums.org/showthread.php?p=4891799#post4891799](http://ubuntuforums.org/showthread.php?p=4891799#post4891799)

---

### Post by erikthedrink on 2009-09-08
In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system. If not, replace 1 with either a 0 or a 2.:P

---

### Post by andrew13321 on 2009-09-08
Open volume control, click preferences, then click on microphone. If it isn't highlighted, highlight it and turn the volume up.

---

