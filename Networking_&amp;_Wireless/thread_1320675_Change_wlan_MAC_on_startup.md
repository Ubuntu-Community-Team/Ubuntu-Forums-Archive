---
title: "Change wlan MAC on startup"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by SmarterThanMyPhone on 2009-11-09
I want to run;
ifconfig wlan0 down
macchanger -a wlan0
ifconfig wlan0 up

when my laptop starts up. How can I add this to the startup and run it with root privileges every time I boot up?

---

### Post by t0mppa on 2009-11-09
A couple of options really, which one to use is a matter of personal preference. First would be to add the lines to /etc/rc.local before the *exit 0* line. The other option is to make a shell script file *<name_you_pick>.sh*, chmod it to be executable and use update-rc.d to have it run at boot.

The former is a bit simpler, but adding lots of different scripts that way gets a bit messy, while the latter is a bit more work, but easier to maintain, better configurable (can choose which run levels to enable it on) and is a more elegant solution, if that floats your boat.

And if you need to do that only when GUI loads up, you write a script and add it to startup applications.

---

### Post by SmarterThanMyPhone on 2009-11-09
going for option 2, I like elegance :)

---

### Post by SmarterThanMyPhone on 2009-11-09
I run;
sudo cp myscript /etc/init.d
sudo chmod +x /etc/init.d/myscript

sudo update-rc.d myscript start 51 S .

get a warning message "warning: /etc/init.d/chmac.sh missing LSB information., reboot and no script.
It requires root priv, so would that change the chmod command?
I'm using;

ifconfig wlan0 down
macchanger -a wlan0
ifconfig wlan0 up

---

### Post by SmarterThanMyPhone on 2009-11-09
after speaking to a friend I rm'd the script from /etc/init.d and added the 3 lines of commands to rc.local, this gives the same result; after rebooting the MAC does not change.

---

### Post by SmarterThanMyPhone on 2009-11-09
SOLVED!

when I added the commands to rc.local I forgot to use sudo.
for anyone going forward;
edit /etc/rc.local and add
sudo ifconfig wlan0 down
sudo macchanger -a wlan0
sudo ifconfig wlan0

save and done :)

---

