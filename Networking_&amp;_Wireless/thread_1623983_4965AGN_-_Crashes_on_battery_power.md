---
title: "4965AGN - Crashes on battery power"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by gibbylinks on 2010-11-17
Hi 

I have a Dell 1501 Inspiron laptop and have swapped out the broadcom network card for an intel 4965AGN so I can use n-speed with my new router.

Everything works sweet except my laptop now crashes if I try to run on battery power.It boots up to the login screen, but once I enter password and login it crashes, just get grey screen and everything locks up. Everything works fine on mains ?

Any ideas ?

It's not a major problem for me as I don't use the laptop "out in the wild" :) Just curious as to whether it can be fixed.

Ta

---

### Post by gibbylinks on 2010-11-22
Bump

---

### Post by grahammechanical on 2010-11-22
Let me see if I understand you correctly. The laptop does not load when running on batteries? So, this is not a Networking & Wireless issue. Is there a problem with your battery? Is it able to accept a charge?

When you replaced the networking card with another type did you re-install Ubuntu? If the machine crashed every time you booted then I would think that Ubuntu was crashing because it had the wrong modules loaded. But you say it "everything works sweet" on mains power. Tricky.

Regards.

---

### Post by chili555 on 2010-11-22
I don't know if this is your exact problem, but I do know that the module *dell-laptop* is troublesome. I suggest you blacklist it:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Now reboot on battery power and give us your report.

By the way, are you certain it's the wireless card? Have you examined /var/log/syslog? /var/log/dmesg.0?

---

### Post by gibbylinks on 2010-11-22
> **grahammechanical said:**
> Let me see if I understand you correctly. The laptop does not load when running on batteries?

The laptop loads as far as the login screen. As soon as I enter my password and hit enter, when the wi-fi led lights up the screen turns grey "all over" and everything locks up.

Only way out is a hard reset.

> **chili555 said:**
> I don't know if this is your exact problem, but I do know that the module *dell-laptop* is troublesome. I suggest you blacklist it:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Now reboot on battery power and give us your report.

By the way, are you certain it's the wireless card? Have you examined /var/log/syslog? /var/log/dmesg.0?

I will try this when I get home.

---

### Post by alexpennos on 2010-11-22
I am on a dell studio 1557 reporting the same problem. When switch to battery power mode, after a few minutes everything freezes and the hard reset is the only solution... :(

---

### Post by chili555 on 2010-11-22
Did you try the same solution I proposed?

---

### Post by gibbylinks on 2010-11-22
> **chili555 said:**
> I don't know if this is your exact problem, but I do know that the module *dell-laptop* is troublesome. I suggest you blacklist it:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```Now reboot on battery power and give us your report.

By the way, are you certain it's the wireless card? Have you examined /var/log/syslog? /var/log/dmesg.0?

Sorry but this didn't work. I'm fairly certain it's the network card, as it was fine with the original Broadcom card in it. I swapped over so I could utilise the n-speed on my router.

---

### Post by alexpennos on 2010-11-22
> **chili555 said:**
> Did you try the same solution I proposed?
No I didn't. I am sorry but i dont know what those lines do, so I am a bit afraid to do so...

---

### Post by chili555 on 2010-11-22
They simply block a temperamental module from loading. You can test it temporarily with:```
sudo rmmod -f dell-laptop
```If it fixes your problem, then you can execute the code above to make it permanent. If not, it will go away upon reboot, or with:```
sudo modprobe dell-laptop
```I wouldn't suggest code if I thought there was a chance it was harmful.

---

### Post by alexpennos on 2010-11-23
> **chili555 said:**
> They simply block a temperamental module from loading. You can test it temporarily with:```
sudo rmmod -f dell-laptop
```If it fixes your problem, then you can execute the code above to make it permanent. If not, it will go away upon reboot, or with:```
sudo modprobe dell-laptop
```I wouldn't suggest code if I thought there was a chance it was harmful.

Thanks but it didn't solve the problem.
I know you your intentions are good but I am not experienced user so before i change anything i would like to ask and learn each time!

Thank you once more, anyway!

---

### Post by alexpennos on 2010-12-01
Ok, i found a solution that works for me on the launchpad.net bugreport. I am quoting it: > I'm sorry, but I was a little bit to fast. After I attached Linux Mint Julia to wlan and USB-Memory, it crashed after the Filetransfer began immediately also.

But I found finally a workaround, which I have tested the last 2 days:

I deinstalled the pm-utils 1.4 with synaptic. Download the package pm-utils 1.3.0-1ubuntu1_all_deb from

"http://packages.ubuntu.com/de/lucid/all/pm-utils/download"

and installed it.

Now it workes fine and all functions remain in the best way.

In my opinion the error lies in the current pm-utils package. But I am only a completely normal user and not a programmer!

Would anybody test it too and write a coment?

Thanks

aspera

Hope this will do the job for you.

---

### Post by gibbylinks on 2010-12-01
> **alexpennos said:**
> Ok, i found a solution that works for me on the launchpad.net bugreport. I am quoting it: 
Hope this will do the job for you.

Thanks for this. It worked for me. Now running on battery power.

Do you have a link for the launchpad bug so I can add my voice to it ?

Cheers

---

### Post by tiredofguessingusernames on 2010-12-02
Thanks alexpennos!

Have been struggling with this for weeks - thank you very much! Would also be interested in adding my 2c to the bug report!

---

### Post by alexpennos on 2010-12-03
Hello there! Totally understand your happiness for this!
Here's the bug No. Bug #656745
:popcorn:

---

### Post by jvgeli on 2011-07-19
I am having the same issue on a lenovo laptop with AMD e350 and an ATI card. Tried forcing the pm utils version to lucid but that didnt work either. The weird thing is that when i boot windows first, restart then boot natty its fine. But when I boot natty first it freezes. need help badly, its not really a laptop if you cant use without having to connect to a electric socket.

---

### Post by kevinzeg on 2012-08-15
> **alexpennos said:**
> Ok, i found a solution that works for me on the launchpad.net bugreport. I am quoting it: 
Hope this will do the job for you.


After that re-install the other packages you removed with pm-utils 1.4. 
Just install "ubuntu-desktop"  with Synaptic after installing pm-utils 1.3.

or in terminal

After installing pm-utils 1.3 

sudo apt-get install ubuntu-desktop

---

