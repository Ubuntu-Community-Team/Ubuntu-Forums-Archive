---
title: "rhythmbox-client info no longer displayed in Conky following upgrade to Xubuntu 15.10"
date: 2016-01-01
forum: Multimedia Software
---

### Post by cannon44fodder on 2016-01-01
I have been using rhythmbox-client to display song info in Conky for a few years now. I recently upgraded from Xubuntu 14.10 to Xubuntu 15.10 and the conky config that worked as expected in 14.10 no longer shows song info when Rhythmbox is playing. 

I checked a Xubuntu 15.04 install, and the rhythmbox-client info doesn't show in Conky there either.

Anybody else having this problem? Can anyone point to a solution?

Conky script included below...

```
background yes
use_xft yes
xftfont sans:size=9:style=bold
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent no
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
#minimum_size 400 200
#maximum_width 600
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
#default_color d8d8d8
#default_color black
default_color white
default_shade_color 000000
default_outline_color d9d7d6
alignment top_middle
gap_x 12
gap_y 0
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
##############################################
TEXT
${color yellow}CPU 1:$color ${cpu cpu1}% ${color yellow}CPU 2:$color ${cpu cpu2}% ${color yellow}RAM:$color $mem ($memperc%) ${if_running rhythmbox}| $color${exec rhythmbox-client --print-playing-format "%ta - %tt [ %te / %td ]"}$endif

```

---

