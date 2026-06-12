---
title: "Brightness problem"
date: 2011-06-02
forum: Multimedia Software
---

### Post by andrei90 on 2011-06-02
Hello,
I have an Acer eXtensa 5635Z with OS Xubuntu 11.04 and I can't change Brightness from my keyboard, I keep pressing Fn+ Left, Right and nothing happens, not even the brightness image doesn't appear! Please help it's killing my eyes, it's too bright!

---

### Post by Toz on 2011-06-02
Here is a reference link: [http://ubuntuforums.org/showthread.php?t=1446943&highlight=5635Z](http://ubuntuforums.org/showthread.php?t=1446943&highlight=5635Z)

Can open up a terminal window, type in the following, and post back the results:```
lspci | grep VGA
```

As a workaround, If we can manually adjust the brightness, then we can create a script to do it and assign that script to the shortcut keys.

I found another link ([http://ubuntuforums.org/showpost.php?p=9831248&postcount=8](http://ubuntuforums.org/showpost.php?p=9831248&postcount=8)) that suggests that using a custom kernel might solve the problem.

---

### Post by andrei90 on 2011-06-10
```
andrei@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

---

### Post by Toz on 2011-06-10
Have you tried implementing the script from [http://ubuntuforums.org/showthread.php?t=1446943&highlight=5635Z]("http://ubuntuforums.org/showthread.php?t=1446943&highlight=5635Z")?

---

### Post by andrei90 on 2011-06-10
No I didn't, but where do I find that file?
-sorry I'm not so experienced, but I'm willing to learn! :)

---

### Post by Toz on 2011-06-11
Okay. To implement that script, follow these instructions:

1. In a terminal window, type in: ```
mousepad ./backlight_d.sh
``` (the mousepad application will open)

2. Copy and paste the following into the mousepad application that just opened:> #!/bin/bash

old_b=9;
declare -i curr_b=240;
declare -i target_b=240;

while : ; do
b=`cat /sys/class/backlight/acpi_video0/brightness`;
delay="0.5"

if [ $old_b != $b ]; then
old_b=$b
let "target_b=$b * 20 + 12"
#printf "Target: %10d\n" $target_b
fi

hex_b=".";

if [ "$curr_b" -lt "$target_b" ] ; then
let "curr_b=$curr_b + 2"
if [ "$curr_b" -gt "$target_b" ] ; then
let "curr_b=$target_b"
fi

hex_b="-"
elif [ "$curr_b" -gt "$target_b" ] ; then
let "curr_b=$curr_b - 2"
if [ "$curr_b" -lt "$target_b" ] ; then
let "curr_b=$target_b"
fi

hex_b="-"
fi

if [ $hex_b != "." ] ; then
hex_b=`printf "%02X" $curr_b`
delay="0.005"
setpci -s 00:02.0 F4.B=$hex_b
fi

sleep $delay
done

3. Save the file:```
File->Save
```

4. Back in the terminal window, type in the following:```
sudo cp ./backlight_d.sh /etc/ && sudo chmod +x /etc/backlight_d.sh
``` (enter your password when prompted).

5. Enter the following into the terminal window:```
sudo mousepad /etc/rc.local
``` (mousepad will open again) and before the **exit 0** line, type in the following: ```
nohup /etc/backlight_d.sh &
``` so it looks like:> nohup /etc/backlight_d.sh &
exit 0

Restart your computer. According to that article, you should be able to adjust your brightness. Post back and let us know if it works. If not, there are a few other things we can try.

---

### Post by andrei90 on 2011-06-11
So if I implement this script, I can change my brightness from Fn+ Left, Right?

LE: The script worked my friend! I can adjust my brightness from the keyboard! Thank you so much for helping me! :)

---

### Post by jackn on 2011-07-18
OK, I've tried the detailed protocol with the mousepad application, but no cigar... I'm running Natty 11.04 on a Samsung NC110.

I'm going to go on using the 
```
setpci -s 00:02.0 F4.B=96 
```
command which you suggested in another [thread]("http://ubuntuforums.org/showthread.php?t=1781081").

TY again, Toz, for all the work and attention you've put into this issue.
jackn

---

### Post by Toz on 2011-07-18
**mousepad** is a text editor that exists on the xubuntu version of natty. On the regular ubuntu version, the editor command would be **gedit**.

---

### Post by prasanth9703 on 2011-08-05
> **Toz said:**
> Okay. To implement that script, follow these instructions:

1. In a terminal window, type in: ```
mousepad ./backlight_d.sh
``` (the mousepad application will open)

2. Copy and paste the following into the mousepad application that just opened:

3. Save the file:```
File->Save
```

4. Back in the terminal window, type in the following:```
sudo cp ./backlight_d.sh /etc/ && sudo chmod +x /etc/backlight_d.sh
``` (enter your password when prompted).

5. Enter the following into the terminal window:```
sudo mousepad /etc/rc.local
``` (mousepad will open again) and before the **exit 0** line, type in the following: ```
nohup /etc/backlight_d.sh &
``` so it looks like:

Restart your computer. According to that article, you should be able to adjust your brightness. Post back and let us know if it works. If not, there are a few other things we can try.


i have tried the above method in my lenovo z570 laptop. the lspci command gives the following output 

"prasanth@prasanth-Ideapad-Z570:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df7 (rev a1)"

i have tried setting the 00:02.0 and 01:00.0 but its not working
 also i have run the backlight_d.sh file in the terminal,but its giving the foll output 
"cat: sys/class/backlight/acpi_vide0/brightness: NO such file or directory
/etc/backlight_d.operator sh: line 11 [: unary operator expected"


can anyone help in this regard.........:(

---

### Post by Toz on 2011-08-05
I believe the ideapad uses the optimus dual video card technology. There are numerous posts on this forum on getting this setup to work.

That being said...Are you running the nvidia driver or has it been disabled? What does:
```
lspci -vnn
```return?

Also,
1. ```
lsmod
```
2. The contents of **/var/log/Xorg.0.log**

2. Have you tried the **acpi_backlight=vendor**, **acpi_osi=Linux** or **acpi_osi=\"Linux\"** kernel parameters?

3. What does:
```
xbacklight -get
``` return? If not an error, does:
```
xbacklight -set 50
``` change the brightness?

---

### Post by Topazkitty on 2012-01-02
> **Toz said:**
> Okay. To implement that script, follow these instructions:

1. In a terminal window, type in: ```
mousepad ./backlight_d.sh
``` (the mousepad application will open)

2. Copy and paste the following into the mousepad application that just opened:

3. Save the file:```
File->Save
```4. Back in the terminal window, type in the following:```
sudo cp ./backlight_d.sh /etc/ && sudo chmod +x /etc/backlight_d.sh
``` (enter your password when prompted).

5. Enter the following into the terminal window:```
sudo mousepad /etc/rc.local
``` (mousepad will open again) and before the **exit 0** line, type in the following: ```
nohup /etc/backlight_d.sh &
``` so it looks like:

Restart your computer. According to that article, you should be able to adjust your brightness. Post back and let us know if it works. If not, there are a few other things we can try.


Thank you for posting this. It works on my gateway t-series laptop I am using ubuntu 11.10 and if anyone wants to do this replace "mousepad" with "gedit".

---

