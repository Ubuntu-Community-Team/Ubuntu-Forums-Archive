---
title: "Network not showing up in Conky"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by TheDexter1111 on 2010-08-20
Hi guys, I apologise if this is the wrong place to post this, please move if necessary. 

Im kinda new to conky, I have everything working fine, but the main reason o wanted to use it was to monitor my network usage etc.. As you can see in the scrot the network is blank...

If anyone knows how i can get my conky to show the network that would help alot :)


here is my conkyrc

------------------------------------------------------------------
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# set to yes if you want Conky to be forked in the background
background yes

# Create own window instead of using desktop (required in nautilus)
own_window no
#own_window_type override
#own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes
xftfont Bitstream Vera Sans Mono:size=8
xftalpha 0.9

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
#font arial

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 60

# stuff after 'TEXT' will be formatted on screen


TEXT

${color white}${color green}[${color white}$nodename${color green}]:
${color white}$sysname $kernel on $machine
${color white}Uptime: $uptime
${color orange}CPU ${hr 2}$color
${freq}MHz   ${color green}Load: ${color white}${loadavg}   ${color green}Temp: ${color white}${acpitemp}F
${color green}processes: ${color white}$processes	${color green}running: ${color white}$running_processes
$cpubar
${cpugraph 00ff00 ffffff}
${color green}NAME             PID       CPU%      MEM%${color white}
${color #ffff00}${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}${color white}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${color orange}MEMORY / DISK ${hr 2}$color
${color green}RAM:   ${color white}$memperc%   ${membar 6}
${color green}Swap:  ${color white}$swapperc%   ${swapbar 6}

${color green}Root:  ${color white}${fs_free_perc /}%   ${fs_bar 6 /}
${color green}ISO :  ${color white}${fs_free_perc /media/hda1}%   ${fs_bar 6 /media/hda1}
${color green}APPS:  ${color white}${fs_free_perc /media/hdb1}%   ${fs_bar 6 /media/hdb1}
${color orange}NETWORK (${addr eth1}) ${hr 2}$color
${color green}Down: ${color white}${downspeed eth1}k/s ${alignr}${color green}Up: ${color white}${upspeed eth1}k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1 
25,140 000000 00ff00}
${color green}Total: ${color white}${totaldown eth1} ${alignr}${color green}Total: ${color white}${totalup eth1}
${color green}Inbound: ${color white}${tcp_portmon 1 32767 count} ${color green}Outbound: ${color white}${tcp_portmon 32768 
61000 count}${alignr}${color green}Total: ${color white}${tcp_portmon 1 65535 count}
Connections ${tcp_portmon 32768 61000 count} ${alignr} Service/Port
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}
${color orange}BLOCKED IPs ${hr 2}$color
${execi 30 tail -n5 /var/log/moblock.log | fold -w50}

-----------------------------------------------------------------

---

### Post by TheDexter1111 on 2010-08-20
Id just like to add that this conky config isn't mine, and I give appropriate credits to the author (who i cannot name as I found this on the web some time ago).

feel free to give credit if you recognise it and/or know who wrote it :D

Thanks

---

### Post by TheDexter1111 on 2010-08-20
anybody? 

if this is the wrong section to post this please direct me to the appropriate thread

---

### Post by TheDexter1111 on 2010-08-22
bump

---

### Post by biltong on 2010-08-22
I have the same problem.  I've been using conky for a while now and moved recently from a PC to a laptop. Everything works fine except the upspeed and downspeed of wlan0, there is simply no activity. My ifconfig only gives me only eth0 & wlan0.

UP: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 BEBEBE BEBEBE}
Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 BEBEBE BEBEBE}

The funny thing is that the signal strength does get displayed.
Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}

Got any ideas.

---

### Post by TheDexter1111 on 2010-08-23
Hmmm not sure, I tried changing mine from eth1 to eth0 as i had noticed that almost everyone elses config was eth0 (i dont really know why but thought it was worth a shot..) but that didn't work.  Would changing the eth1 to wlan1 or wlan0 work?? cant hurt to try i suppose... but Its annoying cos i do a bit of downloading and would like to monitor the ul and dl!

i've been googling like mad to find an answet but to no avail. the crunchbang forums have tones of configs but no threads answering this question.. I might make one tonight.

---

### Post by TheDexter1111 on 2010-08-23
Ok so that solved it.. 

i think i kinda understand why, but the eth1 was wrong.. im assuming thats for ethernet cable internet and wlan0 is for wireless.. none the less, it worked and i now have it all working :)

---

### Post by biltong on 2010-08-23
Well, I tried the following:

Up eth0: ${upspeed eth0} kb/s
Up eth1: ${upspeed eth1} kb/s
Up wlan0: ${upspeed wlan0} kb/s
Up wlan1: ${upspeed wlan1} kb/s

Still no luck... but signal does get displayed on wlan0.

Seems hopeless. :-(

---

