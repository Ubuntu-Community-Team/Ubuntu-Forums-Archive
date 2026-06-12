---
title: "Auto-downloading when Ubuntu automatically is turned on at night?!"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by GnuKian on 2013-03-05
The service pack that I use offers gratis download at night (1AM to 6AM). I usually sleep at 22:30 to wake up soon!
I need to turns the ubuntu at 00:50 AM for downloading; here is my method. please read it and modify/promote it for a better scheduler task!

0. (every week, each day) I've set the bios to turns on the computer at 00:50

1. At 22:10 O'clock => I gather all my straight downlkoad links in a file called "dl.txt"

2. At 22:20 O'clock => I change my user (which is administrator) config from "asking password" to "auto login". this is need to login to ubuntu directly.

3. I've added a simple command to "crontab -e":
```
00 01 * * * aria2c -c -x16 -s16 -k 1M -m10 --retry-wait=30 -i "/PATH/TO/dl.txt" -d "/PATH/TO/DOWNLOAD_DIRECTORY/" -l dllog --log-level=notice
aria2c --on-download-complete echo "PASSWORD"|sudo -S shutdown -h now
59 05 * * * echo "PASSWORD"|sudo -S shutdown -h now
```

4. In the morninig, I re-cofnfig my user to off auto-login (this is my everyday task :icon_frown:) 

If you have any idea about improving this instuction, please me to know :)

---

### Post by GnuKian on 2013-03-06
does your "silence" means that my solution is the best way?

---

### Post by Hadaka on 2013-03-06
Hi, I dont think the silence means anything, It looks
like you are using the tools available to you to get your
desired results. There are many different ways to accomplish
a task using linux. No doubt some super coder would write a
program in some obscure language and the code would be 
unreadable to the average user. I'm sure as time goes on you
will add tweaks and changes,bells and whistles. For now, if
it's not broke, why fix it?

---

### Post by GnuKian on 2013-03-08
It's need to automate 2 & 4 steps, any idea?

---

### Post by Hadaka on 2013-03-08
Hi, I tested this, the command anyway and it seems to work,
you could crontab the commands for your set times.You will first
have to set the autologin line to "#autologin"  this gets the ball rolling
and is a one time entry.
then the 4 following commands
will turn it on and off per your crontab schedule

22:20 To ON autologin  crontab -> echo 'your_password' | sudo -S sed 's/#autologin/autologin/'g /etc/lightdm/lightdm.conf > autologin_on  #<-filename
                                              echo 'your_password' |sudo -S mv               autologin_on /etc/lightdm/lightdm.conf
? AM To OFF autologin   crontab ->   echo 'your_password' | sudo -S sed 's/autologin/#autologin/'g /etc/lightdm/lightdm.conf >                 autologin_off  #<-filename
                                              echo 'your_password' |sudo -S mv autologin_off /etc/lightdm/lightdm.conf
hope that helps.

---

### Post by Hadaka on 2013-03-08
Hi, this should be eaiser to read

Autologin ON
```
echo 'your_password' | sudo -S sed 's/#autologin/autologin/'g /etc/lightdm/lightdm.conf > autologin_on
 echo 'your_password' |sudo -S mv autologin_on /etc/lightdm/lightdm.conf
```

Autologin OFF
```
echo 'your_password' | sudo -S sed 's/autologin/#autologin/'g /etc/lightdm/lightdm.conf > autologin_off
 echo 'your_password' |sudo -S mv autologin_off /etc/lightdm/lightdm.conf
```

more better?
*Don't forget to first set autologin line to -> #autologin-user=your_user_name
 and ................................................ -> #autologin-user-timeout=0

---

### Post by Hadaka on 2013-03-08
Hi, this should be eaiser to read

Autologin ON
```
echo 'your_password' | sudo -S sed 's/#autologin/autologin/'g /etc/lightdm/lightdm.conf > autologin_on
 echo 'your_password' |sudo -S mv autologin_on /etc/lightdm/lightdm.conf
```

Autologin OFF
```
echo 'your_password' | sudo -S sed 's/autologin/#autologin/'g /etc/lightdm/lightdm.conf > autologin_off
 echo 'your_password' |sudo -S mv autologin_off /etc/lightdm/lightdm.conf
```

more better?

---

### Post by Cheesemill on 2013-03-09
Why are you needing to auto-login anyway? Crontab will work just fine whether you are logged in or not (or do you have an encrypted /home).

Also putting your password in a script is a very bad idea security wise. The preferred method would be to edit your sudoers file so that the shutdown command can be run without prompting for a password.

---

### Post by GnuKian on 2013-03-10
@Hadaka
Thankyou for the codes; I'll check them on my home pc when I get home this night.

> **Cheesemill said:**
> Why are you needing to auto-login anyway? Crontab will work just fine whether you are logged in or not
You mean the "download script" will be started from display manager?

> **Cheesemill said:**
> (or do you have an encrypted /home).
No!

> **Cheesemill said:**
> The preferred method would be to edit your sudoers file so that the shutdown command can be run without prompting for a password.
Editing sudoers list or creating /etc/**shutdown.allow** file?

---

### Post by Cheesemill on 2013-03-10
You don't need to be logged on at all for the aria2c program to run, it's a command line program that will quite happily run in the background without anyone logged on to the system.
I would just have the following entries in your crontab...
```
00 01 * * * aria2c -c -x16 -s16 -k 1M -m10 --retry-wait=30 -i "/PATH/TO/dl.txt" -d "/PATH/TO/DOWNLOAD_DIRECTORY/" -l dllog --log-level=notice --on-download-complete="sudo shutdown now -h"
59 05 * * * shutdown now -h
```
To set up sudo to allow you to shutdown without needing a password open the terminal and type the following...
```
EDITOR=nano sudo visudo
```
Now add the following line **to the bottom** of the file...
```
username ALL=(ALL) NOPASSWD: /sbin/shutdown
```
replacing username with your actual username. Save the file and exit and you're good to go.

---

