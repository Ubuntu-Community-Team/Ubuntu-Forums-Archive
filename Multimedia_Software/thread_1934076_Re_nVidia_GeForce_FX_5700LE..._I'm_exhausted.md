---
title: "Re: nVidia GeForce FX 5700LE... I'm exhausted"
date: 2012-03-01
forum: Multimedia Software
---

### Post by AlisPT on 2012-03-01
Maybe I shouldn't be postiong this here but I don't know...
Read this message and please try to awser it since cosimo didn't.

-------------------MESSAGE SENT TO COSIMO----------------------

Hello.
Firstly I want to apologize for my incorect English!!
Now let's go to the main point.
The desktop I usually use has an nvidia 5700 fx le and I had a lots of problems trying to make it work.(I'ts a real pain in the a$$ being a linux newbie and having to do such a hard work!!!) :(
Moving on, while I was searching the web I found a post about ubuntu problems... with my graphic card mentioned!!!!!!!!!!
I read everything and a solution was found.
However, at the end of the topic you wrote this:

"""""""""""""""""""""""""""""""""""""""""""

Re: nVidia GeForce FX 5700LE... I'm exhausted
Hey guys,
This may be a bit late but the fx series card is no longer supported on current kernels by nvidia.
There are no kernel modules for the fx series cards.
So..no matter what you do... you cannot use the fx series nvidia cards on linux any longer
I have found no solution to this other than using a very old kernel :confused:

coz
"""""""""""""""""""""""""""""""""""""""""""

Just to metion, I am using ubuntu 12.04 LTS.
So, are there any solution about using this GPU on the new ubuntu/linux kernels???
If not, what linux OS would you recommend and is compatible at the same time with my GPU?
It shoud also have a good support from user and it must be noob friendly.

Thank you for your patienty and have a nice day!

-------------------MESSAGE SENT TO COSIMO----------------------

Hope you can answer it!

---

### Post by howefield on 2012-03-01
Post moved to its own thread in the "*Multimedia & Video*" forum.

You'll get more help here rather than tagging on to a 3 year old.

---

### Post by BicyclerBoy on 2012-03-01
The Xorg changes broke the older video drivers..
nVidia has a legacy support driver that has been re-built to work with the later Xorg.

I can't find an easy ppa solution but you can download the driver from nVidia.

**First** read (& print) the driver installation instructions.

[http://www.nvidia.com/object/linux-display-amd64-173.14.31-driver.html](http://www.nvidia.com/object/linux-display-amd64-173.14.31-driver.html)

You have to read & understand the install instructions.
You have to install the required dependencies before attempting install.
You have to understand what a console screen/terminal login is...

---

