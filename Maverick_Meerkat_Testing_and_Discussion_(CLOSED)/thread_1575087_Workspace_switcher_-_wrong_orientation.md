---
title: "Workspace switcher - wrong orientation"
date: 2010-09-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Yumi on 2010-09-15
I have my panels on the right sight due to the oblong size of my modern monitor. Since todays update the workspace-switcher does not rotate orientation. It displays normally if I have the panel on the bottom. 

Also the panel refuses to be on the left. Choosing top and the panel is in the middle of the screen!

The picture shows inside the red circle 5 sqashed up workspaces.

---

### Post by UnSandpiper on 2010-09-15
How does it look when you put the panel to the bottom?

Because, I think this is related to the problem that I have.
I only upgraded from 10.04.1 yesterday, so I don't know if it worked correctly before that.

My workspaces are not aligned in rows anymore, although its configured like that.
In the attached picture you can see 4 workspaces side by side, although it should be 2 on top and two below.

---

### Post by Yumi on 2010-09-15
You are right, according to your layout I moved the panel to the bottom, selected 4 workspaces in 2 rows. But it shows only 1 row even if I make the panel 89 pixel in hight.

---

### Post by duketogo on 2010-09-17
I just want to say this problem is happening to me too.  I selected six workspaces in two rows, and they're only displaying in one row.

---

### Post by uRock on 2010-09-17
Does swapping to Ambiance or Radiance, then back again fix it? That is what I have had to do before to get things look right.

---

### Post by Yumi on 2010-09-17
Switching theme had no effect on the original problem. - unfortunately

---

### Post by duketogo on 2010-09-17
Me neither - switching to another theme and back had no effect (I was using Ambiance in the first place).

---

### Post by UnSandpiper on 2010-09-17
It has been fixed for me with todays updates.

---

### Post by Yumi on 2010-09-17
Not here I am afraid.

---

### Post by cariboo on 2010-09-17
Does increasing the height of the lower panel make a difference?

---

### Post by Yumi on 2010-09-17
No! As I mentioned above, I increase the hight of the panel to 86px and the same. Problem is unrelated to panel size.

---

### Post by cariboo on 2010-09-17
Oops, I missed that. 

I don't have the work place switcher in the default location, but there is an entry in gconf for it, does anything look strange there?

---

### Post by Yumi on 2010-09-18
Cariboo you might be onto something. But I know too little about gconf and schemas to find a problem.

However, I found an old bug stating that the panel would not behave as expected when 3D cube functions are enabled. But .....

The problem started when I updated a few days ago and I switchen from nouveau to nvida driver at the same time.

It is getting weird. When I open a second openoffice writer document the program indicator icons on the panel flicker like wild. This stops immediatly as I close the second document.

My hard disk is quite full. Could it have something to do with this? Maybe no space for temporary files?

---

### Post by cariboo on 2010-09-18
You should get a notifiaction when your hard drive has to little free space. I had an app that was filling up a couple of log files and I had a notification pop-up when there was only 200Mb of free space left, this happen three times, so the notification does work. :)

---

### Post by UnSandpiper on 2010-09-20
Strange, it was fixed for me for one day... or until reboot... didn't notice when it stopped working again. Now my workspaces are again in one row.

---

### Post by mortski on 2010-09-20
The LP bug:

[https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/642746](https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/642746)

---

### Post by Yumi on 2010-09-20
Thank you for the bug report. Thats it. It seems to effect only very few systems. We'll see.

---

### Post by Yumi on 2010-09-26
Problem solved by yesterdays update

---

