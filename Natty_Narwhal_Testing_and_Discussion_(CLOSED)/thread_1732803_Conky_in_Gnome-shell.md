---
title: "Conky in Gnome-shell"
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-04-18
I've got conky working in the gnome-shell environment, with some tweaks to the .conkyrc file (the info came from other users, but I can't find the thread now, to credit them, sorry).

All was well but then I did 2 things at once  :(
I ran updates and installed them, and while that was going on I amended the size of the icons in the Applications screen.
So I'm unsure as to which is causing the problem below.

Now, what happens is this.
When I move the pointer to the top left corner I am getting a second conky display up on the left, just for a second or so, as the Windows/Applications screen appears. And the same thing happens when I move the pointer back to the top left corner, or return to the normal desktop.

Comments? Ideas? :-)
Thanks.

---

### Post by 23dornot23d on 2011-04-18
Can you post the file contents for the conky file or a link to it  ,,,,, so we can play with it ....

---

### Post by Quackers on 2011-04-18
Sure :-)
But I don't think it's a conky problem, as it was fine before I updated/changed the icon sizes.
```
alignment top_right
background no
border_width 0
cpu_avg_samples 2
default_color white
default_outline_color black
default_shade_color black
double_buffer yes
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades yes
use_xft yes
xftfont terminus:size=11
gap_x 10
gap_y 50
maximum_width 320
minimum_size 300 100
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no
text_buffer_size 4096

TEXT
${font Terminus:style=bold:size=11}SYSTEM $hr
${font}$sysname $kernel $alignr $machine
Host: $alignr $nodename
Temp: $alignr ${acpitemp}C
${color light blue}
${font Terminus:style=bold:size=11}PROCESSORS $hr
CPU1: ${cpu cpu1}% ${cpubar cpu1}
CPU2: ${cpu cpu2}% ${cpubar cpu2}
${color pink}
${font Terminus:style=bold:size=11}MEMORY $hr
${font}RAM ${alignc}     $mem/$memmax  $alignr $memperc%
${membar}
${color orange}
${font Terminus:style=bold:size=11}DISKS $hr
${font}/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_used_perc /}%
${fs_bar /}
${color red}
${font Terminus:style=bold:size=11}BATTERY $hr
${battery_percent BAT0}% ${battery_bar BAT0}
${color green}
${font Terminus:style=bold:size=11}TOP PROCESSES $hr
${top name 1}$alignr${top cpu 1}%
${top name 2}$alignr${top cpu 2}%
${top name 3}$alignr${top cpu 3}%
${top name 4}$alignr${top cpu 4}%
${color yellow}
${font Terminus:style=bold:size=11}WIRELESS NETWORK $hr
Connection Quality: $alignr ${wireless_link_qual wlan0}%
D/L: ${downspeed wlan0}/s $alignr ${totaldown wlan0}
U/L: ${upspeed wlan0}/s $alignr ${totalup wlan0}
${execpi 1800 conkyForecast --location=UKXX0092 --template=/home/nattybeta2/weather.template}
$hr
${font Terminus:style=bold:size=11}${time %k:%M}${alignr}${time %a/%b/%d}
```
And the weather.template
```

${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=12}TODAY $hr

${color1}${font Bitstream Vera Sans Mono:size=14}[--location=UKXX0092 --datatype=CT]
${image [--location=UKXX0092 --datatype=WI] -p 0,610 -s 90x90 -n}                  ${font ConkyWindNESW:size=45}[--location=UKXX0092 --datatype=BS]${font}

[--location=UKXX0092 --datatype=HT]                               [--location=UKXX0092 --datatype=WS --imperial]  [--location=UKXX0092 --datatype=WD]

${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=12}TOMORROW ${hr}

${font Bitstream Vera Sans Mono:size=14}[--location=UKXX0092 --datatype=CT --startday=1]
${image [--location=UKXX0092 --datatype=WI --startday=1] -p 0,775 -s 90x90 -n}                  ${font ConkyWindNESW:size=45}[--location=UKXX0092 --datatype=BS --startday=1]${font}

[--location=UKXX0092 --datatype=HT --startday=1] / [--location=UKXX0092 --datatype=LT --startday=1]                       [--location=UKXX0092 --datatype=WS --imperial --startday=1]  [--location=UKXX0092 --datatype=WD --startday=1]

${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=12}DAY AFTER $hr

${font Bitstream Vera Sans Mono:size=14}[--location=UKXX0092 --datatype=CT --startday=2]
${image [--location=UKXX0092 --datatype=WI --startday=2] -p 0,940 -s 90x90 -n}                  ${font ConkyWindNESW:size=45}[--location=UKXX0092 --datatype=BS --startday=2]${font}

[--location=UKXX0092 --datatype=HT --startday=2] / [--location=UKXX0092 --datatype=LT --startday=2]                       [--location=UKXX0092 --datatype=WS --imperial --startday=2]  [--location=UKXX0092 --datatype=WD --startday=2]
```
And a screenshot

---

### Post by 23dornot23d on 2011-04-18
Cheers ..... will have a play and come back to this later on ..... ty

---

### Post by Quackers on 2011-04-18
No problem - have fun! :-)
The changes made to make it work in gnome-shell are the "own_window_type" and "own_window_hints" lines (I think I deleted one as well)

---

### Post by 23dornot23d on 2011-04-18
Ok its throwing some errors back at me ...



keith@keith-Aspire-7730ZG:~$ conky conky.rc
Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Conky: forked to background, pid is 6366
keith@keith-Aspire-7730ZG:~$ 
Conky: desktop window (1000019) is subwindow of root window (15a)
Conky: window type - override
Conky: drawing to created window (0x2c00001)
Conky: drawing to double buffer

:confused:

---

### Post by Quackers on 2011-04-18
You're not using my script there?
The 2 relevant lines for gnome-shell are
```
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar
```
I can't find the thread still, but I think own_window_type override was changed to desktop

---

### Post by 23dornot23d on 2011-04-18
Found this[ thread]("http://ubuntuforums.org/showthread.php?t=1309306")

Sorry not used conky in a while .... will be with it shortly .....

---

### Post by Quackers on 2011-04-18
That's the one! Thanks hopeabides for the info :-)

---

### Post by 23dornot23d on 2011-04-18
ok got it running ...... not fully but we are getting there .....

keith@keith-Aspire-7730ZG:~$ conky
Conky: scandir for /proc/acpi/thermal_zone/: No such file or directory
Conky: desktop window (120001a) is subwindow of root window (15a)
Conky: window type - desktop
Conky: drawing to created window (0x6400001)
Conky: drawing to double buffer
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
sh: conkyForecast: not found
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory




[Screenshot]("http://img696.imageshack.us/img696/6872/screenshot12gq.png")

Will try some mods to it now .... seems ok at the moment though can flick back and forth between the application 
screen and the main one and it re-appears and looks the same ....

[Screenshot 2]("http://img824.imageshack.us/img824/9828/screenshot13e.png")

Guess what no alterations and Firefox works ok in KDE ......

[Screenshot 3]("http://img34.imageshack.us/img34/817/desktop1002.jpg")

I have just experienced the same thing - but it was not doing it earlier on ..... the double appearance ..... top left as you say ......
was only after opening an application it started to happen I think ......

No transparency in KDE though ?

Interesting link for all the options Available in [CONKY]("http://conky.sourceforge.net/variables.html")

Got the [Nvidia Temp]("http://img189.imageshack.us/img189/9842/screenshot20rc.png") now and tidied up what does not work on mine >>> but am still getting a second one appearing when swapping to applications

---

### Post by Quackers on 2011-04-18
As you say, you got half of it working. The weather is the other half, but that will be quite involved to get going. But you're seeing the same thing as me. That didn't happen until last night. It's unlikely to be my icon size editing in gnome-shell that's causing it then :-) If you are fully updated it could be an update that hs caused it. Maybe it will right itslef with more updates :-)
Not sure about the transparency in kde though, unless the black background doesn't suit it, for some reason.

---

### Post by 23dornot23d on 2011-04-19
I am going to have a look at this link and see if I can get the weather working too ... [LINK]("http://ubuntuforums.org/showthread.php?t=1156383")

Interesting program ...... a little distracting at times .... but good to see the information

on the screen - superkaramba on KDE used to be good too ....... not had a look at that lately

may see if that works in KDE.

Yep hopefully some updates will sort out [COLOR=Red]**the appearance of the second one on switching to the applications window**[/COLOR].

Thanks for bringing it up I may not have got conky running otherwise ....... ty

---

### Post by Quackers on 2011-04-19
Yes it would be nice to sort that oddity out :-)
Here's a link to kaivalagi's original thread

[http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)

---

### Post by Quackers on 2011-04-19
If you are seeing the temperatures displayed with Å between the 20 and the deg C you will need to add this line before the TEXT line then save the file
```
override_utf8_locale yes
```
(xft needs to be on too)

---

