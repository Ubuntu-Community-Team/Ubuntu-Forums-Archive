---
title: "Internet Usage Monitor (Working)?"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by Suhel28 on 2011-10-02
I've trying Ubuntu for past few weeks and I really like it. The only thing thats not allowing to use it full time is I am not finding a good straight-to-the-point GUI application for monitoring my daily/weekly/monthly internet usage. I've searched through the internet and found some complex methods. I use system monitor to check out the usage but most of the time its slips off my mind and it strikes me back after I shut down the pc. Kindly help. its kinda costly after crossing the fixed free usage:(


EDIT : Voila! this forum is my lucky charm I just searched google again and shifted the search criteria to "Past week" and found this great blog [NTM - EASY UBUNTU DATA USAGE MONITOR]("http://mikebeach.org/2011/09/easy-ubuntu-data-usage-monitor/") it works like a charm :guitar:

---

### Post by ajgreeny on 2011-10-02
Just to offer an alternative which is in the standard repos, vnstat will do all of the things that NTM can do, and more, in terms of monitoring.  It can also be used with conky to give an ongoing live update of speeds and amounts of data up and down.  See screenshot of part of my conky display.

---

### Post by Suhel28 on 2011-10-02
> **ajgreeny said:**
> Just to offer an alternative which is in the standard repos, vnstat will do all of the things that NTM can do, and more, in terms of monitoring.  It can also be used with conky to give an ongoing live update of speeds and amounts of data up and down.  See screenshot of part of my conky display.

wow thats cool, u need to tell me more about it wahts conky anyway??? am just like 1 week old Ubuntu use:)

---

### Post by ajgreeny on 2011-10-02
Conky is a simple desktop monitor program that requires a fairly detailed configuration file to show a lot of details about your computer.

1.  Install conky from repos with software-center or synaptic or ```
sudo apt-get install conky
```
2.  Make a text file in your home called **.conkyrc** (the . in front is needed, and makes the file hidden;  use Ctrl+H to see all hidden files/folders)
3.  Add one of the many sample .conkyrc texts to your file and see what it produces on your desktop when you run conky.  Do a search for **sample conkyrc files** or see [http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

Here's my .conkyrc for you to try as an example
```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=11

# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280

# Maximum width
maximum_width 280

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
# stippled_borders 8

# border margins
# border_margin 2

# border width
# border_width 1

# Default colors and also border colors
default_color white
default_shade_color red
default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 30
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen

TEXT
${font Trebuchet MS:size=30} ${alignc}${time %k:%M}${font Trebuchet MS:size=11}
${font Trebuchet MS:size=20} ${alignc}${time %a %b %d %Y}${font Trebuchet MS:size=11}
${color #56073D}Hostname:${color #DE0084}$alignr$nodename
${color #56073D}Uptime:${color #DE0084}$alignr$uptime

${color #56073D}CPU ${color #DE0084}${cpu cpu1}% ${color #56073D}${cpubar cpu1}
#${color #56073D}Process CPU & MEM Usage${hr 2}        
Processes $alignr CPU%   MEM%   PID
${color #56073D} ${top name 1} ${color #DE0084} $alignr ${top cpu 1}  ${top mem 1}  ${top pid 1}
${color #56073D} ${top name 2} ${color #DE0084} $alignr ${top cpu 2}  ${top mem 1}  ${top pid 2}
#${color #56073D} ${top name 3} ${color #DE0084} $alignr ${top cpu 3}  ${top mem 1}  ${top pid 3}
#${color #56073D} ${top name 4} ${color #DE0084} $alignr ${top cpu 4}  ${top mem 1}  ${top pid 4}

${color #56073D}sda1$alignr ${color #DE0084}${fs_used /}/${fs_size /}
${color #56073D} Root ${color #DE0084}${fs_used_perc /}% ${color #56073D}${fs_bar /}

${color #56073D}sda2$alignr ${color #DE0084}${fs_used /home}/${fs_size /home}
${color #56073D} Home ${color #DE0084}${fs_used_perc /home}% ${color #56073D}${fs_bar /home}

${color #56073D}RAM Used:$alignr${color #DE0084}$mem of $memmax ${color #DE0084}= ${color #DE0084}$memperc%
${color #56073D}Swap:${alignr}${color #DE0084}$swapperc%     $swap of $swapmax

${color #56073D}NETWORK IP:${color #DE0084} $alignr eth0 -  ${color #DE0084}${addr eth0}
${color #56073D}DOWN:${color #DE0084} ${downspeed eth0}/s ${color #56073D}$alignr TOTAL ${color #DE0084}${totaldown eth0}
${color #56073D}${downspeedgraph eth0 20,280 000000 #56073D}
${color #56073D} Up:${color #DE0084} ${upspeed eth0}/s ${color #56073D}$alignr TOTAL ${color #DE0084}${totalup eth0}
${color #56073D}${upspeedgraph eth0 20,280 000000 #56073D}
#
# To make hddtemp run as user use command "sudo chmod u+s /usr/sbin/hddtemp"
# To make vnstat run as user use command "sudo chmod u+s /usr/bin/vnstat"
#
            DOWN:                    $alignr UP:        
${color #56073D}Today: ${color #DE0084}${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${color #56073D}${alignr}Today: ${color #DE0084}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}
${color #56073D}Week:  ${color #DE0084}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${color #56073D}${alignr}Week:  ${color #DE0084}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'}
${color #56073D}Month: ${color #DE0084}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${color #56073D}${alignr}Month: ${color #DE0084}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}

${color #56073D}${font Trebuchet MS:size=12}Drive Temp: Degrees C${font Trebuchet MS:size=11}
${alignc}${execi 60 hddtemp /dev/sda | cut -c 6-28} C
${alignc}${execi 60 hddtemp /dev/sdb | cut -c 6-28} C
```
Some of this will not work in your setup, but it may give you a start and something to try to edit.

---

### Post by Suhel28 on 2011-10-03
> **ajgreeny said:**
> Conky is a simple desktop monitor program that requires a fairly detailed configuration file to show a lot of details about your computer.

1.  Install conky from repos with software-center or synaptic or ```
sudo apt-get install conky
```
2.  Make a text file in your home called **.conkyrc** (the . in front is needed, and makes the file hidden;  use Ctrl+H to see all hidden files/folders)
3.  Add one of the many sample .conkyrc texts to your file and see what it produces on your desktop when you run conky.  Do a search for **sample conkyrc files** or see [http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

Here's my .conkyrc for you to try as an example
```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=11

# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280

# Maximum width
maximum_width 280

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
# stippled_borders 8

# border margins
# border_margin 2

# border width
# border_width 1

# Default colors and also border colors
default_color white
default_shade_color red
default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 30
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen

TEXT
${font Trebuchet MS:size=30} ${alignc}${time %k:%M}${font Trebuchet MS:size=11}
${font Trebuchet MS:size=20} ${alignc}${time %a %b %d %Y}${font Trebuchet MS:size=11}
${color #56073D}Hostname:${color #DE0084}$alignr$nodename
${color #56073D}Uptime:${color #DE0084}$alignr$uptime

${color #56073D}CPU ${color #DE0084}${cpu cpu1}% ${color #56073D}${cpubar cpu1}
#${color #56073D}Process CPU & MEM Usage${hr 2}        
Processes $alignr CPU%   MEM%   PID
${color #56073D} ${top name 1} ${color #DE0084} $alignr ${top cpu 1}  ${top mem 1}  ${top pid 1}
${color #56073D} ${top name 2} ${color #DE0084} $alignr ${top cpu 2}  ${top mem 1}  ${top pid 2}
#${color #56073D} ${top name 3} ${color #DE0084} $alignr ${top cpu 3}  ${top mem 1}  ${top pid 3}
#${color #56073D} ${top name 4} ${color #DE0084} $alignr ${top cpu 4}  ${top mem 1}  ${top pid 4}

${color #56073D}sda1$alignr ${color #DE0084}${fs_used /}/${fs_size /}
${color #56073D} Root ${color #DE0084}${fs_used_perc /}% ${color #56073D}${fs_bar /}

${color #56073D}sda2$alignr ${color #DE0084}${fs_used /home}/${fs_size /home}
${color #56073D} Home ${color #DE0084}${fs_used_perc /home}% ${color #56073D}${fs_bar /home}

${color #56073D}RAM Used:$alignr${color #DE0084}$mem of $memmax ${color #DE0084}= ${color #DE0084}$memperc%
${color #56073D}Swap:${alignr}${color #DE0084}$swapperc%     $swap of $swapmax

${color #56073D}NETWORK IP:${color #DE0084} $alignr eth0 -  ${color #DE0084}${addr eth0}
${color #56073D}DOWN:${color #DE0084} ${downspeed eth0}/s ${color #56073D}$alignr TOTAL ${color #DE0084}${totaldown eth0}
${color #56073D}${downspeedgraph eth0 20,280 000000 #56073D}
${color #56073D} Up:${color #DE0084} ${upspeed eth0}/s ${color #56073D}$alignr TOTAL ${color #DE0084}${totalup eth0}
${color #56073D}${upspeedgraph eth0 20,280 000000 #56073D}
#
# To make hddtemp run as user use command "sudo chmod u+s /usr/sbin/hddtemp"
# To make vnstat run as user use command "sudo chmod u+s /usr/bin/vnstat"
#
            DOWN:                    $alignr UP:        
${color #56073D}Today: ${color #DE0084}${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${color #56073D}${alignr}Today: ${color #DE0084}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}
${color #56073D}Week:  ${color #DE0084}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${color #56073D}${alignr}Week:  ${color #DE0084}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'}
${color #56073D}Month: ${color #DE0084}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${color #56073D}${alignr}Month: ${color #DE0084}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}

${color #56073D}${font Trebuchet MS:size=12}Drive Temp: Degrees C${font Trebuchet MS:size=11}
${alignc}${execi 60 hddtemp /dev/sda | cut -c 6-28} C
${alignc}${execi 60 hddtemp /dev/sdb | cut -c 6-28} C
```
Some of this will not work in your setup, but it may give you a start and something to try to edit.


does this mean I dont have to install vnstat? 

I'd already installed vnstat so I donno, also I used your script but the "week and month" still shows nil, sorry for buggin you so much :)

---

### Post by ajgreeny on 2011-10-03
As you have installed vnstat (and hddtemp?) you will firstly need to wait until there is enough data in the /var/lib/vnstat files.  That can take a day or two, depending on how much use you make of the network.

You may also need to make sure that vnstat is using the correct network, eg eth0, wlan0 or whatever yours happens to be.  You can get this from ifconfig in terminal.

lastly, you may have missed the lines in my .conkyrc file[FONT=monospace]
[/FONT]```
# 
# To make hddtemp run as user use command "sudo chmod u+s /usr/sbin/hddtemp" 
# To make vnstat run as user use command "sudo chmod u+s /usr/bin/vnstat" 
#
```showing the command which you need to run in order to get vnstat to work in conky.

---

### Post by Suhel28 on 2011-10-04
> **ajgreeny said:**
> As you have installed vnstat (and hddtemp?) you will firstly need to wait until there is enough data in the /var/lib/vnstat files. That can take a day or two, depending on how much use you make of the network.
 
You may also need to make sure that vnstat is using the correct network, eg eth0, wlan0 or whatever yours happens to be. You can get this from ifconfig in terminal.
 
lastly, you may have missed the lines in my .conkyrc file
```
# 
# To make hddtemp run as user use command "sudo chmod u+s /usr/sbin/hddtemp" 
# To make vnstat run as user use command "sudo chmod u+s /usr/bin/vnstat" 
#
```showing the command which you need to run in order to get vnstat to work in conky.
 
 
thanks for all your help mate :D :KS

---

