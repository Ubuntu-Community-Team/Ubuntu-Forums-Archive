---
title: "Nvidia settings only working till next boot"
date: 2009-12-01
forum: Multimedia Software
---

### Post by marcgh on 2009-12-01
Hi,

My (new) ATI HD4850 GPU fried a week ago. I got hold on an older type NVIDIA GFORCE 7200GS video card.

My setup (2 screens is as follows:
screen 0: on the right (1024 x 768 )
screen 1: on the left of screen 0 (1440 x 900)

I am using the proprietary driver NVIDIA 180

I can have all this setup and working well by doing this:

1. gksudo nvidia-xconfig   
   followed by logout/login.

2. gksudo nvidia-settings 
   I enable the 2 screens, put them left & right where they belong,
   enable (or not) cinerama and make sceen 1 my default screen.
   Apply and Save to X configuration file.
   Again I logout/login

This will work just fine but if I restart screen 1 and 0 will stay blank and my only way out is CTRL+ALT+F1 then login then again gksudo nvidia-xconfig followed by shutdown 0 command.

I am usually a very patient person, I don't give up easy but after 1 week googling around and reading so much trying to solve this problem I am getting a bit frustrated.

I thank you in advance for any help and assistance,
Marc

---

