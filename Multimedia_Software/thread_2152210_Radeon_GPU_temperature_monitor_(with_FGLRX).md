---
title: "Radeon GPU temperature monitor (with FGLRX)"
date: 2013-06-07
forum: Multimedia Software
---

### Post by Ayel on 2013-06-07
This must be the right forum, since I just installed Ubuntu couple of days ago :P

Ok, so after I installed FGLRX AMD driver, my GPU temp sensor has disappeared. From my research it's normal that lmsensors don't work anymore for the GPU and I can only get the temperature with aticonfig.

Is there any  way to monitor GPU temperature ? 

Ideally, I'd want to make this work with GKrellM, which I really like.

I found a patch, but I don't know if it's any good, since I don't understand how/where to install it (don't understand what the guy means by "run the patch from the base dir of the source"). On the other hand, the link is 5 years old, in the meantime, people may have a better solution.

[http://phoronix.com/forums/showthread.php?12285-Patch-for-radeon-temp-in-gkrellm](http://phoronix.com/forums/showthread.php?12285-Patch-for-radeon-temp-in-gkrellm)

---

### Post by verymadpip on 2013-06-07
There's a command one can issue from the terminal that will give you the temp. (I use it & also one for fan speed).
I'm not near my rig at the moment & for the life of me I can't recall what it is :)
Actually I think it's something like

 ```
aticonfig -odgt
```

It's do-able though.

Good luck.

---

### Post by Ayel on 2013-06-07
Thanks, but I have mentioned that I am already using **aticonfig** successfully as a command line tool.

However this isn't very practical. I mean - having to type into the terminal everytime I wish to keep an eye on my GPU stats.

---

### Post by craig10x on 2013-06-07
A nice little program for monitoring cpu temperature is called: psensor and it's available in the software center...i use it and it works great...
It will start up automatically when you boot up each time and appears on your unity dock as an icon with the main temp reading and you can open it at any time to see all the readings.
After downloading, open it and just check all the boxes on the list you see to activate them all...

If you would rather start it manually each boot up, you can go to "start up programs"and uncheck it...
And if you right click the Psensor Icon on the unity dock and select quit, it will just run on the dock with the main temp number...

---

### Post by QIII on 2013-06-07
Hello and welcome to the forums!

Unfortunately, ATI's Overdrive is a command-line-only affair in Linux.

Not at home right now, but I use conky to monitor my GPU temp and activity.  If I remember, I'll post back with a very basic conky (and instructions how to install the conky packages) that will display the GPU data for you.

Best wishes!

---

### Post by The Cog on 2013-06-07
Moved to multimedia and video. Will probably get better attention and buried more slowly there.

---

### Post by QIII on 2013-06-08
Ayel --

A bit late with this, sorry!  And it's late at night, so I will probably forget something important in the following.  :)

It would be difficult to get into the nitty-gritty of conky in one thread, but I'm going to tell you how to install the conky packages you will need and I'll give you a stripped out conkyrc.  You'll have to make some changes to the conkyrc to fit how often you want it to refresh, colors, fonts, etc.  This may not work right at the start because I got rid of some formatting so you can make it suit your needs.  Also, some of the settings at the top of the sample conkyrc may not apply.

You should be able to find a number of good conky tutorials on the Forum (and I'll check back by if you need help)

So, install what is more or less the necessary parts of conky:

```
sudo apt-get install conky-all
```

Create a folder in your /home/yourusername directory and call it .conky (most people us the "dot", which makes it a hidden folder).

In that folder, open a file with a text editor and paste the following into it:

```
####
#  general startup settings
####

background yes
update_interval 0.5
text_buffer_size 1024
total_run_times 0
alignment top_right
gap_x 35
gap_y 65
minimum_size 250 250
maximum_width 250

####
#  Some window setup
####
own_window_class Conky
own_window yes
own_window_type normal
own_window_argb_visual yes
own_window_transparent yes
own_window_argb_value 0
own_window_hints below,skip_pager,skip_taskbar,undecorated,sticky
background yes
# font defaults:
use_xft yes
xftfont RadioStars:size=7
xftalpha 0.9
override_utf8_locale yes

####
# images, buffering, shading
####
imlib_cache_size 60
double_buffer yes
draw_shades no
default_shade_color 777777

####
# misc text formatting
####
short_units yes
pad_percents 2
border_inner_margin 0
uppercase no
use_spacer right

####
# outlines and borders
####
draw_outline no
draw_borders no
draw_graph_borders no
border_width 0

####
# stdout/console printing
####
out_to_ncurses no
out_to_console no

####
## process settings
top_name_width 4
#no_buffers yes
####

####
# sampling
####
cpu_avg_samples 2
net_avg_samples 2

####
## everything below 'TEXT' is drawn on screen
####
     
TEXT
${color white}${font Monaco:size=7}Load${goto 105}Temp${alignr 30}Fan speed
${voffset 10}${color white}${font Monaco:size=7}${execi 0.2 aticonfig --odgc --odgt --adapter=0 | egrep -i "load|temperature" | xargs echo | awk '{print $4 "  " $9 "°C "}'}${alignr 28}${execi 0.2 aticonfig --pplib-cmd "get fanspeed 0" | grep -i result | awk '{print $4}'} 

```

Save the file as conkyrc

You'll have to fiddle with spacing a little bit.

Test to see if it works by 

```
conky -c /home/yourusername/.conky/conkyrc
```

I'll stop by later and see if you are having any difficulties.

---

### Post by Ayel on 2013-06-08
@ craig10x - Tried psensor, but didn't know how to put aticonfig output into it.

Thanks QIII, seems I got conky working. Quite happy about this :D

Only weird thing is that GPU load is always zero. Even while temperature is getting hot.

---

### Post by manoseskintzis on 2013-12-30
you can add a conky to your desktop show temprature i had problem with nvidia 6100 
temprature was 75-85 so i want to monitor the temp at all times,sorry i didnt read all the thread :(

---

