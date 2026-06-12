---
title: "mythtv shutdown"
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by hulluPeruna on 2006-10-31
Hi

I installed mythtv on my kubuntu box. Installing mythtv and the hardware was no problem. (big thank you to the ubuntu team).
But I am a little stuck configuring it so that I can shut it down via the remote. Lazy as I am I control everything in mythtv with the remote control. I checked the following options but got neither to work:
1. using kdelirc to map shutdown to the power button. I could not figgure out here how to map a custom command to a button. I was able to map logout() to the power button which gave me the logout screen. But since I could not confirm anything with the remote it did not work.
2. using the exit option with in MythTV. In the setup->General one has the option to define a "Halt Command". I inserted here the "/sbin/shutdown -h now" command. The mythtv user is able to execute "/sbin/shutdown -h now". But it does not work. If I insert some application it does not get started either so I am sure the command does not get called upon exiting mythtv. Unfortunately this part is not documented at all.

if someone can bring some light in my dark world I would be really thankfull

HP

---

### Post by superm1 on 2006-11-02
> **hulluPeruna said:**
> Hi

I installed mythtv on my kubuntu box. Installing mythtv and the hardware was no problem. (big thank you to the ubuntu team).
But I am a little stuck configuring it so that I can shut it down via the remote. Lazy as I am I control everything in mythtv with the remote control. I checked the following options but got neither to work:
1. using kdelirc to map shutdown to the power button. I could not figgure out here how to map a custom command to a button. I was able to map logout() to the power button which gave me the logout screen. But since I could not confirm anything with the remote it did not work.
2. using the exit option with in MythTV. In the setup->General one has the option to define a "Halt Command". I inserted here the "/sbin/shutdown -h now" command. The mythtv user is able to execute "/sbin/shutdown -h now". But it does not work. If I insert some application it does not get started either so I am sure the command does not get called upon exiting mythtv. Unfortunately this part is not documented at all.

if someone can bring some light in my dark world I would be really thankfull

HP

HP,

Well if you are running a combined backend/frontend box, then you won't be able to shutdown when closing myth.  There is actually a third option available on frontend only boxes that is "close mythtv and shutdown machine" or something to that nature.

If this is a frontend only box, then you probably want to try launching myth with extra verbosity switches to see if you can find out why it won't launch that command.

Personally, I mapped the power button on my remote to execute a script that I wrote, turnoff_computer.sh

This script handles turning down my receiver volume, turning it off, calling /etc/acpi/sleep.sh, and then powering all the devices back on.

---

