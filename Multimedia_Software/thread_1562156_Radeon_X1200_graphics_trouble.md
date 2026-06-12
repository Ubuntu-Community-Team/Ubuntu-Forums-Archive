---
title: "Radeon X1200 graphics trouble"
date: 2010-08-27
forum: Multimedia Software
---

### Post by Mansteel on 2010-08-27
Please Help me with my new graphics driver someone. 

I have tryed pretty much everything and im becomming tired of not being able to use my laptop fully. 

My graphics card is ATI Radeon X1200 

Very few games work in my PC. When i try to start then i only see a black screen flash quickly and nothing happens. 

I have installed the driver from ATI's homepage. But i am not sure if it works or how to make it work. 

I have tryed to see if i have activated Direct rendering:
> glxinfo | grep rendering


And the output is this. 
> No (If you want to find out why, try setting LIBGL_DEBUG=verbose) 

---

### Post by forcrz69 on 2010-08-27
First and Foremost HI 

2nd. Are you logged in as Admin or as a superuser?

3 Did you just try going to System>Administration>Hardware drivers and see if a driver was already active?

4 What kind of laptop are we looking at here? Dell, Acer, HP....

Let us know that so that way we can know what way we should take you.

---

### Post by Yellow Pasque on 2010-08-27
> I have installed the driver from ATI's homepage.
Don't do that. Your card isn't supported and it will only screw up the system. To fix: 
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

---

### Post by Mansteel on 2010-08-27
> **forcrz69 said:**
> First and Foremost HI 

2nd. Are you logged in as Admin or as a superuser?

Hi thanks for the replies.
I am using sudo when i'm installing stuff. 

> **forcrz69 said:**
> 
3 Did you just try going to System>Administration>Hardware drivers and see if a driver was already active?

Yes tried that it says: 
"No proprietary drivers are in use on this system" 

> **forcrz69 said:**
> 
4 What kind of laptop are we looking at here? Dell, Acer, HP....

Emachine E626 - 3 gb ram.

---

### Post by Mansteel on 2010-08-28
please reply...

---

