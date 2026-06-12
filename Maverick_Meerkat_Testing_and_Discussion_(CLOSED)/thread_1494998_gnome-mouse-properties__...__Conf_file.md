---
title: "gnome-mouse-properties  ...  Conf file?"
date: 2010-05-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by crjackson on 2010-05-27
I'm loving maverick but here is my issue.  Almost 1/2 of the mouse pad surface has become a scroll area.  Is there some way to adjust the size of the scroll area so I can confine it to the edge where it belongs?

---

### Post by wayneericgouin on 2010-05-27
I think I recall a post with a similar issue, someone mentioned the x and y coordinates being in xorg.conf.

check this post to see if it's relevant

[http://ubuntuforums.org/showthread.php?t=519712](http://ubuntuforums.org/showthread.php?t=519712)

---

### Post by crjackson on 2010-05-27
> **wayneericgouin said:**
> I think I recall a post with a similar issue, someone mentioned the x and y coordinates being in xorg.conf.

check this post to see if it's relevant

[http://ubuntuforums.org/showthread.php?t=519712](http://ubuntuforums.org/showthread.php?t=519712)

```
charles@emachines-laptop:~$ synclient -m 500
Can't access shared memory area. SHMConfig disabled?
charles@emachines-laptop:~$
```

Thanks, not working for me at this moment. I think I have to make an xorg.conf file and enable it somehow there in the input section.  I don't have time to research right at this exact moment, I've got to run some errands.  So I dig further when I get back. 

Thanks for the link, I think it gives me a good starting point.

---

### Post by wayneericgouin on 2010-05-27
your welcome, I'll see what else I can dig up.

---

### Post by wayneericgouin on 2010-05-27
Well, I can't say with much certainty that I know enough about touchpads in ubuntu to help, but I did come across this post talking about the "man synaptic" configuration which I do believe has something to do with Gsynaptics. However it does mention SHMconfig and edge coordinates. perhaps someone with more relevant experience can help. But try man synaptic in the terminal and see if it makes you go "Ahah".

---

### Post by crjackson on 2010-05-27
> **wayneericgouin said:**
> Well, I can't say with much certainty that I know enough about touchpads in ubuntu to help, but I did come across this post talking about the "man synaptic" configuration which I do believe has something to do with Gsynaptics. However it does mention SHMconfig and edge coordinates. perhaps someone with more relevant experience can help. But try man synaptic in the terminal and see if it makes you go "Ahah".

If possible I'd like to find a way to tweak the gnome-mouse application rather than adding yet another application to manage the mousepad.  That may or may not be possible.  I'm hoping someone with strong knowledge about how to tweak this thing will chime in.

I've NEVER been able to get my mousepad to work satisfactorily on any release. It's either always too touchy or too unresponsive.  It's my Achilles heel with Linux I suppose.

---

### Post by wayneericgouin on 2010-05-28
Yes, I too hope someone with knowledge of this particular scenario would shed some insight, I fully intend on getting a netbook to play around with and I'm sure having a leg-up on potential mousepad fixes would be beneficial to me as well. I do apologize for not being able to assist though.

---

### Post by crjackson on 2010-05-28
Well I haven't found a good solution for this yet, but I will tell you that by installing gpointing-device-settings and enabling "Palm Detection" the touch pad is MUCH more well behaved.

You know the standard gnome-mouse-properties his this tick box for - disable pad when typing on keyboard?  Well that hasn't worked on ANY of my laptops for several versions.  Installing this package makes it actually work as expected.  I just wish there was a timeout setting on the keyboard thing, and the ability to adjust the area used for scrolling.

---

### Post by Mr. Picklesworth on 2010-05-28
> **crjackson said:**
> ```
charles@emachines-laptop:~$ synclient -m 500
Can't access shared memory area. SHMConfig disabled?
charles@emachines-laptop:~$
```

Thanks, not working for me at this moment. I think I have to make an xorg.conf file and enable it somehow there in the input section.  I don't have time to research right at this exact moment, I've got to run some errands.  So I dig further when I get back. 

Thanks for the link, I think it gives me a good starting point.

synclient has been deprecated for a while now. We now use xinput to configure every attached input device. Sorry, I don't have time to give a detailed tutorial (though I posted some more detailed instructions less than a year ago, and I'm sure there's some other very in-depth stuff out there).

Play around with the xinput command and hopefully it'll start to make sense. You can get a list of all your devices with &#8220;xinput list&#8221;, and a list of all the commands available with &#8220;xinput --help&#8221;.

&#8220;xinput list-props "SynPS/2 Synaptics TouchPad"&#8221; (or 18, which is its id for me), gives me:

```
dylan@dylan-laptop / % xinput list-props 18
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (121):	1
	Device Accel Profile (244):	0
	Device Accel Constant Deceleration (245):
	Device Accel Adaptive Deceleration (247):
	Device Accel Velocity Scaling (248):	1
	Synaptics Edges (297):	1752, 5192, 1620,
	Synaptics Finger (298):	24, 29, 255
	Synaptics Tap Time (299):	180
	Synaptics Tap Move (300):	221
	Synaptics Tap Durations (301):	180, 180,
	Synaptics Tap FastTap (302):	0
	Synaptics Middle Button Timeout (303):	7
	Synaptics Two-Finger Pressure (304):	2
	Synaptics Two-Finger Width (305):	7
	Synaptics Scrolling Distance (306):	1
	Synaptics Edge Scrolling (307):	0, 0, 0
	Synaptics Two-Finger Scrolling (308):	1
	Synaptics Move Speed (309):	0.400000,
	Synaptics Edge Motion Pressure (310):	2
	Synaptics Edge Motion Speed (311):	1
	Synaptics Edge Motion Always (312):	0
	Synaptics Button Scrolling (313):	1
	Synaptics Button Scrolling Repeat (314):	
	Synaptics Button Scrolling Time (315):	1
	Synaptics Off (316):	0
	Synaptics Guestmouse Off (317):	0
	Synaptics Locked Drags (318):	0
	Synaptics Locked Drags Timeout (319):	5
	Synaptics Tap Action (320):	2, 3, 0, 
	Synaptics Click Action (321):	1, 1, 1
	Synaptics Circular Scrolling (322):	0
	Synaptics Circular Scrolling Distance (32
	Synaptics Circular Scrolling Trigger (324
	Synaptics Circular Pad (325):	0
	Synaptics Palm Detection (326):	0
	Synaptics Palm Dimensions (327):	1
	Synaptics Coasting Speed (328):	0.000000
	Synaptics Pressure Motion (329):	2
	Synaptics Pressure Motion Factor (330):	1
	Synaptics Grab Event Device (331):	1
	Synaptics Gestures (332):	1
	Synaptics Capabilities (333):	1, 1, 1, 
	Synaptics Pad Resolution (334):	84, 57
	Synaptics Area (335):	0, 0, 0, 0
	Synaptics Jumpy Cursor Threshold (336):	0

```

From there, I can do something like &#8220;xinput set-prop 18 --type=int 322 1&#8221; to enable Circular Scrolling (322).
To &#8220;save&#8221; a bunch of configuration, you can make a script that runs when you log in and calls the appropriate xinput commands.

Yeah, not as easy as synclient, but it's considerably more sophisticated. GUI tools are getting there, too ;)
If you find this sudden leap in complexity to be demotivating, allow me to re-motivate you: it's possible to add additional mouse pointers (and attach various input devices to them), and GTK+ is going to support that feature much better some day. I'm not telling you how to do it, though :b

I think gpointing-device-settings does xinput, but don't quote me on it&#8230;

---

### Post by crjackson on 2010-05-29
@Mr. Picklesworth,

Okay, thanks for the information.  I'm headed out of town right now and I'll see what I can do with it next week.

---

