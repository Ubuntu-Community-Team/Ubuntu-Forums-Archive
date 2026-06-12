---
title: "video won't save resolution"
date: 2009-05-25
forum: Multimedia Software
---

### Post by steve984 on 2009-05-25
I have a nvidia 6100 with the most recent driver and when I boot up it it starts at a high resolution. I can change it but I have to do it every time I boot up. when I try to csave it it say can write to x-org file. any help would be appreciated

---

### Post by shaloken on 2009-05-25
> **steve984 said:**
> when I try to csave it it say can write to x-org file. 
 you can or can't wite on your xorg.conf?
if you can't :
 try to use sudo gedit /etc/X11/xorg.conf

---

### Post by ibokozan on 2009-05-25
hello this is my first message in here. i am from turkey 21 and student at unv. i use ubuntu 9.04

i have fx 5200 video card. i have the same problem as steve984. how can i edit that file and what must i write there.

i changed the resolution 800/600 to 1024/768 when restart it back to 800/600 when i push the save button it says as in this picture.....

[http://img529.imageshack.us/img529/3448/ekrangrnts.png](http://img529.imageshack.us/img529/3448/ekrangrnts.png)

---

### Post by ibokozan on 2009-05-25
please help me :)

---

### Post by irv on 2009-05-25
> **ibokozan said:**
> hello this is my first message in here. i am from turkey 21 and student at unv. i use ubuntu 9.04

i have fx 5200 video card. i have the same problem as steve984. how can i edit that file and what must i write there.

i changed the resolution 800/600 to 1024/768 when restart it back to 800/600 when i push the save button it says as in this picture.....

[http://img529.imageshack.us/img529/3448/ekrangrnts.png](http://img529.imageshack.us/img529/3448/ekrangrnts.png)
If you are trying to save the setting using NVIDIA X Server Setting, try running it under sudo and then you will have the rights to save it.

---

### Post by irv on 2009-05-25
> **ibokozan said:**
> please help me :)

By what means are you trying to save it? What ever you use you must be super user. "sudo".

---

### Post by ibokozan on 2009-05-25
did you look picture i give on the link?

---

### Post by Brynster on 2009-05-25
ok sussed it

open a terminal window and type

sudo nvidia-settings

it will ask for your password

once your password has been entered the nvidia control panel will appear. set the resolutiuon to what you want and then save.


This worked for me, hope it helps you guys too :-)

---

### Post by ibokozan on 2009-05-25
> **Brynster said:**
> ok sussed it

open a terminal window and type

sudo nvidia-settings

it will ask for your password

once your password has been entered the nvidia control panel will appear. set the resolutiuon to what you want and then save.


This worked for me, hope it helps you guys too :-)

it gives the same error as in the picture :(

---

### Post by Brynster on 2009-05-25
Sorry ibokozan I don't know what that error means. 


Have you tried to google the error see what/if others are saying?

---

### Post by ibokozan on 2009-05-25
> **Brynster said:**
> Sorry ibokozan I don't know what that error means. 


Have you tried to google the error see what/if others are saying?

yes they are saying something in my mother language (turkish) but i really dont understand them :P

[http://ubuntu-tr.org/]("http://forum.ubuntu-tr.org/")

and now this adress is closed for 1 week for going to a new host. :(

---

### Post by ibokozan on 2009-05-27
is there any another one like me have this problem too?

---

### Post by wdypdx1 on 2009-05-30
I have the same issue. I "have" tried saving the xorg file as sudo, but no luck.

I have used the Nvidia X server settings tool under sudo and each time I restart my computer I must reset the resolution to my desired settings. I have a GeForce FX 5700. 

??

---

### Post by xc3RnbFO8P on 2009-05-30
Did you try System> Display (do not use graphics vendors tool)
and choose your resolution.

---

### Post by wdypdx1 on 2009-05-30
Yes, and I get the following message box:

"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?" 

So, I click the "yes" button. And get the nvidia tool.

If I click the "no" button a display preferences window opens. This window shows the correct resolution, but says the monitor is unknown and will not detect my monitor. I clicked apply in that window and now I'll have to restart to see if the res comes back as intended.

---

### Post by wdypdx1 on 2009-05-30
Thanks! That did the trick!

---

