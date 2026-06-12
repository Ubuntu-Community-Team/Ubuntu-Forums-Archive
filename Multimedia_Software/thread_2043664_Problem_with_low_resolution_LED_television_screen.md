---
title: "Problem with low resolution LED television screen"
date: 2012-08-17
forum: Multimedia Software
---

### Post by offir on 2012-08-17
I have a computer and I installed it
Ubuntu 10.04
The graphics card is nvidia fx 5200

The computer is connected to the screen LED television  lg 42lv371y
For some unknown reason
You can not put a higher resolution than 640x480
Drivers manager
Shows me two options for drivers
173 and 93
Of the two the 173 is recommended

I tried to put the 173
No change
I put the 93
Screen went black did not see anything:confused:

I tried without drivers
Maximum resolution up to 1024x768


Screen resolution is 1920x1080:)


Computer is connected to standard CRT screen
Maximum resolution computer gives is 2600x2400
Or even higher](*,)




What could be the problem
Why I can not put a high resolution
Of 1920x1080

By the way I tried to add the resolution manually through the terminal
Also did not help



If the question does not fit this forum
You can delete

---

### Post by offir on 2012-08-17
I have a computer and I installed it
Ubuntu 10.04
The graphics card is nvidia fx 5200

The computer is connected to the screen LED television lg 42lv371y
For some unknown reason
You can not put a higher resolution than 640x480
Drivers manager
Shows me two options for drivers
173 and 93
Of the two the 173 is recommended

I tried to put the 173
No change
I put the 93
Screen went black did not see anything

I tried without drivers
Maximum resolution up to 1024x768


Screen resolution is 1920x1080


Computer is connected to standard CRT screen
Maximum resolution computer gives is 2600x2400
Or even higher




What could be the problem
Why I can not put a high resolution
Of 1920x1080

By the way I tried to add the resolution manually through the terminal
Also did not help



If the question does not fit this forum
You can delete
The question is also the General Help forum
[http://ubuntuforums.org/showthread.php?p=12177805#post12177805]("http://ubuntuforums.org/showthread.php?p=12177805#post12177805")

---

### Post by offir on 2012-08-17
I have a computer and I installed it
Ubuntu 10.04
The graphics card is nvidia fx 5200

The computer is connected to the screen LED television lg 42lv371y
For some unknown reason
You can not put a higher resolution than 640x480
Drivers manager
Shows me two options for drivers
173 and 93
Of the two the 173 is recommended

I tried to put the 173
No change
I put the 93
Screen went black did not see anything

I tried without drivers
Maximum resolution up to 1024x768


Screen resolution is 1920x1080


Computer is connected to standard CRT screen
Maximum resolution computer gives is 2600x2400
Or even higher




What could be the problem
Why I can not put a high resolution
Of 1920x1080

By the way I tried to add the resolution manually through the terminal
Also did not help



If the question does not fit this forum
You can delete
The question is also the General Help forum
[http://ubuntuforums.org/showthread.php?p=12177805#post12177805]("http://ubuntuforums.org/showthread.php?p=12177805#post12177805")

---

### Post by trundlenut on 2012-08-17
How are you connecting the computer and tv? HDMI? VGA?

I had a TV connected to a new windows computer and we couldn't get the resolution past 1024x768 using the VGA connector, switched to HDMI and voila 1920x1080.

Having tried another screen it would appear the problem was the TV.

---

### Post by oldfred on 2012-08-17
@offir 
Threads merged.
Please do not start identical threads in different sub-forums. We are all volunteers and do not want to have to duplicate others responses.

---

### Post by offir on 2012-08-18
I connected using vga cable

I do not have an option for hdmi on the computer


Can I connect hdmi cable to VGA connector with an adapter?


will it work ?



About duplicate messages the reason is i didnt know Where should I post
And as I wrote if that makes a problem feel free to delete it

---

### Post by oldfred on 2012-08-18
I think because video card is so old, it does not have HDMI. You cannot go from VGA analog to HDMI digital. 

There are adapters for DVI digital no sound to HDMI with sound.

So I think the limit is the TVs VGA input only has a lower resolution.

---

### Post by offir on 2012-08-19
I will try to find a graphics card with dvi port

I'll be back here to report


Thank you

---

### Post by offir on 2012-08-24
As I promised
I came back with a report
trundlenut and oldfred You were right
I changed the graphics card
to a Card with a dvi port

I connected to this port adapter from dvi to hdmi
Then using a regular hdmi cable
I connected the computer to the TV

Indeed, there is a high resolution







The joy was premature




I used a graphics card Model mx440
the driver of the card is installed
Driver Number 96

But the resolution does not exceed 1360 x 768

Normal mode without the driver
No problem
But I want to use effects
And i need the driver

So how can we fix it

---

### Post by oldfred on 2012-08-24
Still an older card.

Do you get the nVidia X server settings in Administration? From that you may be able to change if within the allowed ranges.

---

### Post by offir on 2012-08-24
I changed the graphics card again
This time it fx5200 but with dvi port


The computer is turned on and reaches Desktop
The resolution is 1360 x 768

But for once there is a possibility to Reach to 1920 x 1080
The problem is just that you have to change it manually all the time


And for some reason every time you change the resolution
The color go a bit crazy

---

